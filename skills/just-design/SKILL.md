---
name: just-design
description: Resolve UI/UX decisions with the user after scope is confirmed, then save the agreed design to docs/design-<feature-name>.md.
disable-model-invocation: true
---

# Just Design

Turn a confirmed scope into an agreed UI/UX design for customer or internal interfaces. Always write a design document when invoked; add mockups when they help settle decisions. End with the document. Technical architecture, task slicing, and production implementation belong to later work.

## 1. Establish the boundary

Read the supplied scope in full, or find `docs/scope-*.md` and ask which one when unclear. If missing, unconfirmed, or carrying open questions, stop and ask the user to finish scope first.

Keep its R and AC IDs, constraints, and exclusions. If a design decision requires changing requirements, explain the conflict, preserve the design as a draft, and ask the user to update scope before continuing dependent work. Leave the scope file unchanged.

Use the requested output path or `docs/design-<feature-name>.md`, matching the scope's feature name. For other filenames, derive a short hyphenated name from the content. Check the target early. Update when requested, otherwise ask before replacing an existing document. If no repo exists, tell the user and use the current directory.

## 2. Inspect the experience

Read repo instructions and inspect affected journeys, screens, components, design tokens, and existing design guidance. View the current interface when available. Distinguish observed behavior from code evidence. Cite file paths and component or symbol names. Resolve factual questions through inspection before asking the user.

Determine whether the scope changes anything a person sees or does, including staff tools, messages, and interaction behavior. If none does, write a short document linking the scope, with `Status: Not needed`, the evidence for that conclusion, and any limitations. Finish there. Uncertain impact is an open question, not grounds to skip.

## 3. Resolve decisions with the user

Map the open decisions and their dependencies. Ask in rounds of at most 7 questions, using stable IDs DQ1, DQ2, and so on. Ask only questions whose answers change the experience. Carry forward settled scope answers; reopen them only when conflicting evidence appears.

Offer concrete options with trade-offs and one recommendation where evidence supports it. For matters of taste or goals, ask for the user's preference. Turn words such as "intuitive" or "modern" into examples and observable choices. Treat proposals as unsettled until accepted; silence is not agreement. Wait for answers before resolving dependent choices.

Cover every relevant branch:

- **Journey:** actor, entry point, task sequence, navigation, primary action, completion, cancellation, and recovery.
- **Content:** information order, labels, instructions, representative data, and what each role can see or act on.
- **Behavior:** control states, validation timing, feedback, loading, empty results, partial success, errors, and destructive actions.
- **Presentation:** existing conventions to retain, desired direction, references and what to borrow from them, density, and layout.
- **Access and adaptation:** keyboard and focus behavior, assistive technology, contrast, touch, reduced motion, supported sizes, themes, and long or translated content where relevant.

Scale the discussion to the change. A label edit needs a wording decision; a new workflow needs its full journey resolved. An existing convention can settle a detail when evidence shows it applies. New choices need user acceptance, individually or as a concrete proposal. Explicit delegation permits recommendations within the delegated bounds; record that delegation and its resulting choices.

## 4. Use what already exists

When designing interface and frontend elements always take into account what the project already has. Use estabilished design system if one exists. Follow the cues and patterns already present in the repo. Default to native solutions and fallback on primitives. Design custom solution should only be done as last resort.

## 5. Principles of the proposal

- Start with the person's task and the product's subject matter. Explain why the direction fits. Preserve established identity and give new surfaces character through purposeful choices.
- Give each view a clear priority. Use grouping, proportion, type, and spacing to guide attention. Choose density for the work being done.
- Reuse existing controls and semantic tokens. For additions, specify a coherent palette, type scale, spacing, surfaces, and depth, with concrete values where needed.
- Write labels that name actions and feedback that explains the result and next step. Keep terms consistent throughout the journey.
- Use motion to explain change. Include the relevant interaction and data states in the proposal.

## 6. Show it if you can
Use visual or inline-rendering tools and skills if the are available in the session (tools or skills that allow rendering HTML or SVG content, preferably inline on in a built in browser/visualization space).

Use a wireframe, visual mockup, or disposable prototype when text leaves a consequential choice ambiguous. Show realistic content and the states or sizes needed to judge that choice. Label invented sample content. Inspect rendered mockups when tools permit, otherwise use an annotated wireframe and state what remains visually unverified. Keep mockups separate from production code.

Walk through the proposed journey with the user. Check whether the main action is apparent, the information supports it, and failure paths let the person recover. Revise any choice justified only by habit. Close every relevant branch through user acceptance, applicable evidence, or an explicit exclusion consistent with scope. Preserve unanswered questions.

## 7. Save and confirm

Write the document with a title, a link to the scope, and `Status: Draft`. Include:

- **Experience:** affected actors, surfaces, journeys, and design decisions with stable DD1, DD2, ... IDs tied to relevant R IDs.
- **Presentation and behavior:** agreed layout, content, controls, states, accessibility, and adaptation rules. Link existing patterns and supporting mockups; record their authority if illustrations omit detail.
- **Decisions and rationale:** accepted choices, reasons, delegated decisions, and rejected alternatives.
- **Verification:** observable design checks tied to relevant AC IDs. Account for every scoped R and AC ID with design coverage or a reason it has no UI/UX impact.
- **Open questions:** unanswered DQ IDs, dependencies, and what resolves them. Write "None" when empty.

Keep the document understandable without the conversation. Reference scope instead of copying it. Reconcile mockups and prose so they describe the same experience.

Check the document against all agreed answers and scope constraints. Link it and ask the user to confirm it. Set `Status: Confirmed` only after that confirmation, complete coverage, and no open questions or unaccepted assumptions. Revisions return it to draft. If the user stops early, save the draft with its open questions and stop.

## 8. Failsafe

If file access is unavailable, return the document text and explain why it was not saved.
