# DeckCoderAI presentations

An [Agent Skill](https://agentskills.io/) for Codex and Claude Code. Install it once and ask for an interactive presentation in ordinary language. A compatible agent can choose the skill without you naming DeckCoderAI.

The skill teaches the agent to find the desktop app's bundled command-line tool, author the slides, check the deck, render its states, and export an editable `.deckcoder` package or interactive browser HTML. It does not install the desktop app, grant access to an open presentation, or add an MCP server.

## Install

Run the command for your agent in the folder where you want to make presentations. These commands use the [skills CLI](https://skills.sh/docs/cli) and require Node.js with `npx`. Review the displayed source and installation scope. For access across projects instead, add `--global`.

### Install for Codex

```sh
npx skills add tojileon/deckcoderai-skill --skill deckcoderai-presentations --agent codex
```

### Install for Claude Code

```sh
npx skills add tojileon/deckcoderai-skill --skill deckcoderai-presentations --agent claude-code
```

For both clients, specify `--agent codex claude-code`. Start a fresh session in the same project after installation.

### Without npx

Download or clone this repository and copy the **whole** [deckcoderai-presentations folder](skills/deckcoderai-presentations) into `.agents/skills/` for Codex or `.claude/skills/` for Claude Code in your project. The result must be `<skills directory>/deckcoderai-presentations/SKILL.md`.

## Try it

> Make a presentation about how trees cool cities. Let me reveal the temperature differences one at a time.

Ask to see the finished deck and try Next, Back and Reset. If a session doesn't select the skill, explicitly invoke `$deckcoderai-presentations` in Codex or `/deckcoderai-presentations` in Claude Code.

Use the [DeckCoderAI download page](https://deckcoderai.com/download/) for the **separate desktop app**. The public Mac preview has been tested on Apple Silicon. The [release record](https://deckcoderai.com/releases/mac-beta.json) gives the official archive and checksum. The Windows build is an unsigned, untested experiment. A cloud agent without a compatible local runtime cannot run the Mac app.

The desktop app's local MCP connection is optional for creating a saved deck. It is useful when you want to work on the presentation you have open; [the agent guide](https://deckcoderai.com/agent-guide.md) explains how to grant and revoke access. If you need editable native PowerPoint objects, use a PowerPoint workflow; DeckCoderAI's PPTX export contains slide images.

## Licence

The [MIT licence](LICENSE) covers the skill files in this repository. The separate DeckCoderAI desktop app is closed source and has [its own licence](https://deckcoderai.com/legal/license.txt).
