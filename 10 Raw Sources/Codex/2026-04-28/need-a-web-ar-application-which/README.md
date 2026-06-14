# NutriMotion AR

A lightweight WebAR prototype for assigning healthy-eating animations to printed markers.

## What it does

- Lets you assign an animation to each available AR marker.
- Plays the assigned 3D animation when the marker is detected by the camera.
- Includes a no-camera preview mode for quick testing.
- Provides a printable marker sheet from the app.

## Included healthy-eating animations

- **Balanced Plate Orbit**: shows the half-plants, quarter-grains, quarter-protein meal idea.
- **Sugar Swap**: replaces a sugary drink with water.
- **Rainbow Bites**: uses colorful produce to encourage variety.

## Run locally

```bash
python3 -m http.server 5173
```

Then open:

```text
http://localhost:5173
```

Camera access works on `localhost` or HTTPS. If the camera does not appear, check browser camera permissions.

## Using markers

1. Open the app.
2. Click **Print marker sheet** and print the markers.
3. Pick a marker in the control panel.
4. Choose an animation.
5. Click **Assign to marker**.
6. Point your camera at the matching printed marker.

The app uses AR.js marker tracking. The current build supports Hiro, Kanji, and barcode markers 0-3. To use a fully custom image marker, generate an AR.js pattern marker for that image and add a matching `<a-marker>` entry in `index.html`.

## Healthy eating campaign ideas

- Put markers on cafeteria tables: each table reveals one habit.
- Add markers to lunch cards: scanning shows a plate-building challenge.
- Place a marker near drinks: scanning plays the water swap animation.
- Use rainbow produce cards: each scanned card can reveal a fruit or vegetable fact.
