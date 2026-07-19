# Ace Coach — Tennis Stroke Trainer

A single-page PWA that watches a tennis swing through the phone camera
(MediaPipe pose estimation), detects **forehand / backhand**, and gives spoken,
one-cue-at-a-time coaching on stance, shoulder turn, contact point, arm
extension, follow-through and posture. No build step, no dependencies to install
— everything loads from a CDN at runtime.

## Files

| File | Purpose |
|------|---------|
| `index.html` | The whole app (camera, pose, coaching engine, UI). |
| `manifest.webmanifest` | Makes it installable as a home-screen app. |
| `sw.js` | Service worker — offline relaunch + faster second load. |
| `icon-*.png`, `apple-touch-icon.png` | App icons. | Optional Colab pipeline: app samples → Keras `.h5` → TensorFlow.js. |

## Install on the phone

Open the Pages URL on the phone, then:

- **Android / Chrome:** menu (⋮) → *Add to Home screen* / *Install app*.
- **iPhone / Safari:** Share → *Add to Home Screen*.

Launch it from the home-screen icon and it runs full-screen like a native app.

## Using it

1. Tap **Start camera** and allow access. First launch downloads the pose model
   (a few MB) from the jsDelivr CDN — after that the service worker keeps it cached.
2. In **Settings** (gear icon), set the **racket hand** and **backhand style**,
   and adjust **sensitivity** (lower for a small child / gentle swings).
3. Prop the phone up, stand back so the **whole body is in frame**, face the
   camera, and swing. The coach scores each swing and speaks one fix.

The coloured dots on the skeleton (knees, elbow, posture) update live, so posture
feedback is continuous — not only after a completed swing.


## Notes

- Evaluation assumes a **front-facing** setup (child faces the propped phone and
  turns to swing). A single 2D camera can't judge rotation well from a pure side
  view; a dedicated side-view mode can be added if wanted.
- Bump the `CACHE` version string in `sw.js` whenever you edit shell files, so
  installed copies pick up the update.
