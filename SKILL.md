---
name: authoring-realistic-3d-materials
description: Use when creating, texturing, reviewing, or fixing 3D models whose materials, textures, colors, roughness, glass, weathering, or surface depth look flat, plastic, too clean, too noisy, incorrectly scaled, or physically implausible.
---

# Authoring Realistic 3D Materials

## Overview

This skill improves **material realism, texture depth, and color choice** for 3D models across different AI harnesses and DCC/game workflows.

**Core principle:** realism is not random noise. Realistic materials come from identifying the real-world material, reproducing its physical structure at the correct scale, choosing plausible intrinsic color, varying roughness and microstructure, and applying restrained wear where physics and use would actually cause it.

The target is a surface that looks and behaves like a real material at close, medium, and scene distance rather than a color printed onto plastic geometry.

## Capability Truth First

Before acting, classify useful capabilities in the current harness:

- **AVAILABLE NOW** — visibly exposed and usable in this session.
- **CONDITIONAL** — may be available after the user supplies a file, tool, plugin, or environment.
- **EMULATED** — can be reasoned about or specified, but not executed directly.
- **UNAVAILABLE** — cannot be used here.

Never claim to have opened Blender, edited a shader graph, rendered, baked maps, inspected a model, or verified a result unless that actually happened in the current environment.

If direct editing is unavailable, produce the strongest actionable material specification possible.

## Material Realism Workflow

Follow this order unless the task clearly requires a smaller subset.

### 1. Preserve the intended asset

When improving an existing model or reference-matched building, do not casually redesign it.

Preserve unless explicitly asked to change:

- silhouette
- dimensions and proportions
- window count and placement
- doors and storefront layout
- cornices, sills, trim, balconies, roof form
- architectural era and construction logic

Material realism should not become unwanted architectural drift.

### 2. Identify the real material

Before changing a surface, determine what it is likely made from.

Examples:

- painted lime/cement plaster
- stucco/render
- exposed concrete
- granite
- sandstone or limestone
- brick and mortar
- ceramic tile
- painted steel/aluminum
- galvanized metal
- painted or bare wood
- glass
- asphalt
- concrete paving
- composite façade panel

Also identify condition: new, maintained, sun-faded, repaired, wet, dirty, chipped, oxidized, polished, heavily trafficked, or weather-exposed.

Do not texture first and identify later.

### 3. Separate materials by physical behavior

If two regions would weather, reflect, or age differently in reality, they usually need distinct materials, masks, or layered responses.

Typical building separation:

- main façade render
- window/door stone trim
- sill/ledge stone
- storefront framing
- painted shutters
- wood doors
- metal rails
- glass panes
- base/plinth material
- roof material
- paving/asphalt
- repair patches

### 4. Establish correct real-world scale

A high-resolution texture at the wrong scale still looks fake.

Use known architecture as scale reference:

- standard door height
- window dimensions
- brick courses
- curb height
- stone block size
- panel spacing
- timber board width

Check that plaster grain is not boulder-sized, wood pores are not giant, asphalt aggregate is not pebble landscaping, and stone crystals do not read like painted dots.

### 5. Choose intrinsic color, not photographed lighting

Estimate the surface's base/albedo color rather than copying the visible RGB value from a lit photograph.

Account for:

- warm/cool sun
- blue sky cast
- exposure and white balance
- wetness
- reflections
- shadows
- camera processing

Rules:

- avoid pure white and pure black unless physically justified
- slightly desaturated colors are often more believable than game-like saturation
- old painted surfaces should rarely be perfectly uniform
- repair patches may differ subtly in hue/value
- dirt and moisture should affect local value logically

### 6. Build macro, meso, and micro structure

Realism needs several scales of information.

**Macro:** major material zones, stains, repairs, large value variation, construction seams.

**Meso:** stone grain, plaster buildup, brick variation, wood boards, concrete casting variation.

**Micro:** pores, tiny scratches, fine aggregate, subtle surface roughness breakup.

Do not use one procedural noise node at three strengths and call it realism.

### 7. Use PBR maps according to physical meaning

#### Base Color / Albedo

Contains intrinsic color and surface appearance without baked directional lighting.

Use subtle local variation, repairs, stains, and material-specific breakup. Avoid painted-in highlights and shadows.

