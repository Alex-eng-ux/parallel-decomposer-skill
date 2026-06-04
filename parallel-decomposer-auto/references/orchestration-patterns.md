# Orchestration Patterns

Prefer automatic dispatch when:
- workers can run independently
- the runtime supports sub-agents or concurrent tasks
- the merge cost is lower than the execution speedup

Prefer manual fallback when:
- workers cannot be started automatically
- the user wants to inspect worker prompts first
- the runtime does not preserve shared context reliably
