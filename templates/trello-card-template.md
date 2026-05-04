# Trello Card Template

Copy this template for each new task card created during the Trello step.
Replace all {{PLACEHOLDER}} values before creating the card.

---

**Title:** `[SPEC-{{SPEC_NUMBER}}] {{SHORT_DESCRIPTION}}`

**List:** 📋 Backlog

**Labels:** {{LABELS — choose from: Backend, Mobile, Frontend, UI/UX, DevOps, Business}}

---

**Description:**

```markdown
## What
{{ONE_SENTENCE_DESCRIBING_WHAT_THIS_TASK_DELIVERS}}

## Spec reference
Spec: {{SPEC_NUMBER}} — {{SPEC_NAME}}
Task: T{{TASK_NUMBER}} from tasks.md

## API Endpoint
{{IF_BACKEND_LABEL}}
[{{METHOD}} {{PATH}}]({{APIDOG_SHAREABLE_URL}})
{{ELSE — remove this section if not a backend task}}

## Design reference
{{IF_MOBILE_OR_FRONTEND_LABEL}}
[{{SCREEN_NAME}}]({{FIGMA_FRAME_URL}})
{{ELSE — remove this section if no design reference}}

## Pre-conditions
- {{PRE_CONDITION_1}}
- {{PRE_CONDITION_2}}

## Implementation notes
- {{KEY_DECISION_FROM_SPEC_PLAN}}
- {{CONSTRAINT_OR_GOTCHA}}

## Done condition
{{EXACT_DONE_CONDITION_FROM_TASKS_MD}}

## Simulation mode
{{WHICH_FLAGS_APPLY — e.g. "EMAIL_SIMULATION=true required" or "N/A"}}
```
