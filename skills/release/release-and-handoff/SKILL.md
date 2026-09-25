---
name: release-and-handoff
description: >
  TH: ตรวจความพร้อมของผลลัพธ์ที่ผ่าน QA แล้วเลือกโหมด Deploy, Publish, Package,
  Release Document หรือ Handoff ตามบริบท จากนั้นบันทึก Version ขอ Owner Approval
  ดำเนินการเฉพาะที่ได้รับอนุมัติ ตรวจผลหลังส่งมอบ และเตรียม Rollback เมื่อทำได้
  EN: Release a QA-approved deliverable using the appropriate mode—deploy,
  publish, package, release-document, or handoff—after recording a version and
  obtaining explicit Owner approval. Verify the result and prepare rollback when possible.
---

# ปล่อยงานและส่งมอบ / Release and Handoff

## Modes / โหมดการทำงาน

- `DEPLOY` ระบบขึ้น Environment / deploy to an environment
- `PUBLISH` เกมหรือเนื้อหา / publish a game or content
- `PACKAGE` โปรแกรมหรือไฟล์ / package software or files
- `RELEASE-DOCUMENT` ปล่อยเอกสาร Version ใหม่ / release a document version
- `HANDOFF` ส่งต่อให้ผู้ใช้หรือทีม / hand off to a user or team

## Verification Gate / จุดตรวจสอบ

ต้องมี QA Result, Version, Target, Change Summary, Rollback Point เมื่อทำได้
และ Owner Approval สำหรับ Action นั้น / Require QA result, version, target,
change summary, a rollback point when possible, and explicit Owner approval.

ก่อนเริ่มให้ตรวจ Context, Handoff, Change Conflict และ Deployment Readiness
/ Inspect context, handoff, conflicts, and readiness before acting.

## Workflow / ขั้นตอน

1. ระบุ Mode และ Target / Identify the mode and target.
2. ตรวจ QA และ Version / Verify QA and version.
3. ตรวจ Change ที่ชนกัน / Check conflicting changes.
4. บันทึก Version ก่อนดำเนินการ / Save a recoverable version first.
5. ขอ Owner Approval / Request explicit approval.
6. ดำเนินการเฉพาะ Version และ Scope ที่อนุมัติ / Act only on approved version and scope.
7. ตรวจผลหลัง Release และบันทึก Evidence / Verify post-release and record evidence.

## Rules / กฎ

- ห้าม Deploy หากยังไม่มี QA / Never deploy without QA.
- ห้ามถือว่า Approval ระบบเท่ากับ Approval Deploy / System approval is not deployment approval.
- ห้ามแก้ Source Code ระหว่าง Release / Do not patch source during release.
- หยุดเมื่อ Version, Target, Conflict หรือ Rollback ไม่ชัดเจน / Stop when version,
  target, conflict, or rollback is unclear.

## Handoff / การส่งต่อ

ส่งมอบ Version, Mode, Target, เวลา, Evidence, Known Limitations และ Rollback Point
/ Deliver the version, mode, target, time, evidence, limitations, and rollback point.

## Shared Context Contract / สัญญาบริบทกลาง

ก่อน Release ต้องตรวจ QA Status, Version, Target, Existing Deployments, Related
Skills, Connections, Permission State และ Rollback Point. หาก Target หรือสิทธิ์ไม่ชัด
ให้หยุดและขอ Owner Approval / Before release, verify QA status, version, target,
existing deployments, related skills, connections, permission state, and rollback
point. Stop and request Owner approval when the target or authority is unclear.
