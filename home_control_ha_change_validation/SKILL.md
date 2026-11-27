# Home Control Amendment on Home Assistant Change Validation

Repository: https://github.com/pdrakeweb/muse-skills/tree/main/home_control_ha_change_validation

## When this applies
- Apply alongside Home Control for any change to a Home Assistant dashboard, card, automation, helper, or notification.
- Apply before any validation that could change a real entity, fire a real automation branch, or send a notification to a real phone, tablet, or speaker.

## Prepare the change
- Save a timestamped backup of every dashboard, automation, and helper config the change touches before editing it.
- Record each card's and automation's behavior before the edit: what it displays, what tap and hold resolve to, and any color or icon rules.
- Before building a new dashboard or view, present the layout to the user and get approval. Put one primary list in the first view, and put secondary material, such as dismissed items and device detail, in separate tabs.
- Show each control only while its item is active, and put explanatory text in a tooltip or help affordance, not in the primary view.

## Gate live validation side effects
- Before running a validation, list every notification, push, digest, and device action it could fire, with the recipient device, the expected count, and the trigger for each.
- Show that list to the user before any validation that reaches a real device. Wait for approval when the validation would announce an event that did not happen, such as a package delivery.
- Try a route with no live side effect first, such as a test entity, a disabled notification action, or a readback of state and config. Use the live route only when no quieter route can prove the behavior.
- Count the notifications and actions the validation actually sent, compare the count with the prediction, and report any difference in the result instead of calling the validation clean.

## Verify after the change
- Check that each behavior recorded before the edit either survived or changed on purpose. A readback of the new entity alone is not behavioral verification.
- Count the controls on the primary view against the active items, and require the counts to match: two active items means two rows and two action buttons.
- When a card's entity changes to a different domain, work out again what tap, hold, and state rendering resolve to, because the resolved behavior can change with the domain.
- After the change, update the Home Assistant dashboard and automation description documents and keep their published copies current, so the repair reference matches the live setup.

## Available connectors
- [Home Assistant](~/workspace/custom-connectors/custom.legacy-home-assistant/CONNECTOR.md) for the Home Assistant REST and WebSocket helpers used to back up, edit, and read back dashboard and automation config.
- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.
- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Alternatives for better results
- Split a validation into a quiet config check first and a single approved live check second, so most defects are caught before any message reaches a household device.
- When verification shows a behavior changed by accident, restore from the pre-change backup rather than layering a second edit on top of the first.
