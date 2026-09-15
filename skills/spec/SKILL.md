---
name: spec
description: Turn a scope file into a technical specification grounded in the repo, saved to docs/spec-<feature-name>.md.
disable-model-invocation: true
---

# Spec

Turn the given scope into a design another engineer or agent can implement without the conversation.

This skill ends with the specification. Task slicing and implementation are not part of this skill.

If no repo can be found, inform the user about that fact and assume that the current working directory is equivalent to the repo for the purpose of this skill.

## 1. Read the scope

Read the supplied scope file in full. If none is given, look for `docs/scope-*.md` - ask the user to choose when the intended file is unclear.

## 2. Stop early if the scope is missing or unconfirmed

If no scope file was found, stop this skill and ask the user to run the scope skill to create one first.

If the scope is not `Status: Confirmed`, stop and ask the user to finish scoping first.

If the scope has open questions, stop and ask the user to finish scoping first.

## 3. Ground the specification file in facts
Treat the scope file's requirements, acceptance criteria, constraints, and exclusions as the boundary. Keep its R and AC IDs.

Read repo instructions, relevant architecture decisions, code, and tests. Use the project's terms and existing patterns. Stop investigating when further detail cannot affect the design or its verification. Cite existing behavior with file paths and symbol or test names.

## 4. Resolve the design

Choose the simplest design that satisfies the full scope. Define component responsibilities, interactions, and contracts. Cover data changes, permissions, failures, concurrency, and operating constraints where the scope requires them. Include migration and compatibility decisions when existing data or consumers are affected.

Explain consequential choices and why credible alternatives lose. Resolve technical facts from evidence. Ask the user only about decisions that evidence cannot settle and that materially change the design. Give a recommendation and trade-off, then wait for the answer before making dependent design decisions. Record unanswered decisions in the "Unanswered decisions" section.

If the design requires a scope change, surface the conflict to the user. Preserve existing work and stop. Do not edit the scope. Ask the user to update it with the scope skill, then rerun spec.

## 5. Write the specification

Use the requested path or `docs/spec-<feature-name>.md` as default, matching the scope's feature name. If the scope's filename does not follow `scope-<feature-name>.md`, derive a short, hyphenated feature name from its title or content. Update an existing spec when requested, otherwise ask before replacing it and preserve it while awaiting an answer.

Start with the title, a link to the source scope, and `Status: Draft`. 

Always include Overview, Design, Verification and Unanswered decisions. Adapt or omit other headings to fit the work.

- **Overview:** the intended change and a brief description of the design.
- **Design:** components, data flow, contracts, state changes, and failure behavior, tied to R IDs. State exact inputs, outputs, errors, and invariants where needed. Use a small schema, example, or diagram only when it is clearer than prose. Distinguish current behavior from proposed changes.
- **Decisions:** consequential choices and reasons. Mark unverified assumptions explicitly.
- **Verification:** map every acceptance criterion (by AC ID) to an observable result and a test or other check. Prefer existing public interfaces and test patterns. Name where behavior can be exercised. Add a new test boundary only when existing ones cannot verify it.
- **Migration and operations:** required data conversion, compatibility, recovery, and operational checks.
- **Unanswered decisions:** unresolved requirements, design decisions, and assumptions, with their impact and what would resolve them. Write "None" when empty.

Link to scope details instead of duplicating them. Include enough context to understand each technical decision. Keep exact identifiers and contracts; omit speculative file inventories and implementation walkthroughs.

## 6. Check and save

Verify that every R ID has design coverage, every AC ID has a verification method, and all references resolve. Check the design against constraints and exclusions. Remove unsupported claims and resolve contradictions or record them as unanswered decisions.

Set `Status: Confirmed` only when coverage is complete and no open questions or unanswered decisions remain. Otherwise retain the draft status and name the blockers.

Save the file and link it. 

## 7. Failsafe

If file access is unavailable, return the document text and state why it was not saved.
