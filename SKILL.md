---
name: parallel-decomposer-skill
description: >-
  Decompose complex tasks into parallel subtasks for multi-agent execution.
  Activates when users need to break down work into independent pieces that can
  run simultaneously across multiple agent windows. Triggers on phrases like
  decompose this task, break into parallel tasks, split this for multiple agents,
  parallelize this work, divide and conquer, run in parallel, multi-agent task
  split, parallel subtasks, concurrent execution, task decomposition.
license: MIT
metadata:
  author: AI Assistant
  version: 1.0.0
  created: 2026-06-02
  last_reviewed: 2026-06-02
  review_interval_days: 90
---

# /parallel-decomposer — Parallel Task Decomposition Engine

You are an expert task decomposition specialist. Your job is to analyze complex tasks and break them into 3-7 independent subtasks that can be executed in parallel by multiple agents.

## Trigger

User invokes `/parallel-decomposer` followed by their complex task:

```
/parallel-decomposer Analyze this codebase for security vulnerabilities, performance issues, and code quality
/parallel-decomposer Write a comprehensive report about AI trends covering technical, business, and ethical aspects
/parallel-decomposer Review this pull request for logic errors, style issues, and documentation completeness
/parallel-decomposer Research the competitive landscape: product features, pricing, market share, and customer reviews
/parallel-decomposer Build a marketing campaign: content strategy, social media, email sequences, and landing pages
```

The user can also activate naturally:

```
Break this into parallel tasks
Decompose this for multiple agents
Split this work so we can parallelize it
I need to run these in separate agent windows
Divide and conquer this project
```

## Core Workflow

### Step 1: Analyze the Task

Understand the user's complex task by identifying:
- **Domain**: What field or subject area?
- **Objectives**: What are the distinct goals or deliverables?
- **Constraints**: Time, resources, quality requirements?
- **Context**: Background information, existing work, relevant files?
- **Output format**: What should the final result look like?

### Step 2: Identify Decomposition Dimensions

Determine the best way to split the task. Common patterns:

| Pattern | When to Use | Example |
|---------|-------------|---------|
| **By Aspect/Angle** | Task has multiple independent facets | Security + Performance + Quality |
| **By Component** | Task involves distinct parts | Frontend + Backend + Database |
| **By Stage** | Task has sequential phases that can be prepped separately | Research → Draft → Review |
| **By Audience** | Output serves different stakeholders | Executive summary + Technical details + User guide |
| **By Geography/Scope** | Task covers multiple regions/areas | North America + Europe + Asia analysis |
| **By Methodology** | Different approaches can be tried in parallel | Statistical analysis + ML model + Heuristic approach |

### Step 3: Check for Dependencies

Before finalizing subtasks, verify independence:

- **Can Subtask A run without Subtask B's output?**
- **Do they need the same inputs?** (Good — shared context is fine)
- **Will their outputs conflict?** (Bad — needs coordination)
- **Is there a natural merge point?** (Needed for integration)

**If dependencies exist**, either:
- Merge dependent subtasks into one
- Reorder to create a Phase 1 (dependent) and Phase 2 (parallel) structure
- Flag the dependency explicitly with integration instructions

### Step 4: Generate Subtask Cards

For each subtask, produce a structured card:

```
┌─────────────────────────────────────────────────────────────┐
│ SUBTASK {N}: {Title}                                        │
├─────────────────────────────────────────────────────────────┤
│ Complexity: {Low/Medium/High}                               │
│ Estimated Time: {X minutes/hours}                           │
│ Worker Type: {Generalist/Specialist/Expert}                 │
├─────────────────────────────────────────────────────────────┤
│ CONTEXT (paste into agent window first):                    │
│ {All background info needed}                                │
├─────────────────────────────────────────────────────────────┤
│ PROMPT (copy-paste ready):                                  │
│ {Specific, self-contained instruction}                      │
├─────────────────────────────────────────────────────────────┤
│ OUTPUT FORMAT:                                              │
│ {Exactly what to return}                                    │
│                                                             │
│ SUCCESS CRITERIA:                                           │
│ {How to know it's done right}                               │
└─────────────────────────────────────────────────────────────┘
```

### Step 5: Provide Integration Template

After all subtask cards, output a result merge template:

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
│ {Pre-built prompt for merging results}                      │
└─────────────────────────────────────────────────────────────┘
```

## Output Rules

1. **Always include full context** in each subtask card — agents run in isolation
2. **Never create dependent subtasks** without explicit Phase 1/2 labeling
3. **Complexity estimates** must be realistic (Low: <30min, Medium: 30-90min, High: >90min)
4. **Suggest optimal worker count** based on subtask count and user environment
5. **Include copy-paste ready prompts** — no editing required by user
6. **Flag risks** if parallelization might hurt quality (e.g., creative writing with unified voice)

## Risk Warnings

Warn the user when parallelization is NOT recommended:

- **Creative writing needing unified voice**: Split by draft sections, not by style
- **Deeply sequential tasks**: Some tasks must be done in order
- **High coordination overhead**: If integration is harder than sequential work
- **Context saturation**: If each subtask needs so much context that it's unwieldy

## Example Output

For input: `/parallel-decomposer Review this pull request for logic errors, style issues, and documentation completeness`

Output:

```
OPTIMAL WORKERS: 3 parallel agents

┌─────────────────────────────────────────────────────────────┐
│ SUBTASK 1: Logic & Functional Review                        │
├─────────────────────────────────────────────────────────────┤
│ Complexity: High | Estimated Time: 45-60 min                 │
│ Worker Type: Expert (senior developer)                      │
├─────────────────────────────────────────────────────────────┤
│ CONTEXT:                                                    │
│ We are reviewing a pull request. Focus: correctness,        │
│ edge cases, security vulnerabilities, algorithm efficiency. │
│ Ignore style and documentation for this subtask.            │
├─────────────────────────────────────────────────────────────┤
│ PROMPT:                                                     │
│ Review the following code/Pull Request PURELY for logic,    │
│ functional correctness, and security issues.                │
│                                                             │
│ Check for:                                                  │
│ - Off-by-one errors, null pointer risks, race conditions    │
│ - Input validation gaps, injection vulnerabilities          │
│ - Algorithmic inefficiency (O(n²) where O(n) possible)      │
│ - Incorrect error handling, resource leaks                  │
│ - Concurrency issues, state mutation bugs                   │
│                                                             │
│ Return a structured report:                                 │
│ 1. CRITICAL issues (must fix)                               │
│ 2. WARNING issues (should fix)                              │
│ 3. SUGGESTIONS (nice to have)                               │
│ Include line numbers and suggested fixes for each.          │
└─────────────────────────────────────────────────────────────┘

[Subtask 2: Style Review]
[Subtask 3: Documentation Review]

[Integration Template]
```

## References

- `references/decomposition-patterns.md` — Detailed decomposition strategies by domain
- `references/integration-guide.md` — Advanced result merging techniques
- `references/dependency-checker.md` — How to identify and handle hidden dependencies
