---
name: write-governed-spec
description: >
  TH: เปลี่ยนคำขอของ Owner และบริบทโครงการที่ยืนยันแล้วให้เป็น specification, contract, amendment หรือ implementation handoff ที่มี governance ชัดเจน ใช้เมื่อต้องการทำข้อกำหนดให้เป็นทางการ ล็อกแบบ ตรวจความเข้ากันได้กับ baseline กำหนด acceptance criteria หรือเตรียมคำสั่งส่งต่อแบบมีขอบเขต การเขียน spec ไม่ได้ให้อำนาจ implementation โดยอัตโนมัติ
  EN: Turn an Owner request and confirmed project context into a governed specification, contract, amendment, or implementation handoff. Use when formalizing requirements, freezing a design, reconciling a proposed change with an approved baseline, defining acceptance criteria, or preparing scoped execution instructions. Writing a spec does not authorize implementation.
---

# เขียนข้อกำหนดแบบมี Governance / Write Governed Spec

เปลี่ยนข้อกำหนดจากบทสนทนาและแหล่งข้อมูลที่ยืนยันแล้วให้เป็นเอกสารที่คนหรือ Agent อื่นสามารถทำงานต่อได้โดยไม่ต้องเดา Workflow นี้เป็นงานออกแบบและเอกสาร ไม่ใช่อำนาจให้ลงมือ Implementation หรือ Deploy โดยอัตโนมัติ

Turn conversational requirements and confirmed sources into a specification that another person or agent can follow without guessing. This is a design and documentation workflow; it does not grant implementation or deployment authority.

## Authority and Scope / อำนาจและขอบเขต

- ถือว่าผู้ใช้คือ Owner เว้นแต่มีการกำหนด Authority อื่นอย่างชัดเจน / Treat the user as Owner unless another authority is explicitly defined.
- เรียงลำดับอำนาจของแหล่งข้อมูลเป็น: คำสั่ง Owner ล่าสุดที่ชัดเจน → Owner-frozen canon/baseline/amendment → approved specification → reviewed draft → source/reference → assistant inference / Resolve sources in this order: latest explicit Owner instruction → Owner-frozen canon/baseline/amendment → approved specification → reviewed draft → source/reference → assistant inference.
- Approval ใช้ได้เฉพาะเอกสาร Gate Action Environment และ Scope ที่อนุมัติไว้ ห้ามขยายไป Gate ถัดไปโดยอัตโนมัติ / Apply approval only to the exact document, gate, action, environment, and scope stated; never extend it automatically to the next gate.
- แยกโปรเจกต์ออกจากกัน และห้ามแก้ Frozen content แบบเงียบ ๆ ให้ใช้ addendum, amendment, version ใหม่ หรือ supersession record / Keep projects isolated and never silently alter frozen content; use an addendum, amendment, new version, or supersession record.
- หนึ่ง Ticket ควรแก้หนึ่งปัญหาการออกแบบที่ต่อเนื่องกัน แยกงานที่ไม่เกี่ยวข้องและระบุ Dependency / One ticket should solve one coherent design problem; split unrelated problems and record dependencies.

## Workflow / ขั้นตอนการทำงาน

