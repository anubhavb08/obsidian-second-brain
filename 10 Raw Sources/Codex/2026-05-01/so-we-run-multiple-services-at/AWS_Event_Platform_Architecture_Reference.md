# AWS Event Platform Architecture Reference

Date: 2026-05-02  
Prepared for: Multi-application virtual events, live streaming, engagement, and analytics platform

## 1. Executive Summary

The current platform should not be treated as only a live streaming system. It is a broader event-driven SaaS platform with:

- Live video delivery.
- Audience engagement: Q&A, polls, quizzes, reactions, presence, attendance.
- Multiple event-triggered applications.
- Customer-facing dashboards.
- A future analytics and ROI engine.

The recommended target is a hybrid, event-driven AWS architecture:

```text
Route 53
  -> CloudFront
  -> ALB / NLB / API Gateway

Compute
  -> Lambda for lightweight event-triggered workloads
  -> ECS Fargate for longer-running app services and WebSocket services
  -> EC2 Auto Scaling or ECS on EC2 for heavy streaming-specific workloads

Data
  -> DynamoDB for bursty interaction writes
  -> Redis / ElastiCache for live counters, presence, leaderboards, reactions
  -> Aurora / PostgreSQL for relational tenant, event, and business data

Messaging
  -> SQS for queues
  -> EventBridge for app-to-app communication

Analytics
  -> Common event collector
  -> Kinesis Data Firehose
  -> S3 data lake
  -> Glue Data Catalog
  -> Athena first
  -> Redshift Serverless later if needed
  -> QuickSight or custom embedded customer dashboard
```

The best direction is not a pure Fargate migration. It is a hybrid model where each workload uses the right compute option.

## 2. Current State

Current structure:

```text
BigRock DNS with manually entered IPs
  -> EC2 instance running Nginx as load balancer
  -> EC2 application/services
  -> CloudFront for delivery
  -> S3 for storage
```

Known current CloudFront details:

- CloudFront cost is roughly USD 0.03 per GB.
- Average traffic is roughly 10 TB per month.
- Monthly CloudFront delivery cost is approximately:

```text
10 TB x 1024 GB x USD 0.03 = USD 307/month
```

Since CloudFront will remain similar across options, this document excludes CloudFront from compute comparison.

## 3. Current Risks

The main risk is not CloudFront cost. The main risks are platform reliability, manual operations, and inefficient scaling.

Current risks:

- DNS is manually managed in BigRock.
- Public traffic is tied to EC2 public IPs.
- Nginx on EC2 is acting as the public load balancer.
- Event capacity is manually estimated and resized.
- Failover depends on manual intervention.
- Multiple applications are not cleanly decoupled.
- Engagement spikes can overload the primary database if every interaction is handled synchronously.
- Analytics is not yet standardized across all applications.

For a do-it-yourself event SaaS product, these risks become bigger as customers create more events without your team manually preparing infra.

## 4. Target Design Principles

1. Keep idle cost low.
2. Scale automatically during events.
3. Avoid manual DNS/IP changes.
4. Separate video delivery from engagement traffic.
5. Decouple applications using events and queues.
6. Use a common event schema for analytics.
7. Keep the analytics pipeline separate from the transactional application database.
8. Build customer dashboards around journey and ROI, not isolated app metrics.

## 5. Traffic Separation

The platform has two very different traffic types.

| Traffic Type | Characteristics | Recommended Layer |
|---|---|---|
| Video delivery | High bandwidth, cacheable, CDN-heavy | CloudFront + S3/media origin |
| Engagement/app traffic | Low bandwidth, high concurrency, write-heavy, real-time | API Gateway/ALB/WebSocket + DynamoDB/Redis |

Video delivery should not be mixed with app/API compute where possible.

## 6. Compute Options Compared

### Option 0: Current EC2 + Nginx Load Balancer

Architecture:

```text
BigRock DNS
  -> EC2 public IP
  -> Nginx on EC2
  -> EC2 app services
```

Pros:

- Lowest migration effort.
- Familiar and flexible.
- EC2 can be cheaper than Fargate for always-on workloads.
- Nginx can handle custom routing if required.

Cons:

