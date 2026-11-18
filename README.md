# Lumen Pop: Neon Symphony

A seated, hands-only WebXR rhythm game for Meta Quest. Poke glowing orbs to play music: every pop plays the next note of a melody, and your combo adds layers to the soundtrack and a light show to the sky.

Track: **Gaming**. Division: **New Experience**.

**Play:** open the hosted `index.html` link in the Meta Quest Browser and tap **Enter VR**. On desktop, click the orbs with the mouse (press Space to pinch in Look & Pinch mode).

## How it maps to the competition requirements

| Requirement | How Lumen Pop meets it |
|---|---|
| Hands-first, end-to-end with no controller | Two hand inputs, both through the WebXR Hand Input API: an index-fingertip poke (`index-finger-tip` joint) and a thumb-to-index pinch (`thumb-tip` + `index-finger-tip`). Menu, mode choice, settings, gameplay and restart all work with hands only. |
| Eyes and hands | **Look & Pinch** mode: aim at an orb by looking at it (head gaze, shown with a reticle) and pinch to pop it. No reaching needed. |
| Seated, two-foot radius ("airplane seat test") | Orbs spawn 0.38–0.55 m in front of the head, within ±0.3 m horizontally and ±0.17 m vertically. The play space re-anchors to the head at session start and at every round start. |
| 10 minutes or less, fast cold start ("bus stop test") | One round is 60 seconds. No asset downloads: shapes are primitives and all music is generated live with the Web Audio API. |
| Original, not a wrapper | All gameplay, scoring, music and UI are written for this project. No third-party service is used. |
| Accessibility | Large targets mode (bigger, slower, longer-lived orbs), Look & Pinch for players with limited reach, a no-timer Zen mode with no hazards, audio for every pop, and shape plus color differences between hazards and rewards. |
| Reason to come back | Daily Challenge (same orb sequence for everyone each day) with a ghost hand that replays your best run of the day, combo scoring and a saved best score per mode. |
| First five minutes | A mode menu appears immediately, with an in-game tip on the first play. |

## Modes and options
- **Classic 60s**: score as much as you can; dark red orbs cost 30 points and break the music.
- **Zen**: no timer, no hazards, calmer tempo; finish whenever you like.
- **Daily Challenge**: seeded by the date. Your best run of the day is saved on your device and replayed as a ghost hand and ghost score on your next attempt.
- **Large targets** (toggle): bigger, slower orbs.
- **Look & Pinch** (toggle): look at an orb, pinch to pop it. Poking still works.

## Symphony system
- Each cyan pop plays the next note of a C-major pentatonic scale, so a combo becomes a melody. Gold orbs play a chord.
- Combo x5 adds hi-hats, x10 adds a bass line and starts the light show, x20 adds an arpeggio. The tempo rises with the combo.
- Every x10 milestone flashes the sky and fires rings of light. A dark red orb or a missed orb resets the combo and strips the music back.

## Tech
three.js r160 (WebXR) loaded from jsDelivr, a single static `index.html`, no build step. Web Audio API for all sound (oscillators, filtered noise, scheduled beats). `localStorage` for best scores and the daily ghost.

## Deploy (GitHub Pages)
Upload `index.html`, `.nojekyll` and `README.md` to a public repository, then enable Settings > Pages > Deploy from branch `main` / root.

## Automated checking
`window.lumen` exposes `state`, `score`, `mode`, `combo`, `musicLevel`, `largeTargets`, `lookAndPinch` and `ghostScore`.
