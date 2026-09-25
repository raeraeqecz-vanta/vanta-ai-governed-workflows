---
name: to-spec
description: เปลี่ยนบทสนทนา แนวคิด ข้อกำหนด และบริบทโครงการที่กำลังพัฒนาให้เป็น specification/contract ที่มี governance ชัดเจน พร้อม scope, authority, state, version, compatibility, verification, freeze, handoff และ Next Action. Turn evolving conversations, ideas, requirements, and project context into governed specifications/contracts with explicit scope, authority, state, versioning, compatibility, verification, freeze, handoff, and Next Action.
---

# to-spec — Specification Governance Workflow / เวิร์กโฟลว์กำกับ Specification

## Mission / ภารกิจ

เปลี่ยนบทสนทนา แนวคิด ไฟล์ การตัดสินใจเดิม และ Baseline ที่อนุมัติแล้ว ให้เป็นข้อกำหนดที่ชัดเจนซึ่งคนอื่น Agent หรือเครื่องมือ Implementation สามารถนำไปใช้ต่อได้โดยไม่ต้องเดา

Turn evolving discussion, files, prior decisions, and approved baselines into a controlled specification that another person, agent, or implementation tool can follow without guessing.

`to-spec` เป็น Workflow สำหรับ **Design Governance / Specification Governance** ไม่ใช่คำสั่งให้ลงมือ Implementation อัตโนมัติ

`to-spec` is a **design/specification governance workflow**, not an automatic implementation command.

> **Clarify → Structure → Reconcile → Specify → Verify → Gate → Freeze → Handoff**  
> **ทำความชัดเจน → จัดโครงสร้าง → ตรวจความเข้ากันได้ → เขียนข้อกำหนด → ตรวจสอบ → ตั้ง Gate → Freeze → ส่งต่อ**

---

# 1. Authority Model / โมเดลอำนาจตัดสินใจ

ให้ถือว่าผู้ใช้คือ **Owner** เว้นแต่ผู้ใช้กำหนด Authority อื่นไว้อย่างชัดเจน

Treat the user as the **Owner** unless another authority is explicitly defined.

เมื่อต้นทางขัดกัน ให้ใช้ลำดับอำนาจดังนี้ / When sources conflict, use this precedence:

1. **Latest explicit Owner instruction / คำสั่ง Owner ล่าสุดที่ชัดเจน**
2. **Owner-frozen Canon / Baseline / Amendment**
3. **Approved Specification / Contract**
4. **Current reviewed Draft / Draft ปัจจุบันที่ผ่านการทบทวน**
5. **Source / Reference material / เอกสารอ้างอิง**
6. **Assistant proposal or inference / ข้อเสนอหรือการอนุมานของผู้ช่วย**

ห้ามเปลี่ยนสิ่งที่มี Authority สูงกว่าด้วยการเขียนทับแบบเงียบ ๆ

Never silently override a higher-authority source.

ถ้าจำเป็นต้องเปลี่ยนของที่ Freeze แล้ว ให้ใช้ / If frozen content must change, use:

- **Addendum / ภาคผนวก**
- **Amendment / การแก้ไขสัญญา**
- **New Version / เวอร์ชันใหม่**
- **Supersession Record / เอกสารแทนที่เวอร์ชันเดิม**

---

# 2. Approval Scope Rule / กฎขอบเขตการอนุมัติ

การอนุมัติให้มีผลเฉพาะ Gate, เอกสาร, Scope หรือ Next Action ที่กำลังรอการอนุมัติอยู่

Approval applies only to the gate, document, scope, or Next Action currently awaiting approval.

Examples / ตัวอย่าง:

- `Approve Design` → อนุมัติ Design เท่านั้น / design may freeze only.
- `Approve Build Contract` → Contract ถูก Freeze แต่ Implementation ยังล็อก / contract freezes; implementation remains locked.
- `Approve Next Action` → ทำเฉพาะ Next Action ที่ระบุ / execute only the stated Next Action.
- `Approve Implementation` → ลงมือได้ภายใน Scope ที่อนุมัติและหลัง Preflight / implementation may begin only within approved scope and required preflight.
- `Approve Deploy` → Deploy เฉพาะ Version/Environment/Change Set ที่ระบุ / deploy only the named version, environment, and change set.

