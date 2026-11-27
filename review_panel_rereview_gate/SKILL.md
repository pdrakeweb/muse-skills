# Review Panel Re-review Gate

Repository: https://github.com/pdrakeweb/muse-skills/tree/main/review_panel_rereview_gate

## When this applies
- Apply before reconvening a review panel, such as a council or a multi-reviewer audit, on findings that an earlier round left open.
- Apply whenever someone claims a mitigation closes a blocking finding.

## Require execution evidence before reconvening
- Reconvene a review panel only after every claimed mitigation has execution evidence behind it.
- Ask for one artifact per claimed mitigation that shows the mechanism working, or failing, in the real system.
- Accept an emulator run, a test run, a log, or a live observation as evidence.
- Treat a brief edit, a design-doc change, a prose rewrite, or a stated decision as a claim only, not as evidence.
- Before spawning the panel, record each evidence artifact beside the finding it claims to close.
- Refuse to reconvene while any blocking finding has a claim with no artifact.

## Count narrowing as progress only when a finding closes
- Count a finding as closed only when the Judge names the mechanism that is gone and the evidence that proves it.
- Count a finding as narrowed when its scope shrinks but its mechanism remains.
- Report narrowing and closure as separate numbers in every verdict.
- Treat a round with narrowing and zero closures as no progress toward shipping.
- Name the specific missing evidence for each finding that stays open.

## Stop the loop and escalate after repeated rounds with no closure
- Stop reconvening after three rounds that close zero findings.
- Escalate to the user with the open findings, the missing evidence for each, and three options: change the scope, accept the risk, or stop the work.
- Never run a fourth round on the same findings with the same kind of claim.
- Let the user proceed on their own word, for example with a phased implementation, without treating that as a flipped verdict.
- Record the user's decision beside the verdict that still stands.

## Available connectors
- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.
- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Alternatives for better results
- Run the checkable test first, and convene only on the judgment that is left after the test.
- Split one large review into smaller findings that each have a single mechanism to verify.
- Ask the user for the missing fact or decision before spending another review round.
