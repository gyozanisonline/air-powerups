# Changelog

## 1.0.0 (2026-08-17)

First public release. AIR is now a Claude Code plugin marketplace.

**Added**
- **Voiceprint** (skill): build a writing-voice profile from real samples, then draft in that voice.
- **Time Sense** (hook): stamp every prompt with the current local time. Works on macOS, Windows and Linux.
- Plugin marketplace at `.claude-plugin/marketplace.json`, so relics install with `/plugin install <relic>@air`, update themselves, and uninstall cleanly.
- Branded quickstart guide PDFs for both relics.

**Notes**
- Time Sense as a plugin no longer edits your `settings.json` at all. The manual path still exists if you prefer it.
- Every relic file carries a one-line credit back to Gyozan. Nothing more, so an installed relic spends its context on the job rather than on its author.
