# Codex engineering harness

Use `$orchestrate-engineering` when a feature needs a design decision you want to review before anyone starts coding. You work directly with three agents in turn. The brainstormer helps you pin down what the feature should do, the architect works out how it fits the existing code, and the orchestrator delivers it in small changes you can review and commit individually.

## Start a feature

After installing the skill, open a Codex chat in the repository you want to change. Describe who needs the feature, one example of success, and any existing behaviour you care about. It's fine to bring an open question. For example, you could start with this prompt:

> Use $orchestrate-engineering as the brainstormer. Our CLI lists failed jobs, and I want an operator to be able to export that list as CSV to attach to a support ticket. If they filter by project, the export should contain the same jobs they see in the terminal. Existing scripts depend on the current output. I haven't decided which columns belong in the export. Help me settle that, then give me the handoff for the architect.

## What happens in each chat

1. **Brainstormer — agree on the behaviour.** Talk through examples and open questions together. For the CSV feature, you might settle which columns the support team needs and what an empty export should contain. The brainstormer records your answers, constraints and remaining questions in `INTENT.md`. It gives you a prompt to paste into a **new architect chat** in the same working tree. The prompt points to the task documents, so you can leave the conversation history behind.
2. **Architect — review the design.** The architect reads the intent, inspects the repository, and discusses consequential choices with you. You get a proposed design in `DESIGN.md`, a commit-sized sequence of changes in `IMPLEMENTATION.md`, and independent review findings in `REVIEW.md`. If you only want a plan, stop here. When you're ready for implementation, approve the design revision and paste the architect's handoff into a **new orchestrator chat**.
3. **Orchestrator — review the code one change at a time.** The orchestrator delegates the current increment, inspects the diff, builds the affected target, and reports the checks it ran. You get a proposed commit subject and an unstaged change. Ask for revisions in that chat, or commit the change and say to continue. The next increment waits for your go-ahead. If new evidence calls the design into question, the orchestrator arranges architectural review and brings the decision back to you. A fresh reviewer checks the full feature at the end.

## Install from GitHub

Ask Codex to install the skill with this prompt:

> Use $skill-installer to install `skills/orchestrate-engineering` from the GitHub repository `DanParrottMD1/codex-harness`.

## Use a local checkout

If you want Codex to pick up edits from this checkout, run these commands once from the repository root on macOS or Linux:

```sh
mkdir -p "$HOME/.agents/skills"
ln -s "$PWD/skills/orchestrate-engineering" "$HOME/.agents/skills/"
```

The link includes the [skill instructions](skills/orchestrate-engineering/SKILL.md), role briefs and engineering principles. Keep the checkout at that path. Choose one installation method so the skill appears once in the selector. If it doesn't appear, restart Codex. [How Codex discovers skills](https://developers.openai.com/codex/skills)
