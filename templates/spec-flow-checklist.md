# Spec Flow Checklist

Use this checklist for every spec from specify through to done.
Copy it into the spec folder as `checklist.md` and tick off each item.

## Before speckit.specify

- [ ] Feature is understood and scoped
- [ ] No existing spec covers this feature (check .specify/specs/)

## speckit.specify

- [ ] `/speckit.specify` run with full feature description
- [ ] Spec covers: what, why, acceptance checklist, out-of-scope list
- [ ] File exists: `.specify/specs/{number}-{name}/spec.md`

## speckit.clarify

- [ ] `/speckit.clarify` run — all open questions answered
- [ ] Every clarification is marked "Closed" — no open decisions
- [ ] File exists: `.specify/specs/{number}-{name}/clarifications.md`

## speckit.plan

- [ ] `/speckit.plan` run with full tech stack
- [ ] Plan includes: models, services, API contract, error codes, data flow
- [ ] File exists: `.specify/specs/{number}-{name}/plan.md`

## speckit.tasks

- [ ] `/speckit.tasks` run — ordered, dependency-aware task list
- [ ] Each task has: file path, done condition, dependency list
- [ ] File exists: `.specify/specs/{number}-{name}/tasks.md`

## Apidog step (skip if no new API endpoints)

- [ ] New endpoints identified from plan.md
- [ ] Each new endpoint created in Apidog via MCP with full schemas
- [ ] Shareable URL retrieved for each endpoint (new and existing)
- [ ] URLs stored and ready for Trello card descriptions

## Trello step

- [ ] Existing board cards read — no duplicate titles
- [ ] One card created per logical task in Backlog
- [ ] Each card has: correct title format, full description, done condition
- [ ] Each card has at least one label: Backend/Mobile/Frontend/UI/UX/DevOps/Business
- [ ] Backend cards include Apidog URL
- [ ] Mobile/Frontend cards include Figma frame URL
- [ ] Simulation flags noted where applicable

## speckit.implement

- [ ] `/speckit.implement` run
- [ ] All tasks executed in dependency order
- [ ] Acceptance checklist from spec.md fully passed
- [ ] No TODO comments in committed code
- [ ] Tests written alongside implementation

## After implementation

- [ ] Developer moves Trello cards from Backlog → Working On → Testing
- [ ] QA verifies all test cases
- [ ] QA moves cards from Testing → Done
- [ ] PR opened and merged
- [ ] openapi.yaml regenerated if API contract changed
