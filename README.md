<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/air-wordmark-dark.png">
  <img src="assets/air-wordmark.png" width="150" alt="AIR · Artificial Intelligence Resources">
</picture>

# Powerups for Claude Code

Small upgrades that change how Claude works. Each one is a **relic**: you equip it once, and it stays part of your setup.

Free. Take what you need.

## What's in here

| Relic | What it grants | Kind |
|---|---|---|
| [**Voiceprint**](#voiceprint) | Claude learns how you actually write, then drafts in your voice | skill |
| [**Time Sense**](#time-sense) | Claude always knows the real date and time | hook |

**Getting started:** [Equip them](#equip-them) · [Requirements](#requirements) · [Manual install](#manual-install) · [Uninstall](#uninstall) · [Made by](#made-by) · [License](#license)

---

## Voiceprint

**skill** · drops into `~/.claude/skills/`

> Claude learns how you actually write, then drafts in your voice.

Most attempts at "write like me" fail the same way. You describe your tone, the model returns a generic average of that description, and it sounds like everyone and no one.

Voiceprint works the other direction. It reads writing you have already done and pulls out the concrete patterns that make it yours: how you open, how you hedge, the punctuation you lean on, the emoji that mean something to you, and the words you would never use. Those go into a profile file. Every draft after that is just the profile applied.

The rule it holds itself to: **every pattern has to trace back to something you actually wrote.** The moment it starts guessing from adjectives, it drifts generic, which is the exact failure it exists to prevent.

**Two modes**

| Mode | When | What happens |
|---|---|---|
| **Build** | No profile yet | Collect samples, extract the patterns, write the profile, then test it on a real draft and correct it |
| **Draft** | Profile exists | Say what you need written, get it in your voice at the right register |

**Feeding it.** The fastest source is your sent folder, since it covers every register from cold client mail to messages to close friends. If you have a Gmail connection in Claude, say *"learn my voice from my sent mail."* Otherwise paste 5 to 15 varied samples: one cold email, one message to a friend, one client reply, one caption, one annoyed-but-polite note. Variety teaches more than volume.

Profiles are saved to `~/.claude/voiceprint-profiles/<name>.md`, outside the skill, so they survive updates and stay private. One file per voice, and it works for a persona or brand voice too, not just your own.

**Inside:** [`skills/voiceprint`](skills/voiceprint) carries the skill plus its extraction methodology, profile template, a guide to where voice hides across channels, and a full worked example. Quickstart: [Voiceprint-Guide.pdf](guides/Voiceprint-Guide.pdf).

---

## Time Sense

**hook** · merges into `settings.json`

> Claude always knows the real date and time.

Claude Code learns the date once when a session starts and never sees the clock again. So halfway through a long session it will happily tell you to get some rest, at noon, and it has no idea whether you stepped away for four minutes or four hours.

This stamps every message you send with the current local time:

```
Now: Mon, 2026-08-17, 11:30 GMT+3
```

One line, injected right before Claude reads your prompt. From there it gets the part of day right, knows how much time passed between your messages, and can reason about deadlines and "by end of day" against the real clock.

**Why it is cheap.** Under ten tokens per message, and it fires only on your prompts, never on tool output.

**Why it works everywhere.** It is a single inline Node command, and Node ships with Claude Code, so it behaves identically whether Claude Code is running bash, zsh, or PowerShell. Because the command is inline and uses no `require` or `import`, a stray `"type": "module"` in a nearby `package.json` cannot silently kill it, the way it can with file-based script hooks.

**The clock is yours.** The stamp is a normal JavaScript date format, so you can switch to a 12-hour clock, add seconds, drop the time and keep the date, or change the locale. [HOOK.md](hooks/time-sense/HOOK.md) has the table.

**Inside:** [`hooks/time-sense`](hooks/time-sense) carries the exact snippet plus full notes. Quickstart: [Time-Sense-Guide.pdf](guides/Time-Sense-Guide.pdf).

---

## Equip them

There is no installer, and nothing to download by hand. Claude does the install.

Open Claude Code anywhere and paste this:

> Install the AIR powerups from https://github.com/gyozanisonline/air-powerups : clone it to a temp folder, copy every folder in `skills/` into my `~/.claude/skills/`, then merge every `hooks/*/settings-snippet.json` into the `UserPromptSubmit` array of my Claude Code `settings.json`, keeping the hooks I already have. Confirm what is now available, then delete the temp clone.

That works from any folder, on a machine that has never seen this repo. Claude clones it, finds your real config paths, moves the files, validates the JSON, and cleans up after itself. Start a new session afterward so everything loads.

Want only one of them? Say so: *"...copy only `skills/voiceprint`"*, or *"...only merge `hooks/time-sense`"*.

### If you already cloned it

Open Claude Code inside the folder and paste the same request without the clone step:

> Install the AIR powerups in this repo: copy every folder in `skills/` into my `~/.claude/skills/`, then merge every `hooks/*/settings-snippet.json` into the `UserPromptSubmit` array of my Claude Code `settings.json`, keeping the hooks I already have. Then tell me what is now available.

### Manual install

**Skills.** Copy the folder into your skills directory:

```bash
cp -R skills/voiceprint ~/.claude/skills/
```

On Windows, copy it into `%USERPROFILE%\.claude\skills\`.

**Hooks.** Open your `settings.json` (`~/.claude/settings.json`, or `%USERPROFILE%\.claude\settings.json` on Windows) and add the object in `hooks/time-sense/settings-snippet.json` as one more entry in the `hooks.UserPromptSubmit` array. Create the array if it is not there. Do not overwrite hooks you already have. If the `Now:` line does not appear on your next message, open `/hooks` once so Claude Code reloads the config.

### Requirements

Claude Code, either the CLI, the desktop app, or an IDE extension. Nothing else to install.

### Uninstall

Skills: delete the folder from `~/.claude/skills/`. Hooks: remove the entry you added from the `UserPromptSubmit` array. Or just ask Claude to undo it.

---

## Made by

**Gyozan** (Yoel Zajdner) · [www.gyozan.com](https://www.gyozan.com)

Gyozan is the working name of Yoel Zajdner, a designer and generative artist who builds interactive installations and web work. AIR is the shelf for the Claude Code tools that came out of that practice. Each relic here started as something built to solve an actual problem in real work, and the ones that kept earning their place got packaged and put here.

Every relic carries a one-line credit so you can always trace it back. Nothing more than that, since a skill you install should spend its context on the job, not on its author.

More relics on the way. If one of these saves you an hour, that is the whole point.

## License

MIT, see [LICENSE](LICENSE). Use them, change them, build on them.

The AIR name, logo and brand artwork are not part of that license. Those stay mine.
