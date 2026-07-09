# DJConnect Pi Releases Agent Instructions

This repository follows the canonical DJConnect design foundation in `pcvantol/djconnect`.

Before changing Pi release artifacts, release notes, publication flow, checksums, download structure, or security/privacy behavior, read the source-of-truth documents in the Home Assistant integration repo.

## Role

This repo is a distribution surface for public/community DJConnect Pi release artifacts and release notes.

It does not own product logic, Pi client source, platform contracts or roadmap decisions. It must preserve release integrity, version clarity, artifact consistency, and safe update paths.

Canonical source files live in `pcvantol/djconnect`:

- `DJCONNECT_CONSTITUTION.md`
- `PRODUCT_VISION.md`
- `DESIGN_PRINCIPLES.md`
- `ARCHITECTURE_PRINCIPLES.md`
- `PRODUCT_LANGUAGE.md`
- `PLATFORM_GOVERNANCE.md`
- `PLATFORM_QUALITY_STANDARD.md`
- `CI_CD_RELEASE_GOVERNANCE.md`
- `SYNC_PROMPTS.md`
- `PRODUCT_ROADMAP.md`
- `INNOVATION_LAB.md`

## Rules

- Keep artifacts traceable to source commits in `pcvantol/djconnect-pi`.
- Keep artifacts, manifests, checksums, and release notes aligned.
- Do not publish signing secrets, tokens, private keys, private logs, private user/device data or Home Assistant credentials.
- Release notes should be user-facing and use official product language.
- Do not fork roadmap or sync prompts locally.
- Contract changes must be reflected in `pcvantol/djconnect/SYNC_PROMPTS.md` and the canonical roadmap.
- Pi release changes must preserve the Pi role as a community Ambient Client.
