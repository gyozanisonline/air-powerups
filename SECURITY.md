# Security

## What these relics can do

Be clear-eyed about what you are installing, here and anywhere else.

- **Skills** are instructions. They shape how Claude behaves and what it reads or writes, within the permissions your Claude Code setup already grants. They are readable markdown, so you can check exactly what a skill tells Claude to do before you install it.
- **Hooks** are different. A hook runs a command on your machine automatically on a lifecycle event. Read a hook before installing it, from anyone.

**Time Sense** is a single inline `node -e` command that formats the current date and prints it. It reads no files, opens no network connections, and takes no input from your prompt. The whole command is visible in [`plugins/time-sense/hooks/hooks.json`](plugins/time-sense/hooks/hooks.json), and it is short enough to read in one go.

**Voiceprint** reads writing samples that you provide and writes a profile file to `~/.claude/voiceprint-profiles/`. If you point it at your sent mail, it reads your mail through whatever connection you already authorized in Claude. Your samples and your profile stay on your machine, and nothing is sent anywhere.

## Reporting something

Open a [GitHub issue](https://github.com/gyozanisonline/air-powerups/issues) for anything non-sensitive.

For something you would rather not post publicly, use the contact route on [www.gyozan.com](https://www.gyozan.com).

## Supply chain

This repo has no dependencies, no build step, no install script, and no postinstall hook. Everything here is markdown, JSON, and two PDFs. There is nothing to `npm install`, which is deliberate.
