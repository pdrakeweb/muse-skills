# App Creation Amendment on Settled State and Async Failure Paths

Repository: https://github.com/pdrakeweb/muse-skills/tree/main/app_creation_settled_verification

## When this applies
- Apply alongside App Creation when an artifact runs async analysis or shows a running state before results appear.
- Apply when the same quantity appears in more than one section, chart, chip, or tooltip.
## Gate verification on settled state
- Verify only after settled signals fire, such as all background runs idle and the saved state banner showing.
- Read headline values twice and require identical values across both reads before reporting a defect or a fix.
- Treat a screenshot or audit taken while a recalculation runs as no evidence, and retake it after settled signals fire.
- Never ask the user to sign in to another product to reach a Muse artifact.
## Build failure paths into async sections
- Give every long analysis request a retry on a dropped connection, a guard blocking a second run while one is in flight, and a visible error state with a retry control when it still fails.
- Treat a section sitting on a running label with no failure path as a defect, even when the calculation is correct.
- Keep errors visible where the user is looking instead of hiding them in a collapsed panel.
- Watch for repeated work inside the calculation, such as re-sorting the same values for every percentile, before assuming a timeout is a network problem.
## Tie numbers across sections
- Pick one canonical calculation for each shared quantity and delete local copies that recompute it from older inputs.
- Check that a value in a hero, a tab, a chip, and a chart agrees to the dollar before calling the artifact fixed.
- Remove any hard coded copy of a computed value, since it will silently diverge from the live calculation.
## Available connectors
- Use muse.connector_search to find other connectors and muse.skill_search to find related skills.
- If nothing here fits, look on the web for a maintained API or MCP server and set it up with Custom Connectors and MCPs, or build a custom connector.
## Alternatives for better results
- Reuse one computed run across every section that needs it instead of running the same analysis once per section.
- Skip month by month detail for runs that only need a summary, when the artifact supports that distinction.