#### Roughness

Treat roughness as a primary realism channel.

Vary it by material and condition:

- old plaster: broad matte response with small local variation
- polished stone: lower roughness with mineral variation
- dirty or oxidized metal: rougher affected zones
- painted wood: coating response distinct from exposed substrate
- wet asphalt: much lower roughness in wet zones
- touched handles/rails: local wear may alter roughness

Never assign one uniform roughness value to an entire mixed façade.

#### Normal

Use for small and medium surface relief that does not need to alter the silhouette.

Examples: plaster grain, pores, shallow stone texture, fine wood grain, tiny mortar irregularity.

Normal detail must have believable amplitude. Strong noisy normals are a common CG giveaway.

#### Height / Displacement

Use for depth that should meaningfully affect surface profile or parallax:

- recessed mortar
- stone relief
- chipped plaster buildup
- panel seams
- deeper grooves
- curb/paving transitions

Do not force major architectural form into a tiny normal map.

#### Ambient Occlusion

Use carefully for cavities and local contact behavior. Do not use heavy AO to fake detail or bake dirty black outlines around everything.

#### Metallic

Only conductive bare metal regions should behave as metallic. Painted metal coatings are generally dielectric until the metal substrate is exposed.

#### Opacity / Transmission / Glass

Glass should respond to angle, reflection, interior darkness, cleanliness, and framing. Avoid identical black windows or perfect mirrors across a whole building.

### 8. Make depth correspond to the material

**Plaster/stucco:** fine aggregate, trowel irregularity, shallow pits, restrained repairs.

**Granite:** mineral/crystalline breakup, cut-face roughness, subtle chipped edges; not a smooth brown slab with speckles painted on.

**Sandstone/limestone:** layered/mineral variation, porous response, edge erosion appropriate to age.

**Brick:** real mortar recession, restrained brick-to-brick variation, slightly imperfect edges.

**Wood:** correct grain direction, pores/fibers, board seams, coating behavior, wear at contact points.

**Painted metal:** coating roughness separated from exposed substrate; oxidation only where plausible.

**Concrete:** pores, subtle aggregate/casting variation, optional formwork logic when appropriate.

**Asphalt:** aggregate structure, patching and traffic wear at realistic scale.

### 9. Apply weathering by cause

Weathering should answer **why is this mark here?**

Plausible locations include:

- beneath sills and ledges
- below cornices
- splash zones near ground
- rain paths
- drainpipes and outlets
- joints and seams
- outward exposed edges
- repeated human-contact zones
- repair boundaries
- storefront bases

Keep weathering restrained unless the reference shows severe neglect.

Avoid:

- evenly distributed dirt
- identical cracks everywhere
- random rust on protected metal
- giant structural cracks added merely for "detail"
- turning a maintained building into a ruin

### 10. Control repetition

Prevent obvious tiling using a small number of physically justified layers:

- macro color variation
- secondary roughness breakup
- decals or repair masks
- per-instance variation
- alternate patches/tiles when needed

Do not hide repetition by drowning the material in noise.

### 11. Decide geometry vs texture correctly

Prefer geometry or meaningful displacement for features that cast a visible profile or shadow:

- sills
- cornices
- moldings
- deep joints
- façade relief
- door panel depth
- curb height
- strong stone offsets

Prefer texture maps for:

- pores
- shallow plaster irregularity
- fine grain
- micro scratches
- subtle stone breakup
- hairline surface cracks

### 12. Differentiate old and new construction

For mixed urban streets:

- older façades usually need more subtle irregularity, repairs, edge wear, and color drift
- modern façades can be cleaner but still require physical roughness and manufacturing variation
- ground floors usually show more moisture, dirt, impact, and human wear
- storefront systems should read differently from upper residential walls
- adjacent windows should not all have identical reflectivity or interior darkness

## Material Quick Rules

### Plaster / Stucco

Must have subtle unevenness, fine grain, slight tonal drift, believable roughness, and localized rain/dirt behavior.

Avoid glossy walls, crater noise, uniform gray bump, and excessive cracks.

### Granite / Natural Stone

Must have mineral structure, physical roughness, real scale, sharper but imperfect edges, and restrained grime in recesses.

