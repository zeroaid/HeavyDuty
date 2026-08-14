# Heavy Duty

A Mike Mentzer HIT workout tracker. Log, track and analyse your Heavy Duty training — built as a single-file PWA with a native Android wrapper. No account, no server, no subscriptions.

**[Open the app →](https://zeroaid.github.io/HeavyDuty/)**

---

## What is Heavy Duty?

Heavy Duty is Mike Mentzer's High Intensity Training methodology — brief, brutal, and basic. One working set per exercise, taken to absolute muscular failure, with full recovery between sessions. No junk volume, no guesswork.

This app gives you everything you need to follow the system. Consolidated and Legacy splits with a full exercise library, progressive overload tracking, rest-pause logging, exercise variations, custom workouts, and an in-app guide with form cues and Mentzer quotes for every movement. Log your active recovery sessions with photos and let Claude pull your equipment stats (distance, speed, heart rate, calories) straight from the display. AI-powered training analysis, overload trends and HIT-specific coaching — all running locally in your browser with your own API key.

---

## Features

### Workout Tracking
- **Workout logging** — full Heavy Duty exercise library covering HD I, HD II, HIT Mentzer Way and Consolidated routines, plus custom workouts
- **Exercise variations** — for exercises like Pec Deck / Dumbbell Flyes, pick which variation you actually performed
- **Progressive overload** — see your last performance on every exercise before you lift
- **Rest-pause support** — log RP clusters the way Mentzer prescribed
- **Workout history** — full session log with calendar view and date filtering
- **Exercise guide** — form cues, technique notes and Mentzer quotes for every movement

### Active Recovery
- **Recovery logging** — log light cardio and movement sessions between heavy training days
- **Photo capture** — attach a photo to each session via camera or gallery
- **AI photo analysis** — Claude identifies the activity, heart rate zone, duration and recovery observations
- **Equipment stats** — reads distance, speed, heart rate and calories directly from equipment displays, converting to your preferred unit system on the fly
- **Bulk import** — import multiple sessions at once from your camera roll
- **Duplicate detection** — SHA-256 fingerprinting so the same photo can't be imported twice
- **Re-analyse** — re-run AI analysis on any session or all sessions at once
- **Filtering** — filter by activity type, zone, time of day or month

### AI Insights
- **Training analysis** — Claude-powered deep-dive into your workout history, progressive overload trends and recovery patterns
- **HIT-specific coaching** — analysis framed around Heavy Duty principles, not generic fitness advice
- **Mentzer's Verdict** — modify a built-in workout and Claude analyses your changes through the lens of Heavy Duty principles
- **Athlete profile** — age, training history, goal and lifestyle factors fed into every analysis
- **API key management** — bring your own Anthropic key, stored only in `localStorage`

### Data & Backup
- **JSON backup / restore** — full export including workouts, recovery logs, photos and athlete profile
- **Google Drive auto-backup** — syncs after every save, surfaces a reconnect prompt when the session expires
- **IndexedDB photo storage** — no localStorage quota limits
- **Auto migration** — existing photos move from localStorage to IndexedDB on first launch

### App
- **Offline-first PWA** — works without a connection once installed
- **Native Android app** — TWA with branded splash screen, black nav bar, no browser chrome
- **Metric / Imperial** — switch between kg and lbs in Settings; weights, AI analysis and recovery stats all convert on the fly
- **Calendar view** — monthly overview of training and recovery sessions
- **Dark theme** — high-contrast UI optimised for gym and outdoor lighting
- **User manual** — in-app help accessible from Settings
- **Reps validation** — can't save a workout with missing reps

---

## Install

### Browser (PWA)
Visit **[zeroaid.github.io/HeavyDuty](https://zeroaid.github.io/HeavyDuty/)** and tap *Add to Home Screen*.

### Android (native TWA)
Grab the latest `app-release.apk` from [Releases](https://github.com/zeroaid/HeavyDuty/releases), enable *Install unknown apps* in your Android settings and install.

> The TWA uses Digital Asset Links for verification. Once Chrome verifies the app, the URL bar disappears and it runs fully native with a black system nav bar.

---

## AI Insights setup

The AI tab uses the [Anthropic Claude API](https://console.anthropic.com/). You supply your own key — it's stored in your browser's `localStorage` and only ever sent directly to Anthropic's API.

1. Get an API key at [console.anthropic.com](https://console.anthropic.com/)
2. Open the app → Insights tab → paste your key

---

## Data & privacy

- All workout and recovery data stored in `localStorage`
- Photos stored in `IndexedDB`
- No server, no account, no analytics
- Export your data any time via Settings → Export JSON Backup
- Optional Google Drive backup — stores one JSON file in your own Drive account
- Your Claude API key never leaves your device

---

## Tech stack

| Layer | Detail |
|---|---|
| App | Single-file HTML/CSS/JS (`index.html`) |
| Hosting | GitHub Pages |
| PWA | Service worker (`sw.js`), Web App Manifest |
| Android | Trusted Web Activity via `android-browser-helper` |
| AI | Anthropic Claude API (`claude-opus-4-8`) — raw `fetch` |
| Storage | `localStorage` + `IndexedDB` (photos) |
| Build | GitHub Actions (TWA APK signing + release) |

---

## Changelog

### v1.6.0
- History stats replaced with progression-based insight — PBs (personal bests) This Month and Improved vs Last replace the old frequency stats (This Month / Avg Gap / Longest Gap); both tiles drill down into a sheet listing the underlying exercises, tapping through to that exercise's full history chart
- History heatmap replaced with a collapsible mini-calendar — defaults to collapsed, with inline month navigation, Today link, and training days colour-coded red for Consolidated / grey for Legacy; tap a day to jump to that session, tap the month label to open the full calendar
- Active Recovery gets its own collapsible mini-calendar, same pattern as History — tap a day to open that recovery session's detail
- Consolidated Method now auto-expands on the History screen by default; Legacy stays collapsed
- Renamed PRs to PBs (personal bests) across History UI text
- Fixed stale version number in Settings — two hardcoded version strings (footer and About row) could drift out of sync; both now read from a single APP_VERSION constant
- Android APK version bumped to match

### v1.5.0
- Per-exercise history — tap any exercise name or pill to see its own progress chart, stats (current/change/low/high), and every logged session, matching the Strong/Hevy pattern of drilling into a single exercise
- Body weight history — tap the BW stat on the home screen for a range-filterable chart (1M/3M/6M/1Y/All) with a touch crosshair, same chart engine reused for exercise history
- Tap the "Next Workout" title on the home screen to jump straight to your last session of that same workout
- Full-screen photo lightbox on recovery entries, reworked with pinch-to-zoom, pan, and double-tap gestures matching standard app conventions
- Fixed "No previous data" and missing muscle-group subtitles for variant exercises (e.g. Pec Deck / Dumbbell Flyes) — history and muscle info now correctly combine across all variant names, including sessions logged before the variant picker existed
- Fixed recovery analysis reading the hourly calorie rate instead of total calories burned
- Fixed BW exercise weight display showing belt weight alone instead of the combined bodyweight + belt total
- Google Drive reconnect reworked: tries a fast silent reconnect first, falls back to the account picker only if needed, instead of always forcing a full re-authorization
- Equipment Units toggle added to the recovery log sheet

### v1.4.0
- Dark / Light / Auto theme toggle — Dark for the gym, Light for outdoors, Auto follows your phone's system setting
- Recent Sessions moved above Workouts on the home screen
- BW exercises with a belt now show the combined total (BW + belt) in the Last hint
- Google Drive reconnect handled with a full-screen branded overlay instead of a random flash
- Updated User Manual with Appearance section, reps validation note, and recovery stats conversion
- Hardcoded dark colours replaced with CSS variables so both themes render cleanly

### v1.3.0
- Metric / Imperial toggle in Settings — all weights convert between kg and lbs on the fly, data stored internally in kg
- Recovery stats (distance, speed) convert on the fly between miles/km and mph/kph based on your unit preference
- Recovery analysis prompts now report stats in your preferred units
- AI Insights sends workout data with the right unit field names so Claude responds correctly
- Branded splash screen on the TWA — Heavy Duty logo on red instead of the Chrome logo
- Restored the // separator in the athlete profile training years card
- Fixed recovery detail stats overflowing into one row — wraps into a 3-column grid now

### v1.2.0
- Equipment stats extraction on recovery photos — Claude reads distance, speed, heart rate and calories directly from equipment displays
- User Manual and About sections in Settings
- Reps validation — can't save a workout with missing reps
- Better outdoor readability — bumped contrast on secondary text colours
- Fixed exercise pills showing the wrong variation name after editing
- Fixed updateWorkout overwriting the logged variation with the template name
- Fixed DONE button in the numpad sheet not filling the width
- Fixed Google Drive auto-backup failing silently after token expiry
- Fixed Drive dirty flag not persisting across app close
- Fixed Static Holds YouTube link pointing to a deleted video

### v1.1.1
- Fixed Chrome autofill on all exercise form inputs — numpad buttons with hidden inputs and contenteditable for notes
- Fixed exercise history pills only showing the last word of exercise names
- Prompt caching on all Claude API calls

### v1.1.0
- Built-in workout editing with EDITED badge and AI REVIEW chip
- Mentzer's Verdict — Claude analyses workout modifications in real time
- Exercise variation selection at log time
- Full HD I / HD II / HIT Mentzer Way program attribution in the Guide
- Three-dot overflow menu on workout rows
- Settings auto-refresh after changes
- Exercise search now matches muscle groups
- Various bug fixes (exercise picker focus, AI verdict streaming, custom workout footer, autofill, badge overflow)

### v1.0.1
- HIT Recommendation text contrast fix
- Google Drive auto-backup popup and token expiry fixes
- Android back button now closes overlays before exiting
- Full-width Log Session button

### v1.0.0
- Initial release — workout tracking, active recovery, Google Drive backup, AI Insights, PWA + TWA

---

## Contributing

Issues and PRs are welcome. A few things to know:

- The whole app is `index.html` — one file, intentionally
- No build step, no bundler, no dependencies
- CSS design tokens live in `:root` at the top of `<style>`
- Workout types and exercises are in the JS constants near the top of `<script>`
- Bump the service worker cache version in `sw.js` if you change any static assets

See [CONTRIBUTING.md](CONTRIBUTING.md) for the full guide.

---

## License

MIT — see [LICENSE](LICENSE).

---

## Disclaimer

This app has no affiliation with [mikementzer.org](https://mikementzer.org) or Mike Mentzer's estate. Built independently to help followers of the Heavy Duty / HIT methodology track their progress.

If the estate wishes to get in contact: **zeroaid@gmail.com**

---

## Acknowledgements

Inspired by the work and philosophy of **Mike Mentzer** (1951–2001), whose *Heavy Duty* system proved that intensity, not volume, is the stimulus for growth.

> *"The only way to achieve the goal you desire is to take the exact steps necessary to get there."*
> — Mike Mentzer
