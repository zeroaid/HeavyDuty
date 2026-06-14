# Contributing to Heavy Duty

Thanks for your interest. This is a small, focused project — contributions that stay true to the Heavy Duty philosophy (brief, purposeful, no excess) are most welcome.

## Getting started

No build step required. Clone the repo and open `index.html` directly in a browser, or serve it locally:

```bash
git clone https://github.com/zeroaid/HeavyDuty.git
cd HeavyDuty
npx serve .   # or any static file server
```

## Project structure

```
index.html              # The entire app — HTML + CSS + JS in one file
sw.js                   # Service worker (offline caching)
manifest.json           # PWA manifest
icon-192.png            # App icon
icon-512.png            # App icon (large)
icon-512-maskable.png   # Maskable icon for Android
heavy-duty-logo.png     # Logo shown on home screen
twa-app/                # Android TWA source (Gradle project)
.github/workflows/      # GitHub Actions — TWA build & release
.well-known/            # Digital Asset Links (served via GitHub Pages)
```

## Making changes

### CSS
Design tokens live in `:root` near the top of `<style>`. Match the existing aesthetic — hard edges, Impact for headings, system-ui for body, `#d41414` accent.

### Workout types / exercises
`WK` and `ROT` constants define the splits. `MUSCLE_MAP` maps exercise names to muscle groups. `EXERCISE_GUIDE_DATA` holds the guide content.

### Service worker
If you change any file listed in `STATIC` inside `sw.js`, bump the cache version string (e.g. `heavy-duty-v13` → `heavy-duty-v14`) so existing installs pick up the update.

### TWA
The Android app lives in `twa-app/`. Changes there trigger the GitHub Actions build automatically on push to `main`. To cut a release (creates a GitHub Release with the APK), trigger the workflow manually from the Actions tab.

## Pull request guidelines

- Keep PRs focused — one feature or fix per PR
- Test on mobile (the app is designed for phone use)
- Don't introduce external dependencies or a build step
- Update the service worker cache version if you change static assets
- Describe what you changed and why in the PR body

## Reporting bugs

Open an issue with:
- What you expected to happen
- What actually happened
- Your device / browser / OS

## Feature requests

Open an issue describing the use case. Features that align with Mike Mentzer's principles of doing less but doing it right are most likely to be accepted.
