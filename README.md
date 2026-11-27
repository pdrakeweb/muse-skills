# muse-skills

Agent skills for Muse, maintained here so they can be versioned and updated.

## Skills in this repo

| Skill | What it covers |
|---|---|
| [android_long_running_work](android_long_running_work/) | Build Android extracts, exports and other long running jobs that stay alive, resume where they stopped, and settle honestly when the system kills them. |
| [app_creation_settled_verification](app_creation_settled_verification/) | Amendment to App Creation adding settled state verification, single flight retry handling, and numeric tie out for data heavy Muse artifacts. |
| [card_account_verification](card_account_verification/) | Verify a card account's current number, holder, and renewal date before reporting any downgrade, cancel, or fee action. |
| [cf-cli](cf-cli/) | Cloudflare's official cf CLI (beta) for the public Cloudflare API and Workers projects. Use for finding and running Cloudflare commands from the terminal — sign-in and profiles, cf cli search, cf schema, cf deploy/dev/build, resource commands for DNS, zones, D1, KV, and R2 — and for choosing between cf and Wrangler in a project. |
| [cloudflare-email-service](cloudflare-email-service/) | Implement or troubleshoot Cloudflare Email Sending and Email Routing integrations and their delivery configuration. |
| [cloudflare-one-migrations](cloudflare-one-migrations/) | Assess and plan migrations from existing VPN, SWG, or SASE platforms to Cloudflare One, including policy mapping, parity gaps, and rollout. |
| [cloudflare-one](cloudflare-one/) | Design, configure, troubleshoot, or review Cloudflare One Zero Trust and SASE deployments. Use cloudflare-one-migrations for migration planning from other vendors. |
| [durable-objects](durable-objects/) | Build, debug, or review Cloudflare Durable Objects code for persistent state and coordination. |
| [gateway-workers](gateway-workers/) | Build, debug, or review Cloudflare Workers invoked by the Forward action in Gateway HTTP policies, including the GatewayMiddleware entrypoint, Gateway types, context, and continuation. |
| [home_control_ha_change_validation](home_control_ha_change_validation/) | Amendment to Home Control that adds a live side effect gate, a per item control count, and behavioral verification for Home Assistant dashboard and automation changes. |
| [medication_regimen_updates](medication_regimen_updates/) | Keep every medication reminder, alarm label and schedule page matching the regimen the user last confirmed whenever a dose, interval or time changes. |
| [review_panel_rereview_gate](review_panel_rereview_gate/) | Gate a second review panel verdict on verified execution evidence for each claimed mitigation, so prose edits alone never close a finding. |
| [sandbox-migrate-to-next](sandbox-migrate-to-next/) | Migrate Cloudflare Sandbox apps from stable @cloudflare/sandbox to @cloudflare/sandbox@next (SDK 1.0 preview). Use sandbox-next for apps already on the preview. |
| [trip_planning_points_verification](trip_planning_points_verification/) | Amendment to Trip Planning that verifies points hotel claims before reporting them, covering booking windows, property identity, tier rates and program terms. |
| [ui-ux-pro-max](ui-ux-pro-max/) | UI/UX design intelligence for web, mobile, and desktop. This skill should be used when designing, building, reviewing, or fixing interfaces, including pages, components, design systems, accessibility, interaction, responsive layout, typography, color, charts, and stack-specific UI implementation. Searchable local data: 79 searchable styles (50 active), 192 product palettes and reasoning profiles, 74 font pairings, 119 UX guidelines, 105 icons, 17 GSAP presets, 25 chart types, and 22 stacks. |
| [windows_powershell_snippet_safety](windows_powershell_snippet_safety/) | Check every PowerShell snippet against Windows PowerShell 5.1 before sending it, so parser errors, missing methods, and dollar sign expansion do not reach the user. |
| [workers-best-practices](workers-best-practices/) | Cloudflare Workers best practices for production applications. Use when writing, reviewing, or configuring Workers. |
| [workers-profiling](workers-profiling/) | Profile or debug CPU usage and memory allocation in deployed Cloudflare Workers and Durable Objects. Then use this information to optimize your code. |
| [wrangler](wrangler/) | Run or troubleshoot Wrangler CLI commands in projects that have a wrangler.jsonc, wrangler.json, or wrangler.toml file, including local development, Previews, deployment, and resource management. For new projects and projects without a Wrangler configuration file, use the cf CLI instead. |

## Already published elsewhere

These skills live in their own repos and are not duplicated here:

- [android-app-development](https://github.com/pdrakeweb/android-app-development-skill) — guided native Android app development
- [council](https://github.com/pdrakeweb/council-skill) — a council of sub-agents debates a hard question; a Judge rules
- [food-photo-nutrition](https://github.com/pdrakeweb/food-photo-nutrition-skill) — calories and macros from a food photo
- [local-monarch](https://github.com/pdrakeweb/monarch-money-skill/tree/main/monarch-money) — Monarch Money data pull (private repo)
- [muse-parallel-work](https://github.com/pdrakeweb/muse-parallel-work) — parallel work governor: dispatch, admit, spawn, reconcile (private repo)

## Layout

Each skill is one directory holding a `SKILL.md` plus its `references/`, `scripts/`, or `data/` where applicable. `skill.yaml` files are intentionally not published: they carry internal skill-improvement loop metadata.
