# Skill System Guide / คู่มือระบบ Skill

**System:** `thai-ai-governed-workflows`  
**Document:** Skill System Guide  
**Version:** `v0.1`  
**Status:** Proposed Baseline / Approved for implementation planning  
**Language:** Thai–English

## 1. Purpose / วัตถุประสงค์

กำหนดมาตรฐานกลางสำหรับการติดตั้ง เรียกใช้ ตรวจบริบท ตรวจความสามารถ จัดการทรัพยากร และส่งต่องานระหว่าง Skill บน ChatGPT และ Codex โดยให้ทุก Skill ทำงานร่วมกันได้อย่างเป็นระเบียบ ไม่ถามข้อมูลซ้ำ และไม่ดำเนินการเกินสิทธิ์ที่ได้รับ

Define the shared standard for installing, invoking, discovering context and capabilities, resolving resources, and handing work between Skills across ChatGPT and Codex. Every Skill must operate consistently, avoid redundant questions, and stay within its granted authority.

## 2. Repository and Collection Model / โมเดล Repository และชุด Skill

```text
Repository: thai-ai-governed-workflows
Current collection: governed-project-delivery
```

Recommended top-level collections:

```text
skills/
├── foundation/       # Context, capability, conflict, and routing
├── specification/    # Requirements, governed specs, and task breakdown
├── implementation/   # Approved implementation and code review
├── documentation/    # Manuals and operational documentation
├── release/          # Release, handoff, and delivery readiness
└── domains/          # Web, game, Roblox, business, research, and future domains
```

## 3. Foundation Skill / Skill ชั้นพื้นฐาน

`setup-skill-context` is the required context entry point for a new project, a newly installed Skill set, or an uncertain working state.

หน้าที่หลัก:

- ตรวจสอบห้องทำงาน โปรเจกต์ ไฟล์ และผลลัพธ์ก่อนหน้า
- ตรวจสอบ Repository, Git Remote และตำแหน่งจัดเก็บ
- ตรวจสอบ Skill, App, Plugin และ Connection ที่ระบบเปิดเผย
- ตรวจสอบระดับสิทธิ์และข้อจำกัด
- ตรวจสอบทรัพยากรที่ยังขาด
- ตรวจ Skill หรือการเปลี่ยนแปลงที่อาจทำงานชนกัน
- สร้าง `Current Work Context` ให้ Skill ถัดไป

## 4. Context and Capability Levels / ระดับการรับรู้

| Level | English | Thai | Default |
|---|---|---|---|
| L0 | User Input | ข้อมูลจากผู้ใช้โดยตรง | Required |
| L1 | Project Context | โปรเจกต์ ห้องทำงาน ไฟล์ และสถานะ | Required |
| L2 | Skill Registry | Skill ที่ติดตั้งและเกี่ยวข้อง | Required |
| L3 | Capability Metadata | Apps, Plugins, Tools และ Connections ที่ระบบประกาศ | Required when exposed |
| L4 | Permission State | สถานะ Read, Write, Action หรือไม่ทราบ | Required when exposed |
| L5 | External Data or Action | ข้อมูลจริงหรือการกระทำภายนอก | Task-specific only |

**Rule:** Detected capability does not equal authorized action.  
**กฎ:** การตรวจพบความสามารถไม่เท่ากับการได้รับอนุญาตให้ดำเนินการ

## 5. Capability and Resource Resolution / การแก้ช่องว่างของทรัพยากร

ทุก Skill ต้องตรวจตามลำดับนี้ก่อนเริ่มงาน:

```text
Detect context
→ Detect capabilities
→ Detect connections
→ Detect target resources
→ Identify missing information
→ Propose resolutions
→ Request Owner approval when needed
→ Execute within scope
```

หากตรวจพบ Connection แต่ไม่พบ Repository, ชื่อ, ตำแหน่ง หรือทรัพยากรเป้าหมาย ให้เสนอทางเลือก เช่น:

1. ใช้ทรัพยากรที่ตรวจพบแล้ว
2. ค้นหาทรัพยากรเดิมที่เกี่ยวข้อง
3. ร่างโครงสร้างหรือชื่อใหม่
4. ขออนุมัติจัดสร้างทรัพยากรใหม่
5. ดำเนินงานต่อโดยไม่ใช้ทรัพยากรนั้น

Skill ต้องไม่สร้าง Repository, Connection, Secret, Push หรือ Deploy โดยอัตโนมัติ

## 6. Authority Levels / ระดับสิทธิ์

| Authority | Allowed behavior | ตัวอย่าง |
|---|---|---|
| `DISCOVER` | Read and report | ตรวจพบ Repository และสถานะ |
| `PROPOSE` | Suggest options and drafts | เสนอชื่อและโครงสร้าง |
| `CREATE` | Create or modify real resources after approval | สร้างไฟล์หรือ Repository หลังอนุมัติ |
| `PUBLISH` | Push, release, deploy, or external action | ส่งมอบหรือ Deploy หลังอนุมัติเฉพาะกิจ |

ค่าเริ่มต้นของทุก Skill คือ `DISCOVER + PROPOSE` การใช้ `CREATE` หรือ `PUBLISH` ต้องมี Owner Approval ที่ชัดเจน

## 7. Standard Context Report / รูปแบบรายงานมาตรฐาน

