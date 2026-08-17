<p>
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/air-wordmark-dark.png">
    <img src="assets/air-wordmark.png" width="150" alt="AIR · Artificial Intelligence Resources">
  </picture>
  <br>
  By <a href="https://www.gyozan.com"><strong>Gyozan</strong></a>
</p>

# AIR: Artificial Intelligence Resources

Powerups for Claude Code. Small upgrades that change how Claude works, and each one is a **relic**: you equip it once, and it stays part of your setup.

Free. Take what you need.

## What's in here

| Relic | What it grants | Kind |
|---|---|---|
| [**Voiceprint**](#voiceprint) | Claude learns how you actually write, then drafts in your voice | skill |
| [**Time Sense**](#time-sense) | Claude always knows the real date and time | hook |

**Getting started:** [Equip them](#equip-them) · [Manual install](#manual-install) · [Update](#update) · [Uninstall](#uninstall) · [Made by](#made-by) · [License](#license)

---

## Equip them

AIR is a Claude Code **plugin marketplace**. Add it once, then install whichever relics you want:

```
/plugin marketplace add gyozanisonline/air-powerups
/plugin install voiceprint@air
/plugin install time-sense@air
```

Run those inside Claude Code. If the install summary says `Run /reload-plugins to activate.`, run that.

Installing this way means relics **update themselves** when new versions land, hook relics never touch your `settings.json`, and uninstalling is one command instead of hunting down files.

<details>
<summary><strong>If <code>marketplace add</code> fails</strong></summary>

The `owner/repo` shorthand clones over SSH by default, which fails if you have no SSH key loaded. Either use the full HTTPS URL:

```
/plugin marketplace add https://github.com/gyozanisonline/air-powerups.git
```

or set `CLAUDE_CODE_PLUGIN_PREFER_HTTPS=1` in your environment so the shorthand uses HTTPS.
</details>

### Update

```
/plugin marketplace update air
```

### Uninstall

```
/plugin uninstall voiceprint
```

---

## Voiceprint

**skill** · `/plugin install voiceprint@air`

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

Profiles are saved to `~/.claude/voiceprint-profiles/<name>.md`, outside the relic, so they survive updates and stay private. One file per voice, and it works for a persona or brand voice too, not just your own.

**Inside:** [`plugins/voiceprint`](plugins/voiceprint) carries the skill plus its extraction methodology, profile template, a guide to where voice hides across channels, and a full worked example. Quickstart: [Voiceprint-Guide.pdf](guides/Voiceprint-Guide.pdf).

---

## Time Sense

**hook** · `/plugin install time-sense@air`

> Claude always knows the real date and time.

Claude Code learns the date once when a session starts and never sees the clock again. So halfway through a long session it will happily tell you to get some rest, at noon, and it has no idea whether you stepped away for four minutes or four hours.

This stamps every message you send with the current local time:

```
Now: Mon, 2026-08-17, 11:30 GMT+3
```

One line, injected right before Claude reads your prompt. From there it gets the part of day right, knows how much time passed between your messages, and can reason about deadlines and "by end of day" against the real clock.

**Why it is cheap.** Under ten tokens per message, and it fires only on your prompts, never on tool output.

**Why it works everywhere.** It is a single inline Node command, and Node ships with Claude Code, so it behaves identically whether Claude Code is running bash, zsh, or PowerShell. Because the command is inline and uses no `require` or `import`, a stray `"type": "module"` in a nearby `package.json` cannot silently kill it, the way it can with file-based script hooks.

**The clock is yours.** The stamp is a normal JavaScript date format, so you can switch to a 12-hour clock, add seconds, drop the time and keep the date, or change the locale. [HOOK.md](plugins/time-sense/HOOK.md) has the table.

**Inside:** [`plugins/time-sense`](plugins/time-sense). Quickstart: [Time-Sense-Guide.pdf](guides/Time-Sense-Guide.pdf).

---

## Manual install

You do not need this if you used the marketplace, but relics are plain files and you can always place them yourself.

**Skills.** Copy the skill folder into your skills directory, then start a new session:

```bash
cp -R plugins/voiceprint/skills/voiceprint ~/.claude/skills/
```

On Windows, copy it into `%USERPROFILE%\.claude\skills\`.

**Hooks.** Open your `settings.json` (`~/.claude/settings.json`, or `%USERPROFILE%\.claude\settings.json` on Windows) and merge the entry from [`plugins/time-sense/hooks/hooks.json`](plugins/time-sense/hooks/hooks.json) into your own `hooks.UserPromptSubmit` array. Create the array if it is not there, and do not overwrite hooks you already have. If the `Now:` line does not appear on your next message, open `/hooks` once so Claude Code reloads the config.

To undo a manual install: delete the folder from `~/.claude/skills/`, or remove the entry you added from the `UserPromptSubmit` array.

## Requirements

Claude Code, either the CLI, the desktop app, or an IDE extension. Nothing else to install.

---

## Made by

[**Gyozan**](https://www.gyozan.com) (Yoel Zajdner), Creative technologist, designer, maybe a bit of a scientist. Enjoy!

More relics on the way. If one of these saves you an hour, let me know!

## License

MIT, see [LICENSE](LICENSE). Use them, change them, build on them.

The AIR name, logo and brand artwork are their own private entity and are not part of this license.
