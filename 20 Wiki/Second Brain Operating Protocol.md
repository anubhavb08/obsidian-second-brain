---
type: wiki
domain: codex_history
status: active
source_count: 0
last_reviewed: 2026-06-15
---

# Second Brain Operating Protocol

This page records how AB's Second Brain should be used with Codex, ChatGPT, Claude, Obsidian, and future project discussions.

## Core Agreement

The Second Brain is the visible long-term memory layer. It is not automatically updated after every chat.

Use this trigger when a discussion produces something worth keeping:

> Update Second Brain.

When this happens, the assistant should file the useful memory into the right area, update relevant links, and append a note to [[00 Control/log|Vault Log]].

## Context Trigger

Use this trigger when starting a new discussion that should use the vault:

> Use Second Brain context.

When this happens, the assistant should read [[00 Control/index|Vault Index]] first, then the relevant dashboard:

- [[Zlicc HQ]] and [[Zlicc Operating Layer]] for Zlicc work.
- [[Personal Growth Lab]] for personal growth, skills, and independent business ideas.
- [[Life Automation OS]] for routines, personal systems, and automations.

The Second Brain should ground the discussion, not limit it. The assistant can still inspect current project files, add fresh strategy, and make new recommendations.

## Filing Rules

When updating the Second Brain from a conversation, capture:

- Key decisions.
- Important context.
- Next actions.
- Open questions.
- Links to related wiki pages and raw sources.

If a point is uncertain, mark it as draft, assumption, candidate, or open question. Do not treat loose discussion as a finalized decision.

## Separation Rules

- Keep Zlicc work in [[Zlicc HQ]] and its related pages.
- Keep Personal Growth work in [[Personal Growth Lab]] and its related pages.
- Keep Life Automation work in [[Life Automation OS]].
- Keep [[Growth Automation Studio]] separate from Zlicc unless explicitly comparing.
- Treat `Zandem.ai` as a discussed candidate name only, not a finalized brand.

## Tool Integration Notes

### Codex

Codex can read and write the local vault when working inside the vault or when given the vault path. Use `Update Second Brain` for deliberate writes.

### ChatGPT Web

ChatGPT web does not automatically read the local Obsidian folder. It needs selected uploads, a cloud-backed copy, a connector, or a private repo mirror.

### Claude Desktop

Claude Desktop can potentially use local filesystem access through MCP, if configured. Access should be scoped to this vault and should follow the same `Update Second Brain` write rule.

### Obsidian App

Using the Obsidian app is helpful but not mandatory. Treat it as a control room for weekly review, browsing, and manual thinking. Day-to-day filing can happen through Codex.

## Dashboard Strategy

Dashboards should become actionable through live work, not decorative pages.

The next logical Zlicc move is:

1. Build the [[Zlicc Campaign Focus|Agency Tech Partner Stack]] campaign hub.
2. Create campaign tasks, proof requirements, outreach, and deck outline.
3. Then create or refine a Zlicc weekly command dashboard around that live campaign.

## Health Snapshot: 2026-06-15

- Markdown files: 65.
- Raw-source snapshots: 32.
- Wiki pages: 25.
- Wiki links: 362.
- Missing links: 0.
- Git status: local protocol update pending at review time.

Current strongest areas:

- Zlicc operating structure.
- Personal Growth skill memory.
- Cross-vault guardrails.

Current weakest area:

- [[Life Automation OS]] is still mostly a placeholder and needs real source material.
