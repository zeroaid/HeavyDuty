# Security Policy

## Supported versions

Only the latest version deployed at [zeroaid.github.io/HeavyDuty](https://zeroaid.github.io/HeavyDuty/) is actively maintained.

## Data handling

- All workout data is stored in **your browser's `localStorage`** — nothing is sent to any server owned by this project
- Your Claude API key (if set) is stored in `localStorage` and is only ever sent directly to Anthropic's API endpoints
- Optional Google Drive backup writes a single JSON file to **your own** Google Drive account via OAuth — no third-party server is involved

## Reporting a vulnerability

If you discover a security vulnerability, please **do not** open a public GitHub issue.

Instead, report it privately via [GitHub's private vulnerability reporting](https://github.com/zeroaid/HeavyDuty/security/advisories/new).

Include:
- A description of the vulnerability
- Steps to reproduce
- Potential impact
- Any suggested fix if you have one

You can expect an acknowledgement within 72 hours. If the vulnerability is confirmed, a fix will be prioritised and you will be credited in the release notes (unless you prefer to remain anonymous).
