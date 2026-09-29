# opentest.design-hub

The OpenTest Labs design hub repository.

## Current brand assets

The approved PNG masters in `logos/final/` are the visual source of truth:

- [Brand test-loop icon](./logos/final/opentest-brand-loop.png) — for brand, test execution, documentation, and launch surfaces
- [Desktop application icon](./logos/final/opentest-app-icon.png) — desktop program icon (enlarged OT glyph, no outer loop)
- [Asset usage and locked-glyph specification](./logos/final/README.md)

Production outputs:

- `logos/brand-loop/` — PNG sizes 16, 20, 24, 32, 40, 48, 64, 128, 256, 512, and 1024
- `logos/app-icon/` — the same PNG sizes plus a multi-resolution Windows `ICO`

Regenerate the size sets from the repository root with `python logos/generate-final-assets.py` (requires Pillow). Vector (SVG) production is still pending; the custom OT glyph is locked and must not be altered.

## Ecosystem profile

- [`profile/`](./profile/) — OpenTest Labs GitHub organization profile page, including the ecosystem map, repository responsibilities and boundaries, planned tooling, and governance rules
