# VANTA AI Governed Workflows

Thai–English governed AI skills for project context, specification, task breakdown, implementation, quality assurance, documentation, and release workflows.

## Install / ติดตั้ง

```bash
npx skills@latest add raeraeqecz-vanta/vanta-ai-governed-workflows -y -g
```

เฉพาะ Skill:

```bash
npx skills@latest add raeraeqecz-vanta/vanta-ai-governed-workflows --skill=setup-skill-context
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

## License

MIT License
