---
name: parallel-decomposer-auto
description: Convert a complex request into orchestration-ready subtask specs for automatic sub-agent execution, worker-thread dispatch, or manual fallback. Use when the runtime supports sub-agents or concurrent workers and the user wants complex work split into independent subtasks with shared context, dependency handling, and a merge plan. If automatic execution is unavailable, fall back to copy-paste-ready worker prompts.
---

# Parallel Decomposer Auto

Use this skill when the environment can orchestrate multiple workers automatically. Prefer generating worker specs for sub-agents over asking the user to open separate windows. If needed, produce manual fallback prompts from the same decomposition.

## Workflow

1. Clarify the goal.
   - Identify the final deliverable, relevant files or data, constraints, and known non-goals.
   - Note assumptions explicitly if they affect decomposition.

2. Choose the split strategy.
   - Split by aspect, component, audience, method, or phase depending on the task.
   - Avoid splits that create heavy coordination or file ownership conflicts.

3. Create a shared handoff brief.
   - Include the original goal, shared context, relevant files, constraints, non-goals, and expected final deliverable.
   - Pass this brief to every worker as shared context.

4. Generate orchestration-ready worker specs.
   - Define one worker spec per independent subtask.
   - Assign ownership boundaries when multiple workers touch the same project area.
   - Include a merge strategy and dependency notes.

5. Dispatch or fall back.
   - If sub-agent execution is available, dispatch worker specs automatically.
   - If unavailable, emit copy-paste-ready worker prompts without changing the decomposition.

6. Merge results.
   - Deduplicate overlaps.
   - Resolve contradictions explicitly.
   - Preserve important uncertainty and blockers.

## Output Shape

```markdown
## Handoff Brief
Original goal: {goal}
Shared context: {facts every worker needs}
Relevant files or data: {paths, links, artifacts}
Constraints and non-goals: {limits}
Final deliverable: {merged result shape}

## Worker Specs
### Worker 1: {Title}
- Goal: {worker objective}
- Inputs: {files, data, handoff brief}
- Focus: {what this worker should handle}
- Avoid: {what to leave alone}
- Output: {required result shape}

## Merge Strategy
- Merge order: {recommended order}
- Deduplicate: {likely overlap}
- Resolve: {expected conflicts}
- Finalize: {how to produce the final deliverable}
```

## Bundled Resources

- Read `references/orchestration-patterns.md` when choosing between automatic dispatch and manual fallback.
- Use `assets/worker-spec-template.md` when reusable worker specs would help.
