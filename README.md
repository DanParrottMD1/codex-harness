# Codex engineering harness

The [orchestrate-engineering skill](skills/orchestrate-engineering/SKILL.md) guides a feature through three owner-facing chats: brainstorming, architecture and implementation orchestration. Install it once to use it across projects.

## Install from GitHub

Ask Codex:

> Use $skill-installer to install `skills/orchestrate-engineering` from the GitHub repository `DanParrottMD1/codex-harness`.

## Use a local checkout

If you want Codex to pick up edits from this checkout, run these commands once from the repository root on macOS or Linux:

```sh
mkdir -p "$HOME/.agents/skills"
ln -s "$PWD/skills/orchestrate-engineering" "$HOME/.agents/skills/"
```

The link includes the role briefs and engineering principles. Keep the checkout at that path. Choose one installation method so the skill appears once in the selector. [How Codex discovers skills](https://developers.openai.com/codex/skills)

## Start a feature

Open Codex in the project you want to change and start a chat with:

> Use $orchestrate-engineering as the brainstormer for [feature].

The brainstormer gives you a prompt for a fresh architect chat. After design approval, the architect gives you the orchestrator prompt. If the skill does not appear in the selector, restart Codex.