1. **Normalize intent / ทำความต้องการให้ชัดเจน** — ระบุผลลัพธ์ที่ Owner ต้องการโดยรักษาคำศัพท์ของโดเมน แยก Requirement, Suggestion และ Assistant Inference ออกจากกัน / State the Owner’s intended outcome using their domain terms and separate requirements, suggestions, and assistant inference.
2. **Confirm context / ยืนยันบริบท** — ใช้ `reconcile-work-context` เมื่อบริบทกระจัดกระจายหรือ Authority/Current State ไม่ชัด และไม่ทำ Discovery ซ้ำเมื่อมีหลักฐานครบแล้ว / Use `reconcile-work-context` when context is scattered or authority/current state is unclear; do not repeat discovery when the relevant evidence is already available.
3. **Set boundaries / กำหนดขอบเขต** — ระบุ In Scope, Out of Scope, Deferred, Dependencies และ Non-goals พร้อมบอกว่าเป็น Design-only, Implementation Planning หรือ Approved Execution Handoff / Define in-scope, out-of-scope, deferred items, dependencies, and non-goals, and identify whether the task is design-only, implementation planning, or an explicitly approved execution handoff.
4. **Reconcile canon / เทียบกับ Canon** — เทียบข้อเสนอกับ Frozen Baseline และ Contract ที่เกี่ยวข้อง แล้วจัดประเภทเป็น `PASS`, `CARRY`, `REWORK`, `CONFLICT` หรือ `DEFER` ห้ามแก้ Conflict จริงแบบเงียบ ๆ / Compare the proposal with frozen baselines and related contracts, classify each relevant point as `PASS`, `CARRY`, `REWORK`, `CONFLICT`, or `DEFER`, and never silently resolve a real conflict.
5. **Write the contract / เขียน Contract** — ใส่เฉพาะหัวข้อที่เกี่ยวข้อง เช่น actors/ownership, entities/identity, states/transitions, inputs/outputs, permissions, provenance, behavior, persistence, errors/edge cases, compatibility, versioning, security boundaries และ operational constraints / Include only applicable elements such as actors/ownership, entities and identity, states/transitions, inputs/outputs, permissions, provenance, behavior, persistence, errors/edge cases, compatibility, versioning, security boundaries, and operational constraints.
6. **Design verification / ออกแบบการตรวจสอบ** — กำหนด Acceptance Criteria, Positive/Negative Cases, Evidence, Success Condition และ Stop Conditions โดยใช้ข้อความที่วัดได้เมื่อทำได้ / Define acceptance criteria, representative positive and negative cases, required evidence, success condition, and stop conditions using measurable statements when possible.
7. **State the gate / ระบุ Gate** — ระบุการตัดสินใจของ Owner ที่ต้องการอย่างแม่นยำ และใช้สถานะเอกสารให้ถูกต้อง เช่น `DRAFT`, `READY FOR OWNER REVIEW`, `OWNER FROZEN`, `BLOCKED` ห้ามเรียกเอกสารว่า Frozen ก่อนได้รับอนุมัติ / State exactly which Owner decision is required and mark document state accurately; never call a document frozen before approval.
8. **Create the right artifact / สร้าง Artifact ที่เหมาะสม** — สำหรับ Milestone สำคัญ เอกสารที่ผู้ใช้ร้องขอ หรือ Executor Handoff ให้สร้างไฟล์ Markdown จริง ค่าเริ่มต้นเป็น TH–EN เว้นแต่ Owner สั่งเป็นอย่างอื่น / For significant milestones, requested documents, or executor handoffs, create a real Markdown file; default to Thai–English unless the Owner directs otherwise.
9. **Close with handoff / ปิดด้วย Handoff** — รายงานสิ่งที่เปลี่ยน การตรวจสอบที่ทำ ข้อจำกัด สถานะ Implementation Authority และ Next Action เดียวที่ชัดเจน / Report what changed, verification performed, limitations, implementation authority state, and one explicit Next Action.

## Implementation and High-Impact Boundaries / ขอบเขต Implementation และงานผลกระทบสูง

Build Contract ไม่ใช่ Implementation Approval ก่อนแก้ Code, Repository, Roblox Studio, Database, Runtime, External Service หรือ Hosting ต้องทำ Preflight ที่เกี่ยวข้องและมี Explicit Approval ตามที่กำหนด ห้ามอนุมานสิทธิ์สำหรับ Deploy, Migration, Production, Secrets, Auth, Storage, Billing หรือ High-impact State

A build contract is not implementation approval. Before code, repository, Roblox Studio, database, runtime, external-service, or hosting mutation, require the relevant preflight and explicit approval where required. Never infer permission to deploy, migrate, change production, secrets, auth, storage, billing, or other high-impact state.

