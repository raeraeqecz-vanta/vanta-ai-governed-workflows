---
name: stress-test-and-sharpen
description: >
  TH: ตรวจจับจุดอ่อน ความเสี่ยง ช่องว่าง และความไม่สอดคล้องของแนวคิด ระบบ
  หรือข้อกำหนดด้วยการรับฟังข้อมูลก่อน แล้ว Stress Test อย่างเป็นกลาง พร้อม
  ลับคมด้วยคำถามทีละข้อ ใช้เมื่อผู้ใช้ต้องการตรวจทานหรืออุดรอยรั่ว
  EN: Detect weaknesses, risks, gaps, and inconsistencies in ideas, systems,
  or requirements through open intake and objective stress testing, then sharpen
  them with one focused question at a time. Use for review and hardening.
---

# ทดสอบแรงกดดันและลับคม / Stress Test and Sharpen

## Workflow / ขั้นตอน

1. อ่าน Project Context และผลลัพธ์ก่อนหน้า / Read project context and prior outputs.
2. แยก `Verified`, `Assumption`, `Unknown` / Separate facts, assumptions, and unknowns.
3. สรุปเจตนาและขอบเขต / Reflect intent and scope.
4. ตรวจ Blind Spots, Conflict, Edge Cases และ Performance Risks / Check blind
   spots, conflicts, edge cases, and performance risks.
5. ถามหนึ่งคำถามที่ลดความไม่แน่นอนมากที่สุด / Ask one highest-value question.
6. เมื่อข้อมูลพอ ให้ส่ง Blueprint พร้อม Scope และ Stop Conditions / Deliver a
   blueprint with scope and stop conditions when evidence is sufficient.

## Rules / กฎ

- ห้ามเดาข้อเท็จจริง / Do not invent facts.
- ใช้ Specialist Lens ได้ แต่ห้ามอ้างว่าเป็น Agent อิสระจริง / Use bounded
  specialist lenses without claiming autonomous agents were created.
- ห้ามเปิดเผยกระบวนการคิดภายใน / Do not expose hidden chain-of-thought.
- ห้ามเขียนโค้ดจริงในขั้นนี้ / Do not write production code here.

## Handoff / การส่งต่อ

เมื่อ Blueprint ได้รับการยืนยัน ให้แนะนำ `blueprint-to-tasks` / When the blueprint
is confirmed, recommend `blueprint-to-tasks`.

## Shared Context Contract / สัญญาบริบทกลาง

ก่อน Stress Test ให้ตรวจบริบทและการเปลี่ยนแปลงก่อนหน้า รวมถึง Skill หรือระบบที่อาจ
ทำงานชนกัน. รายงานสิ่งที่ตรวจพบ สิ่งที่ยังขาด และข้อจำกัดของ Connection โดยไม่อ้างว่า
เข้าถึงข้อมูลภายนอกได้หากยังไม่ได้รับสิทธิ์ / Before stress testing, inspect prior
context and changes, including Skills or systems that may conflict. Report what was
detected, what is missing, and connection limits without claiming external access
that has not been granted.
