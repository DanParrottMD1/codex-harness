---
name: pilot-b-handoffs
description: Run the selected brainstormer, architect, or orchestrator chat in arm B of the engineering workflow pilot, using file handoffs between three top-level chats.
---

# B · Three specialised chats

Use this skill in three separate top-level chats opened by the user. Act as the role named in the current request and execute only that stage. If the role is unclear, ask which stage the user wants. Read the [shared pilot agreement](../pilot-agreement.md). Use the same B source snapshot and task document directory across all three chats.

## Chat 1 · Brainstormer

Discuss the initial feature brief directly with the user. Explore observable behaviour, side effects, changes to existing functionality, constraints, and exclusions. Leave implementation choices to the architect. End questioning when remaining unknowns can be investigated in source, deferred, or recorded as open decisions.

Write INTENT.md in the task directory. Preserve confirmed requirements, concrete acceptance examples, constraints and their reasons, and unresolved questions. Where a detail could rule out an approach, preserve the user's relevant words or label it as the brainstormer's proposal. Drop discarded discussion unless the reason for rejection constrains the design. Identify the agreed source location and revision so a fresh chat can find the same evidence.

End with a link to INTENT.md and a ready-to-use request for a new chat that names this skill, the architect role, and the actual task directory. The intent report is the handoff.

## Chat 2 · Architect

Read INTENT.md. Clarify consequential product gaps directly with the user and record the answers there. Frame the repository questions before choosing a solution. Delegate using the [investigator brief](../roles/investigator.md), with the source snapshot, relevant intent, and the decisions those questions inform. Follow up or inspect decisive references yourself.

Write DESIGN.md and IMPLEMENTATION.md. Preserve the first submitted design for comparison. Delegate design review to a fresh agent using the [reviewer brief](../roles/reviewer.md), with the intent, source snapshot, design, and plan. Have it write findings to REVIEW.md. Address each blocker and ask the reviewer to verify the revision. Present any unresolved trade-off to the user when further review needs their judgment.

Present the reviewed DESIGN.md to the user. A planning-only run ends here. For implementation, record the user's explicit approval against the specific design revision in REVIEW.md. Hand off the task directory and authorised working-tree location in a ready-to-use request for a new orchestrator chat. Leave the decision to open that chat to the user.

## Chat 3 · Orchestrator

Read INTENT.md, DESIGN.md, IMPLEMENTATION.md, and REVIEW.md from the handoff directory. Before delegating edits, verify that the design matches the recorded approval, blockers are resolved, and the user has authorised implementation in the identified working tree. If design approval is still pending, present that revision to the user for a decision.

Own task order, progress, integration, and retries. Delegate each ready task in a fresh context using the [implementor brief](../roles/implementor.md). Supply its objective, files and repository guidance, prerequisites, approved contracts and their rationale, exclusions, checks, acceptance criteria, and paths to the governing documents. Keep a failing task with its implementor while the fix stays within scope. If it conflicts with an approved decision, pause the affected work, record the conflict, and give the user a concise handback for the architect chat. Resume after the revised decision is reviewed and approved.

Run tasks sequentially by default. Parallelise only when prerequisites are satisfied, write ownership is disjoint, and each task can be verified independently. Check the integrated result and delegate implementation review to a fresh agent using the [reviewer brief](../roles/reviewer.md), with the intent, approved design, diff, and validation results. Route findings to the relevant implementor, verify corrections, and close under the shared agreement.
