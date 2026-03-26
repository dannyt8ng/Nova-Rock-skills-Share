---
name: execution-planning
version: 1.0.0
description: Use when a task has multiple steps, dependencies, handoffs, or non-trivial risks, before starting execution. Turn ambiguous work into a concrete staged plan with validation points.
---

# Execution Planning

**Core principle:** A plan is not a list of intentions. It's an execution order with validation points.

## When This Skill Activates

- Task involves 3+ distinct steps or components
- Task has dependencies, risks, or rollback considerations
- Work needs to be handed off to subagents or ACP sessions
- The goal is clear but the path is not
- User asks to get X done, and X clearly involves multiple stages, dependencies, handoffs, or non-trivial risk

## When NOT to Use

- Simple single-step tasks
- Clearly scoped fixes with an obvious path
- Exploratory / research work where the goal is to discover, not execute
- Lightweight thinking, simple recommendations, or short answer tasks

## The Planning Process

### Step 1: Define Goal and Scope
- What does success look like? (concrete, not vague)
- What is explicitly OUT of scope?
- What are the acceptance criteria?

### Step 2: Identify Stages
- Break work into phases where each has a clear output
- Each stage should be completable and verifiable independently
- Typical phase: 1 focused outcome, not a mega-step

### Step 3: Add Validation to Each Stage
- How do you know this stage is actually done?
- What command, check, output, or observable state confirms it?

### Step 4: Map Dependencies and Risks
- What must be true before each stage can start?
- What could block or break it?
- Is there a rollback/recovery path if a stage fails?

### Step 5: Mark Delegation Candidates
- Which stages can run independently in a subagent or ACP session?
- Which stages need main session control (auth, approval, state-dependent)?

## Rules

- **计划不是口号，是执行顺序 + 验证点。** Vague phases ("set up the system") are not plans.
- **Every stage needs a done-signal.** If you can't describe how to verify a stage is complete, the stage is not well-defined.
- **复杂任务先切块，再推进。** Don't start executing before the plan is clear enough to hand off to someone else.
- **Plans can be updated.** If you discover new information mid-execution, revise the plan explicitly rather than silently deviating.

## Output Template

```
[目标]
- 要达到的具体状态：

[范围边界]
- 包含：
- 不包含：

[执行计划]

阶段 1：[名称]
- 产出：
- 验证：
- 风险/依赖：

阶段 2：[名称]
- 产出：
- 验证：
- 风险/依赖：

（继续按需）

[委派建议]
- 可交给 subagent/ACP：
- 需要主会话保留控制的部分：

[风险汇总]
- 已识别风险：
- 缓解措施：
```

## Relationship to Other Skills

- **high-agency**: Provides drive and momentum. This skill gives that momentum a skeleton so it doesn't scatter.
- **root-cause-debugging**: When a stage fails unexpectedly, use this to find why before replanning.
- **evidence-before-claims**: Use at the end of each stage to confirm it's actually complete before moving on.

## What This Skill Does NOT Do

- Does not require git branches, commits, or specific file structures
- Does not mandate TDD or any specific development methodology
- Does not replace judgment — the template is a scaffold, not a cage

---

*每一步都要知道做完后怎么看它真的完成。复杂任务先切块，再推进。*
