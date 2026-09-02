# Harness Portability

The skill is intentionally tool-agnostic. Its behavior should scale to the capabilities of the current harness.

## Capability levels

### Text-only agent

Can:
- identify likely materials from user description
- produce PBR specifications
- propose map ranges and shader structure
- write correction prompts/checklists

Cannot honestly claim:
- it opened the model
- it rendered the scene
- it visually verified a material

### Vision-capable agent

Can additionally:
- inspect references/renders
- compare material appearance
- identify likely scale/color/roughness failures
- perform visual QA on supplied images

### Filesystem/code-capable agent

Can additionally:
- inspect material definitions/scripts
- modify text-based assets/configs
- generate helper scripts when appropriate
- validate repository/file structure

### DCC-integrated agent

When actual Blender/Maya/Houdini/etc. control is exposed, it may directly edit materials, mapping, nodes, UV-related settings, render tests, and iterate from visual QA.

It still must state what it actually verified.

## Harness-specific adaptation rule

Never weaken the material reasoning because the harness is limited. Instead change the **execution form**:

- direct tool access → execute and verify
- partial access → edit what is available and specify the rest
- no edit access → produce a precise implementation spec

## Portability anti-patterns

Avoid instructions that require:

- a specific hidden agent system
- shell access that may not exist
- a particular renderer unless the task names it
- pretending chat-only models can manipulate `.blend` files directly
- claiming universal installation paths

The portable core is the reasoning and QA standard, not one product's tool API.