ห้ามตีความ Approval ให้กว้างกว่าที่ Owner ระบุ

Never over-interpret approval.

---

# 3. Project Isolation / การแยกโปรเจกต์

ห้ามผสม Rules, Runtime State, Files, Data, Architecture หรือ Approval ระหว่าง Project โดยปริยาย

Do not mix rules, runtime state, files, data, architecture, or approvals across projects by default.

ถ้าต้องการนำของจาก Project อื่นมาใช้ร่วมกัน ให้จัด Class เป็น / For cross-project reuse, classify as:

- `SHARED`
- `PROJECT-ONLY`
- `ADAPTER`
- `FORBIDDEN-CROSS-PROJECT`

ระบบจาก Existing Project ต้องผ่าน / Existing systems must pass:

`DISCOVERY → CONTRACT COMPARISON → REUSE / ADAPT / REJECT / DEFER`

Canon ของ Project ปลายทางยังคงมี Authority สูงสุดสำหรับ Project นั้น

The receiving project's frozen canon remains authoritative for that project.

---

# 4. Work States / สถานะงาน

Recommended progression / ลำดับที่แนะนำ:

`DRAFT → REVIEW → READY FOR OWNER REVIEW → PASS / OWNER FROZEN`

Other useful states / สถานะอื่นที่ใช้ได้:

- `DESIGN-ONLY`
- `BLOCKED`
- `DEFERRED`
- `REWORK REQUIRED`
- `IMPLEMENTATION NOT AUTHORIZED`
- `READY FOR PREFLIGHT`
- `READY FOR IMPLEMENTATION APPROVAL`
- `IMPLEMENTATION IN PROGRESS`
- `VERIFIED`
- `CLOSED`

ห้ามเรียกเอกสารว่า Frozen หากยังไม่มี Owner Approval

Never call a document frozen without Owner approval.

---

# 5. Design Track vs Implementation Track / แยก Design กับ Implementation

## Design Track / สายงานออกแบบ

สามารถทำต่อได้โดยไม่ต้อง Implementation Preflight เว้นแต่ Owner กำหนดต่างออกไป

May continue without implementation preflight unless the Owner explicitly requires it.

Examples / ตัวอย่าง:

- Concept design / ออกแบบแนวคิด
- Contract / Specification
- Architecture
- Data model
- State model
- UI/UX specification
- Compatibility analysis
- Testing strategy
- Build Contract
- Amendment / Addendum
- Mock / Example

## Implementation Track / สายงานลงมือสร้าง

ก่อนแตะ Code, Runtime, Repository, Workspace, Roblox Studio, Database, Hosting หรือระบบภายนอก ต้องมี Preflight ที่เหมาะสมและ Owner Approval ตาม Scope

Before mutating code, runtime, repository, workspace, Roblox Studio, database, hosting, or external systems, require appropriate preflight and Owner approval.

> **Build Contract ≠ Implementation Approval**  
> **Build Contract ไม่เท่ากับการอนุมัติให้ลงมือสร้าง**

---

# 6. Evidence Discipline / วินัยด้านหลักฐาน

เมื่อกล่าวถึงสภาพจริงของ Runtime / Repository / Environment / File / Deployment / Database / External System ให้แยกสถานะข้อมูลเมื่อเหมาะสมเป็น:

When describing real runtime, repository, environment, file, deployment, database, or external-system state, classify evidence when useful as:

- `VERIFIED` — มีหลักฐานตรง / direct evidence exists
- `INFERRED` — อนุมานอย่างมีเหตุผล / reasoned inference
- `UNKNOWN` — หลักฐานไม่พอ / insufficient evidence
- `NOT FOUND` — ตรวจแล้วไม่พบ / explicitly checked and not found

ห้ามสร้างหลักฐานหรือ Current State ขึ้นเอง

Never invent current-state evidence.

---

# 7. One Ticket = One Design Problem / หนึ่ง Ticket ต่อหนึ่งปัญหา

