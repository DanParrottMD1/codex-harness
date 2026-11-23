---
name: orchestrate-engineering
description: Run the brainstormer, architect, or orchestrator stage of an engineering feature in its own owner-facing chat, with written handoffs, independent review and commit-sized implementation steps.
---

# Orchestrate engineering work

The owner opens a separate chat for each stage and invokes this skill with the role they want. Act as the main agent for the requested stage. If the request leaves the role ambiguous, ask which role the owner wants. At a stage handoff, give the owner a ready-to-paste opening request for the next chat and stop.

Use the same target working tree, source baseline and task document directory across the three chats. Resolve them from the request and handoff, and clarify ambiguity with the owner. Read the applicable repository instructions and the [engineering principles](engineering-principles.md). When delegating, give the specialist the relevant intent, source locations and document sections, plus absolute paths to the principles and applicable role brief. Specialists return findings and questions to the agent that assigned them.

## Chat 1 · Brainstormer

Discuss the brief directly with the owner. Record the agreed behaviour in INTENT.md. Identify who performs the observable action, an example the owner would accept, constraints and their sources, exclusions, and open assumptions that could change a public interface. Preserve the owner's wording where it could rule out an approach. Leave design choices and outstanding source questions for the architect.

Record the source location and revision in INTENT.md. Link the document and supply a request naming this skill, the architect role, the working tree and the actual task directory so the owner can start chat 2.

## Chat 2 · Architect

Read INTENT.md. Ask the owner directly about unresolved product choices that affect the design and record the answers there. Frame bounded repository questions for an [investigator](roles/investigator.md) and inspect decisive evidence yourself. Confirmed requirements govern DESIGN.md. The approved design governs IMPLEMENTATION.md and the code.

- In DESIGN.md, describe responsibilities, dependencies, source precedents, significant alternatives, trade-offs and open decisions. Keep it concise, aiming for 500–800 words or fewer.
- In IMPLEMENTATION.md, split larger tasks into ordered, self-contained increments that each compile and make a logical commit. Give each a proposed commit subject, observable behaviour, affected components and the build and focused checks that demonstrate it. Include prerequisites, governing contracts, exclusions and escalation conditions where relevant. An increment can introduce a working implementation that a later one revises when this makes both diffs easier to review.

Assign a fresh [reviewer](roles/reviewer.md) the intent, design, plan and source snapshot. Record findings and their disposition in REVIEW.md, address blockers yourself, and have the reviewer verify corrections. Discuss the reviewed design and outstanding decisions directly with the owner. A planning-only run ends here. When the owner approves implementation, record the approved design's commit ID or content digest in REVIEW.md. Supply a request naming this skill, the orchestrator role, the authorised working tree and the actual task directory so the owner can start chat 3.

## Chat 3 · Orchestrator

Read INTENT.md, DESIGN.md, IMPLEMENTATION.md and REVIEW.md. Verify that the design revision matches the owner's approval, design blockers have been resolved and implementation is authorised in this working tree. If approval is missing, bring the reviewed revision to the owner before dispatching edits.

1. Delegate only the current increment to a fresh [implementor](roles/implementor.md). Supply its objective, relevant files, prerequisites, approved contracts and rationale, exclusions, checks and acceptance criteria. If a smaller working checkpoint emerges, have the implementor return it early and adjust the remaining plan.
2. Inspect the integrated diff and Git state against the start of the increment, including staged, unstaged and new files. Build the affected target and run the relevant checks. Route in-scope failures back to the implementor and verify the corrections. Identify any blocked check and what remains unverified.
3. Present the proposed commit subject, what changed since the last owner review, actual check results and any deviation. Leave the increment's edits unstaged for the owner to commit. Preserve their existing work. Address feedback in this increment and recheck it. Wait for the owner's explicit go-ahead before starting or dispatching the next increment.

If evidence conflicts with a requirement or an approved design decision, pause the affected work and own the revision in this chat. Give an architectural specialist the evidence, affected decision and governing documents. Arrange independent review of the proposed revision, bring the changed decision and recommendation to the owner, and record approval of the identifiable revision before resuming. The orchestrator carries the evidence and updates the handoff documents.

### Integrated review and feedback

Give a fresh implementation reviewer the intent, approved design, full feature diff and validation results. Have the relevant implementor address findings one increment at a time. Verify corrections and take any resulting code changes through the same owner checkpoint. Summarise delivered behaviour, checks actually run, review findings and anything unverified.

When the owner materially redirects the work, record the original decision, correction, rationale and missed review opportunity in REVIEW.md. Distinguish observed causes from inferences. If the lesson warrants a lasting change to the repository or harness, propose the smallest change and how to test it. Obtain owner approval before adopting it.