- Manual DNS/IP management.
- Nginx load balancer is self-managed and can become a single point of failure.
- Manual scaling before events.
- Higher operational burden.
- Harder to automate for a DIY SaaS model.
- Failover and health checks need custom engineering.

Best fit:

- Short-term baseline only.
- Internal or low-criticality services.
- Workloads where migration cannot happen immediately.

Approximate compute cost profile, excluding CloudFront:

| Scale | Estimate |
|---|---:|
| Small | USD 200-800/month |
| Medium | USD 800-3,000/month |
| Large | Risky without major redesign |

### Option 1: EC2 + Route 53 + Managed ALB/NLB

Architecture:

```text
Route 53
  -> ALB for HTTP/HTTPS APIs and web apps
  -> NLB for TCP/RTMP/WebSocket-heavy ingress if needed
  -> EC2 app services
```

Pros:

- Removes manual IP dependency.
- Improves health checks and failover.
- Keeps application changes low.
- Good transitional architecture.
- EC2 remains cost-efficient for steady workloads.

Cons:

- Still EC2-heavy.
- Still requires patching, AMI management, capacity planning, scaling policies.
- Scaling is not as granular as Lambda or Fargate.
- Some idle capacity remains.

Best fit:

- First migration step.
- Existing services that are difficult to containerize immediately.
- Heavy workloads that are already optimized on EC2.

Approximate compute/platform cost, excluding CloudFront:

| Scale | Estimate |
|---|---:|
| Small | USD 300-1,200/month |
| Medium | USD 1,000-4,000/month |
| Large | USD 4,000-15,000/month |

### Option 2: EC2 Auto Scaling + ALB/NLB

Architecture:

```text
Route 53
  -> ALB/NLB
  -> EC2 Auto Scaling Groups
```

Pros:

- Better than manual resizing.
- Cost-effective for predictable or heavy workloads.
- Works well with reserved instances or Compute Savings Plans.
- Good for streaming workers or protocol-specific services.

Cons:

- Still manages servers.
- Scaling takes longer than Lambda and can be slower than Fargate task scaling.
- Requires good autoscaling policies.
- Idle baseline capacity still costs money.

Best fit:

- Heavy streaming-origin services.
- Long-running services with steady baseline load.
- Services needing host-level tuning.

Approximate compute/platform cost, excluding CloudFront:

| Scale | Estimate |
|---|---:|
| Small | USD 350-1,500/month |
| Medium | USD 1,200-5,000/month |
| Large | USD 5,000-20,000/month |

### Option 3: ECS on EC2

Architecture:

```text
Route 53
  -> ALB/NLB
  -> ECS cluster backed by EC2 instances
  -> Containerized services
```

Pros:

- Containers improve deployment and service isolation.
- Cheaper than Fargate at high utilization.
- Better packing of multiple applications onto shared EC2 capacity.
- Good bridge between old EC2 and modern containers.

Cons:

- You still manage EC2 cluster capacity.
- Requires ECS operational maturity.
- Capacity fragmentation can happen if tasks are not sized well.

Best fit:

- Many always-on or semi-steady services.
- Workloads where Fargate is too expensive at scale.
- Teams comfortable managing cluster capacity.

Approximate compute/platform cost, excluding CloudFront:

| Scale | Estimate |
|---|---:|
| Small | USD 400-1,500/month |
| Medium | USD 1,200-5,500/month |
| Large | USD 5,000-18,000/month |

### Option 4: ECS Fargate Hybrid

Architecture:

```text
Route 53
  -> ALB/API Gateway
  -> ECS Fargate services
  -> SQS/EventBridge
  -> DynamoDB/Redis/Aurora
```

Pros:

- No EC2 server management.
- Good for bursty applications.
- Per-service autoscaling.
- Better isolation across the 10 applications.
- Strong fit for SaaS application services and engagement services.

Cons:

- More expensive than EC2 for always-on high-utilization workloads.
- Requires containerization.
- Costs can increase if services are oversized or left running 24x7.
- NAT Gateway, public IPv4, logs, and ALB can add hidden costs.

Best fit:

- Customer dashboards.
- Admin apps.
- App APIs.
- Long-running WebSocket/engagement services.
- Services that need more control than Lambda but less server management than EC2.

Approximate compute/platform cost, excluding CloudFront:

