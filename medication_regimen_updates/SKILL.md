# Medication Regimen Updates

Repository: https://github.com/pdrakeweb/muse-skills/tree/main/medication_regimen_updates

## When this applies
- Apply whenever the user changes a medication's dose, interval, or times, adds or stops a medication, or corrects a reminder that went out with the wrong dose.
- Apply before sending any scheduled medication reminder whose job body might be stale.

## Inventory every surface before editing
- Before changing anything, list every place the current regimen appears: scheduled reminder jobs, phone alarms, phone reminders, any schedule page or artifact, and the memory entry that records the regimen.
- Read the full body of each reminder job with `cron.list` and `cron.view`, not just its schedule.
- When a phone alarm is one of the surfaces, run `device.list` and `device.describe` before `device.invoke`, so the inventory includes the alarm label text.
- Inventory the phone's reminders separately from its Clock alarms, because `alarm.list` does not show them. Pull `reminder.list` through `device.invoke`, and check every medication-labeled series for dose and time. (Example: after the chat jobs and alarms were cleaned up, a leftover daily phone reminder still fired a stale dose at 2 PM, and other series on the same layer carried stale doses too.)
- Write the new dose, interval, and times as one confirmed regimen taken from the user's latest correction. That wording is the single source every surface must match.

## Update the text, not only the timing
- Change the dose and interval wording inside each reminder job body and each alarm label, not just the fire times.
- Convert each local dose time to the time zone the scheduler uses, and check the job's next fire time after the edit. A schedule that is correct in UTC but wrong locally is a wrong dose time.
- Update the schedule page or artifact and the memory entry in the same turn as the reminder jobs, so no surface keeps the old regimen.
- Remove the alarms and reminder slots the new regimen no longer has, including overnight slots dropped by a sleep consolidation. Adding the new slots is not enough.
- Leave historical log entries unchanged. Edit only live surfaces that will fire, display, or be read as current guidance.

## Read back and search for the old wording
- Read each edited job back with `cron.view` and each edited alarm and reminder back through the device, and compare the dose, interval, and time against the confirmed regimen word for word.
- Search the workspace with `muse.exec` and memory with `muse.memory_search` for the old dose and interval wording, and fix every live surface the search still finds.
- Confirm the result to the user by naming each surface you checked, so a partial update is visible instead of assumed complete.
- Report any surface you could not read or edit as unverified. Never say the regimen is updated everywhere unless every surface was read back.

## Deliver reminders against the current regimen
- Before a reminder goes out, read the current regimen from memory whenever the job body and the memory entry could differ.
- When a stale job body disagrees with the confirmed regimen, send the confirmed dose and interval, and flag the mismatch in the same message so the stale job gets fixed.
- Never send a reminder that repeats a dose the user has already corrected, even when the scheduled job text still carries it.
- Never change a dose, interval, or time on your own inference. Every regimen change comes from the user's own words.

## Available connectors
- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.
- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Alternatives for better results
- When corrections arrive piecemeal over several messages, ask the user to confirm the full regimen in one message, then apply that one confirmed version everywhere.
- Keep one schedule page as the readable summary of the regimen and point reminder checks at it, rather than keeping separate free-text copies that can drift apart.
