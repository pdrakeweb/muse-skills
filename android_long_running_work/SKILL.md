# Android Long Running Work

Repository: https://github.com/pdrakeweb/muse-skills/tree/main/android_long_running_work


## Keep the run alive or settle it honestly

- Pin a foreground service for the whole run when a job can outlast about ten minutes, because background workers are killed past that window.

- Attempt foreground promotion a bounded number of times and then settle the run as Failed in plain words when promotion is refused, rather than retrying forever before any work is created.

- Give the user a Stop control in the foreground notification and in the app, and settle a stopped run as Cancelled.

- Treat cancellation as its own terminal state and never report it as a per item failure or format a raw exception class name as the reason.

## Checkpoint inside each type of work

- Persist progress page by page as the work runs, storing each page and its resume position in the same transaction.

- Resume an interrupted run inside the current type as well as across types, so a long type that can never finish in one window still completes across runs.

- Make a fresh start request on an interrupted run resume from the saved checkpoints instead of resetting them, and keep enqueues from cancelling an in flight run by replacing it.

- Write the completion flag only from the same code path that reads it back on the next launch.

## Reconcile state whenever the app opens

- Reconcile every run and export row marked running against whether a live job exists each time the app opens, not only inside the worker.

- Adopt or resume a running row that still has a live job and settle a running row with no live job as Interrupted in plain words.

- Judge liveness by whether the work can still report progress, and cancel orphaned queued work that the reconciler reads as alive but that can never run.

- Discard stale per item failure rows from an earlier attempt before rendering status, and render progress from live progress rather than from per item rows alone.

## Stream output without retaining it

- Stream exports file by file and page by page, writing each chunk and releasing it before reading the next, so memory stays flat across the whole run and not only between files.

- Watch for record payloads that embed their whole series, because one such record can be tens of kilobytes and a retained structure over them grows until a single buffer doubling allocation fails.

- Catch errors as well as exceptions in the runner, because an out of memory failure bypasses ordinary handlers, kills the process and leaves the row stuck at running.

- Count bytes as written bytes in the file encoding and count files and rows from what actually landed, so a failed export never reports zero files when some files completed.

- Keep a durable export and run log that flushes line by line to storage the user can open from settings, and include that log in a completed export.

## Prove it on the device

- Bump the version code on every delivered build so Android accepts install over the previous build instead of silently refusing it.

- Test with a payload shaped like the real data at real scale under a constrained heap, because host tests passed while the on device run still died from memory growth.

- Verify the healed behaviour on the device after an interrupted run and after an app update, and report host only test results as unverified for on device behaviour.

- Hash a rebuilt artifact before delivering it and compare it with the file it replaces, so a stale binary is never shipped under a new version name.

## Available connectors

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Alternatives for better results

- Prefer several smaller resumable jobs over one long job when the platform allows it, because each job then fits inside one foreground window.

- Reduce the data moved in one pass by exporting a narrower date range or a single data type when a full export keeps dying, and say plainly that the scope changed.