| Scale | Estimate |
|---|---:|
| Small | USD 500-2,000/month |
| Medium | USD 1,500-7,000/month |
| Large | USD 7,000-25,000/month |

### Option 5: Serverless First

Architecture:

```text
Route 53
  -> API Gateway
  -> Lambda
  -> DynamoDB
  -> SQS/EventBridge
  -> Firehose/S3/Athena
```

Pros:

- Lowest idle cost.
- Excellent for event-triggered applications.
- Scales automatically.
- Good for webhooks, lead sync, notifications, data ingestion, lightweight APIs.
- Strong fit for DIY SaaS where events appear and disappear.

Cons:

- API Gateway and Lambda costs rise with very high request volume.
- Cold starts need attention for latency-sensitive APIs.
- Lambda has duration/runtime limits.
- Not ideal for long-running WebSockets or heavy streaming workers.
- Distributed debugging is more complex.

Best fit:

- Lead sync.
- Lead pulse triggers.
- Webhooks.
- Notifications.
- Analytics event ingestion.
- Lightweight APIs.
- Background jobs.

Approximate compute/platform cost, excluding CloudFront:

| Scale | Estimate |
|---|---:|
| Small | USD 200-1,500/month |
| Medium | USD 800-5,000/month |
| Large | USD 5,000-25,000/month |

### Option 6: Recommended Hybrid Platform

Architecture:

```text
Route 53
  -> CloudFront
  -> ALB/NLB/API Gateway

Lambda
  -> triggers, webhooks, lightweight jobs, event collector

ECS Fargate
  -> app services, dashboards, WebSocket/engagement services

EC2 Auto Scaling / ECS on EC2
  -> heavy streaming-specific workloads only

SQS/EventBridge
  -> app-to-app communication

DynamoDB/Redis/Aurora
  -> engagement and business data

Firehose/S3/Athena/Redshift
  -> analytics and ROI engine
```

Pros:

- Best balance of cost, reliability, and automation.
- Low idle cost for bursty workloads.
- Keeps EC2 only where it has a cost or technical advantage.
- Supports DIY event creation.
- Supports shared analytics across applications.
- Avoids one-size-fits-all architecture.

Cons:

- More architecture discipline required.
- Requires standard event schema and service boundaries.
- Requires observability across multiple managed services.
- Migration needs phased execution.

Best fit:

- Your described business model.
- Multiple event-triggered applications.
- Live engagement plus video.
- Customer-facing ROI analytics.

Approximate compute/platform cost, excluding CloudFront:

| Scale | Estimate |
|---|---:|
| Small | USD 700-2,500/month |
| Medium | USD 2,000-8,000/month |
| Large | USD 8,000-30,000/month |

## 7. Compute Cost Model

The exact monthly bill depends on:

- Number of services.
- Number of always-on services.
- Event count per month.
- Average and peak concurrent users.
- Request volume.
- WebSocket connection minutes.
- Database writes/reads.
- Analytics event volume.
- Log volume.
- NAT/public IPv4 usage.
- Region and Savings Plan commitments.

Planning formula:

```text
Total platform cost excluding CloudFront =
  Load balancing and API cost
  + compute cost
  + database cost
  + queue/event bus cost
  + cache cost
  + analytics ingestion/storage/query cost
  + logs/monitoring
```

### Example Assumption

For the 10 applications:

```text
Baseline: 2 units of 4 vCPU / 8 GB always available
Peak: 8 units during event windows
Event compute window: 60 hours/month
```

Rough comparison:

| Compute Model | Rough Monthly Compute + Front Door Cost |
|---|---:|
| Current EC2 + Nginx | USD 180-500 |
| EC2 Auto Scaling + ALB/NLB | USD 205-650 |
| ECS on EC2 + ALB | USD 225-750 |
| Fargate always-on minimum + event scale | USD 225-850 |
| Fargate event-only/scale-low | USD 105-500 |
| Lambda/API Gateway for triggers | USD 30-300 at low/medium request volume |
| Hybrid Fargate + Lambda | USD 200-800 |

This example is intentionally compute-focused. It excludes CloudFront and assumes database/analytics are estimated separately.

## 8. Workload Placement Recommendation

