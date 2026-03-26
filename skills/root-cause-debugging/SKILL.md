---
name: root-cause-debugging
version: 1.0.0
description: Use when debugging a non-trivial bug, failure, regression, unexpected behavior, or unclear broken workflow, especially when the cause is not yet understood. Investigate root cause before proposing or applying fixes.
---

# Root Cause Debugging

**Core principle:** Understand *why* before deciding *what to change*. Symptoms are not root causes.

## When This Skill Activates

- Something is broken, failing, or behaving unexpectedly
- A workflow or service that worked before has stopped working
- You've already tried 1–2 fixes and the problem persists
- The error message is unclear or misleading
- Multiple components are involved and the failure source is uncertain

## The Four Phases

### Phase 1: Read the Failure Signal
- Collect the actual error message, log output, stack trace, or observable symptom
- Note the exact reproduction path (what steps / what conditions)
- Do NOT start fixing yet

### Phase 2: Stabilize Observation
- Can you reproduce it reliably? If yes, lock down the reproduction steps
- If not reproducible: collect more data before proceeding (logs, timing, environment diffs)
- Check: what changed recently? (config, deps, code, environment, network)

### Phase 3: Form a Single Hypothesis
- State one specific hypothesis: "I believe the failure is caused by X because Y"
- Design the smallest possible verification: what would confirm or disprove this?
- Run only that verification — not a batch of changes

### Phase 4: Apply Fix (Only After Hypothesis Is Confirmed)
- Fix the confirmed root cause, not the symptom
- Verify the fix with `evidence-before-claims` before declaring resolved

## Rules

- **症状不是根因。** Don't fix what looks wrong — fix what *is* wrong.
- **One hypothesis at a time.** Changing multiple things at once destroys signal.
- **3 failed attempts = stop and reconsider direction.** If you've tried 3+ different fixes without success, suspect the diagnosis, not the fix.
- **Multi-component failures**: trace the data/event flow end-to-end. Identify at which boundary the failure occurs before localizing.
- **"It worked before"** is a clue, not a solution. Find what changed.

## Escalation Trigger

If after 3+ attempts the problem persists:
- Stop applying patches
- Step back and question the architecture / approach / assumptions
- Consider: is this the right layer to fix? Is the problem upstream?

## Output Template

```
[问题定义]
- 现象：
- 影响范围：
- 复现方式：

[证据]
- 观察 1：
- 观察 2：
- 最近变化/相关上下文：

[当前假设]
- 我怀疑：
- 因为：

[验证动作]
- 我将用什么最小方式验证：

[结论]
- 假设成立 / 不成立
- 下一步：
```

## Relationship to Other Skills

- **high-agency**: Drives you to keep pushing. This skill ensures pushing doesn't mean random thrashing.
- **evidence-before-claims**: Confirms the fix actually resolved the root cause.

## What This Skill Does NOT Do

- Does not require a failing test for every fix (useful but not mandatory in all contexts)
- Does not apply to clearly understood single-cause issues with known fixes — **if the cause is already obvious and verified, you do not need the full framework**
- Does not replace judgment — use the phases as a framework, not a ritual

---

*先搞清楚为什么，再决定改什么。如果每次修复都冒出新问题，别再硬拧——先怀疑路径本身。*
