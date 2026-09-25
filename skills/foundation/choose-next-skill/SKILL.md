---
name: choose-next-skill
description: >
  TH: วิเคราะห์บริบท สถานะงาน และเป้าหมายปัจจุบันเพื่อแนะนำ Skill ที่เหมาะสม
  ที่สุดเป็นลำดับถัดไป พร้อมบอกเหตุผล Dependency และ Approval ที่ต้องมี โดยไม่
  เรียกใช้หรือดำเนินการแทนผู้ใช้ ใช้เมื่อผู้ใช้ไม่แน่ใจว่าควรใช้ Skill ใด
  EN: Analyze current context, work status, and intent to recommend the most
  appropriate next skill with reasons, dependencies, and required approvals,
  without invoking or executing it. Use when the user is unsure which skill to use.
---

# เลือก Skill ถัดไป / Choose Next Skill

## Purpose / วัตถุประสงค์

TH: เป็น Router สำหรับชุด Skill โดยอ่านสถานะจริงก่อนแนะนำ ไม่ตัดสินใจแทน Owner

EN: Route work through the skill suite using current evidence without making
decisions on behalf of the Owner.

## Suite Map / แผนผังชุด Skill

```text
setup-skill-context
→ choose-next-skill
→ stress-test-and-sharpen
→ blueprint-to-tasks
→ implement-approved-task
→ code-review-and-fix
→ write-user-manual
→ release-and-handoff
```

## Workflow / ขั้นตอน

1. อ่าน Context และ Handoff ล่าสุด / Read current context and handoff records.
2. ระบุเป้าหมายปัจจุบัน / Identify the current goal.
3. ตรวจว่า Output จากด่านก่อนหน้ามีจริงหรือไม่ / Verify the prior output exists.
4. ตรวจ Conflict, Unknown และ Approval / Check conflicts, unknowns, and approvals.
5. แนะนำ Skill เดียวที่เหมาะสมที่สุด / Recommend one best next skill.
6. อธิบายเหตุผลและเงื่อนไขก่อนเริ่ม / State the reason and prerequisites.

## Output / รูปแบบผลลัพธ์

```markdown
**Current State / สถานะปัจจุบัน:** ...
**Recommended Skill / Skill ที่แนะนำ:** ...
**Why / เหตุผล:** ...
**Prerequisites / สิ่งที่ต้องมีก่อน:** ...
**Conflicts / ความขัดแย้ง:** ...
**Owner Decision / การตัดสินใจของ Owner:** ต้องยืนยันหรือไม่
```

## Rules / กฎ

- ห้ามเรียกใช้ Skill อื่นเอง / Never invoke another skill automatically.
- ห้ามข้าม QA ก่อน Release / Never skip QA before release.
- หากมีหลายทางเลือก ให้แนะนำหนึ่งทางเลือกหลักและระบุทางเลือกสำรอง / Recommend
  one primary route and list alternatives only when useful.
- หาก Context ไม่พอ ให้ตอบ `UNKNOWN` และถามหนึ่งคำถาม / State `UNKNOWN` and ask
  one question when context is insufficient.

## Context and Capability Check / ตรวจบริบทและความสามารถ

ตรวจ Project State, Existing Work, Related Skills, Available Apps or Connections,
Permission State และ Missing Resources ก่อนแนะนำ Skill. หากมีหลายเส้นทาง ให้เสนอ
เส้นทางหลักหนึ่งทางพร้อมเหตุผล และไม่ถือว่าการตรวจพบเครื่องมือเป็นการอนุญาตให้ใช้
เครื่องมือนั้น / Check project state, existing work, related skills, available
apps or connections, permission state, and missing resources before recommending
a Skill. Recommend one primary route with reasons, and never treat a detected
tool as authorization to use it.
