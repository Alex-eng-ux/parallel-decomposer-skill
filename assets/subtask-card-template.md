# Subtask Card Template

Copy and fill in for each parallel subtask:

```
┌─────────────────────────────────────────────────────────────┐
│ SUBTASK {N}: {Title}                                        │
├─────────────────────────────────────────────────────────────┤
│ Complexity: {Low/Medium/High}                               │
│ Estimated Time: {X minutes/hours}                           │
│ Worker Type: {Generalist/Specialist/Expert}                 │
├─────────────────────────────────────────────────────────────┤
│ CONTEXT (paste into agent window first):                    │
│                                                             │
│ {All background information the agent needs:}               │
│ - Original task description                                 │
│ - Relevant files or data                                    │
│ - Constraints and requirements                              │
│ - What has already been done                                │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│ PROMPT (copy-paste ready):                                  │
│                                                             │
│ {Specific instruction. Include:}                            │
│ - What to analyze or create                                 │
│ - What to focus on                                          │
│ - What to ignore (scope exclusion)                          │
│ - Specific checklist or criteria                            │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│ OUTPUT FORMAT:                                              │
│                                                             │
│ {Exactly what the agent should return:}                     │
│ - Structure (bullet points, sections, table)                │
│ - Level of detail                                           │
│ - Examples if helpful                                       │
│                                                             │
│ SUCCESS CRITERIA:                                           │
│                                                             │
│ {How to know the subtask is complete:}                      │
│ - Specific deliverables                                     │
│ - Quality thresholds                                        │
│ - Completeness checks                                       │
└─────────────────────────────────────────────────────────────┘
```

## Integration Template

```
┌─────────────────────────────────────────────────────────────┐
│ RESULT INTEGRATION TEMPLATE                                 │
├─────────────────────────────────────────────────────────────┤
│ Paste all subtask results below, then ask the agent to:     │
│                                                             │
│ 1. DEDUPLICATE: Remove overlapping content across results   │
│ 2. HARMONIZE: Resolve any contradictions                    │
│ 3. SEQUENCE: Order outputs logically                        │
│ 4. ENRICH: Add cross-references between sections            │
│ 5. FINALIZE: Produce unified output in {format}             │
├─────────────────────────────────────────────────────────────┤
│ INTEGRATION PROMPT (copy-paste ready):                      │
│                                                             │
│ I have {N} parallel subtask results below. Please:          │
│                                                             │
│ 1. Read and understand all results                          │
│ 2. Remove duplicate findings                                │
│ 3. Resolve any contradictions with reasoning                │
│ 4. Organize into a coherent {output_type}                   │
│ 5. Add transitions and cross-references                     │
│ 6. Produce final unified output                             │
│                                                             │
│ RESULTS:                                                    │
│ {paste all subtask outputs here}                            │
└─────────────────────────────────────────────────────────────┘
```
