# Example: Building Façade Review

## Input situation

A street render has correct building geometry, but the façades look clean, flat, and game-like. The user wants the architecture preserved while improving realism.

## Material identification

- main wall: painted plaster/render
- window surrounds: natural stone/granite
- storefront band: painted metal/composite
- frames: painted metal or wood depending on reference
- glazing: architectural glass
- road/sidewalk: asphalt and stone/concrete paving

## Problems found

- wall albedo is too uniform
- roughness is nearly constant
- stone trim reads as colored geometry rather than mineral material
- windows are too identical
- shallow façade detail relies on geometry but has no micro-surface character
- ground-floor surfaces are as clean as upper floors

## Improvement plan

### Plaster

Use a muted intrinsic base color with broad low-contrast tonal drift. Add fine plaster aggregate in normal, subtle roughness variation, faint repairs, and localized rain/splash staining. Keep large cracks absent unless shown in reference.

### Stone trim

Introduce real-scale mineral breakup and cut-stone roughness. Add tiny chips only on exposed edges. Keep stone hue variation inside a coherent mineral family.

### Glass

Vary interior darkness and reflection slightly per window group. Preserve physically plausible reflection and avoid pure black.

### Ground floor

Increase localized grime and moisture response near pavement, frames, and recesses without turning the building abandoned.

## QA

At street distance, the building should first read as the same architecture. The material pass should be noticeable through physical response and subtle imperfection, not through dramatic color or random damage.
