# Skill Sync Protocol v1

## Goal

Keep shared skills synchronized between Nova (AWS) and Rock (Mac mini) with a clear source of truth and a simple verification loop.

## Scope

This protocol applies only to shared skills that should behave the same in both environments.

## Roles

- **Danny** — sets direction, approves what should become a shared skill
- **Nova** — drafts/updates the shared skill files and pushes the canonical repo version
- **Rock** — reviews the skill design/content, installs from repo on Mac mini, and verifies checksums

## Source of Truth

The GitHub repo is the source of truth for shared skills.

Do not treat Discord text, screenshots, or pasted snippets as the final sync source.
Those are for discussion/review only.

## Standard Flow

### 1. Propose
A new skill or skill change is proposed in chat.

### 2. Draft
Nova prepares or updates the canonical `SKILL.md` file.

### 3. Review
Rock reviews for:
- trigger scope
- overlap/conflict with existing skills
- platform neutrality
- clarity of rules and boundaries

### 4. Approve
Danny decides whether to ship.

### 5. Publish
Nova pushes the approved file(s) to this repo.

### 6. Install
Rock pulls from this repo and copies the skill file(s) into the Mac mini workspace.

### 7. Verify
Both sides compute sha256 on the shared files.
Sync is complete only when the checksums match.

## Required Checks

For each shared skill, verify:
- file path exists
- `name` is correct
- `version` is correct
- `description` is correct
- sha256 matches across both sides

## Versioning Rule

Any content change to a shared skill should bump `version`.

Recommended:
- patch (`1.0.1`) for wording/clarity-only changes
- minor (`1.1.0`) for meaningful behavior/trigger/rule changes
- major (`2.0.0`) for breaking conceptual changes

## Completion Standard

A skill is only considered **synced** when:
1. the repo contains the final approved file
2. Nova and Rock both use that repo version
3. sha256 matches on both sides

## Repo Hygiene

Keep this repo small and clean.

Include:
- shared production skills
- index/checksum docs
- sync protocol docs

Avoid adding:
- local-only notes
- secrets
- scratch files
- unfinished experiments unless clearly isolated

## Failure Handling

If checksums do not match:
1. stop claiming sync is complete
2. pull from repo again
3. reinstall from repo, not from chat text
4. recompute sha256
5. only then confirm sync

## Current Team Rhythm

- Danny sets direction
- Rock extracts/reviews the methodology
- Nova turns it into canonical files and publishes
- Rock installs and verifies on Mac mini

This rhythm is the default unless Danny changes it.
