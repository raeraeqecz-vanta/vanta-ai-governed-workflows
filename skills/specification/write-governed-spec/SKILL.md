---
name: write-governed-spec
description: Turn an Owner request and confirmed project context into a governed specification, contract, amendment, or implementation handoff. Use when asked to formalize requirements, freeze a design, reconcile a proposed change with an approved baseline, define acceptance criteria, or prepare scoped execution instructions. Preserve authority boundaries; writing a spec does not authorize implementation.
---

# Write Governed Spec

Turn conversational requirements and confirmed sources into a specification that another person or agent can follow without guessing. This is a design and documentation workflow; it does not grant implementation or deployment authority.

## Authority and Scope

- Treat the user as Owner unless they define a different authority.
- Resolve sources in this order: latest explicit Owner instruction; Owner-frozen canon/baseline/amendment; approved specification; reviewed draft; source/reference; assistant inference.
- Apply approval only to the exact document, gate, action, environment, and scope stated. Do not ask again for an already approved action within its approved scope; do not extend that approval to the next gate.
- Keep projects isolated. Do not silently alter frozen content; use an addendum, amendment, new version, or supersession record.
- One ticket should solve one coherent design problem. Split unrelated design problems and record dependencies.

## Workflow

1. **Normalize intent.** State the outcome the Owner wants, preserving their domain terms. Separate requirements from suggestions and assistant inference.
2. **Confirm context.** Use `reconcile-work-context` when context is scattered or authority/current state is unclear. Do not repeat discovery when the relevant sources are already in hand.
3. **Set boundaries.** Define in-scope, out-of-scope, deferred, dependencies, and non-goals. Identify whether the task is design-only, implementation planning, or an explicitly approved execution handoff.
4. **Reconcile canon.** Compare the proposal with frozen baselines and related contracts. Classify each relevant point as `PASS`, `CARRY`, `REWORK`, `CONFLICT`, or `DEFER`. Do not silently resolve real conflicts.
5. **Write the contract.** Include only applicable elements: actors/ownership, entities and identity, states/transitions, inputs/outputs, permissions, provenance, behavior, persistence, errors/edge cases, compatibility, versioning, security boundaries, and operational constraints.
6. **Design verification.** Define acceptance criteria, representative positive and negative cases, required evidence, success condition, and stop conditions. Use measurable statements when possible.
7. **State the gate.** Say exactly what Owner decision is needed, if any. Mark document state accurately (`DRAFT`, `READY FOR OWNER REVIEW`, `OWNER FROZEN`, `BLOCKED`, etc.). Never call a document frozen without approval.
8. **Create the right artifact.** For significant milestones, requested documents, or executor handoffs, create a real Markdown file. Default to Thai–English (TH–EN) unless the Owner directs otherwise. Keep UI language requirements distinct from document language.
9. **Close with handoff.** Report what changed, verification performed, limitations, implementation authority state, and one explicit Next Action.

## Implementation and High-Impact Boundaries

A build contract is not implementation approval. Before code, repository, Roblox Studio, database, runtime, external-service, or hosting mutation, require the relevant preflight and explicit approval where required. Never infer permission to deploy, migrate, change production, secrets, auth, storage, billing, or other high-impact state.

For websites, apps, and code, apply the user's universal **Save Version Before Deploy** control: preserve a recoverable candidate before deployment when supported, and record its identifier/name, time, environment, change summary, and approver when available. If required preflight facts are unknown or unsafe, stop before mutation and report the blocker.

## Document Metadata and Shape

For a formal document, normally record project, document/ticket ID, title, version, type, language, status, date, parent/dependencies, and implementation authorization state. Use only relevant sections, commonly:

1. Purpose and context
2. Scope and non-goals
3. Authority, definitions, and invariants
4. Contract or behavior
5. Compatibility and unresolved decisions
6. Acceptance and verification
7. Stop conditions and required evidence
8. Status, approval request, and Next Action

For executor instructions, include objective, authoritative inputs, allowed/forbidden actions, preflight, target environment, tests, success/stop conditions, evidence/reporting format, and version/deploy controls.

## Stop Conditions

Stop or mark blocked when required authority is missing; two authoritative sources conflict without an Owner decision; environment or target identity is unknown before a mutation; or the request would exceed the approved scope. Continue independent design work where safe, and label assumptions instead of presenting them as fact.

## Shared Context Contract / สัญญาบริบทกลาง

ต้องตรวจบริบท Repository, Source of Truth, Related Skills, Available Connections,
Permission State และทรัพยากรเป้าหมายก่อนสร้าง Spec. หากต้องจัดสร้างทรัพยากร ให้เสนอ
ทางเลือกและรอ Owner Approval / Check the repository, sources of truth, related
skills, available connections, permission state, and target resources before
creating a spec. If a resource must be created, propose options and wait for
Owner approval.
