# Review Panel Re-review Gate

Repository: https://github.com/pdrakeweb/muse-skills/tree/main/review_panel_rereview_gate


## Require execution evidence before reconvening

- Reconvene a review panel only after each claimed mitigation has execution evidence behind it.

- Ask for one artifact per claimed mitigation that shows the mechanism working or failing in the real system.

- Accept an emulator run, a test run, a log, or a live observation as evidence.

- Treat a brief edit, a design doc change, a prose rewrite, or a stated decision as a claim only.

- Record the evidence artifact beside the finding it claims to close before you spawn the panel.

- Refuse to reconvene when any blocking finding has a claim with no artifact.

## Count narrowing as progress only when a finding closes

- Count a finding as closed only when the Judge names the mechanism that is gone and the evidence that proves it.

- Count a finding as narrowed when its scope shrinks but its mechanism remains.

- Report narrowing and closure as separate numbers in every verdict.

- Treat a round with narrowing and zero closures as no progress toward shipping.

- Name the specific missing evidence for each finding that stays open.

## Stop the loop and escalate after repeated no closure rounds

- Stop reconvening after three rounds with zero findings closed.

- Escalate to the user with the open findings, the missing evidence for each one, and the options to change scope, accept the risk, or stop the work.

- Do not run a fourth round on the same findings with the same kind of claim.

- Let the user proceed on their own word, as with a phased implementation, without treating that as a flipped verdict.

- Record the user decision and the verdict that still stands beside it.

## Available connectors

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Alternatives for better results

- Run the checkable test first and convene only on the judgment that remains after the test.

- Split one large review into smaller findings that each have a single mechanism to verify.

- Ask the user for the missing fact or decision before spending another review round.