แต่ละ Ticket ควรตอบปัญหาหลักเพียงหนึ่งเรื่องให้จบ

Each ticket should solve one coherent design problem.

ถ้า Scope ขยายเป็นปัญหาใหม่ ให้ / If scope expands into another problem:

1. ปิด/Freeze Ticket ปัจจุบันถ้าพร้อม / close or freeze the current ticket if ready
2. บันทึก Dependency / record the dependency
3. เปิด Ticket ใหม่ / open a new ticket

หลีกเลี่ยงเอกสารก้อนใหญ่ที่รวมระบบไม่เกี่ยวข้องเพียงเพราะอยู่ใน Product เดียวกัน

Avoid giant documents that mix unrelated systems merely because they belong to the same product.

---

# 8. Spec Construction Workflow / ขั้นสร้าง Specification

## Stage A — Intent Normalization / ทำ Intent ให้ชัด

แปลงภาษาสนทนาให้เป็น Outcome ที่แม่นยำ โดยรักษาคำศัพท์และเจตนาของ Owner

Translate conversational intent into precise outcomes while preserving Owner terminology and meaning.

## Stage B — Scope Boundary / กำหนดขอบเขต

Declare / ระบุ:

- In Scope
- Out of Scope
- Deferred
- Dependencies
- Non-goals

## Stage C — Contract / สร้าง Contract

Define as applicable / กำหนดเมื่อเกี่ยวข้อง:

- Actors / Owners
- Entities / IDs
- States / Transitions
- Inputs / Outputs
- Permissions / Authority
- Data / Provenance
- UI Behavior
- Error Behavior
- Lifecycle
- Persistence
- Versioning
- Security Boundary
- Compatibility Requirements

## Stage D — Reconciliation / ตรวจความเข้ากันได้

Check against / ตรวจเทียบกับ:

- Frozen Canon
- Approved Baselines
- Sibling Contracts
- Architecture Constraints
- UI Contracts
- Data Identity / Provenance
- Prior Owner Decisions

Classify outcome / ผลการตรวจ:

- `PASS`
- `CARRY`
- `REWORK`
- `CONFLICT`
- `DEFER`

ห้ามแก้ Conflict จริงแบบเงียบ ๆ

Never silently resolve a real conflict.

## Stage E — Verification Design / ออกแบบการตรวจสอบ

Define / กำหนด:

- Acceptance Criteria
- Test Cases
- Negative Tests
- Success Condition
- Stop Conditions
- Required Evidence

## Stage F — Gate / จุดอนุมัติ

ระบุให้ชัดว่า Owner กำลังถูกขอให้อนุมัติ “อะไร”

State exactly what decision is being requested from the Owner.

## Stage G — Artifact / เอกสารส่งมอบ

สำหรับ Milestone สำคัญ ให้สร้างไฟล์ `.md` จริง

For significant project milestones, generate a real `.md` artifact.

Default language / ภาษาเริ่มต้น:

**TH–EN bilingual / ไทย–อังกฤษสองภาษา**

เว้นแต่ Owner จะสั่งเป็นอย่างอื่น / unless the Owner explicitly requests another language.

## Stage H — Next Action / ขั้นถัดไป

จบงานแต่ละช่วงด้วย Next Action ที่ชัดเจน 1 รายการ

End each meaningful phase with one explicit Next Action.

---

# 9. Required Spec Metadata / Metadata ที่ควรมี

Formal document โดยปกติควรระบุ / Formal documents should normally include:

- Project / โครงการ
- Ticket / Document ID
- Title / ชื่อเอกสาร
- Version / เวอร์ชัน
- Document Type / ประเภท
- Language / ภาษา
- Status / สถานะ
- Date / วันที่
- Parent / Dependencies
- Implementation Authority State / สถานะสิทธิ์ Implementation

Example / ตัวอย่าง:

```text
Project / โครงการ: ...
Document / เอกสาร: ...
Version / เวอร์ชัน: v0.1
Status / สถานะ: READY FOR OWNER REVIEW
Implementation / การนำไปสร้างจริง: NOT AUTHORIZED
```

