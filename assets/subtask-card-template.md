# Subtask Card Template

Use this template when a user wants formal cards for parallel workers.

```markdown
## Subtask {N}: {Title}

Complexity: {Low/Medium/High}
Estimated time: {X minutes/hours}
Worker type: {Generalist/Specialist/Expert}

### Context
{Minimum sufficient background for an isolated agent. Include the original goal, relevant files or data, hard constraints, and known decisions.}

### Prompt
{Specific, copy-paste-ready instruction. State what to analyze or create, what to focus on, what to ignore, and any checklist the worker must follow.}

### Output Format
{Exact structure the worker should return. Include headings, tables, bullets, severity levels, or examples if needed.}

### Success Criteria
- {Specific deliverable}
- {Quality threshold}
- {Completeness check}
```

## Integration Template

```markdown
# Integration Prompt

I have {N} parallel subtask results below. Combine them into one coherent {output_type}.

Please:
1. Read all results.
2. Remove duplicate findings.
3. Resolve contradictions with brief reasoning.
4. Preserve important dissent or uncertainty.
5. Organize the final output in this order: {desired_order}.
6. Produce the final unified deliverable.

Subtask results:
{paste all subtask outputs here}
```
