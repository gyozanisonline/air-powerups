# Time Sense — a UserPromptSubmit hook for Claude Code

## What it does
By default Claude Code learns the date once, when a session starts, and never sees the clock again. So halfway through a long session it will happily say "tonight" at noon, or misjudge how long you have been away.

This hook fixes that. It stamps every message you send with the current local time, so Claude always knows what time it actually is:

```
Now: Mon, 2026-07-20, 12:55 GMT+3
```

That single line is injected into context right before Claude reads your prompt. Weekday, date, 24-hour clock, timezone. From that point on Claude can:
- Say the right part of day (morning / afternoon / evening / night) instead of guessing.
- Tell how much time passed between your messages in a long session.
- Reason about deadlines, "by end of day", "in an hour", and scheduling against the real clock.

It runs a tiny Node command (Node ships with Claude Code, so it is always there), emits under ten tokens per message, and fires only on your prompts, never on tool output.

## Install (any OS: macOS, Windows, Linux)
Open Claude Code and paste this one line:

> Install this AIR hook: merge the object in `hook/settings-snippet.json` into the `hooks.UserPromptSubmit` array of my Claude Code `settings.json`. Keep my other hooks, add this alongside them. Then confirm it is wired.

Claude finds your `settings.json`, merges the snippet, and validates it. Done. If the `Now:` line does not appear on your next message, open `/hooks` once (or restart the session) so Claude Code reloads the config.

### Manual install
Add the contents of `hook/settings-snippet.json` as one more entry in the `hooks.UserPromptSubmit` array of your `settings.json`:

- macOS / Linux: `~/.claude/settings.json`
- Windows: `%USERPROFILE%\.claude\settings.json`

```json
{
  "hooks": {
    "UserPromptSubmit": [
      {
        "matcher": "*",
        "hooks": [
          {
            "type": "command",
            "command": "node -e \"const s=new Date().toLocaleString('en-CA',{weekday:'short',year:'numeric',month:'2-digit',day:'2-digit',hour:'2-digit',minute:'2-digit',hour12:false,timeZoneName:'short'});process.stdout.write(JSON.stringify({hookSpecificOutput:{hookEventName:'UserPromptSubmit',additionalContext:'Now: '+s}}))\"",
            "timeout": 5
          }
        ]
      }
    ]
  }
}
```

If you already have `UserPromptSubmit` hooks, add this as another item in that array rather than overwriting it. The exact same line works on all three operating systems.

## Customize the clock
The stamp is a standard JavaScript date format. Edit the options inside `toLocaleString(...)`:

| You want | Change |
|---|---|
| Default (weekday, ISO date, 24h, tz) | as shipped |
| 12-hour clock with am/pm | set `hour12:true` |
| Add seconds | add `second:'2-digit'` |
| Date only | drop `hour`, `minute`, `hour12`, `timeZoneName` |
| Different date style | swap the `'en-CA'` locale (for example `'en-US'`) |

The `Now:` label is a tiny anchor so Claude never mistakes the stamp for a date mentioned in passing. Keep it, or rename it.

## Uninstall
Remove the entry you added from the `hooks.UserPromptSubmit` array in your `settings.json`, or paste:

> Remove the AIR Time Sense hook (the one that stamps my prompts with `Now:`) from my settings.json.

## Compatibility
- **macOS, Windows, and Linux.** The command is a single inline Node call, so it behaves identically no matter which shell Claude Code uses (bash, zsh, or PowerShell).
- No extra runtime to install: Node already ships with Claude Code.
- Because the command is inline and uses no `require`/`import`, it cannot be silently disabled by a stray `"type": "module"` in a nearby `package.json`, the way file-based script hooks can.
- Claude Code CLI, desktop, or IDE extension.

---
AIR · Artificial Intelligence Resources · level up your practice.
