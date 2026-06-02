---
name: parallel-decomposer-skill
description: Decompose a complex request into independent parallel subtasks for Codex or other agents. Use when the user asks to split work, parallelize tasks, divide and conquer, coordinate multiple agent windows, or create copy-paste-ready prompts for research, code review, writing, planning, analysis, or implementation work. Avoid using for small single-step requests where decomposition would add overhead.
---

# Parallel Task Decomposer

Use this skill to turn one complex request into a small set of independent worker prompts plus a merge plan. Prefer 3-7 subtasks. Keep the output immediately usable by another agent with minimal editing.

## Workflow

1. Clarify the target outcome.
   - Identify the domain, final deliverable, quality bar, constraints, relevant files or data, and any time or coordination limits.
   - If key context is missing but a reasonable assumption is safe, state the assumption and continue.
   - Ask the user only when the decomposition would materially change based on the answer.

2. Choose the decomposition pattern.
   - Split by aspect when the work has independent lenses, such as security, performance, UX, market, legal, or operations.
   - Split by component when different parts can be handled independently, such as frontend, backend, database, docs, or tests.
   - Split by audience when each output serves a different reader, such as executive, technical, end user, or support.
   - Split by method when parallel approaches can be compared, such as qualitative research, quantitative analysis, and benchmark testing.
   - Use phased decomposition only when a prerequisite must happen before useful parallel work can begin.

3. Check independence before producing tasks.
   - Each subtask must be runnable without waiting for another subtask's result.
   - Shared context is fine, but shared mutable outputs require explicit ownership.
   - If two subtasks would produce conflicting edits to the same file or section, merge them or assign one as owner and the other as reviewer.
   - If integration looks harder than doing the work sequentially, warn the user and propose a smaller split.

4. Write compact, self-contained task cards.
   - Include only the context each worker needs, not every detail from the original conversation.
   - State the subtask focus, exclusions, inputs, deliverables, success criteria, and expected output format.
   - Make each prompt copy-paste-ready for a fresh agent or fresh Codex thread.
   - Include an estimated complexity and worker type when useful.

5. Provide a merge plan.
   - Explain how to combine the worker results.
   - Name likely duplicates or contradictions to resolve.
   - Provide a final integration prompt when the user will paste results back into another agent.

## Output Shape

Use this structure unless the user asks for another format:

```markdown
Optimal workers: {N}
Parallelization risk: {Low/Medium/High} - {one-sentence reason}

## Subtask 1: {Title}
- Complexity: {Low/Medium/High}
- Worker type: {Generalist/Specialist/Expert}
- Context: {minimum sufficient background}
- Prompt: {copy-paste-ready instruction}
- Output format: {exact return shape}
- Success criteria: {completion checks}

---

## Subtask 2: {Title}
...

## Integration Plan
- Merge order: {recommended order}
- Deduplicate: {likely overlap}
- Resolve: {known tension points}
- Final output: {target deliverable}

## Integration Prompt
{copy-paste-ready prompt for combining completed subtask outputs}
```

## Risk Rules

Warn before decomposing when:

- The task needs one unified creative voice.
- The task is mostly sequential.
- Every worker would need the same large context.
- The integration result is likely to be lower quality than a single pass.
- The user appears to need implementation, not orchestration.

When warning, still offer the smallest useful split, such as "research first, then one implementation agent."

## Bundled Resources

- Read `references/decomposition-patterns.md` when the domain or split strategy is unclear.
- Read `references/dependency-checker.md` when subtasks might have hidden ordering or ownership dependencies.
- Read `references/integration-guide.md` when the merge step is complex or high risk.
- Use `assets/subtask-card-template.md` when the user wants a reusable template or a more formal task-card format.
