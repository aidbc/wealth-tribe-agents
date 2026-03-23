---
description: Write a structured user story from notes, context, or attached design screens
argument-hint: "<feature name or short description>"
---

# /write-user-story — User Story Writer

Turn rough notes, ideas, or design screens into a well-structured user story ready for your backlog. Combines your input with relevant product and technical knowledge to produce a complete, actionable story.

## Invocation

```
/write-user-story Add a dark mode toggle to the settings screen
/write-user-story [paste your notes or bullet points]
/write-user-story [attach a design screen or mockup]
/write-user-story [attach a screen + paste notes]
/write-user-story                                    # asks for feature details interactively
```

## What You Can Provide

- **Notes** — raw bullet points, Slack messages, meeting summaries, anything goes
- **Design screens** — attach images of mockups, Figma exports, or wireframes
- **Both** — notes and screens together give the richest output
- **Just a feature name** — Claude will use project knowledge from previous threads and its knowledge to fill in context

---

## Workflow

### Step 1: Accept Input

Accept input in any form:
- Freeform notes or bullet points
- A feature name or one-liner
- Attached design screens (images)
- A combination of the above

If nothing is provided, ask:
- "What feature or task are you writing this story for?"
- "Do you have any notes or a design screen to share?"

### Step 2: Clarify if Needed

If the input is ambiguous or missing key context, ask targeted questions — no more than 2-3 at a time:
- Who is the primary user of this feature?
- What problem does this solve for them?
- Are there any known constraints (platform, permissions, tech stack)?

If the input is clear, proceed without asking.

### Step 3: Generate the User Story

Produce a complete user story using the structure below.

---

## Output Structure

```
## User Story: [Short Title]

### Story
**As a** [user type], **I want** [capability or action], **so that** [benefit or outcome].

---

### Context / Background
[1–3 sentences explaining why this story exists. Include the user problem, business motivation, or product goal. Reference the design screen or notes if provided.]

---

### Acceptance Criteria
- [ ] [Criterion 1 — observable, testable behaviour]
- [ ] [Criterion 2]
- [ ] [Criterion 3]
- [ ] [Criterion 4 — include edge cases and error states where relevant]

---

### Technical Notes *(optional)*
[Only include if there are meaningful technical implications: API dependencies, data model changes, platform constraints, performance considerations, or work that needs a spike. Omit this section if not applicable.]

---

### Other Notes *(optional)*
[Anything that doesn't fit above: open questions, design references, out-of-scope items, follow-up stories to consider. Omit this section if not applicable.]
```

---

## Writing Guidelines

**Story line**
- Use the format: "As a [user type], I want [capability], so that [benefit]"
- Be specific about the user type — avoid "user" if a more precise role applies
- The benefit should describe real value, not just echo the capability

**Context / Background**
- Explain *why* this story exists, not just *what* it does
- Connect to a user problem, business goal, or product principle
- If a design screen is attached, reference what it shows

**Acceptance criteria**
- Each criterion must be independently testable by QA
- Cover the happy path, key edge cases, and error states
- Write in present tense: "The user can…", "The system displays…"
- Aim for 3–6 criteria — enough to define done, not a full test plan

**Technical Notes**
- Only include if there's something a developer genuinely needs to know upfront
- Flag spikes: if technical investigation is needed before the story can be estimated, say so
- Keep it brief — this is a heads-up, not a tech spec

**Other Notes**
- Use for things that are true but don't fit elsewhere
- Good candidates: design file links, out-of-scope reminders, follow-up story ideas, unresolved questions

---

## After Generating

Offer relevant next steps based on the story:

- "Want me to **write acceptance test scenarios** for this story?"
- "Should I **break this into smaller stories** if it feels too large for one sprint?"
- "Want me to **add a technical spike story** for any uncertain parts?"
- "Should I **write a second story** for the error or empty state?"

---

## Notes

- One story = one deployable unit of value. If the story only makes sense after another story ships, consider combining them or making the dependency explicit.
- Technical Notes and Other Notes are intentionally optional — don't invent content to fill them.
- If a design screen is attached, use it: reference specific UI elements, flows, or states visible in the screen.
- If the feature is large enough to warrant multiple stories, say so and offer to generate the full set using `/write-stories`.
