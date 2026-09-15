---
name: scope
description: Scope repository work through relentless questioning until every requirement is clear. Use when defining a feature, exploring a request, or planning any new work.
---

# Scope

Gather extensive requirements through relentless questioning and brainstorming with the user. Ground the discussion in the repo and record the entire agreed scope in `docs/scope.md`, unless the user specifies another location.

This skill ends with the scope document. Slicing, cutting scope, preparing tickets, implementation, and delivery planning are outside its remit.

## 1. Ground the request

Identify who needs the change, what they cannot do today, and what they should be able to do afterward.

Read the repo's instructions, relevant docs, code, and tests. Trace the affected flow, its callers, and dependencies. Cite evidence for current behavior. If repo access is missing, request it and continue questions that do not depend on inspection.

Finding facts is your job. Investigate what the repo can answer; ask the user for goals and decisions. Keep questions that depend on unfinished research pending while advancing the rest.

Establish a concrete before/after example and the constraints that could change the work.

## 2. Grill in rounds

Map a decision tree. Each answer can unlock further decisions. Keep track of resolved questions, unanswered questions, and dependencies.

In each round, ask every unresolved question whose prerequisites are settled. Number the questions. Prefer multiple options per question, marking exactly one with "(recommended)" and explaining why. When multiple options would not help, give one reasonable recommendation with clear reasoning. Wait for answers before asking dependent questions. Carry unanswered questions forward; silence is not agreement.

After each round, update the tree and probe the answers. Resolve vague terms against the repo's vocabulary. Challenge contradictions with code evidence or concrete counterexamples. For example, does cancelling one item cancel its whole order? Replace "simple", "fast", and "later" with explicit behavior, limits, or exclusions.

Brainstorm with the user when the desired behavior is unclear. Offer concrete possibilities, explain trade-offs, and explore the implications of their choices. Treat suggestions as proposals until accepted. Expand the requirements as needed to capture the full intent.

Work through every applicable branch:

- Users, problem, desired outcome, and why the work matters.
- All requested behavior and explicit exclusions agreed with the user.
- Domain terms, ownership, relationships, and state changes.
- Entry points, affected components, interfaces, and dependencies.
- Permissions, invalid input, failure, retries, concurrency, and edge cases.
- Data requirements, compatibility, retention, and recovery expectations.
- Performance, accessibility, security, operational visibility, and other constraints.
- Acceptance criteria and concrete examples of success and failure.

Revisit settled answers only when new evidence conflicts with them. A branch closes through an answer, repo evidence, or an explicit user decision to exclude it. Recommendations and assumptions remain open until accepted. If the user delegates a decision, make it, record the reason, and inspect what it unlocks.

Continue until every branch is resolved and no question or investigation remains pending. An empty round caused by blocked dependencies is not completion.

## 3. Write scope.md

Use `scope.md` to capture requirements, not to decide roles, permissions, user stories, data modeling, API contracts, or other technical implementation details.

Write the complete scope to `docs/scope.md` at the repo root, creating `docs/` if needed. Use the user's requested path when provided. Read an existing file before updating it and preserve relevant agreed requirements.

Capture the entire scope discussed, including supporting requirements and edge cases. Consolidate repeated answers and retain the final decision when an earlier answer was superseded. Distinguish agreed requirements from ideas the user rejected or explicitly excluded.

Use the following structure, adapting headings to the work:

- **Purpose and context:** users, problem, current behavior, and intended outcome.
- **Requirements:** the full agreed behavior, workflows, and concrete examples.
- **Boundaries:** explicit exclusions and interactions with existing functionality.
- **Domain and data:** terms, relationships, ownership, and state changes.
- **Interfaces and dependencies:** affected systems and required interactions.
- **Constraints and quality requirements:** agreed limits and operating expectations.
- **Failure and edge cases:** expected behavior when the normal flow breaks down.
- **Acceptance criteria:** observable conditions that establish each requirement is met.
- **Decisions and rationale:** agreed choices, reasons, and accepted assumptions.

Write requirements precisely enough for another reader to understand the work without the conversation. Describe required outcomes and constraints; leave task breakdowns, execution steps, and scheduling to later work.

## 4. Check completeness

Check the document against the entire discussion. Account for every agreed requirement, give each an acceptance criterion, and resolve contradictions, omissions, and vague language through further questions. Keep the document marked as a draft while questions remain.

Link the written file and ask the user to confirm that it captures the full scope. Corrections reopen the relevant branches and update the file. Finish when no scope questions remain, the user confirms the document, and `scope.md` contains the complete agreed requirements.
