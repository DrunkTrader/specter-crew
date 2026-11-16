---
description: How to investigate Specter apparitions (fog, ghost, locked door) and report them
always: false
---

# Exorcism

Specter shows a production system as a haunted house. Apparition ids look like `fog:payment`, `ghost:checkout`, `locked-door:currency`.

| Apparition | Meaning | Root-cause signal |
|---|---|---|
| fog | latency | p95 self-time far above baseline |
| ghost | errors | the service's own spans fail |
| locked-door | dependency down | callers get connection refused |

## Rules
1. Lead with the fact and numbers with units. At most one spooky clause, never instead of a fact.
2. Cite trace IDs. Never invent evidence.
3. State confidence and what would change it.
4. The time window moves between calls, so exact trace IDs may differ; say so rather than hide it.
5. A failing caller is usually a symptom. Name the service whose own work fails or that cannot be reached.
