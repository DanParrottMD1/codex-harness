---
name: pilot-a-lead
description: Run arm A of the engineering workflow pilot when the user selects the continuous lead, investigator, and reviewer approach.
---

# A · Continuous lead

Read the [shared pilot agreement](../pilot-agreement.md). You are the lead. Keep the same conversation from clarification through delivery. Use native subagents for investigation and review. Own the design decisions, implementation, and user interaction yourself.

## Establish intent and investigate

Start from the supplied feature brief. Ask the user about gaps that could change observable behaviour, compatibility, scope, or acceptance. Keep the answers and open questions in this thread. Resolve questions answerable from code through investigation.

Delegate using the [investigator brief](../roles/investigator.md). Supply the confirmed source snapshot, feature intent, and specific questions tied to the decisions you face. Inspect the cited code yourself where a decision turns on an inference.

## Design, review, and approval

Write DESIGN.md and a short task outline. Delegate design review to a fresh agent using the [reviewer brief](../roles/reviewer.md). Supply the confirmed requirements, repository snapshot, design, and outline. Capture its findings and your disposition in REVIEW.md. Correct blockers and have the reviewer verify the affected decisions. Bring unresolved trade-offs to the user.

Present the reviewed design for the approval described in the shared agreement. After approval, expand the outline into IMPLEMENTATION.md. Check each task against the approved design. If detailing a task exposes a missing consequential decision, reopen that decision before editing code.

## Deliver

Implement the bounded tasks sequentially in this thread. Run each task's checks and the relevant integrated checks. Delegate implementation review to a fresh agent using the [reviewer brief](../roles/reviewer.md), with the requirements, approved design, actual diff, and validation results. Resolve concrete defects, rerun affected checks, and record the outcome in REVIEW.md. Close with the evidence and correction record specified in the shared agreement.
