# Home Control Amendment on Home Assistant Change Validation

Repository: https://github.com/pdrakeweb/muse-skills/tree/main/home_control_ha_change_validation


## When this applies

- Apply this amendment alongside Home Control for any Home Assistant dashboard, card, automation, helper, or notification change.

- Apply it before validation that could change a real entity, fire a real automation branch, or send a notification to a real phone, tablet, or speaker.

## Prepare the change

- Save a timestamped backup of every dashboard, automation, and helper config the change touches before editing it.

- Record the observable behavior of each card or automation before the edit, including what it displays, what tap and hold do in resolved terms, and any color or icon rules.

- Present the layout design to the user and get approval before building a new dashboard or a new view, with one primary list in the first view and secondary material such as dismissed items and device detail in separate tabs.

- Gate every control per active item, so a button exists only while its item is active, and keep explanatory text in a tooltip or help affordance instead of in the primary view.

## Gate live validation side effects

- List every notification, push, digest, and device action the planned validation could fire before running it, naming the recipient device, the expected count, and the trigger for each one.

- Flag that list to the user before running any validation that reaches a real device, and wait for approval when the validation would announce an event that did not happen, such as a package delivery.

- Prefer a route with no live side effect first, such as a test entity, a disabled notification action, or a readback of state and config, and use the live route only when no quieter route proves the behavior.

- Count the notifications and actions the validation actually sent, compare that count with the predicted count, and report any difference in the result instead of treating the validation as clean.

## Verify after the change

- Verify each behavior recorded before the edit survived or changed intentionally, and do not treat a readback of the new entity alone as behavioral verification.

- Count the controls on the primary view against the active items and require the counts to match, so a view with two active items shows two rows and two action buttons.

- Re-derive what tap, hold, and state rendering resolve to whenever a card entity changes to a different domain, because the resolved behavior can change with the domain.

- Update the Home Assistant dashboard and automation description documents after the change and keep their published copies current, so the repair reference matches the live setup.

## Available connectors

- [Home Assistant](~/workspace/custom-connectors/custom.legacy-home-assistant/CONNECTOR.md) for the Home Assistant REST and WebSocket helpers used to back up, edit, and read back dashboard and automation config.

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Alternatives for better results

- Split a validation into a quiet config check first and a single approved live check second, so most defects are caught without any message reaching a household device.

- Restore from the pre change backup when verification shows a behavior changed unintentionally, instead of layering a second edit on top of the first.
