# Trip Planning Points Stay Verification

Repository: https://github.com/pdrakeweb/muse-skills/tree/main/trip_planning_points_verification

## When this applies
- Apply alongside Trip Planning whenever a plan quotes a points rate for a hotel stay, or relies on a points program feature, a card credit, or a booking channel benefit.

## Verify the booking window before quoting a rate
- Compute the months between today and the travel dates from the calendar dates before describing how far away the trip is.
- Before quoting a points rate, check whether the live booking calendar is open for the exact travel dates.
- When the calendar is not open for those dates, say that no live price exists. Never quote a rate from a different date range as the rate for those dates.
- Carry the exact dates, party size, and room occupancy into every live check, and record the date you checked.

## Confirm the property identity before quoting its rate
- Verify the property's current brand and name from a current source before quoting its points rate.
- When a property name matches more than one property, or has changed over time, check a dated source for a rebrand, closure, or reopening.
- Never carry a rate from a similarly named property over to the one you are reporting.
- Verify the location of the property you are reporting. A name match alone is not enough.

## Verify the points tier and party pricing
- Before quoting a per-night rate, read the current points tier chart and record its publication date and any reshuffle date.
- Quote the per-night rate for the exact party size and room type, and check whether extra guests change the points price.
- Never quote a flat rate from an older chart when the current chart prices the property in a tier or a range.
- Label a rate unverified when you could not confirm it against a current tier chart or the live calendar.

## Verify program features and credit terms
- Before saying a program feature works, check that it exists for the exact program, card, and booking channel.
- Read the current terms for any credit you quote: the amount, the booking channel, any minimum-stay or prepaid condition, and the date window.
- Never present a feature or credit as available when the source you checked covers a different channel or product.
- Make any recommendation that depends on an unverified feature or credit conditional, and say what is still unverified.

## Available connectors
- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.
- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Alternatives for better results
- When the live calendar is phone only, ask the hotel or the program directly, and record the answer with the date you asked.
- When the points rate is unverified, compare a cash rate for the same dates, so the user can judge the trip without relying on an unestablished points figure.
