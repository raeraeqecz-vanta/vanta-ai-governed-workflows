---
name: reconcile-work-context
description: Reconstruct and reconcile scattered work context from the current conversation, user-provided files, or explicitly accessible Library items. Use when asked to summarize prior work, recover project decisions, create a handoff context, verify which source is authoritative, or identify conflicts and unknowns before further work. Keep project boundaries intact and label evidence; do not claim access to unseen account history or systems.
---

# Reconcile Work Context

Recover a reliable, project-scoped view of prior decisions and current task context. Produce an evidence-aware summary or handoff; do not turn it into a formal specification unless requested.

## Workflow

1. **Define the retrieval boundary.** Identify the project, question, date/version range, and permitted sources. Use available conversation context first. When the user refers to a named Library artifact, resolve and read that artifact using the Library skill. Inspect files, systems, or external sources only when the task calls for them and access is available.
2. **Separate projects.** Keep each project's rules, state, approvals, files, runtime, and terminology distinct. Mark an explicitly shared rule as `SHARED`; otherwise assume `PROJECT-ONLY`. Do not transfer authority or implementation state between projects.
3. **Build a source ledger.** For each material claim, record its source and date/version if available. Prefer direct evidence over recollection. Do not treat search snippets as sufficient evidence for claims that require file contents.
4. **Resolve authority.** When sources conflict, apply this order: latest explicit Owner instruction; Owner-frozen canon/baseline/amendment; approved specification; reviewed draft; source/reference material; assistant inference. Do not silently rewrite a higher-authority decision.
5. **Label claim status.** Use `VERIFIED` for direct evidence, `INFERRED` for reasoned conclusions, `UNKNOWN` when evidence is insufficient, and `NOT FOUND` only after an explicit search of stated sources. A missing source or inaccessible history is not `NOT FOUND`.
6. **Classify conflicts and gaps.** Distinguish contradiction, version drift, ambiguity, missing evidence, and non-conflicting difference. Preserve unresolved conflicts as open decisions. Record dependencies and any fact that could change the next action.
7. **Return a usable output.** Choose the lightest useful format: concise context summary, decision register, source/evidence table, or project handoff. For formal handoffs, normally use TH–EN unless the Owner specifies another language. State the coverage boundary and avoid implying that all account history was searched.
8. **Give one Next Action.** Recommend one concrete next step based on the reconciled evidence. Do not execute a mutation simply because it appears as a recommended step.

## Output Pattern

Use relevant sections only:

- Project and retrieval boundary
- Current objective
- Accepted decisions / frozen canon
- Current state, with source and status labels
- Conflicts, unknowns, and deferred items
- Dependencies and constraints
- Handoff / next action

For a simple question, answer directly and omit a formal report. If useful work can proceed despite a gap, proceed on independent parts and mark the limitation.

## Stop Conditions

Stop and report the exact blocker when project identity is ambiguous and cross-project contamination is likely; a source needed for a factual claim is inaccessible; or a decision requires Owner authority. Do not ask the Owner to repeat facts already established in available context. Never infer permission to edit code, runtime, data, access, secrets, billing, or production systems from context-recovery work.

## Shared Context Contract / สัญญาบริบทกลาง

รายงาน Capability และ Resource ที่ตรวจพบ แยกจากสิทธิ์ที่ได้รับเสมอ หากพบ Connection
แต่ไม่พบ Resource เป้าหมาย ให้เสนอทางเลือกก่อนดำเนินการ และส่งต่อ Context ที่ยืนยันแล้ว
พร้อม Pending Decisions, Conflicts และ Recommended Next Skill / Always separate
detected capabilities and resources from granted authority. If a connection exists
but the target resource is missing, propose options before acting, and hand off
verified context with pending decisions, conflicts, and the recommended next skill.