```markdown
## Context & Capability Check / ตรวจบริบทและความสามารถ

### Detected / ตรวจพบ
- Project:
- Repository:
- Git Remote:
- Skills:
- Apps and Connections:
- Permission State:

### Missing / ยังไม่พบ
- Target resource:
- Target path:
- Required permission:

### Conflicts / ความเสี่ยงการชนกัน
- Existing work:
- Related Skill:
- Possible overwrite:

### Proposed Resolution / ทางเลือก
1.
2.
3.

### Owner Decision / การตัดสินใจของ Owner
[ถามเฉพาะข้อมูลหรือการอนุมัติที่ยังจำเป็น]
```

## 8. Cross-Platform Model / โมเดลข้ามแพลตฟอร์ม

ทุก Skill ควรแยกเป็น 3 ชั้น:

```text
Core Skill Logic       = กฎและกระบวนการกลาง
Platform Adapter       = วิธีติดตั้งและเรียกใช้บน ChatGPT หรือ Codex
Capability Adapter     = วิธีตรวจไฟล์ เครื่องมือ Apps และสิทธิ์
```

ตรรกะหลักควรใช้ร่วมกันได้ แต่คำสั่งติดตั้ง การเรียกใช้ และความสามารถจริงอาจแตกต่างกันตามแพลตฟอร์ม

## 9. Conflict and Handoff Rules / กฎการชนกันและส่งต่องาน

ก่อนเริ่มงาน Skill ต้องตรวจว่า:

- มีผลลัพธ์เดิมที่อาจถูกเขียนทับหรือไม่
- ผู้ใช้หรือระบบอื่นแก้ไขเป้าหมายไปแล้วหรือไม่
- มี Skill อื่นทำงานเดียวกันหรือไม่
- สถานะงานถึงจุดที่ควรใช้ QA, manual หรือ release Skill หรือไม่
- ต้องหยุดรอ Owner Decision หรือไม่

ทุก Handoff ต้องส่งต่ออย่างน้อย:

- Current Context
- Confirmed Decisions
- Pending Decisions
- Changed Files or Outputs
- Known Risks
- Recommended Next Skill

## 10. Installation and Invocation / การติดตั้งและเรียกใช้

ตัวอย่างติดตั้งทั้งชุด:

```bash
npx skills@latest add OWNER/thai-ai-governed-workflows -y -g
```

ตัวอย่างติดตั้งเฉพาะ Skill:

```bash
npx skills@latest add OWNER/thai-ai-governed-workflows --skill=setup-skill-context
```

คำสั่งเรียกใช้ต้องอิงตามแพลตฟอร์มที่กำลังทำงานอยู่ และต้องไม่สรุปว่าความสามารถของ ChatGPT กับ Codex เหมือนกันทั้งหมด

## 11. Safety and Approval Gate / ความปลอดภัยและจุดรออนุมัติ

ต้องขอ Owner Approval ก่อน:

- สร้างหรือแก้ไขทรัพยากรภายนอก
- สร้างหรือใช้ Secret, Token หรือ Credential
- Push หรือ Merge การเปลี่ยนแปลง
- Deploy หรือ Release
- เปลี่ยนแปลง Storage, Database, Auth หรือ Billing
- ดำเนินการที่ย้อนกลับได้ยาก

ห้าม Skill อ้างว่าดำเนินการสำเร็จ หากยังไม่ได้ตรวจสอบผลลัพธ์จริง

## 12. Required Skill Contract / สัญญาที่ทุก Skill ต้องมี

ทุก `SKILL.md` ต้องระบุอย่างน้อย:

- Scope and purpose / ขอบเขตและวัตถุประสงค์
- Trigger / เงื่อนไขการเรียกใช้
- Context requirements / บริบทที่ต้องใช้
- Capability detection / การตรวจความสามารถ
- Required resources / ทรัพยากรที่ต้องใช้
- Missing resource resolution / วิธีจัดการสิ่งที่ขาด
- Authority and approval gate / สิทธิ์และจุดรออนุมัติ
- Conflict detection / การตรวจการชนกัน
- Input and output / ข้อมูลนำเข้าและผลลัพธ์
- Handoff / วิธีส่งต่องาน
- Stop conditions / เงื่อนไขหยุด

## 13. Success Criteria / เงื่อนไขความสำเร็จ

ระบบจะถือว่าการทำงานถูกต้องเมื่อ:

1. Skill ตรวจบริบทก่อนถามข้อมูลที่มีอยู่แล้ว
2. รายงานสิ่งที่พบและสิ่งที่ยังขาดอย่างชัดเจน
3. เสนอทางเลือกเมื่อทรัพยากรเป้าหมายยังไม่มี
4. ไม่สร้างหรือดำเนินการเกินสิทธิ์
5. ตรวจงานเดิมและ Skill ที่อาจชนกัน
6. ส่งต่อ Context และผลลัพธ์ให้ Skill ถัดไปได้
7. ใช้ได้กับสภาพแวดล้อมที่รองรับ Skill โดยไม่ผูกติดกับแพลตฟอร์มเดียว

## 14. Next Action / ขั้นตอนถัดไป

1. นำ Guide นี้ไปใช้เป็นมาตรฐานกลางของ Repository
2. ปรับปรุง `setup-skill-context` ให้เป็น Foundation Skill
3. เพิ่ม Context Contract ให้ Skill เดิมทุกตัว
4. ตรวจและปรับชื่อ โครงสร้าง และเอกสารติดตั้งของแต่ละ Skill
5. ทดสอบการส่งต่อระหว่าง ChatGPT และ Codex