Avoid flat painted speckles and plastic-looking slabs.

### Brick / Masonry

Must have mortar depth, brick variation within a believable family, and small edge imperfections.

Avoid flat photo wallpaper and identical repeating bricks.

### Wood

Must have correct grain direction, real-scale fibers/pores, coating response, and localized wear.

Avoid giant grain and glossy plastic response.

### Metal

Must use appropriate reflectivity/roughness and distinguish coating from substrate.

Avoid making every metal chrome or adding random rust.

### Glass

Must have angle-dependent reflection, believable framing, variation between rooms/panes, and some sense of depth when appropriate.

Avoid pure black rectangles and identical mirrors.

### Concrete

Must have restrained pores and casting/material variation.

Avoid perfectly smooth gray planes and generic high-strength noise.

### Asphalt / Pavement

Must have aggregate at correct scale, subtle patching/traffic wear, and plausible wetness response when applicable.

Avoid smooth gray floors and exaggerated damage.

## Anti-Plastic Checklist

When something looks "printed on plastic," inspect these first:

1. uniform roughness
2. overly flat base color
3. missing medium-scale depth
4. wrong texture scale
5. too-clean edges
6. dead/identical glass
7. lighting baked into color
8. geometry that should have actual profile but only has bump

Fix the physical cause instead of simply increasing texture contrast.

## Reference Matching Rules

When references are supplied:

1. Treat them as evidence, not decoration.
2. Identify which reference best shows color, material, depth, and weathering separately.
3. Do not infer hidden details confidently when they are not visible.
4. Preserve verified architecture.
5. Use multiple references to distinguish material color from lighting.
6. If a reference is low quality, state uncertainty rather than inventing exact microstructure.

## Performance and Texture Resolution

Higher resolution does not automatically mean more realism.

Prioritize in this order:

1. correct material identity
2. correct scale
3. correct roughness behavior
4. correct depth hierarchy
5. controlled variation
6. sufficient resolution

For game assets, choose texture size based on camera distance, projected screen size, reuse, and platform budget. Do not make every surface 8K by default.

When multiple quality tiers are required, preserve material identity across tiers while reducing expensive displacement, unique maps, shader complexity, and texel density progressively.

## Mandatory QA Pass

If visual inspection is available, review at three distances:

### Close

Check grain scale, pores, normal strength, edge behavior, seams, glass, and micro roughness.

### Medium

Check whether each material reads immediately as plaster/stone/wood/metal/glass rather than generic "texture."

### Scene / Street Distance

Check overall color balance, repetition, age differences, roughness readability, and whether the asset still feels physically grounded.

Ask:

- Does anything look flat?
- Does anything look plastic?
- Does anything look too clean?
- Does anything look too noisy?
- Is texture scale believable?
- Are colors too saturated or too uniform?
- Does weathering have a cause?
- Are roughness changes meaningful?
- Does any normal/displacement amplitude look exaggerated?
- Are repeated windows/materials too identical?

If direct visual inspection is unavailable, explicitly state that visual QA was not performed and provide the QA checklist for the user/harness that can render it.

## Required Output Pattern

When applying this skill, use a compact structure appropriate to task size:

1. **Material identification** — what the major surfaces actually are.
2. **Problems found** — flatness, scale, color, roughness, depth, repetition, glass, or weathering issues.
3. **Improvement plan** — per material: color, roughness, normal/height, geometry, weathering.
4. **Execution/specification** — make edits when tools exist; otherwise provide precise instructions.
5. **QA** — state what was actually inspected and any remaining uncertainty.

## Non-Negotiable Rules

1. Do not confuse noise with realism.
2. Do not use one perfectly flat color for a real aged material.
3. Do not copy photographed lighting tint into base color without correction.
4. Do not make every material equally rough.
5. Do not over-weather maintained assets.
6. Do not ignore real-world texture scale.
7. Do not use bump/normal as a substitute for major geometry.
8. Do not make all glass panes identical.
9. Do not change verified architecture just to make a texture pass "more interesting."
10. Do not claim rendering or visual verification that did not happen.
11. Do not stop at "more detail"; require believable physical material behavior.
12. When in doubt, prefer restrained, physically explainable variation over dramatic procedural effects.