| Workload | Recommended Compute |
|---|---|
| Event setup | Lambda |
| Webhooks | Lambda |
| Lead sync triggers | Lambda |
| Notifications | Lambda + SQS |
| Lightweight APIs | Lambda + API Gateway |
| Customer dashboards | Fargate or Lambda |
| Admin apps | Fargate |
| Poll APIs | Lambda or Fargate |
| Quiz APIs | Lambda or Fargate |
| Q&A | Lambda/Fargate + DynamoDB |
| Emoji reactions | API + Redis + async persistence |
| Live presence | Redis or DynamoDB with TTL |
| WebSocket engagement service | ECS Fargate |
| Heavy streaming/origin workers | EC2 Auto Scaling or ECS on EC2 |
| Analytics event collector | Lambda or small Fargate service |
| Background processing | SQS + Lambda first, Fargate workers if heavy |

## 9. Engagement Layer Architecture

Engagement features should not directly overload the primary relational database.

Recommended flow:

```text
User action
  -> API Gateway / ALB / WebSocket
  -> Lambda or Fargate service
  -> DynamoDB for durable interaction record
  -> Redis for live counters/presence/leaderboards
  -> EventBridge or Firehose for analytics event
  -> WebSocket broadcast back to attendees
```

Feature mapping:

| Feature | Recommended Design |
|---|---|
| Q&A | Write to DynamoDB/Aurora, moderation queue, broadcast approved questions |
| Polls | Store vote, aggregate in Redis, persist final result |
| Quizzes | Store answers, Redis leaderboard, async scoring/reporting |
| Emoji reactions | Aggregate in Redis, batch persist to analytics |
| Attendance | Session events to analytics lake, presence in Redis/DynamoDB TTL |
| CTA clicks | Track as analytics events and lead score inputs |

## 10. App-to-App Communication

The 10 applications should communicate through events wherever possible.

Recommended pattern:

```text
Application A emits event
  -> EventBridge
  -> Application B consumes event
  -> Analytics collector also receives event
```

Example events:

```text
registration.completed
attendee.joined_event
attendee.watched_session
poll.vote_submitted
quiz.answer_submitted
question.asked
cta.clicked
lead.score_updated
followup.created
```

Benefits:

- Applications are decoupled.
- Adding new applications becomes easier.
- Analytics becomes consistent.
- Customer journey can be reconstructed from events.

## 11. Analytics and ROI Engine

The analytics engine should be built around a common event schema.

Example event:

```json
{
  "tenant_id": "customer_123",
  "event_id": "event_456",
  "user_id": "user_789",
  "session_id": "session_abc",
  "app": "quiz",
  "event_type": "answer_submitted",
  "timestamp": "2026-05-02T10:30:00Z",
  "properties": {
    "question_id": "q1",
    "answer": "B",
    "is_correct": true
  }
}
```

Recommended analytics pipeline:

```text
Frontend/backend event
  -> Event Collector API
  -> Kinesis Data Firehose
  -> S3 raw data lake
  -> Optional transformation to Parquet
  -> Glue Data Catalog
  -> Athena for low-cost ad hoc queries
  -> Redshift Serverless for heavier dashboards
  -> QuickSight or custom embedded dashboard
```

Start with S3 + Athena. Add Redshift Serverless only when dashboards become heavy, frequent, or customer-facing at scale.

## 12. Customer Dashboard Model

The dashboard should summarize the entire customer journey, not just isolated product features.

Recommended sections:

| Dashboard Area | Metrics |
|---|---|
| Registration | registrations, source, campaign, drop-offs |
| Attendance | joins, unique attendees, peak concurrency, attendance rate |
| Video | watch time, completion rate, session drop-off |
| Engagement | poll votes, quiz attempts, Q&A, reactions |
| Lead Quality | engagement score, intent score, CTA clicks |
| Content Performance | best session, best speaker, highest drop-off |
| Journey Timeline | user-level actions across all apps |
| ROI | cost per attendee, cost per qualified lead, conversion value |

ROI formula examples:

```text
Cost per attendee = event cost / attended users
Cost per qualified lead = event cost / qualified leads
Engagement rate = engaged users / attended users
Lead score = weighted sum of watch time, poll answers, quiz score, Q&A, CTA clicks
Pipeline ROI = attributed pipeline value / event cost
```

