# Devpost submission – copy each part into the matching field

## Project name (60 characters max)
Lumen Pop: Neon Symphony

## Elevator pitch (200 characters max)
A seated, hands-only VR rhythm game: poke glowing orbs to play a melody, grow the music and light show with every combo, and race your own ghost in the Daily Challenge.

## Track / Division
Gaming / New Experience

---

## About the project (paste everything between the lines)

---
## Inspiration
Most VR games ask for controllers, standing room and long sessions. We wanted the opposite: a game you can play on a bus seat or a sofa, in 60 seconds, with nothing but your hands. Then we asked a second question: what if every touch made music? Lumen Pop turns your index finger into an instrument.

## What it does
Glowing orbs bloom within a two-foot radius in front of you. Poke a cyan orb and it plays the next note of a melody, so a combo literally becomes a tune. Gold orbs play a chord and score more. Dark red orbs break the music and cost points.

The soundtrack grows with your skill: at combo x5 hi-hats join in, at x10 a bass line kicks in and the sky starts a light show, at x20 an arpeggio takes over and the tempo keeps rising. Miss and the music strips back down.

**Modes**
- **Classic 60s**: a fast, score-chasing round.
- **Zen**: no timer, no hazards, a calmer tempo.
- **Daily Challenge**: the same orb sequence for every player each day. Your best run of the day is replayed as a ghost hand and a live ghost score, so every retry is a race against yourself.

**Options**
- **Look & Pinch**: look at an orb (a reticle shows your aim) and pinch thumb and index finger to pop it. You can play without reaching at all.
- **Large targets**: bigger, slower, longer-lived orbs.

## How we built it
- **WebXR + three.js r160** in a single static `index.html`, no build step, hosted on GitHub Pages.
- **WebXR Hand Input API**: the `index-finger-tip` joint for poking, and the distance between `thumb-tip` and `index-finger-tip` (with hysteresis) for pinching.
- **Head gaze** from the XR camera, with an angular tolerance and a visible reticle, for Look & Pinch.
- **Web Audio API** for all sound: oscillators for notes and chords, filtered noise for hi-hats, pitch-swept kicks, and a look-ahead scheduler that keeps the beat in time while the tempo follows your combo. There are no audio files to download.
- **Seeded random generator** keyed by date so every player gets the same daily orb sequence.
- **localStorage** for best scores and the daily ghost, which is stored as a short list of pop times and positions.
- Canvas textures for text panels (redrawn only when the text changes, to keep frame rates high on Quest), and a mouse and keyboard fallback for desktop preview.

## Challenges we ran into
- **Keeping everything reachable while seated.** We re-anchor the play space to the player's head at the start of every round, so orbs always appear in front of you, whichever way you sit.
- **Making pokes feel fair.** Hand tracking jitters, so the hit test adds a small tolerance to each orb's radius and ignores orbs that are still growing in.
- **Pinches that don't double-fire.** A pinch triggers below 1.8 cm between thumb and index tip and only re-arms above 3.5 cm.
- **Music that never drifts.** Notes are scheduled slightly ahead on the audio clock instead of the frame clock, so the beat stays steady even when the frame rate dips.

## Accomplishments that we're proud of
A complete hands-only experience, from menu to restart, with no controller at any point. Rounds take 60 seconds, the game loads almost instantly, there are two ways to play (touch, or look and pinch), and a music system makes every run feel like a small performance.

## What we learned
Hands remove the gap between wanting to play and playing. Sound turns out to be the best feedback for hand input: when every touch makes a note, players stop thinking about the controls and start playing for the music.

## What's next for Lumen Pop: Neon Symphony
- An online daily leaderboard, and racing a friend's ghost instead of only your own.
- True eye tracking for Look & Pinch on devices that expose it.
- Two-player duet mode, where two players build one song together.
- Unlockable instruments and color themes earned through combos.
---

## Built with (add each as a separate tag)
javascript, html5, three.js, webxr, webxr-hand-input, web-audio-api, github-pages, meta-quest

## "Try it out" links
1. Your GitHub Pages URL, for example `https://YOUR-USERNAME.github.io/lumen-pop/`
2. Your GitHub repository URL, for example `https://github.com/YOUR-USERNAME/lumen-pop`

## Image gallery (3:2 ratio, under 5 MB each)
Take these screenshots in the headset (or record a video and grab frames):
1. The main menu with the mode orbs.
2. A hand poking a cyan orb mid-combo.
3. The light show at combo x10 ("SYMPHONY x10!").
4. Look & Pinch mode with the reticle on an orb.
5. Daily Challenge with the ghost hand and ghost score visible.
6. The end screen showing "You beat your ghost!".

---

# Demo video script (under 3 minutes)

| Time | On screen | Voice-over |
|---|---|---|
| 0:00–0:10 | Title card "Lumen Pop: Neon Symphony", then the in-headset menu | "This is Lumen Pop: a seated VR game you play with nothing but your hands." |
| 0:10–0:25 | Show both hands, no controllers; poke "Classic 60s" | "No controllers, no standing. Just poke to start." |
| 0:25–1:15 | Classic gameplay: build a combo, hit a gold orb, reach x10 and the light show, then hit a dark red orb | "Every orb is a note. Your combo becomes a melody, and the music grows: hi-hats, then bass, then a light show. Hit a dark red orb and the music breaks." |
| 1:15–1:45 | Daily Challenge with the ghost hand racing you; end screen "You beat your ghost!" | "The Daily Challenge gives everyone the same orbs each day, and your best run comes back as a ghost to race." |
| 1:45–2:10 | Turn on Look & Pinch: look at orbs and pinch | "Look & Pinch lets you aim by looking and pop with a pinch, so you can play without reaching." |
| 2:10–2:30 | Zen mode and Large targets | "Zen mode and Large targets make it relaxing and accessible." |
| 2:30–2:50 | Back to the menu, end card | "Seated, 60 seconds, hands only, built with WebXR and live procedural music. Lumen Pop: Neon Symphony." |

Upload to YouTube as **Public** (or Unlisted if the rules allow it) and paste the link into the video field.

---

# Pre-submission checklist
- [ ] Repository is public and contains `index.html`, `.nojekyll`, `README.md`
- [ ] GitHub Pages is on, and the https URL opens in the Meta Quest Browser
- [ ] Tested in the headset with hands only: menu, all three modes, both toggles, and a Daily Challenge played twice (so the ghost appears)
- [ ] Video is public and under 3 minutes
- [ ] Screenshots uploaded (3:2 ratio)
- [ ] All Devpost fields filled in and submitted before the deadline (Nov 18)