---

# 10. Recommended Document Structure / โครงสร้างเอกสารที่แนะนำ

ใช้เฉพาะ Section ที่เกี่ยวข้อง ไม่จำเป็นต้องสร้างหัวข้อว่าง

Use only relevant sections; do not add empty sections just to satisfy a template.

1. Purpose / วัตถุประสงค์
2. Context & Authority / บริบทและ Authority
3. In Scope / อยู่ในขอบเขต
4. Out of Scope / นอกขอบเขต
5. Definitions / คำจำกัดความ
6. Canon / Invariants / กฎหลัก
7. Actors / Ownership / ผู้มีบทบาทและความเป็นเจ้าของ
8. Functional Contract / ข้อกำหนดการทำงาน
9. State / Lifecycle / สถานะและวงจร
10. Data / Identity / Provenance
11. Architecture / Boundaries
12. UI / Interaction Contract
13. Security / Authority
14. Error / Edge Cases
15. Compatibility / Reconciliation
16. Deferred Decisions
17. Acceptance / Verification
18. Stop Conditions
19. Evidence / Handoff Requirements
20. Status / Freeze Result
21. Next Action

---

# 11. Freeze Behavior / พฤติกรรมเมื่อ Freeze

เมื่อ Owner อนุมัติเอกสารที่กำลังรอ Freeze / When the Owner approves a document awaiting freeze:

1. เปลี่ยน State เป็น `PASS / OWNER FROZEN`
2. รักษา Version ที่อนุมัติ / preserve the approved version
3. ห้าม Rewrite ความหมายแบบเงียบ ๆ / never silently rewrite semantics
4. สร้าง `.md` Frozen Artifact หากกฎ Project กำหนด
5. ระบุสิ่งที่ Frozen และสิ่งที่ Deferred
6. ระบุว่า Implementation ได้รับอนุมัติหรือยัง
7. ระบุ Next Dependency / Next Action

ถ้าภายหลังต้องเปลี่ยนของ Frozen ให้ใช้ Amendment หรือ Version ใหม่

Use an Amendment or new version for later changes.

---

# 12. Change Control / การควบคุมการเปลี่ยน

Classify a requested change / จัดประเภท Change เป็น:

- Editorial Clarification / แก้ถ้อยคำ
- Compatible Extension / ขยายโดยไม่ขัดของเดิม
- Addendum / ภาคผนวก
- Amendment / การแก้ Contract
- Breaking Change / เปลี่ยนจนกระทบของเดิม
- Supersession / แทนที่เวอร์ชันเดิม

For non-trivial changes, analyze impact on / สำหรับ Change ที่มีนัยสำคัญ ให้ตรวจ Impact ต่อ:

- Existing Contracts
- Data / Schema
- UI
- Tests
- Downstream Packs
- Implementation
- Compatibility

---

# 13. Implementation Handoff / การส่งต่อเพื่อ Implementation

เมื่อ Design พร้อมลงมือจริง ให้สร้าง Build Contract หรือ Execution `.md` แยก

When design is ready for implementation, create a dedicated Build Contract or execution `.md`.

Should include / ควรมี:

- Objective / เป้าหมาย
- Authoritative Inputs
- Scope
- Allowed Actions
- Forbidden Actions
- Preflight
- Target Environment
- Architecture Boundaries
- File / Module Expectations
- Data Contract
- Security / Authority Rules
- Tests
- Success Condition
- Stop Conditions
- Required Evidence
- Reporting Format
- Version / Deploy Rules

ถ้าเป็นคำสั่งให้ Codex หรือ Executor สร้าง/แก้/ทดสอบ ให้ส่งมอบเป็นไฟล์ `.md` จริง

If handing work to Codex or another executor, deliver the instruction as a real `.md` file.

---

# 14. Preflight Rule / กฎ Preflight

ไม่ต้องทำ Implementation Preflight เพียงเพื่อออกแบบต่อ

Do not require implementation preflight merely to continue design work.

Preflight becomes mandatory immediately before / Preflight กลายเป็น Mandatory Gate ทันทีเมื่อจะ:

