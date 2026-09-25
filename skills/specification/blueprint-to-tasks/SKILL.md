---
name: blueprint-to-tasks
description: >
  TH: ตรวจสอบ Blueprint ที่ได้รับการยืนยัน ล็อก Master Structure และแปลงเป็น
  Directory Tree กับ Atomic Task Tickets ที่มี Scope, Input, Output, Dependency
  และ Definition of Done ชัดเจน โดยไม่เขียนโค้ดจริง
  EN: Verify an approved blueprint, lock its Master Structure, and convert it
  into a Directory Tree and atomic task tickets with explicit scope, inputs,
  outputs, dependencies, and Definition of Done without writing production code.
---

# แปลงพิมพ์เขียวเป็นตั๋วงาน / Blueprint to Tasks

## Verification Gate / จุดตรวจสอบ

ก่อนสับงานต้องสรุป Blueprint, Master Structure, Verified, Pending และ Conflicts
แล้วรอ Owner ยืนยัน / Summarize the blueprint, Master Structure, verified,
pending, and conflicts, then wait for Owner confirmation before breakdown.

## Breakdown Rules / กฎการแบ่งงาน

- หนึ่งตั๋วต่อหนึ่งความรับผิดชอบ / One ticket per coherent responsibility.
- ระบุ Dependency อย่างตรงไปตรงมา / Declare dependencies explicitly.
- ห้ามเพิ่มฟีเจอร์หรือโมดูล / Do not invent features or modules.
- แยกไฟล์ตามการตรวจสอบ ไม่ใช่แยกจนซับซ้อน / Split files for verifiability,
  not needless fragmentation.
- ทุกตั๋วต้องมี Objective, Scope, Input, Output, Constraints, Verification,
  Definition of Done และ Stop Condition.

## Ticket Format / รูปแบบตั๋ว

```markdown
### [T-XX] ชื่อตั๋ว / Ticket Name
- Status / สถานะ:
- Master Module / โมดูล:
- Objective / วัตถุประสงค์:
- Scope / ขอบเขต:
- Out of Scope / นอกขอบเขต:
- Dependencies / Dependency:
- Inputs / ข้อมูลเข้า:
- Outputs / ผลลัพธ์:
- Verification / การตรวจสอบ:
- Definition of Done / เกณฑ์จบ:
- Stop Condition / เงื่อนไขหยุด:
```

## Handoff / การส่งต่อ

หลังสร้าง Ticket ให้แนะนำ `implement-approved-task` เฉพาะ Ticket ที่พร้อม
และไม่เรียกใช้เอง / Recommend `implement-approved-task` only for a ready ticket;
do not invoke it automatically.

## Shared Context Contract / สัญญาบริบทกลาง

ต้องยืนยัน Master Structure, Existing Work, Related Skills, Target Resource,
Permission State และ Conflict ก่อนแตก Ticket. หากพบ Resource ไม่ครบ ให้ระบุ Missing
Resource และเสนอวิธีจัดการโดยไม่สร้างเอง / Confirm the master structure, existing
work, related skills, target resource, permission state, and conflicts before
breaking down tickets. If a resource is missing, identify it and propose a
resolution without creating it automatically.
