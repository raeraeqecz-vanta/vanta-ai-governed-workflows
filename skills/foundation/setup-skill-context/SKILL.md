---
name: setup-skill-context
description: >
  TH: ตั้งค่าบริบทของโปรเจกต์สำหรับชุด Skill โดยตรวจ Repository เอกสารเดิม
  โครงสร้างงาน แหล่งเก็บ Context และกฎการส่งต่องาน จากนั้นเสนอให้ผู้ใช้ยืนยัน
  ก่อนบันทึกไฟล์ตั้งค่า ใช้ครั้งแรกของแต่ละโปรเจกต์หรือเมื่อบริบทเปลี่ยนแปลง
  EN: Set up project context for the skill suite by inspecting the repository,
  existing documents, work structure, context locations, and handoff rules,
  then request confirmation before writing configuration files. Use once per
  project or when its context changes.
---

# ตั้งค่าบริบท Skill / Set Up Skill Context

## Purpose / วัตถุประสงค์

TH: ทำให้ Skill อื่นรู้ว่าโปรเจกต์นี้มี Source of Truth, Context, Handoff,
Issue, Domain Docs และข้อจำกัดอยู่ที่ใด โดยบันทึกเป็นเอกสารในโปรเจกต์

EN: Make the other skills aware of this project's sources of truth, context,
handoffs, issues, domain docs, and constraints through project-local documents.

## Rules / กฎ

- อ่านสถานะก่อนเขียนเสมอ / Read current state before writing.
- ห้ามเขียนทับเอกสารเดิมโดยไม่ตรวจสอบ / Never overwrite existing docs silently.
- เสนอสิ่งที่พบและรอ Owner confirmation ก่อนบันทึก / Propose findings and wait
  for Owner confirmation before writing.
- ห้ามเปลี่ยน Source Code, Database, Deployment หรือ Runtime / Do not mutate
  source code, databases, deployments, or runtime.
- ตรวจ Capability และ Resource ก่อนถาม Owner / Detect capabilities and resources
  before asking the Owner.
- การตรวจพบ Connection ไม่ถือเป็นการอนุญาตให้ใช้หรือแก้ไข / A detected
  connection is not authorization to use or mutate it.
- หากพบ Connection แต่ไม่พบ Resource เป้าหมาย ให้รายงานช่องว่างและเสนอทางเลือก
  ก่อนจัดสร้าง / If a connection exists but the target resource is missing,
  report the gap and propose options before creating anything.

## Workflow / ขั้นตอน

1. ตรวจ Repository และโฟลเดอร์ปัจจุบัน / Inspect the repository and current directory.
2. ค้นหา `AGENTS.md`, `CLAUDE.md`, `CONTEXT.md`, `docs/agents/` และเอกสารที่เกี่ยวข้อง
   / Find existing agent, context, and domain documentation.
3. ตรวจ Issue Tracker หรือวิธีจัดการงานที่มีอยู่ / Identify the issue or work tracker.
4. เสนอ Context Map, Domain Docs Location และ Handoff Location / Propose the
   context map, domain-doc location, and handoff location.
5. ขอคำยืนยันหนึ่งครั้ง / Request one confirmation.
6. หลังยืนยัน จึงสร้างหรือแก้เฉพาะเอกสาร Context ที่อนุญาต / After confirmation,
   write only approved context documents.
7. รายงานไฟล์ที่สร้าง สถานะ และผลกระทบ / Report files, status, and impact.
8. ตรวจ Capability ระดับที่ระบบเปิดเผย เช่น Apps, Plugins, Tools และ Connections
   / Detect exposed capability metadata such as Apps, Plugins, Tools, and
   Connections.
9. ตรวจ Resource เป้าหมาย ชื่อ ตำแหน่ง และสิทธิ์ที่ยังขาด / Resolve target
   resource, name, location, and missing permissions.
10. จัดทำ Context Report และรอ Owner Decision เฉพาะจุดที่จำเป็น / Produce a
    Context Report and request only necessary Owner decisions.

## Capability and Resource Resolution / การแก้ช่องว่างของทรัพยากร

รายงานอย่างน้อย 4 ส่วน:

```text
Detected / ตรวจพบ
Missing / ยังไม่พบ
Conflicts / ความเสี่ยงการชนกัน
Proposed Resolution / ทางเลือกแก้ไข
```

ใช้ระดับอำนาจดังนี้:

- `DISCOVER`: ตรวจพบและรายงาน
- `PROPOSE`: เสนอชื่อ ตำแหน่ง โครงสร้าง หรือแนวทาง
- `CREATE`: สร้างหรือแก้ทรัพยากรจริงหลังได้รับอนุมัติ
- `PUBLISH`: Push, Release หรือ Deploy หลังได้รับอนุมัติเฉพาะกิจ

ค่าเริ่มต้นคือ `DISCOVER + PROPOSE` ห้ามใช้ `CREATE` หรือ `PUBLISH` โดยอัตโนมัติ

## Standard Context Output / รูปแบบผลลัพธ์มาตรฐาน

```markdown
## Context & Capability Check / ตรวจบริบทและความสามารถ
- Project:
- Repository and Git Remote:
- Existing Skills:
- Apps, Plugins, and Connections:
- Permission State:
- Missing Resources:
- Conflicts or Possible Overwrites:
- Proposed Resolution:
- Owner Decision Required:
```

## Recommended Project Context / โครงสร้างบริบทแนะนำ

```text
docs/agents/
├── project-context.md
├── skill-runtime-state.md
├── skill-handoff-log.md
├── change-impact-log.md
└── deployment-readiness.md
```

ใช้โครงสร้างเดิมของโปรเจกต์ก่อน หากมีอยู่แล้ว / Preserve existing project
conventions when they already exist.

## Stop Conditions / เงื่อนไขหยุด

หยุดเมื่อไม่ทราบโปรเจกต์เป้าหมาย พบ Context ขัดแย้ง ต้องแก้ไฟล์นอกขอบเขต หรือ
ต้องใช้สิทธิ์เพิ่มเติม / Stop when the target project is unclear, context
conflicts, out-of-scope files are required, or additional authority is needed.

## Handoff / การส่งต่อ

เมื่อ Context ถูกยืนยันแล้ว ให้แนะนำ `choose-next-skill` หรือ Skill ที่ตรงกับ
สถานการณ์ โดยไม่เรียกใช้เอง / After context is confirmed, recommend
`choose-next-skill` or the appropriate skill without invoking it automatically.

ส่งต่อ `Current Work Context`, `Confirmed Decisions`, `Pending Decisions`,
`Known Risks` และ `Recommended Next Skill` ทุกครั้ง / Always hand off the
current context, confirmed decisions, pending decisions, known risks, and
recommended next skill.
