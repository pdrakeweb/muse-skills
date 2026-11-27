# App Creation Amendment on Settled State and Async Failure Paths

Repository: https://github.com/pdrakeweb/muse-skills/tree/main/app_creation_settled_verification

## When this applies
- Apply alongside App Creation when an artifact runs async analysis or shows a running state before its results appear.
- Apply when the same quantity appears in more than one section, chart, chip, or tooltip.

## Gate verification on settled state
- Verify only after the settled signals fire, such as every background run idle and the saved-state banner showing.
- Read the headline values twice, and require identical values across both reads before reporting a defect or a fix.
- Treat a screenshot or audit taken while a recalculation runs as no evidence, and retake it after the settled signals fire.

## Build failure paths into async sections
- Give every long analysis request three things: a retry on a dropped connection, a guard that blocks a second run while one is in flight, and a visible error state with a retry control when the request still fails.
- Treat a section stuck on a running label with no failure path as a defect, even when the calculation is correct.
- Show errors where the user is looking, not in a collapsed panel.
- Before blaming a timeout on the network, look for repeated work inside the calculation, such as re-sorting the same values for every percentile.

## Tie numbers across sections
- Pick one canonical calculation for each shared quantity, and delete local copies that recompute it from older inputs.
- Check that a value agrees to the dollar across the hero, tabs, chips, and charts before calling the artifact fixed.
- Remove every hard-coded copy of a computed value, because it will silently diverge from the live calculation.

## Access
- Never ask the user to sign in to another product to reach a Muse artifact.

## Available connectors
- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.
- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Alternatives for better results
- Compute a run once and reuse it in every section that needs it, rather than running the same analysis once per section.
- Skip month-by-month detail for runs that only need a summary, when the artifact supports that distinction.
