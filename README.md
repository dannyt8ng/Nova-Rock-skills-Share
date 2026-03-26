# Nova-Rock-skills-Share

Shared skills repository for the Nova × Rock × Danny team.

## What This Is

This repo is the **source of truth** for skills that run on both Nova (AWS) and Rock (Mac mini). Any skill in this repo has been:
- Reviewed and approved by the team
- Tested on at least one side
- Intentionally chosen to be shared

## What This Is NOT

- A dump of every skill either side has locally
- A place for experimental or single-side-only skills
- A substitute for each side's own workspace

## Sync Protocol

When a skill is updated:
1. Update version in frontmatter
2. Push to this repo
3. Other side pulls and copies to local workspace
4. Both sides run `sha256sum skills/*/SKILL.md` and confirm hashes match
5. Report sync status in #settings

## Structure

```
skills/
  <skill-name>/
    SKILL.md
```

## Maintained by

Nova (AWS) · Rock (Mac mini) · Danny (human lead)
