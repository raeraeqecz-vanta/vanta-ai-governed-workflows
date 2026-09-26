# VANTA Skills

Thai–English governed AI skills for project context, specification, task breakdown, implementation, quality assurance, documentation, and release workflows.

VANTA Skills is designed to make structured AI workflows easier to understand and use, while keeping governance, authority, evidence, and handoff rules explicit.

## Install / ติดตั้ง

ติดตั้งแบบโต้ตอบ / Interactive install:

```bash
npx skills add raeraeqecz-vanta/skills-th-en
```

ติดตั้งแบบ Global และข้ามคำถามยืนยัน / Global non-interactive install:

```bash
npx skills add raeraeqecz-vanta/skills-th-en -g -y
```

ติดตั้งเฉพาะ Skill / Install a specific Skill:

```bash
npx skills add raeraeqecz-vanta/skills-th-en --skill setup-skill-context
```

## Collections / หมวด Skill

- `foundation/` — context, capability, reconciliation, routing
- `specification/` — requirements, governed specs, task breakdown
- `implementation/` — approved implementation and code review
- `documentation/` — user manuals
- `release/` — release and handoff
- `domains/` — future domain-specific skills

## Governance / การควบคุม

ทุก Skill ต้องตรวจบริบท ความสามารถ ทรัพยากร สิทธิ์ และงานที่อาจชนกันก่อนดำเนินการ การตรวจพบ Connection ไม่เท่ากับการได้รับอนุญาตให้ใช้หรือแก้ไขระบบ

Every Skill must inspect context, capabilities, resources, permissions, and possible conflicts before execution. A detected connection is not authorization to use or mutate a system.

ดูมาตรฐานกลางได้ที่ [Skill System Guide](docs/SKILL-SYSTEM-GUIDE_v0.1_TH-EN.md).

## Repository Identity / อัตลักษณ์ Repository

- Brand / แบรนด์: `VANTA`
- Product / ผลิตภัณฑ์: `VANTA Skills`
- Repository: `raeraeqecz-vanta/skills-th-en`
- Language model / รูปแบบภาษา: Thai–English (TH–EN)

## License

MIT License
