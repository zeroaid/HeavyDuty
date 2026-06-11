# Heavy Duty

A Mike Mentzer Heavy Duty workout tracker — built as a progressive web app (PWA) and available as a native Android TWA.

**[Open the app →](https://zeroaid.github.io/HeavyDuty/)**

---

## What is Heavy Duty?

Heavy Duty is Mike Mentzer's High Intensity Training (HIT) methodology — brief, brutal, and basic. One working set per exercise, taken to absolute muscular failure, with full recovery between sessions. No junk volume, no guesswork.

This app tracks your Consolidated and Legacy split workouts, logs every set with weight and reps, monitors rest periods and progressive overload, and gives you AI-powered analysis of your training via the Claude API.

---

## Features

- **Workout logging** — A1/A2 (Consolidated) and Legacy Upper/Lower splits
- **Progressive overload tracking** — see your last performance on every exercise before you lift
- **Rest-pause set support** — log RP clusters with the exact cadence Mentzer prescribed
- **Workout history** — full session log with calendar view and filtering
- **Athlete profile** — training age, goal, recovery factors fed into AI analysis
- **AI Insights** — Claude-powered analysis of your training data (bring your own API key)
- **JSON backup / restore** — full export including workout history and athlete profile
- **Google Drive auto-backup** — optional sync after every session
- **Exercise guide** — cues, technique notes, and Mentzer quotes for every movement
- **Offline-first PWA** — works without a connection once installed
- **Native Android app** — TWA with black navigation bar, no browser chrome

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

- All workout data is stored in your browser's `localStorage`
- No server, no account, no analytics
- Export your data any time: Settings → Export JSON Backup
- Optional Google Drive backup stores one JSON file in your own Drive account

---

## Tech stack

| Layer | Detail |
|---|---|
| App | Single-file HTML/CSS/JS (`index.html`) |
| Hosting | GitHub Pages |
| PWA | Service worker (`sw.js`), Web App Manifest |
| Android | Trusted Web Activity via `android-browser-helper` |
| AI | Anthropic Claude API — raw `fetch` SSE streaming |
| Storage | `localStorage` only |
| Build | GitHub Actions (TWA APK signing + release) |

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
