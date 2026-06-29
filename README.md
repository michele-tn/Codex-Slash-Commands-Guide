# Codex Slash Commands Guide

<!-- ![Codex Slash Commands Guide cover](https://raw.githubusercontent.com/michele-tn/Codex-Slash-Commands-Guide/refs/heads/main/codex-slash-commands-cover.svg) -->
https://github.com/user-attachments/assets/6af2bdd9-9fa1-41f3-8763-3ea4aa24bda9 -->
## 🎬 𝘿𝟯𝙈𝟬
<video controls preload="metadata" style="width: 100%; max-width: 960px; height: auto;">
  <source
    src="https://github.com/user-attachments/assets/6af2bdd9-9fa1-41f3-8763-3ea4aa24bda9"
    type="video/mp4">
  Il tuo browser non supporta la riproduzione video.
</video>

## Overview

This guide documents the slash commands available across Codex surfaces and provides a production-ready reference for teams that want to standardize Codex usage in a repository.

Covered surfaces:

- **Codex desktop app**: slash commands in the thread composer.
- **Codex IDE extension**: slash commands in the IDE chat input.
- **Codex CLI**: slash commands in the terminal UI.
- **Reusable workflows**: skills and custom prompts for team-specific commands.

Command availability can vary by Codex version, account access, enabled features, installed plugins, workspace policy, and whether the session is local or cloud-based.

## How to Use Slash Commands

1. Open the Codex composer, IDE chat input, or CLI composer.
2. Type `/`.
3. Select a command from the menu, or keep typing to filter the list.
4. Press `Enter`.

In Codex CLI, if a task is already running, type a slash command and press `Tab` to queue it for the next turn.

## Codex Desktop App Commands

| Command | Purpose | Recommended use |
| --- | --- | --- |
| `/feedback` | Opens the feedback dialog and can include logs. | Report product issues, defects, or diagnostics. |
| `/goal` | Sets a persistent goal for Codex to work toward. | Use for long-running objectives that should remain attached to the thread. |
| `/init` | Generates an `AGENTS.md` scaffold for the current project. | Create durable repository instructions for Codex. |
| `/mcp` | Opens MCP status and shows connected servers. | Confirm which MCP servers and tools are available. |
| `/plan` | Toggles plan mode for multi-step planning. | Use before risky, broad, or ambiguous implementation work. |
| `/review` | Starts code review mode. | Review uncommitted changes or compare against a base branch. |
| `/status` | Shows thread ID, context usage, and rate limits. | Inspect the state of the current thread. |

### Enable `/goal`

If `/goal` is not visible, enable goals in `config.toml`:

```toml
[features]
goals = true
```

You can also enable the feature from Codex CLI:

```bash
codex features enable goals
```

Use `/plan` before `/goal` when the objective still needs refinement.

## Codex IDE Extension Commands

| Command | Purpose | Recommended use |
| --- | --- | --- |
| `/auto-context` | Turns Auto Context on or off. | Automatically include recent files and IDE context. |
| `/cloud` | Switches to cloud mode. | Run the task remotely when cloud access is available. |
| `/cloud-environment` | Selects the cloud environment. | Choose the target environment while in cloud mode. |
| `/feedback` | Opens the feedback dialog and can include logs. | Report issues or send diagnostics. |
| `/goal` | Sets a persistent goal for Codex to work toward. | Keep a larger objective active across turns. |
| `/local` | Switches to local mode. | Run the task in the local workspace. |
| `/review` | Starts code review mode. | Review uncommitted changes or compare against a base branch. |
| `/status` | Shows thread ID, context usage, and rate limits. | Inspect the state of the current IDE session. |

## Codex CLI Commands

Codex CLI provides the broadest slash-command surface. Use these commands to manage permissions, models, context, plugins, background work, review workflows, and session state directly from the terminal.

| Command | Purpose | Recommended use |
| --- | --- | --- |
| `/permissions` | Updates what Codex can do without asking first. | Tighten or relax approval requirements during a session. |
| `/ide` | Includes IDE context such as open files and current selection. | Pull editor context into the next request. |
| `/keymap` | Remaps TUI keyboard shortcuts. | Inspect or persist shortcut bindings in `config.toml`. |
| `/vim` | Toggles Vim mode for the composer. | Use Vim-style editing in the CLI composer. |
| `/sandbox-add-read-dir` | Grants sandbox read access to an extra directory on Windows. | Allow reads from an absolute directory outside the current readable roots. |
| `/agent` | Switches the active agent thread. | Inspect or continue work from a spawned subagent. |
| `/apps` | Browses apps and connectors. | Attach an app as `$app-slug` before asking Codex to use it. |
| `/plugins` | Browses installed and discoverable plugins. | Inspect plugin tools, suggested installs, or plugin availability. |
| `/hooks` | Views and manages lifecycle hooks. | Inspect, trust, or disable hooks before they run. |
| `/clear` | Clears the terminal and starts a new chat. | Reset the visible UI and conversation together. |
| `/archive` | Archives the current session and exits Codex. | Remove the session from active lists without deleting its transcript. |
| `/delete` | Permanently deletes the current session and exits. | Remove transcript and descendant sessions when archiving is insufficient. |
| `/compact` | Summarizes the visible conversation to free tokens. | Preserve key context after long sessions. |
| `/copy` | Copies the latest completed Codex output. | Reuse the latest answer, plan, or generated text. |
| `/diff` | Shows the Git diff, including untracked files. | Review local changes before testing, committing, or requesting review. |
| `/exit` | Exits the CLI. | Alias of `/quit`. |
| `/experimental` | Toggles experimental features. | Enable optional capabilities when available. |
| `/approve` | Approves one retry of a recent auto-review denial. | Retry a denied command or action once. |
| `/memories` | Configures memory use and generation. | Manage memory injection or generation behavior. |
| `/skills` | Browses and applies skills. | Select a specialized workflow for the next request. |
| `/import` | Imports supported Claude Code setup, project files, or recent chats. | Migrate external-agent artifacts into Codex. |
| `/feedback` | Sends feedback and logs. | Report issues or share diagnostics. |
| `/init` | Generates `AGENTS.md` in the current directory. | Create repository-level instructions. |
| `/logout` | Signs out of Codex. | Clear local credentials, especially on shared machines. |
| `/mcp` | Lists configured MCP tools. | Check external tools available to the session; use `verbose` for server details. |
| `/mention` | Attaches a file or folder to the conversation. | Point Codex at specific project context. |
| `/model` | Sets the active model and reasoning effort when available. | Switch between faster and deeper reasoning models. |
| `/fast` | Toggles or checks the Fast service tier when exposed by the model catalog. | Reduce latency when the active model supports Fast mode. |
| `/plan` | Switches to plan mode, optionally with an inline prompt. | Ask Codex to propose an execution plan before implementation. |
| `/goal` | Sets, views, pauses, resumes, or clears a task goal. | Attach a persistent target to the active thread. |
| `/personality` | Sets the communication style. | Choose a more concise, pragmatic, friendly, or neutral style when supported. |
| `/ps` | Shows experimental background terminals and recent output. | Check long-running background commands. |
| `/stop` | Stops all background terminals. | Cancel background work started by the current session. |
| `/fork` | Forks the current conversation into a new thread. | Explore an alternative approach without losing the current transcript. |
| `/side` | Starts an ephemeral side conversation. | Ask a focused follow-up without disrupting the main thread. |
| `/btw` | Starts an ephemeral side conversation. | Alias of `/side`. |
| `/raw` | Toggles raw scrollback mode. | Make terminal selection and copying less formatted. |
| `/resume` | Resumes a saved conversation. | Continue a previous CLI session. |
| `/new` | Starts a new conversation inside the same CLI session. | Reset chat context without leaving the CLI. |
| `/quit` | Exits the CLI. | Leave the session after saving important work. |
| `/review` | Reviews the working tree. | Ask Codex to review local changes. |
| `/status` | Displays session configuration and token usage. | Confirm model, approval policy, writable roots, and remaining context. |
| `/usage` | Shows account token usage or rate-limit reset information. | Inspect ChatGPT token activity from the TUI. |
| `/debug-config` | Prints config layer and requirements diagnostics. | Debug configuration precedence and policy requirements. |
| `/statusline` | Configures TUI status-line fields. | Choose footer fields such as model, context, limits, Git, tokens, and session. |
| `/title` | Configures terminal title fields. | Include project, status, thread, branch, model, or task progress in the title. |
| `/theme` | Selects a syntax-highlighting theme. | Customize code rendering in the terminal. |

## Practical CLI Examples

Inspect the active session:

```text
/status
```

Change the active model:

```text
/model
```

Check or change Fast mode:

```text
/fast status
/fast on
/fast off
```

Set and manage a persistent goal:

```text
/goal Finish the migration and keep tests green
/goal
/goal pause
/goal resume
/goal clear
```

Start planning with an inline prompt:

```text
/plan Propose a migration strategy for this service
```

Inspect configured MCP servers:

```text
/mcp verbose
```

Review local changes:

```text
/diff
/review
```

## Revisioning Workflow

Claude Code documents review-oriented commands such as `/review` and `/code-review`, and a session-history command such as `/rewind`. Codex does not document an official built-in command named `/revisioning`.

For Codex, use the following production equivalent:

| Need | Codex command or workflow |
| --- | --- |
| Inspect local changes | `/diff` |
| Ask Codex to review changes | `/review` |
| Preserve a long-session summary before continuing | `/compact` |
| Branch the conversation before trying another approach | `/fork` |
| Start a clean continuation | `/new` or `/resume` |
| Standardize a team revision workflow | Create a `revisioning` skill, or use `/prompts:revisioning` as a compatibility fallback. |

### Recommended Team Workflow

Use this sequence when you want a Claude Code-style revisioning pass in Codex:

```text
/diff
/review
```

Then ask Codex to produce a revision plan:

```text
Create a revisioning report for the current changes. Include changed files, behavioral risks, missing tests, recommended fixes, and a release-readiness decision.
```

### Optional Compatibility Command: `/prompts:revisioning`

Custom prompts are deprecated in Codex in favor of skills, but they can still be used in Codex CLI and the Codex IDE extension when a slash-command-style workflow is required.

Create this file:

```text
~/.codex/prompts/revisioning.md
```

Recommended content:

```markdown
---
description: Review the current changes and produce a release-ready revisioning report
argument-hint: [BASE_BRANCH=] [FOCUS=""]
---

Run a revisioning pass for the current workspace.

If BASE_BRANCH is provided, compare the working tree against that branch.
If FOCUS is provided, prioritize that area.

Produce:

1. Change summary
2. Files changed
3. Behavioral risks
4. Security or data-handling risks
5. Missing tests
6. Required fixes before production
7. Optional improvements
8. Release-readiness decision: ready, ready with caveats, or not ready

Use repository evidence. Do not invent changes that are not visible in the workspace.
```

Invoke it with:

```text
/prompts:revisioning BASE_BRANCH=main FOCUS="reverse proxy changes"
```

For new team workflows, prefer a Codex skill named `revisioning` and invoke it through the skill picker or `$revisioning` where available.

## Skills and `$` Commands

Codex can also invoke skills by typing `$` in the composer when skills are available. Enabled skills can appear in command menus depending on the surface and configuration.

Use skills for reusable, shareable workflows that need instructions, references, scripts, or domain-specific procedures. For new workflows, prefer skills over custom prompts.

## Custom Prompts

Custom prompts convert Markdown files into local slash commands with this format:

```text
/prompts:prompt-name
```

This feature is deprecated. Use skills for new reusable workflows.

### Create a Custom Prompt

Create the prompts directory:

```bash
mkdir -p ~/.codex/prompts
```

Create a Markdown file directly inside that directory:

```text
~/.codex/prompts/draftpr.md
```

Example:

```markdown
---
description: Prepare a branch, commit, and draft pull request
argument-hint: [FILES=] [PR_TITLE=""]
---

Create a branch named `dev/` for this work.
If files are specified, stage them first: $FILES.
Commit the staged changes with a clear message.
Open a draft pull request. Use $PR_TITLE when supplied; otherwise write a concise title.
```

Restart Codex or open a new chat, then invoke:

```text
/prompts:draftpr FILES="src/index.ts src/api.ts" PR_TITLE="Add API proxy"
```

### Supported Placeholders

| Placeholder | Meaning |
| --- | --- |
| `$1` through `$9` | Positional arguments. |
| `$ARGUMENTS` | All supplied arguments. |
| `$FILE`, `$TICKET_ID`, etc. | Named uppercase arguments supplied as `KEY=value`. |
| `$$` | A literal `$` character. |

Codex scans only top-level Markdown files in `~/.codex/prompts/`. Restart Codex or open a new chat after editing prompt files.

## Command Availability Matrix

| Command | Desktop app | IDE extension | CLI |
| --- | --- | --- | --- |
| `/archive` | No | No | Yes |
| `/agent` | No | No | Yes |
| `/apps` | No | No | Yes |
| `/approve` | No | No | Yes |
| `/auto-context` | No | Yes | No |
| `/btw` | No | No | Yes |
| `/clear` | No | No | Yes |
| `/cloud` | No | Yes | No |
| `/cloud-environment` | No | Yes | No |
| `/compact` | No | No | Yes |
| `/copy` | No | No | Yes |
| `/debug-config` | No | No | Yes |
| `/delete` | No | No | Yes |
| `/diff` | No | No | Yes |
| `/exit` | No | No | Yes |
| `/experimental` | No | No | Yes |
| `/fast` | No | No | Yes |
| `/feedback` | Yes | Yes | Yes |
| `/fork` | No | No | Yes |
| `/goal` | Yes | Yes | Yes |
| `/hooks` | No | No | Yes |
| `/ide` | No | No | Yes |
| `/import` | No | No | Yes |
| `/init` | Yes | No | Yes |
| `/keymap` | No | No | Yes |
| `/local` | No | Yes | No |
| `/logout` | No | No | Yes |
| `/mcp` | Yes | No | Yes |
| `/memories` | No | No | Yes |
| `/mention` | No | No | Yes |
| `/model` | No | No | Yes |
| `/new` | No | No | Yes |
| `/permissions` | No | No | Yes |
| `/personality` | No | No | Yes |
| `/plan` | Yes | No | Yes |
| `/plugins` | No | No | Yes |
| `/prompts:*` | No | Yes | Yes |
| `/ps` | No | No | Yes |
| `/quit` | No | No | Yes |
| `/raw` | No | No | Yes |
| `/resume` | No | No | Yes |
| `/review` | Yes | Yes | Yes |
| `/sandbox-add-read-dir` | No | No | Windows only |
| `/side` | No | No | Yes |
| `/skills` | Surface-dependent | Surface-dependent | Yes |
| `/status` | Yes | Yes | Yes |
| `/statusline` | No | No | Yes |
| `/stop` | No | No | Yes |
| `/theme` | No | No | Yes |
| `/title` | No | No | Yes |
| `/usage` | No | No | Yes |
| `/vim` | No | No | Yes |

## Operational Best Practices

- Use `/status` at the beginning of important sessions.
- Use `/plan` before broad, risky, or ambiguous changes.
- Use `/diff` before asking for `/review`.
- Use `/review` before committing or opening a pull request.
- Use `/compact` after long conversations that need to continue.
- Use `/permissions` deliberately and keep the approval policy aligned with task risk.
- Use `/mcp` when an expected external tool is missing.
- Use `/goal` for long-running objectives that should remain visible and trackable.
- Prefer skills over custom prompts for new reusable workflows.
- Treat `/prompts:*` commands as compatibility tools, not the default extension mechanism.

## Official References

- [Codex app commands](https://developers.openai.com/codex/app/commands)
- [Codex IDE extension slash commands](https://developers.openai.com/codex/ide/slash-commands)
- [Slash commands in Codex CLI](https://developers.openai.com/codex/cli/slash-commands)
- [Codex custom prompts](https://developers.openai.com/codex/custom-prompts)
- [Codex skills](https://developers.openai.com/codex/skills)
- [Claude Code slash commands](https://docs.anthropic.com/en/docs/claude-code/slash-commands)
