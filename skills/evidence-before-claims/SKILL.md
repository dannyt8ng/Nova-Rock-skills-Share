---
name: evidence-before-claims
version: 1.0.0
description: Use when you are about to claim that something is complete, fixed, working, passing, configured correctly, or ready. Requires fresh verification evidence before any success claim.
---

# Evidence Before Claims

**Core principle:** No fresh verification evidence = no completion claim. Period.

## When This Skill Activates

Before making any success or correctness claim, including (but not limited to):
- "Done / Fixed / Working / Works now"
- "Tests passing / All checks passed"
- "Config is live / Applied successfully"
- "The issue is resolved"
- "Ready to use / This should work"

**This also applies to paraphrases or implied success claims, not just these exact phrases.**

## The Gate (Non-Negotiable)

Before claiming completion, you MUST:

1. **Define what proof looks like**
   - What command, test, request, log check, or observable output would confirm success?
   - Name it explicitly before running it.

2. **Run fresh verification this session**
   - Old results don't count. Prior session results don't count.
   - If you can't run verification, say so explicitly.

3. **Read the actual output**
   - Exit codes, failure counts, key log lines, response status, UI state.
   - Don't infer success from absence of errors.

4. **Match evidence to conclusion**
   - Evidence supports claim → state the claim with the evidence.
   - Evidence is partial → state what IS confirmed and what is NOT.
   - Evidence fails → describe actual state, not hoped-for state.

## Rules

- **"应该" / "大概率" / "看起来" are not evidence.** These are guesses dressed as conclusions.
- **Partial proof = partial claim.** lint passed ≠ build passed ≠ bug fixed ≠ feature works end-to-end.
- **If verification is blocked**, say: "I cannot verify this right now because [reason]. Current known state: [state]."
- **Never claim done to save face.** Honest partial progress > false completion.

## Output Template

```
[验证目标]
我需要证明的是：
- ...

[已执行验证]
- 命令/动作：
- 结果：
- 这能证明：

[当前结论]
- 已验证成立：
- 尚未验证 / 不能证明：
```

## Relationship to Other Skills

- **high-agency**: Drives momentum and prevents giving up. This skill prevents momentum from becoming self-delusion.
- **root-cause-debugging**: Finds the real problem. This skill confirms the fix actually worked.

## What This Skill Does NOT Do

- Does not require exhaustive testing for simple tasks
- Does not block progress — it blocks *false claims of progress*
- Does not apply to exploratory work or clearly stated WIP

---

*证据优先于信心。能证明什么，就只说到什么程度。*
