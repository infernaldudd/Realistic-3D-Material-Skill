# Installation / Usage

This repository is designed to be portable. Exact installation paths vary by harness and can change over time, so the safest rule is: **place the full skill folder wherever your harness loads user skills/instructions, and keep the relative `references/`, `examples/`, and `tests/` folders intact.**

## Agent Skills-style harnesses

Where the harness supports Agent Skills-style directories, install the whole repository folder as a skill directory and make sure `SKILL.md` is the entry file.

Common examples include a user-level skills directory such as:

```text
~/.agents/skills/authoring-realistic-3d-materials/
```

Some harnesses use their own skill root instead. For example, Claude Code commonly uses a Claude-specific skills directory. Prefer the harness's documented location if it differs.

## Chat-based harnesses

For chat products that do not expose a local skill filesystem, use one of these methods:

- attach or paste `SKILL.md` as reusable project/workspace instructions where supported
- keep the repository linked as a reference and ask the model to follow `SKILL.md`
- paste the relevant reference file for a focused task

Do not assume a chat product automatically executes or installs repository skills merely because the repository exists.

## DCC / 3D tools

This is an AI behavior skill, not a Blender add-on. It does not itself install nodes or scripts.

When an agent has Blender or another DCC available, the skill tells it how to reason about and QA material work. When it does not, the agent should output an actionable PBR/material specification instead.

## Updating

Replace the installed skill folder with the newer repository version, preserving any local project-specific notes outside this repository.
