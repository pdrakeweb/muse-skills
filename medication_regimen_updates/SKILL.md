# Medication Regimen Updates

Repository: https://github.com/pdrakeweb/muse-skills/tree/main/medication_regimen_updates


## Inventory every surface before editing

- List every place the current regimen appears before changing any of them, covering scheduled reminder jobs, phone alarms, any schedule page or artifact, and the memory entry that records the regimen.

- Use `cron.list` and `cron.view` to read the full body of each reminder job, not only its schedule.

- Use `device.list` and `device.describe` before `device.invoke` when a phone alarm is one of the surfaces, so the alarm label text is in the inventory too.

- Inventory the phone's reminder notifications as a separate surface from its Clock alarms: `alarm.list` does not show them. Pull `reminder.list` through `device.invoke` and check every medication-labeled series for dose and time. (Example: after the chat jobs and alarms were already clean, a leftover daily phone reminder still fired a stale dose at 2 PM, and the same layer carried other stale dose series.)

- Write the new dose, interval and times as one confirmed regimen from the user's latest correction, and treat that wording as the single source every surface must match.

## Update the text, not only the timing

- Change the dose and interval wording inside each reminder job body and each alarm label, not only the fire times.

- Update the schedule page or artifact and the memory entry in the same turn as the reminder jobs, so no surface keeps the older regimen.

- Remove alarms and reminder slots the new regimen no longer has, including overnight slots removed by a sleep consolidation, rather than only adding the new ones.

- Keep historical log entries unchanged, and limit edits to live surfaces that will fire, display or be read as current guidance.

## Read back and search for the old wording

- Read each edited job back with `cron.view` and each edited alarm back through the device, and compare the dose, interval and time against the confirmed regimen word by word.

- Search the workspace and memory with `muse.exec` and `muse.memory_search` for the old dose and old interval wording, and fix any live surface the search still finds.

- Confirm the result to the user by naming each surface checked, so a partial update is visible instead of assumed complete.

- Report any surface you could not read or edit as unverified, rather than saying the regimen is updated everywhere.

## Deliver reminders against the current regimen

- Read the current regimen from memory before a reminder message goes out when the job body and the memory entry could differ.

- Send the dose and interval from the confirmed regimen when a stale job body disagrees, and flag the mismatch in the same message so the stale job gets fixed.

- Never send a reminder that repeats a dose the user has already corrected, even when the scheduled job text still carries it.

## Available connectors

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Alternatives for better results

- Ask the user to confirm the full regimen in one message when corrections arrive piecemeal across several messages, then propagate that one confirmed version everywhere.

- Keep one schedule page as the readable summary of the regimen and point reminder checks at it, instead of maintaining separate free text copies that can drift apart.
