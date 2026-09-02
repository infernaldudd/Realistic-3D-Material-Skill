# Realistic 3D Material Skill

A portable AI skill for improving **3D material realism, texture depth, PBR behavior, and color choice** without falling into the common "add random noise" trap.

The skill is designed for architecture, environment art, props, game assets, Blender workflows, OBJ/FBX pipelines, and visual QA. Its core instructions are harness-agnostic: an agent should use whatever capabilities are actually available and never pretend it rendered or edited something when it did not.

## What it improves

- flat/plastic-looking façades
- incorrect color choices caused by photographed lighting
- uniform roughness
- weak or fake material depth
- wrong texture scale
- dead or identical windows
- unrealistic stone, plaster, wood, concrete, metal, glass, and asphalt
- excessive random noise
- excessive weathering
- obvious texture repetition
- bad geometry-vs-normal decisions

## Repository layout

```text
Realistic-3D-Material-Skill/
├─ SKILL.md
├─ README.md
├─ INSTALL.md
├─ LICENSE
├─ references/
│  ├─ material-cheatsheet.md
│  ├─ blender-pbr-checklist.md
│  └─ harness-portability.md
├─ examples/
│  ├─ building-facade-review.md
│  └─ material-spec-template.md
└─ tests/
   └─ pressure-scenarios.md
```

## Basic use

Load `SKILL.md` whenever an agent is creating, reviewing, or fixing a 3D asset whose materials look flat, plastic, too clean, too noisy, incorrectly scaled, or physically implausible.

The skill follows this core flow:

**preserve asset → identify material → establish scale → choose intrinsic color → build PBR response → add physical depth → weather by cause → control repetition → QA at multiple distances**

## Harness support

The skill itself is intentionally portable. Installation differs between products. See [`INSTALL.md`](INSTALL.md) and [`references/harness-portability.md`](references/harness-portability.md).

A harness does **not** need Blender access for the skill to be useful: without direct editing tools it can still produce a precise material specification, shader plan, map plan, QA report, or correction prompt.

## Design philosophy

> More texture is not automatically more realism.

The skill prioritizes material identity, physical structure, scale, roughness, depth hierarchy, and restrained imperfection before resolution or procedural complexity.

## License

MIT. See [`LICENSE`](LICENSE).
