---
name: implement-approved-task
description: >
  TH: รับ Atomic Task ที่ได้รับการยืนยันและเขียนหรือแก้ไข Source Code เฉพาะ
  Scope ของตั๋วนั้น โดยตรวจ Preflight, Input/Output, Error Handling, Test และ
  ผลกระทบ โดยไม่เพิ่มฟีเจอร์หรือแก้ Master Structure
  EN: Implement a confirmed atomic task within its approved scope, checking
  preflight, inputs/outputs, error handling, tests, and impact without adding
  features or changing the Master Structure.
---

# ลงมือทำตั๋วงานที่อนุมัติแล้ว / Implement Approved Task

## Rules / กฎ

- ต้องมี Ticket, Scope, Input, Output และ Definition of Done / Require a complete ticket.
- ทำทีละหนึ่ง Ticket / Implement one ticket per run.
- ตรวจ Context และ Repository ก่อนแก้ไข / Inspect context and repository first.
- แก้เฉพาะไฟล์ที่อนุญาต / Edit only allowed files.
- ห้ามเพิ่ม Feature, API, Schema หรือ Abstraction เผื่ออนาคต / No feature creep,
  contract changes, or speculative abstractions.
- ห้ามแก้ Production, Migration, Auth, Secret, Storage หรือ Billing โดยไม่มี Approval.

## Workflow / ขั้นตอน

1. สรุป Ticket หนึ่งประโยค / Restate the ticket in one sentence.
2. ทำ Non-mutating Preflight / Run a non-mutating preflight.
3. ระบุ Files และ Change Plan / State target files and change plan.
4. Implement ตาม Scope / Implement within scope.
5. รัน Syntax, Type, Test และตรวจ Diff / Run checks and inspect the diff.
6. รายงานผลและข้อจำกัด / Report results and limitations.

## Handoff / การส่งต่อ

เมื่อโค้ดพร้อมตรวจ ให้แนะนำ `code-review-and-fix` / When code is ready for review,
recommend `code-review-and-fix`.

## Shared Context Contract / สัญญาบริบทกลาง

ก่อนแก้ไขต้องตรวจ Target File, Approved Ticket, Existing Diff, Related Skills,
Available Tools และ Permission State. ห้ามใช้ Connection หรือแก้ Resource ภายนอก
เพียงเพราะระบบตรวจพบว่ามีอยู่ / Before editing, verify the target file, approved
ticket, existing diff, related skills, available tools, and permission state. Do
not use a connection or mutate an external resource merely because it was detected.
