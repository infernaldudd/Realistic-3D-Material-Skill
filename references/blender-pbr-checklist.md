# Blender PBR Checklist

This file is a Blender-oriented companion, but the principles generalize to other PBR renderers.

## Before shader work

- Confirm scene units and object scale are correct.
- Apply/understand object scale before judging texture scale.
- Inspect UV density or mapping method.
- Confirm the material identity from references.
- Separate surfaces that need physically different responses.

## Color management

- Treat albedo/base color as intrinsic color, not a screenshot color sample.
- Avoid baked light/shadow in albedo.
- Use correct image color-space handling: color textures as color data; data maps such as roughness/normal/height as non-color data where appropriate.
- Judge colors under a neutral-enough lighting test before tuning to a dramatic final shot.

## Principled-style PBR logic

- Metallic: only actual exposed metal should be metallic.
- Roughness: drive with physically meaningful variation, not one constant value.
- Normal: keep strength restrained and scale-correct.
- Height/displacement: reserve for depth that should actually change profile/parallax.
- IOR/transmission/glass: use physically plausible glass behavior and account for scene/reflection context.

## Multi-scale breakup

Use independent but related layers:

1. macro color/repair variation
2. material-scale grain/structure
3. micro roughness/normal

Avoid reusing the same noise at multiple scales with only different strength values.

## Edge treatment

Real edges are rarely mathematically razor sharp. Use geometry bevels where the physical object has rounded/chipped manufactured or weathered edges. Do not attempt to fake every structural edge only with a normal map.

## Test lighting

Before approval, inspect the asset under:

- neutral diffuse/overcast-like light for color and roughness
- grazing light for normal/height and edge quality
- intended scene lighting for final integration

A material that only looks good under one dramatic HDRI is not robust.

## Distance QA

### Close
- no giant grain
- no noisy normals
- seams and masks hold up
- stone/plaster/wood microstructure is plausible

### Medium
- material identity is obvious
- roughness changes are visible but not patchy
- repairs/weathering do not dominate

### Far
- façade color remains believable
- no obvious tiling
- windows do not become a repeated black grid
- material differences still separate forms
