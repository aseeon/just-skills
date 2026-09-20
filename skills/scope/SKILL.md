---
name: scope
description: Scope a feature or change by questioning the user and inspecting the repo, then write the agreed requirements to docs/scope-<feature-name>.md.
disable-model-invocation: true
---

# Scope

Gather extensive requirements through relentless questioning and brainstorming with the user. Ground the discussion in the repo and record the entire agreed scope in `docs/scope-<feature-name>.md`, unless the user specifies another location.

This skill ends with the scope document. UI/UX design, architecture, program design, slicing and preparing tickets, implementation, quality assurance and delivery planning are outside its responsibilities.

Record exclusions the user chooses. Do not propose cuts, smaller versions, or phases.

If no repo can be found, inform the user about that fact and assume that the current working directory is equivalent to the repo for the purpose of this skill.

## 1. Ground the request

Read the repo's instructions, relevant docs, code, and tests. Read only enough to describe current behavior relevant to the feature or change being scoped and answer factual questions. Stop tracing a path once it no longer affects a requirement. Cite evidence as file paths with the function, class, or test name.

Check the target path as soon as the feature name is settled, using the user's requested path or `docs/scope-<feature-name>.md` by default. If the user supplies a path up front, check it immediately. Update an existing scope when requested, otherwise ask before replacing it. Preserve the existing file while awaiting the answer.

Finding facts is your job. Investigate what the repo can answer. Ask the user for goals and decisions. Keep questions that depend on unfinished research pending while advancing the rest.

## 2. Grill in rounds

### Round format

Map a decision tree. Each answer can unlock further decisions. Give each question a stable ID (Q1, Q2, ...) and keep it across rounds. Show only the questions being asked in the current round.

Ask a question only if its answer would change a requirement, a boundary, or an acceptance criterion. Drop questions that would only affect technical specification or implementation.

Ask at most 7 questions per round. Choose questions whose prerequisites are settled and whose answers unlock the most other decisions. In the first round, ask who needs the change and for a concrete before/after example, unless already answered.

Prefer multiple options per question, marking exactly one with "(recommended)" and explaining why. When multiple options would not help, give one reasonable recommendation with clear reasoning. Skip the recommendation when the question is about the user's goals or priorities and the repo gives no basis for one.

Wait for answers before asking dependent questions. Carry unanswered questions forward; silence is not agreement.

### Probing answers

After each round, update the tree and probe the answers. Resolve vague terms against the repo's vocabulary. Challenge contradictions with code evidence or concrete counterexamples. For example, does cancelling one item cancel its whole order? Replace "simple", "fast", and "later" with explicit behavior, limits, or exclusions.

Brainstorm with the user when the desired behavior is unclear. Offer concrete possibilities, explain trade-offs, and explore the implications of their choices. Treat suggestions as proposals until accepted. Add a requirement only after the user accepts it.

### Coverage checklist

Use this checklist to find questions. Apply the relevance filter to each one before asking it.

- Users, problem, desired outcome, and why the work matters.
- All requested behavior and explicit exclusions agreed with the user.
- Domain terms, ownership, relationships, and state changes.
- Entry points, affected components, interfaces, and dependencies.
- Permissions, invalid input, failure, retries, concurrency, and edge cases.
- Data requirements, compatibility, retention, and recovery expectations.
- Performance, accessibility, security, operational visibility, and other constraints.
- Acceptance criteria and concrete examples of success and failure.

### Closing branches

Revisit settled answers only when new evidence conflicts with them. A branch closes through an answer, repo evidence, or an explicit user decision to exclude it. Recommendations and assumptions remain open until accepted.

Continue until every relevant branch is resolved and no question or investigation affecting requirements remains pending. If every open question is blocked, finish the research that blocks them, or ask about the unanswered prerequisites.

If the user asks to stop or to write the document before all branches close, write it. List every unresolved item under "Open questions" and keep the draft status. End the questioning as requested.

## 3. Write scope-<feature-name>.md

Record permissions, data, and interfaces as required behavior. For example, "Only the person who placed an order can cancel it." Leave role models, schemas, API shapes, and user stories to later work.

Write the complete scope to the target path established in section 1, creating its parent folder if needed. For an existing document about the same work, preserve agreed requirements unless superseded.

Start the file with "Status: Draft". An updated scope returns to "Status: Draft". Change it to "Status: Confirmed" only after the user confirms the document and there are no open questions left.

Capture the entire scope discussed, including supporting requirements and edge cases. Consolidate repeated answers and retain the final decision when an earlier answer was superseded. Distinguish agreed requirements from ideas the user rejected or explicitly excluded.

Draft acceptance criteria from the agreed requirements. The user's confirmation of the document accepts them.

Always include Requirements, Acceptance criteria, and Open questions. Adapt or omit other headings to fit the work.

- **Purpose and context:** users, problem, current behavior, intended outcome, and repo evidence cited as file paths with the function, class, or test name.
- **Requirements:** the full agreed behavior, workflows, and concrete examples, numbered R1, R2, and so on. Number required behavior in "Constraints and quality requirements" and "Failure and edge cases" from the same sequence. Keep IDs stable through revisions.
- **Boundaries:** user-chosen exclusions, interactions with existing functionality, and a "Rejected ideas" subsection.
- **Domain and data:** terms, relationships, ownership, and state changes.
- **Interfaces and dependencies:** affected systems and required interactions.
- **Constraints and quality requirements:** agreed limits and operating expectations.
- **Failure and edge cases:** expected behavior when the normal flow breaks down.
- **Acceptance criteria:** observable conditions that establish each requirement is met, each with a unique, stable ID (AC1, AC2, and so on) and references to the applicable requirement IDs. Keep IDs stable through revisions.
- **Decisions and rationale:** agreed choices, reasons, and accepted assumptions.
- **Open questions:** unresolved items with their question IDs, dependencies, and what would resolve them; write "None" when empty.

Write requirements precisely enough for another reader to understand the work without the conversation. Describe required outcomes and constraints; leave task breakdowns, execution steps, and scheduling to later work.

## 4. Check completeness

Check the document against the entire discussion. Account for every agreed requirement. Verify that each acceptance criterion has a unique AC ID, every requirement ID has an acceptance criterion, and every acceptance reference points to an existing requirement. Resolve contradictions, omissions, and vague language through further questions, unless the user stopped early; then record them under "Open questions".

Link the written file and ask the user to confirm that it captures the full scope. Corrections reopen the relevant branches and update the file. Finish when no relevant scope questions remain, the user confirms the document, and the file contains the complete agreed requirements with no open questions left. 

If the user stopped early, hand back the draft with its open questions and stop.

## 5. Failsafe

If file access is unavailable, return the document text and state why it was not saved.
