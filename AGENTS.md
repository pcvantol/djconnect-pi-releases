# DJConnect Pi Releases Agent Instructions

## DJConnect Platform Bootstrap

For a clean Codex/AI-agent session, first follow the canonical platform bootstrap:

`pcvantol/djconnect/BOOTSTRAP_CODEX_SESSION.md`

Then continue with the repository-specific instructions in this file.

This repository extends the DJConnect Platform Foundation. It does not redefine it.

This must be additive only. Existing repo-specific AGENTS guidance remains authoritative for implementation details.


This repository follows the canonical DJConnect design foundation in `pcvantol/djconnect`.

## Role

This repo is a distribution surface for public/community DJConnect Pi release artifacts and release notes.

It does not own product logic, Pi client source, platform contracts or roadmap decisions.

Canonical source files live in `pcvantol/djconnect`:

- `DJCONNECT_CONSTITUTION.md`
- `PRODUCT_VISION.md`
- `PRODUCT_LANGUAGE.md`
- `PLATFORM_GOVERNANCE.md`
- `PLATFORM_QUALITY_STANDARD.md`
- `SYNC_PROMPTS.md`
- `PRODUCT_ROADMAP.md`

## Rules

- Keep artifacts traceable to source commits in `pcvantol/djconnect-pi`.
- Do not publish signing secrets, tokens, private user data or Home Assistant credentials.
- Release notes should be user-facing and use official product language.
- Do not fork roadmap or sync prompts locally.
- Pi release changes must preserve the Pi role as a community Ambient Client.