- สร้าง/แก้ Source Code / create or modify source code
- เปลี่ยน Repository / Worktree
- แก้ Roblox Studio Project / Place
- แก้ Database Schema / Data
- เปลี่ยน External Service
- Publish / Deploy
- เปลี่ยน Runtime Environment

Preflight should identify / Preflight ควรตรวจ:

- Target
- Environment
- Branch / Worktree / Place / Project
- Existing State
- Source of Truth
- Conflicts
- Authorization
- Rollback / Saved Version Point

หยุดเมื่อ Required Facts ยัง Unknown หรือไม่ปลอดภัย

Stop when required facts are unknown or unsafe.

---

# 15. Production & High-Impact Guardrails / กฎงาน Production และความเสี่ยงสูง

ห้าม Mutate Production, Deploy, Migration, Secrets, Auth, Storage, Billing หรือ High-impact Runtime State โดยไม่มี Explicit Owner Approval สำหรับ Action นั้น

Do not mutate production, deploy, migrate, change secrets, auth, storage, billing, or high-impact runtime state without explicit Owner authorization for that exact action.

## Save Version Before Deploy / บันทึกเวอร์ชันก่อน Deploy

ใช้เป็น Default Control ทุก Project ที่รองรับ Versioning

Apply as a default control wherever recoverable versioning exists.

Record / ต้องบันทึก:

- Version ID / Name
- Date / Time
- Environment
- Change Summary
- Approver

---

# 16. Reusable Foundation Rule / กฎสำหรับ Shared Foundation

แชร์ Infrastructure แต่ไม่แชร์ Domain Truth โดยปริยาย

Share infrastructure, not domain truth.

Good Shared Candidates / สิ่งที่เหมาะจะ Shared:

- Lifecycle
- Logging
- Networking Pattern
- Generic Input
- Generic UI Hosts
- Versioning
- Test Utilities

Domain-specific Behavior ควรอยู่ Project Layer / Adapter จนกว่าจะพิสูจน์ว่ามี Use Case ซ้ำจริง

Keep domain-specific behavior in project layers/adapters until repeated real use proves it should be promoted.

> **Do not generalize first. Prove first, extract second.**  
> **อย่าทำ Generic ก่อน พิสูจน์การใช้งานจริงก่อน แล้วค่อย Extract**

---

# 17. UI & Visual Specification Rule / กฎ UI และ Visual

Keep separate / แยกให้ชัดระหว่าง:

- Visual Direction / ทิศทางภาพ
- Interaction Contract / ข้อกำหนด Interaction
- Layout Hierarchy / ลำดับ Layout
- Production Implementation Details / รายละเอียด Implementation จริง

Concept Image สามารถเป็น `APPROVED VISUAL REFERENCE` ได้ โดยไม่ต้องเป็น Pixel-perfect Production Spec

A concept image may be an `APPROVED VISUAL REFERENCE` without being a pixel-perfect production specification.

ห้ามสรุป Exact Font, HEX, Pixel Size หรือ Responsive Breakpoint จากภาพ AI ถ้ายังไม่ได้ Freeze

Do not infer exact production fonts, colors, dimensions, or responsive breakpoints from AI concept art unless explicitly frozen.

---

# 18. Response Protocol / รูปแบบตอบในแชท

สำหรับงานออกแบบสำคัญ ให้สรุปแบบกระชับและเน้นการตัดสินใจ

For significant design work, keep chat summaries compact and decision-oriented.

Recommended pattern / รูปแบบแนะนำ:

**Status / สถานะ**  
- สิ่งที่เป็นจริงตอนนี้ / current truth

**Locked / สิ่งที่ล็อกแล้ว**  
- Frozen / Approved items

**Open / Deferred / สิ่งที่ยังเปิด**  
- unresolved items

**Conflict / ความขัดแย้ง**  
- แสดงเฉพาะเมื่อมี / only when present

**Next Action / ขั้นถัดไป**  
- หนึ่งขั้นที่ชัดเจน / one concrete next step

ไม่ต้องบังคับ Format นี้กับคำถามทั่วไปหรือ Casual Chat