สำหรับ Website, App และ Code ให้ใช้กฎ **Save Version Before Deploy**: เก็บ Candidate ที่ย้อนกลับได้ก่อน Deploy เมื่อแพลตฟอร์มรองรับ และบันทึก Identifier/Name, Time, Environment, Change Summary และ Approver เมื่อมีข้อมูล หาก Preflight ที่จำเป็นยังไม่ชัดหรือไม่ปลอดภัย ให้หยุดก่อน Mutation และรายงาน Blocker

For websites, apps, and code, apply **Save Version Before Deploy**: preserve a recoverable candidate before deployment when supported and record its identifier/name, time, environment, change summary, and approver when available. If required preflight facts are unknown or unsafe, stop before mutation and report the blocker.

## Document Metadata and Shape / Metadata และโครงสร้างเอกสาร

เอกสารทางการควรบันทึก Project, Document/Ticket ID, Title, Version, Type, Language, Status, Date, Parent/Dependencies และ Implementation Authorization State ตามความเหมาะสม / A formal document should normally record project, document/ticket ID, title, version, type, language, status, date, parent/dependencies, and implementation authorization state as applicable.

หัวข้อที่ใช้บ่อย / Common sections:

1. Purpose and context / วัตถุประสงค์และบริบท
2. Scope and non-goals / ขอบเขตและสิ่งที่ไม่ทำ
3. Authority, definitions, and invariants / Authority คำจำกัดความ และกฎคงที่
4. Contract or behavior / Contract หรือพฤติกรรม
5. Compatibility and unresolved decisions / Compatibility และประเด็นที่ยังไม่ตัดสิน
6. Acceptance and verification / Acceptance และ Verification
7. Stop conditions and required evidence / Stop Conditions และ Evidence
8. Status, approval request, and Next Action / สถานะ การขออนุมัติ และ Next Action

สำหรับ Executor Instructions ต้องมี Objective, Authoritative Inputs, Allowed/Forbidden Actions, Preflight, Target Environment, Tests, Success/Stop Conditions, Evidence/Reporting Format และ Version/Deploy Controls / Executor instructions must include objective, authoritative inputs, allowed/forbidden actions, preflight, target environment, tests, success/stop conditions, evidence/reporting format, and version/deploy controls.

## Stop Conditions / เงื่อนไขหยุด

หยุดหรือทำเครื่องหมาย `BLOCKED` เมื่อ Authority ที่จำเป็นหายไป, แหล่งข้อมูลที่มี Authority สองแหล่งขัดกันและยังไม่มี Owner Decision, ไม่ทราบ Environment/Target Identity ก่อน Mutation หรือคำขอเกิน Scope ที่อนุมัติ งานออกแบบอิสระที่ปลอดภัยยังทำต่อได้ แต่ต้องติดป้าย Assumption ให้ชัด

Stop or mark `BLOCKED` when required authority is missing, two authoritative sources conflict without an Owner decision, environment or target identity is unknown before a mutation, or the request would exceed the approved scope. Continue independent design work where safe, and label assumptions instead of presenting them as fact.

## Shared Context Contract / สัญญาบริบทกลาง

ต้องตรวจ Repository, Source of Truth, Related Skills, Available Connections, Permission State และ Target Resources ก่อนสร้าง Spec หากตรวจพบ Connection แต่ยังไม่พบชื่อ ตำแหน่ง หรือ Resource เป้าหมาย ให้เสนอทางเลือกในการค้นหา ใช้ของเดิม หรือจัดสร้างใหม่ และรอ Owner Approval ก่อนสร้างหรือแก้ Resource จริง

Check the repository, sources of truth, related skills, available connections, permission state, and target resources before creating a spec. If a connection is detected but the target name, location, or resource is still missing, propose options to find, reuse, or create the resource and wait for Owner approval before creating or mutating real resources.

## Handoff / การส่งต่อ

เมื่อ Spec พร้อม ให้ส่งต่ออย่างน้อย: Current Context, Confirmed Decisions, Pending Decisions, Changed Outputs, Known Risks, Implementation Authority State และ Recommended Next Skill / When the spec is ready, hand off at least the current context, confirmed decisions, pending decisions, changed outputs, known risks, implementation authority state, and recommended next skill.
