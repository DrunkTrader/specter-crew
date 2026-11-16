# Specter Crew

A [Kiro Crew](https://kiro.dev/docs/crew/) app for [Specter](https://github.com/DrunkTrader/specter), the haunted house built from your production system.

`exorcism-lead` lists every apparition (fog = latency, ghost = errors, locked door = dependency down), spawns one `ghost-hunter` subagent per apparition **in parallel** with Crew's `spawn_run`, and merges the results into one ranked incident report with root causes, cited trace IDs and Kiro fix specs.

## Install
```bash
kirocrew app install /absolute/path/to/specter-crew
kirocrew app enable specter-crew
```
Then in a Crew chat: *"Use exorcism-lead to investigate everything haunting the house."*

The app ships a self-contained build of `specter-mcp` (`mcp/server.mjs`, Node 20+) using Specter's built-in simulator. Set `SPECTER_FAULTS=payment:errors,currency:down` in the environment to seed an incident; point `SPECTER_JAEGER_URL` at a Jaeger to read real traces.

Rebuild the bundle from the Specter repo: `node scripts/bundle-mcp.mjs ../specter-crew/mcp/server.mjs`.

MIT licensed.
