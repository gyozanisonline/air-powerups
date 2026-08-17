<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/air-wordmark-dark.png">
  <img src="assets/air-wordmark.png" width="150" alt="AIR · Artificial Intelligence Resources">
</picture>

# Powerups for Claude Code

Small upgrades that change how Claude works. Each one is a **relic**: you equip it once, and it stays part of your setup.

Free. Take what you need.

---

## The relics

### Voiceprint · skill

**Claude learns how you actually write, then writes like you.**

Most attempts at "write like me" fail the same way: you describe your tone, the model returns a generic average of that description, and it sounds like everyone and no one. Voiceprint works the other direction. It reads writing you have already done, pulls out the concrete patterns (how you open, how you hedge, the punctuation you lean on, the words you would never use), and saves them to a profile file. Every draft after that comes out in your voice.

Two modes: **build** a profile from real samples, **draft** anything in it later.

Fastest way to feed it is your sent folder. If you have a Gmail connection in Claude, say *"learn my voice from my sent mail."*

[`skills/voiceprint`](skills/voiceprint) · [quickstart guide (PDF)](guides/Voiceprint-Guide.pdf)

### Time Sense · hook

**Claude always knows what time it is.**

Claude Code learns the date once when a session starts and never sees the clock again, so at noon it will happily tell you to get some rest. This stamps every message you send with the current local time:

```
Now: Mon, 2026-08-17, 11:30 GMT+3
```

From there Claude gets the part of day right, knows how long you were away, and can reason about deadlines against the real clock. Under ten tokens per message, and it fires only on your prompts, never on tool output.

[`hooks/time-sense`](hooks/time-sense) · [how it works and how to customize the clock](hooks/time-sense/HOOK.md) · [quickstart guide (PDF)](guides/Time-Sense-Guide.pdf)

---

## Equip them

There is no installer. Download this repo, open Claude Code in the folder, and paste one line:

> Install the AIR powerups in this repo: copy every folder in `skills/` into my `~/.claude/skills/`, and merge every `hooks/*/settings-snippet.json` into the matching hook array in my Claude Code `settings.json`. Keep the hooks I already have, add alongside them. Then tell me what is now available.

Claude finds the right paths, moves the files, and validates the JSON. Start a new session afterward so everything loads.

### Manual install

**Skills.** Copy the folder into your skills directory:

```bash
cp -R skills/voiceprint ~/.claude/skills/
```

On Windows, copy it into `%USERPROFILE%\.claude\skills\`.

**Hooks.** Open your `settings.json` (`~/.claude/settings.json`, or `%USERPROFILE%\.claude\settings.json` on Windows) and add the object in `hooks/time-sense/settings-snippet.json` as one more entry in the `hooks.UserPromptSubmit` array. Create the array if it is not there. Do not overwrite hooks you already have. If the `Now:` line does not appear on your next message, open `/hooks` once so Claude Code reloads the config.

### Requirements

Claude Code, either the CLI, the desktop app, or an IDE extension. Nothing else to install. The hook runs a single inline Node command, and Node ships with Claude Code, so it behaves the same on macOS, Windows and Linux.

### Uninstall

Skills: delete the folder from `~/.claude/skills/`. Hooks: remove the entry you added from the `UserPromptSubmit` array. Or just ask Claude to undo it.

---

## Made by

[Gyozan](https://www.gyozan.com) (Yoel Zajdner), designer and generative artist. AIR is the shelf these live on.

More relics on the way. If one of these saves you an hour, that is the whole point.

## License

MIT, see [LICENSE](LICENSE). Use them, change them, build on them.

The AIR name, logo and brand artwork are not part of that license. Those stay mine.
