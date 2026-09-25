---
name: write-user-manual
description: >
  TH: แปลงระบบหรือผลลัพธ์ที่ผ่านการตรวจสอบแล้วเป็นคู่มือการใช้งานภาษาไทย
  พร้อมภาษาอังกฤษคู่ขนานเมื่อจำเป็น โดยใช้ขั้นตอนสั้น คำอธิบายชัดเจน และ
  Troubleshooting ที่อิงหลักฐาน ห้ามเพิ่มความสามารถที่ระบบไม่มี
  EN: Convert a verified system or deliverable into a concise Thai-first user
  manual with parallel English when needed, clear steps, and evidence-based
  troubleshooting without inventing capabilities.
---

# จัดทำคู่มือการใช้งาน / Write User Manual

## Workflow / ขั้นตอน

1. อ่าน Context, QA Result และขอบเขตระบบ / Read context, QA result, and scope.
2. ระบุผู้ใช้เป้าหมายและงานที่ต้องทำ / Identify users and tasks.
3. เขียน How to Run, Key Commands/UI, Troubleshooting และ Success Criteria.
4. ตรวจว่าทุกขั้นตอนทำได้จริง / Verify every step is executable.
5. แยก Known Limitations และ Stop Conditions / State limitations and stop conditions.

## Rules / กฎ

- ใช้ภาษาไทยเป็นหลัก / Use Thai first.
- ใช้ขั้นตอนสั้นและไม่เพิ่มศัพท์เทคนิคโดยไม่จำเป็น / Keep steps short and avoid needless jargon.
- ห้ามอ้างฟีเจอร์ที่ไม่มีในระบบ / Do not document unavailable features.
- คู่มือต้องตรงกับ Version ที่ตรวจสอบแล้ว / Tie the manual to the verified version.

## Required Sections / หัวข้อบังคับ

```markdown
# ชื่อระบบ / System Name
## วิธีเปิดใช้งาน / How to Run
## คำสั่งหรือส่วนควบคุม / Key Commands or UI
## วิธีแก้ปัญหา / Troubleshooting
## ข้อจำกัด / Limitations
## เกณฑ์ความสำเร็จ / Success Criteria
## Version และวันที่ / Version and Date
```

## Handoff / การส่งต่อ

เมื่อคู่มือผ่านการตรวจ ให้แนะนำ `release-and-handoff` หากผู้ใช้ต้องการเผยแพร่
หรือส่งมอบ / Recommend `release-and-handoff` when the user wants to publish or hand off.

## Shared Context Contract / สัญญาบริบทกลาง

ตรวจผลลัพธ์ที่ผ่าน QA, Target Audience, Available Outputs, Related Skills และ
ข้อจำกัดของแพลตฟอร์มก่อนเขียนคู่มือ. หากยังไม่พบข้อมูลสำคัญ ให้ระบุ Missing Input
แทนการเดา / Check the QA-approved result, target audience, available outputs,
related skills, and platform limits before writing. If required information is
missing, mark it as Missing Input instead of guessing.
