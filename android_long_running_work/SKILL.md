# Android Long Running Work

Repository: https://github.com/pdrakeweb/muse-skills/tree/main/android_long_running_work

## When this applies
- Apply when building or fixing an Android extract, export, sync, or import that can run longer than a few minutes, or that has to survive process death, app updates, or a user Stop.
- Apply alongside android-app-development when that skill drives the project. This skill covers only the long-running job.

## Keep the run alive or settle it honestly
- Run any job that can outlast about ten minutes as foreground work for the whole run (WorkManager `setForeground` or a foreground service), because a plain background worker is stopped at the ten-minute execution limit.
- Declare the matching `foregroundServiceType` and its permission (for example `dataSync` with `FOREGROUND_SERVICE_DATA_SYNC`), because from Android 14 the start fails without them. Budget for the Android 15 `dataSync` limit of six hours in 24, and settle the run when `onTimeout` fires.
- Expect promotion to be refused when the app is in the background on Android 12 or later (`ForegroundServiceStartNotAllowedException`). Attempt it a bounded number of times, then settle the run as Failed in plain words. Never retry forever before any work is created.
- Give the user a Stop control in the foreground notification and in the app, and settle a stopped run as Cancelled.
- Treat cancellation as its own terminal state. Never report it as a per-item failure, and never format a raw exception class name as the reason.

## Checkpoint inside each type of work
- Persist progress page by page as the work runs, storing each page and its resume position in the same transaction.
- Resume an interrupted run inside the current type as well as across types, so a type too long to finish in one window still completes across runs.
- Make a fresh start request on an interrupted run resume from the saved checkpoints instead of resetting them. Enqueue with a unique work name and `KEEP` or `APPEND`, never `REPLACE`, so an enqueue cannot cancel an in-flight run.
- Read and write the completion flag through one accessor (same store, same key), so the value written is the value the next launch reads.

## Reconcile state whenever the app opens
- Reconcile every run and export row marked running against whether a live job exists each time the app opens, not only inside the worker.
- Adopt or resume a running row that still has a live job, and settle a running row with no live job as Interrupted in plain words.
- Judge liveness by whether the work can still report progress. Cancel orphaned queued work that the reconciler reads as alive but that can never run.
- Discard stale per-item failure rows from an earlier attempt before rendering status, and render progress from live progress, not from per-item rows alone.

## Stream output without retaining it
- Stream exports file by file and page by page: write each chunk and release it before reading the next, so memory stays flat across the whole run and not only between files.
- Watch for record payloads that embed their whole series. One such record can be tens of kilobytes, and a structure that retains them grows until a single buffer-doubling allocation fails.
- Catch `OutOfMemoryError` as well as exceptions at the runner boundary, because it bypasses ordinary `Exception` handlers, kills the process, and leaves the row stuck at running. In coroutines, rethrow `CancellationException` from any broad catch, or Stop stops working.
- Count bytes as written bytes in the file encoding, and count files and rows from what actually landed, so a failed export never reports zero files when some files completed.
- Keep a durable run log that flushes line by line to storage the user can open from settings, and include that log in a completed export.

## Prove it on the device
- Raise the version code on every delivered build, so an install is never a downgrade (which Android refuses) and every build can be told apart on the device.
- Test with a payload shaped like the real data at real scale under a constrained heap, because host tests passed while the on-device run still died from memory growth.
- Verify the healed behaviour on the device after an interrupted run and after an app update. Report host-only test results as unverified for on-device behaviour.
- Hash a rebuilt artifact before delivering it and confirm the hash differs from the file it replaces, so a stale binary is never shipped under a new version name.

## Available connectors
- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.
- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Alternatives for better results
- Prefer several smaller resumable jobs over one long job when the platform allows it, so each job fits inside one foreground window.
- For a user-started transfer on Android 14 or later, consider a user-initiated data transfer job (`JobInfo.Builder.setUserInitiated`), which is exempt from the ten-minute limit and from the background-start restriction.
- When a full export keeps dying, move less data in one pass (a narrower date range or a single data type), and tell the user plainly that the scope changed.