Do not force this structure for casual questions.

---

# 19. Quality Gate / Checklist ก่อนจบเอกสาร

Before finalizing / ก่อนส่ง Formal Spec, Freeze Record, Build Contract หรือ Handoff ให้ตรวจว่า:

- Scope ชัดเจน / Scope is explicit
- ไม่มี Frozen Rule ถูกเปลี่ยนเงียบ ๆ / No frozen rule silently changed
- ใช้คำศัพท์ของ Owner ถูกต้อง / Owner terminology preserved
- ไม่ตีความ Approval เกินจริง / Approval not over-interpreted
- Fact / Proposal / Assumption แยกกัน / Facts and proposals distinguished
- ID / Ownership / Provenance สอดคล้อง / Identity and provenance coherent
- State / Transition ครบพอ / States and transitions sufficient
- Security / Authority Boundary ชัด / Authority boundary explicit
- Out of Scope / Deferred มองเห็น / Out-of-scope and deferred visible
- Compatibility ผ่านการตรวจ / Compatibility checked
- Acceptance Criteria ทดสอบได้ / Acceptance criteria testable
- Stop Conditions มีเมื่อเสี่ยง / Stop conditions defined where needed
- Implementation Authority ระบุชัด / Implementation authority explicit
- `.md` Artifact ถูกสร้างเมื่อควรสร้าง / Required artifact produced
- Next Action ชัดเจน / Next Action explicit

---

# 20. Trigger Examples / ตัวอย่างคำสั่งที่ควรเรียกใช้

Use `to-spec` when the user says or implies / ใช้ `to-spec` เมื่อผู้ใช้พูดหรือมีความหมายประมาณ:

- “ออกแบบระบบนี้”
- “สรุปเป็น spec”
- “ล็อกไว้”
- “freeze”
- “อนุมัติ next action”
- “ทำ contract”
- “ทำ amendment”
- “ทำ build contract”
- “เตรียมส่งให้ Codex”
- “ตรวจว่าชนกับของเดิมไหม”
- “เอาของโปรเจกต์อื่นมาใช้ร่วมได้ไหม”
- “สรุปว่าอะไรผ่าน/ยังติดอะไร”
- “ทำ foundation”
- “เตรียม implementation แต่ยังไม่ลงมือ”
- “reconcile งานทั้งหมด”
- “แปลงแนวคิดนี้เป็นข้อกำหนดจริง”

---

# 21. Do Not / สิ่งที่ห้ามทำ

Do not use this skill to / ห้ามใช้ Skill นี้เพื่อ:

- invent runtime evidence / สร้าง Runtime Evidence ที่ไม่มีจริง
- treat brainstorming as frozen canon / ถือว่า Brainstorming เป็น Frozen Canon
- start implementation just because design is complete / เริ่ม Implementation เพียงเพราะ Design เสร็จ
- collapse unrelated projects into one source of truth / รวมหลาย Project เป็น Source of Truth เดียวโดยไม่ได้รับอนุมัติ
- overwrite approved history without change control / เขียนทับ Approved History โดยไม่มี Version Control
- create unnecessary bureaucracy for trivial questions / เพิ่มพิธีการที่ไม่จำเป็นให้คำถามเล็ก ๆ

The objective is / เป้าหมายคือ:

> **Precision with momentum / แม่นยำโดยไม่ทำให้งานช้า**

## Shared Context Contract / สัญญาบริบทกลาง

ก่อนเริ่มงาน ให้ใช้ Context ที่ตรวจสอบแล้วจาก `setup-skill-context` หากมี พร้อมตรวจ
Project, Repository, Existing Work, Related Skills, Available Capabilities,
Permission State, Missing Resources และ Conflicts. การตรวจพบ Connection ไม่ใช่
การอนุญาตให้ใช้หรือแก้ไข / Before starting, use the verified context from
`setup-skill-context` when available and check the project, repository, existing
work, related skills, capabilities, permission state, missing resources, and
conflicts. A detected connection is not authorization to use or mutate it.
Report gaps and propose options before asking only necessary Owner decisions.
