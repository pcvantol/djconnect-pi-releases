# DJConnect Agent Guidance

This repository follows the DJConnect design foundation maintained in `pcvantol/djconnect`.

Before changing Pi release artifacts, release notes, publication flow, checksums, download structure, or security/privacy behavior, read the source-of-truth documents in the Home Assistant integration repo:

1. `DJCONNECT_CONSTITUTION.md`
2. `PRODUCT_VISION.md`
3. `DESIGN_PRINCIPLES.md`
4. `ARCHITECTURE_PRINCIPLES.md`
5. `CI_CD_RELEASE_GOVERNANCE.md`
6. `PRODUCT_ROADMAP.md`
7. `INNOVATION_LAB.md`
8. `SYNC_PROMPTS.md`

## Repository role

`pcvantol/djconnect-pi-releases` is a public release/distribution surface for Pi client artifacts and release metadata.

It should not own product logic. It must preserve release integrity, version clarity, artifact consistency, and safe update paths.

## Release rules

- Do not publish secrets, tokens, private keys, private logs, or production user/device data.
- Keep artifacts, manifests, checksums, and release notes aligned.
- Public release notes should be clear enough for community users to decide whether to update.
- Contract changes must be reflected in `pcvantol/djconnect/SYNC_PROMPTS.md` and the canonical roadmap.
