# Stitch Design Skills

A collection of agent skills and plugins for [Google Stitch](https://stitch.withgoogle.com), following the [Agent Skills](https://agentskills.io) open standard. Compatible with coding agents such as Codex, Antigravity, Gemini CLI, Claude Code, and Cursor.

## Quick Start

### 1. Install Plugins (Recommended)
The fastest way to set up the full Stitch plugin suite globally.

#### Codex

In Codex, add this repository as a plugin marketplace:

| Field | Value |
|---|---|
| Source | `https://github.com/google-labs-code/stitch-skills` |
| Git ref | `main` |
| Sparse paths | Leave empty, or use the paths below for a smaller checkout |

Optional sparse paths:

```text
.agents/plugins
plugins/stitch-design
plugins/stitch-build
plugins/stitch-utilities
```

Do not use `plugins/codex`; that path does not exist in this repository.

The equivalent Codex CLI command is:

```bash
codex plugin marketplace add google-labs-code/stitch-skills --ref main \
  --sparse .agents/plugins \
  --sparse plugins/stitch-design \
  --sparse plugins/stitch-build \
  --sparse plugins/stitch-utilities
```

After adding the marketplace, install the plugins you need from the `Stitch Skills` marketplace:

- `stitch-design`
- `stitch-build`
- `stitch-utilities`

#### Claude Code

```bash
npx plugins add google-labs-code/stitch-skills --scope project --target claude-code
```

> **Personal note:** I primarily use Claude Code with `--scope user` instead of `--scope project` so the plugins are available across all my local repos without needing to re-add them each time.

### 2. Install Skills Selectively
Choose only the specific skills you need.

> [!IMPORTANT]
> Stitch Design Skills often have inter-dependencies. If you choose to install skills selectively, ensure you include all required dependencies.

```bash
npx skills add google-labs-code/stitch-skills
```

You can run the following commands to see the help documentation for plugins and skills:

```bash
npx plugins --help

npx skills --help
```

## Prerequisites

These skills require the **Stitch MCP** server to be configured and running in your agent's environment. Make sure you have followed the [Stitch MCP Setup Instructions](https://stitch.withgoogle.com/docs/mcp/setup/) to register the server and set up appropriate environment variables and credentials.

## Available Plugins

### Design (`stitch-design`)

Core design workflows for creating, managing, and optimizing designs within Stitch.

| Skill | Description | Prompt Example |
|---|---|---|
| [stitch::code-to-design](plugins/stitch-design/skills/code-to-design/) | Convert frontend code (React, Vue, etc.) to a Stitch Design via HTML extraction + design system + upload | *"Upload the frontend code at `/path/to/dashboard` into a Stitch project named 'Dashboard-Migration-2026'."* |
| [stitch::generate-design](plugins/stitch-design/skills/generate-design/) | Generate new screens from text or images, edit existing screens, and create design variants | · *"Make a browse tab for a mobile app for romance and date night ideas."*<br>· *"Edit the login screen to add a 'Remember Me' checkbox and change the button color to blue."*<br>· *"Generate 3 design va
