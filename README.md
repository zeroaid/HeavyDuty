# Heavy Duty

A Mike Mentzer Heavy Duty workout tracker — built as a progressive web app (PWA) and available as a native Android TWA.

**[Open the app →](https://zeroaid.github.io/HeavyDuty/)**

---

## What is Heavy Duty?

Heavy Duty is Mike Mentzer's High Intensity Training (HIT) methodology — brief, brutal, and basic. One working set per exercise, taken to absolute muscular failure, with full recovery between sessions. No junk volume, no guesswork.

This app tracks your Consolidated and Legacy split workouts, logs every set with weight and reps, monitors rest periods and progressive overload, and gives you AI-powered analysis of your training via the Claude API.

---

## Features

### Workout Tracking
- **Workout logging** — A1/A2 (Consolidated) and Legacy Upper/Lower splits
- **Progressive overload tracking** — see your last performance on every exercise before you lift
- **Rest-pause set support** — log RP clusters with the exact cadence Mentzer prescribed
- **Rest timer** — automatic countdown between sets
- **Workout history** — full session log with calendar view and date filtering
- **Exercise guide** — cues, technique notes, and Mentzer quotes for every movement

### Active Recovery
- **Recovery session logging** — log light cardio and movement sessions between heavy training days
- **Photo capture** — attach a photo to each recovery session via camera or gallery
- **AI photo analysis** — Claude analyses each photo and identifies activity, heart rate zone, duration, and recovery observations
- **Bulk photo import** — import multiple sessions at once from your camera roll
- **Duplicate detection** — SHA-256 fingerprinting prevents the same photo being imported twice
- **Re-analyse** — re-run AI analysis on any individual session or all sessions at once
- **Recovery filtering** — filter by activity type, zone, time of day, or month
- **Pull-down to dismiss** — swipe down to close any recovery sheet

### AI Insights
- **Training analysis** — Claude-powered deep-dive into your workout history, progressive overload trends, and recovery patterns
- **HIT-specific coaching** — analysis framed around Heavy Duty principles, not generic fitness advice
- **Athlete profile** — age, training history, goal, and lifestyle factors fed into every analysis
- **API key management** — bring your own Anthropic key, stored only in `localStorage`

### Data & Backup
- **JSON backup / restore** — full export including workouts, recovery logs, photos, and athlete profile (v3 format)
- **Google Drive auto-backup** — automatic sync after every save when token is valid; pending indicator when re-auth is needed
- **IndexedDB photo storage** — photos stored in IndexedDB (no localStorage quota limits)
- **Automatic migration** — existing photos migrate from localStorage to IndexedDB on first launch

### App
- **Offline-first PWA** — works without a connection once installed
- **Native Android app** — TWA with black navigation bar, no browser chrome
- **Android back button support** — back button closes overlays and sheets before navigating screens
- **Dark / light theme** — follows system preference
- **Calendar view** — monthly overview of training and recovery sessions
- **Debug panel** — tap Insights title 5× to access API log and app state (for troubleshooting)
- **Version footer** — live version, date, and time in Settings

---

## Install

### Browser (PWA)
Visit **[zeroaid.github.io/HeavyDuty](https://zeroaid.github.io/HeavyDuty/)** and tap *Add to Home Screen* in your browser menu.

### Android (native TWA)
Download the latest `app-release.apk` from [Releases](https://github.com/zeroaid/HeavyDuty/releases), enable *Install unknown apps* in your Android settings, and install.

> The TWA uses Digital Asset Links for verification. Once verified by Chrome, the URL bar disappears and the app runs fully native with a black system navigation bar.

---

## AI Insights setup

The AI tab uses the [Anthropic Claude API](https://console.anthropic.com/). You supply your own key — it is stored only in your browser's `localStorage` and never sent anywhere except directly to Anthropic's API.

1. Get an API key at [console.anthropic.com](https://console.anthropic.com/)
2. Open the app → Insights tab → paste your key

---

## Data & privacy

- Workout and recovery metadata stored in `localStorage`
- Photos stored in `IndexedDB` — no quota limits
- No server, no account, no analytics
- Export your data any time: Settings → Export JSON Backup
- Optional Google Drive backup stores one JSON file in your own Drive account
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

### v1.0.1
- Fixed HIT Recommendation text contrast — now readable in normal lighting
- Fixed Google Drive auto-backup triggering a popup in the background
- Fixed Google Drive auto-backup not firing when token had expired
- Fixed Android back button — now closes overlays and sheets before leaving the screen
- Improved "+ Log Session" button — full-width accent CTA inspired by top fitness apps

### v1.0.0
- Initial release
- Workout tracking (Consolidated + Legacy splits)
- Active Recovery logging with AI photo analysis
- Google Drive backup
- JSON export / import (v3 format with photos)
- IndexedDB photo storage with automatic migration
- Bulk photo import with duplicate detection and rate-limit retry
- AI Insights powered by Claude
- PWA + Android TWA

---

## Contributing

Issues and pull requests are welcome. A few things to know before diving in:

- The entire app is `index.html` — one file, intentionally
- No build step, no bundler, no dependencies
- CSS design tokens are in `:root` at the top of `<style>`
- Workout types and exercise definitions are in the JS constants near the top of `<script>`
- The service worker cache version (`sw.js`, line 1) must be bumped on any change to cached static assets

See [CONTRIBUTING.md](CONTRIBUTING.md) for the full guide.

---

## License

MIT — see [LICENSE](LICENSE).

---

## Disclaimer

This app has no affiliation with [mikementzer.org](https://mikementzer.org) or Mike Mentzer's estate. It has been created independently to help followers of the Heavy Duty / HIT training methodology track their progress.

If the estate wishes to get in contact, please email: **zeroaid@gmail.com**

---

## Acknowledgements

Inspired by the work and philosophy of **Mike Mentzer** (1951–2001), whose *Heavy Duty* system proved that intensity, not volume, is the stimulus for growth.

> *"The only way to achieve the goal you desire is to take the exact steps necessary to get there."*
> — Mike Mentzer
