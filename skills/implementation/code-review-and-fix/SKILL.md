---
name: code-review-and-fix
description: >
  TH: ตรวจ Diff หรือ Source Code เทียบกับ Ticket และ Definition of Done เพื่อ
  ค้นหา Bug, Edge Case, Regression, Error Handling และ Performance Risk แล้ว
  แก้ไขเฉพาะประเด็นที่อยู่ใน Scope พร้อมรายงานหลักฐาน
  EN: Review a diff or source code against the ticket and Definition of Done to
  find bugs, edge cases, regressions, error-handling gaps, and performance risks,
  then fix only in-scope findings with evidence.
---

# ตรวจโค้ดและแก้ไข / Code Review and Fix

## Workflow / ขั้นตอน

1. อ่าน Context, Ticket, Diff และ Test / Read context, ticket, diff, and tests.
2. จัดประเภทผลตรวจเป็น `Confirmed`, `Risk`, `Unknown`, `Not Found` / Classify findings.
3. รายงานผลก่อนแก้ไข / Report findings before editing.
4. ขออนุญาตแก้ไขเมื่อมี Change / Request permission before changes.
5. ทดสอบ Edge Cases และ Regression / Test edge cases and regressions.
6. แก้เฉพาะ Root Cause ที่ยืนยันได้ / Fix only verified root causes.
7. ตรวจ Diff และรายงานผล / Recheck the diff and report evidence.

## Rules / กฎ

- ห้ามเรียก Risk ว่า Confirmed Bug / Do not call a risk a confirmed bug.
- ห้ามอ้างว่าไม่มีบั๊กโดยไม่มี Coverage / Do not claim zero bugs without coverage.
- ห้ามแก้ไฟล์นอก Scope / Do not edit out-of-scope files.
- ห้าม Deploy / Do not deploy.

## Handoff / การส่งต่อ

เมื่อ Review ผ่าน ให้แนะนำ `write-user-manual` และหากต้อง Release ให้ใช้
`release-and-handoff` หลังคู่มือและ Readiness พร้อม / Recommend `write-user-manual`,
then `release-and-handoff` only when documentation and readiness are complete.

## Shared Context Contract / สัญญาบริบทกลาง

ตรวจ Source, Diff, Approved Scope, Existing QA Evidence, Related Skills, Target
Environment และสิทธิ์ก่อนตรวจหรือแก้. หากผลลัพธ์อาจชนกับการเปลี่ยนแปลงก่อนหน้า ต้อง
หยุดและรายงานก่อน / Check the source, diff, approved scope, existing QA evidence,
related skills, target environment, and authority before reviewing or editing. Stop
and report when the result may conflict with prior changes.