## 13. Recommended Migration Plan

### Phase 1: Stabilize the Front Door

Actions:

- Keep domain registration at BigRock if preferred.
- Create Route 53 hosted zone.
- Point BigRock nameservers to Route 53.
- Move records to Route 53.
- Use aliases to CloudFront, ALB, and NLB.

Outcome:

- No more manual EC2 IP updates.
- Safer failover and routing.

### Phase 2: Replace Public Nginx Load Balancing

Actions:

- Add ALB for HTTP/HTTPS app traffic.
- Add NLB if TCP/RTMP/protocol-heavy ingest is needed.
- Keep Nginx only behind ALB/NLB if custom routing is required.

Outcome:

- Managed health checks.
- Better availability.
- Lower operational risk.

### Phase 3: Introduce Event Backbone

Actions:

- Add EventBridge for app-to-app events.
- Add SQS for async jobs.
- Define canonical event names and schemas.

Outcome:

- Applications become decoupled.
- Analytics starts becoming standardized.

### Phase 4: Move Bursty Apps to Lambda/Fargate

Actions:

- Move lightweight triggers to Lambda.
- Move heavier services to ECS Fargate.
- Keep heavy streaming-specific components on EC2 Auto Scaling or ECS on EC2.

Outcome:

- Lower idle cost.
- Automated scaling.
- Less manual event preparation.

### Phase 5: Build Analytics Lake

Actions:

- Build event collector.
- Send normalized events to Firehose.
- Store raw and curated data in S3.
- Query initially with Athena.
- Add Redshift Serverless when dashboard load justifies it.

Outcome:

- Unified customer analytics.
- Foundation for ROI reporting.

### Phase 6: Customer ROI Dashboard

Actions:

- Build dashboard around journey and ROI.
- Expose tenant/event-level analytics.
- Add lead scoring and campaign attribution.

Outcome:

- Analytics becomes a product feature, not just internal reporting.

## 14. Final Recommendation

Recommended target:

```text
Route 53 + CloudFront + ALB/NLB/API Gateway
+ Lambda for triggers
+ ECS Fargate for app services
+ EC2/ECS-EC2 only for heavy streaming workloads
+ DynamoDB/Redis for live engagement
+ SQS/EventBridge for app communication
+ S3/Athena/Redshift analytics layer
```

The immediate priority should be:

1. Route 53.
2. Managed ALB/NLB.
3. EventBridge/SQS.
4. Lambda/Fargate for bursty apps.
5. DynamoDB/Redis for engagement.
6. Firehose/S3/Athena analytics foundation.
7. Redshift/QuickSight/custom dashboard when customer-facing analytics scales.

This balances automation, cost control, reliability, and product maturity.

## 15. AWS Pricing and Documentation References

Pricing changes over time. Use these pages as the live source of truth:

- AWS Fargate pricing: https://aws.amazon.com/fargate/pricing/
- AWS Lambda pricing: https://aws.amazon.com/lambda/pricing/
- Amazon API Gateway pricing: https://aws.amazon.com/api-gateway/pricing/
- Amazon ECS pricing: https://aws.amazon.com/ecs/pricing/
- Elastic Load Balancing pricing: https://aws.amazon.com/elasticloadbalancing/pricing/
- Amazon Route 53 pricing: https://aws.amazon.com/route53/pricing/
- Amazon DynamoDB on-demand pricing: https://aws.amazon.com/dynamodb/pricing/on-demand/
- Amazon SQS pricing: https://aws.amazon.com/sqs/pricing/
- Amazon EventBridge pricing: https://aws.amazon.com/eventbridge/pricing/
- Amazon Data Firehose pricing: https://aws.amazon.com/kinesis/data-firehose/pricing/
- Amazon ElastiCache pricing: https://aws.amazon.com/elasticache/pricing/
- Amazon Athena pricing: https://aws.amazon.com/athena/pricing/
- Amazon Redshift pricing: https://aws.amazon.com/redshift/pricing/
- Amazon QuickSight pricing: https://aws.amazon.com/quicksight/pricing/
- Amazon CloudFront pricing: https://aws.amazon.com/cloudfront/pricing/

