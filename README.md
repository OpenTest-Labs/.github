# OpenTest Labs · organization repository

This repository is the organization-level `.github` repository for the
[OpenTest-Labs](https://github.com/OpenTest-Labs) GitHub organization. It holds
the files GitHub renders for the organization itself. It is not a product,
library, or service repository.

## What GitHub renders from here

| Path | Where it appears |
| --- | --- |
| [`profile/README.md`](./profile/README.md) | The organization profile page: <https://github.com/OpenTest-Labs> |
| `README.md` (this file) | This repository's own landing page: <https://github.com/OpenTest-Labs/.github> |
| [`profile/assets/`](./profile/assets/) | Images referenced by the organization profile |

Only files under `profile/` are published on the organization page; every other
path is only read in this repository's context.

## Editing rules

- The organization profile is the single source of truth for the ecosystem
  introduction, repository responsibilities and boundaries, and the ecosystem
  map. Maintain it in `profile/README.md` and nowhere else — a second copy kept
  in another repository will drift out of date.
- Keep this root README about the repository itself. Ecosystem content belongs
  in `profile/README.md`, so that it is written and reviewed only once.
- Reference images with paths relative to `profile/`, for example
  `./assets/opentest-brand-loop-256.png`.
- The organization profile is public. Do not add product secrets, private
  hostnames, or unreleased customer information.
- Product source code, releases, and deployment assets never belong here; every
  project owns its own repository.

## Organization-level files

Community health files that should apply to every repository in the
organization — for example `CONTRIBUTING.md`, `SECURITY.md`, and issue and
pull-request templates under `.github/` — belong in this repository so that each
repository inherits them. None are published yet.

## Brand

The OpenTest glyph is locked: do not alter its shapes, proportions, or the red
status dot. Asset masters, size sets, and usage guidance live in
[opentest.design-hub](https://github.com/OpenTest-Labs/opentest.design-hub).

## Ecosystem

For the repository map, responsibilities, boundaries, and governance, see the
[organization profile](./profile/README.md) or the rendered page at
<https://github.com/OpenTest-Labs>.
