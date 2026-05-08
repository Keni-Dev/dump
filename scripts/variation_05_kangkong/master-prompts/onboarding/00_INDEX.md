# Onboarding Master Prompt Chain

A 6-stage chain of AI personas that takes a project idea (or `project_specification.md`) and produces a complete, production-ready mobile onboarding flow — strategy, designs, architecture, implementation prompts, telemetry, and monetization + compliance — without you having to know all six domains.

> Each prompt file in this folder is a **system prompt** you paste into a new AI conversation. The output of one stage becomes the input to the next. Like an assembly line for onboarding.

---

## The Chain

```
[your app idea or project_specification.md from SpecCraft]
        │
        ▼
┌──────────────────────────────────────────────────────────┐
│ 01 — HookCraft (Strategy & Psychology)                   │
│ produces: onboarding_strategy.md                         │
│ - Aha moment, pattern pick, questionnaire spec, KPIs,    │
│   antipattern audit, monetization brief, compliance brief│
└──────────────────────────────────────────────────────────┘
        │
        ▼
┌──────────────────────────────────────────────────────────┐
│ 02a — StitchCraft Onboarding (Google Stitch design)      │
│   OR                                                     │
│ 02b — ClaudeDesign Onboarding (Claude Design)            │
│ produces: ordered design prompts (one per onboarding screen)│
│ + a screen-list summary (input to stage 03)              │
└──────────────────────────────────────────────────────────┘
        │
        ▼
┌──────────────────────────────────────────────────────────┐
│ 03 — FlowCraft (Architecture)                            │
│ produces: onboarding_architecture.md                     │
│ - FSM blueprint, persistence model, SDUI decision,       │
│   TS types, telemetry event taxonomy, error handling     │
└──────────────────────────────────────────────────────────┘
        │
        ▼
┌──────────────────────────────────────────────────────────┐
│ 04 — OnboardBuild (Implementation Prompt Files)          │
│ produces: prompts/phase_onboarding/*.md                  │
│ - one prompt file per implementation step that an AI     │
│   coding agent (Claude Code/Codex/Cursor) can execute    │
└──────────────────────────────────────────────────────────┘
        │
        ▼
┌──────────────────────────────────────────────────────────┐
│ 05 — FunnelCraft (Telemetry + A/B + Cohorts)             │
│ produces: onboarding_telemetry.md +                      │
│   prompts/phase_onboarding_telemetry/*.md                │
│ - tracking plan, funnel def, experiment slate,           │
│   feature flags, dashboards                              │
└──────────────────────────────────────────────────────────┘
        │
        ▼
┌──────────────────────────────────────────────────────────┐
│ 06 — GateCraft (Paywall + Consent + Compliance)          │
│ produces: onboarding_monetization.md +                   │
│   prompts/phase_onboarding_monetization/*.md             │
│ - RevenueCat config, paywall pattern, CMP,               │
│   age gate, App Store + Play Store compliance audit      │
└──────────────────────────────────────────────────────────┘

    Stages 05 and 06 can run in parallel after 04 (mostly disjoint files)
```

---

## File Catalog

| # | File | Persona | Deliverable | Lines |
|---|---|---|---|---|
| — | [`00_INDEX.md`](./00_INDEX.md) | (this file) | Chain overview + how to use | — |
| 01 | [`01_strategy.md`](./01_strategy.md) | **HookCraft** | `onboarding_strategy.md` (Aha, pattern, questionnaire, KPIs, antipattern audit) | ~510 |
| 02a | [`02_design_stitch.md`](./02_design_stitch.md) | **StitchCraft Onboarding** | Google Stitch prompts (one per screen) | ~410 |
| 02b | [`02_design_claude.md`](./02_design_claude.md) | **ClaudeDesign Onboarding** | Claude Design prompts (XML-structured, runnable HTML output) | ~410 |
| 03 | [`03_architecture.md`](./03_architecture.md) | **FlowCraft** | `onboarding_architecture.md` (FSM, persistence, types, telemetry taxonomy, errors) | ~470 |
| 04 | [`04_implementation.md`](./04_implementation.md) | **OnboardBuild** | `prompts/phase_onboarding/*.md` (step prompt files) | ~390 |
| 05 | [`05_instrumentation.md`](./05_instrumentation.md) | **FunnelCraft** | `onboarding_telemetry.md` + `prompts/phase_onboarding_telemetry/*.md` | ~410 |
| 06 | [`06_monetization_compliance.md`](./06_monetization_compliance.md) | **GateCraft** | `onboarding_monetization.md` + `prompts/phase_onboarding_monetization/*.md` | ~480 |

---

## How to Use the Chain

### Quick path (greenfield project, ~3–5 hours total of focused work):

1. **Stage 01 (HookCraft).** Open a new AI conversation. Paste the system prompt from `01_strategy.md`. Describe your app or paste `project_specification.md`. HookCraft interviews you in batches and produces `onboarding_strategy.md`. Save it.
2. **Stage 02 (StitchCraft OR ClaudeDesign).** Open a new conversation. Paste the system prompt from `02_design_stitch.md` (or `02_design_claude.md`). Paste your strategy doc + design tokens (or codebase). Get a sequence of design prompts. Generate the screens in Stitch / Claude Design. Save the screen list summary.
3. **Stage 03 (FlowCraft).** New conversation, paste `03_architecture.md`. Paste the strategy doc + screen list. Get `onboarding_architecture.md`. Save it.
4. **Stage 04 (OnboardBuild).** New conversation, paste `04_implementation.md`. Paste the strategy + screen list + architecture. Get a directory of step prompt files in `prompts/phase_onboarding/`. Hand each step prompt to your AI coding agent (Claude Code / Codex / Cursor) for execution.
5. **Stage 05 (FunnelCraft).** New conversation, paste `05_instrumentation.md`. Paste strategy + architecture + confirmation that stage 04 is in progress. Get `onboarding_telemetry.md` + telemetry implementation prompts. Hand to coding agent.
6. **Stage 06 (GateCraft).** New conversation, paste `06_monetization_compliance.md`. Paste strategy + architecture + telemetry. Get `onboarding_monetization.md` + monetization implementation prompts. Hand to coding agent.

### Stages 05 + 06 can run in parallel after 04
They touch mostly disjoint files (telemetry wires events on top of FSM transitions; paywall + CMP wire new screens at specific FSM states). If you have multi-agent capacity, run them simultaneously to halve calendar time.

### Audit / Refactor Path
Each stage supports an "audit mode" — paste your existing onboarding artifacts (current strategy, current screens, current code, current paywall) and the persona will produce a gap analysis + redesign brief instead of greenfield.

---

## When to Use Which Design Sibling (`02a` vs `02b`)

| You should use | When |
|---|---|
| `02a` StitchCraft Onboarding (Google Stitch) | Greenfield, no codebase yet, free-tier matters, you want fast first-iteration mockups |
| `02b` ClaudeDesign Onboarding (Claude Design) | You have a codebase Claude can ingest, you want runnable HTML/CSS/JS prototypes, you'll hand off to Claude Code for implementation, you have Claude Pro/Max/Team/Enterprise |
| Both | Parallel exploration — Stitch for speed, Claude Design for production fidelity. Pick the winner per screen. |

---

## When NOT to Use This Chain

- **Single-purpose utility apps** (calculator, color picker, level) — onboarding is `Brief-Demo` pattern, doesn't need 6 stages. Run only Stage 01 + maybe Stage 02 + minimal Stage 04.
- **Internal tools** — onboarding antipatterns aren't the bottleneck; just write the spec.
- **APIs / backend-only** — there's no onboarding flow.
- **Apps already in production with strong onboarding** — use audit mode of individual stages, not the whole chain.

---

## Stack Assumptions (default — override at start of any stage)

| Layer | Default | Why |
|---|---|---|
| Mobile framework | Expo + React Native + TypeScript | Fast iteration, OTA updates, single codebase, strong hiring market |
| State machine | XState v5 | Full TS inference, persistence helpers, devtools, statechart visualization |
| Persistence (durable, fast) | MMKV | Synchronous, faster than AsyncStorage |
| Persistence (server) | Supabase | Generous free tier, RLS, edge functions, Postgres |
| Telemetry + feature flags | PostHog | Telemetry + flags + experiments in one platform; EU/US hosting |
| Subscriptions / IAP | RevenueCat | Near-universal among new subscription apps in 2026 |
| Error tracking | Sentry | Standard for mobile + web |
| CMP (consent) | Axeptio | Generous free tier, geo-aware |
| Web (if applicable) | Next.js | SSR/SSG, Vercel deploy, large ecosystem |

If your stack differs, declare it at the start of each stage's conversation. The personas will adapt — they're not hardcoded to the defaults.

---

## What You End Up With

After running the full chain on a new project, you have:

- `onboarding_strategy.md` (~3,000 words) — psychology + KPIs + questionnaire spec
- 6–15 design prompts (Stitch or Claude Design) — one per onboarding screen
- `onboarding_architecture.md` (~4,000 words) — FSM, types, persistence, telemetry taxonomy, error handling
- `prompts/phase_onboarding/` — 8–20 step files an AI coding agent can execute
- `onboarding_telemetry.md` — tracking plan, funnel, experiment slate, dashboards
- `prompts/phase_onboarding_telemetry/` — 7–9 step files for telemetry wiring
- `onboarding_monetization.md` — paywall, RevenueCat config, CMP, compliance audit
- `prompts/phase_onboarding_monetization/` — 9–11 step files for paywall + consent

That's ~50 artifacts total. They self-reference and dovetail. The downstream stages quote upstream stages by section number, so changing strategy ripples to architecture to implementation in a coordinated way.

---

## Why a Chain Instead of One Mega-Prompt

- **Each stage has one concern.** Easier to debug a broken stage than a 50-page mega-prompt.
- **Each stage produces a saveable artifact** you can review, revise, version-control before moving on.
- **You can re-run individual stages** when one input changes — the rest doesn't need to redo work.
- **Each persona is a deep specialist.** A monolith would be a generalist hand-waving across psychology + design + engineering + analytics + monetization + law. The chain trades context-passing overhead for depth.
- **Stages 05 + 06 can parallelize** because their concerns are orthogonal — chains support this naturally; mega-prompts don't.

---

## Reference Material

The personas in this chain reference (and bake in) knowledge from:

- **[Deep Dive Into App Onboarding (PDF, 21 pages)](../../research/Deep%20Dive%20Into%20App%20Onboarding.pdf)** — psychology, hook model, paywalls, state machines, GDPR/CCPA, antipatterns
- **Nir Eyal — Hooked: How to Build Habit-Forming Products** (Hook Model)
- **Brian Balfour — Reforge growth essays** (cohort thinking, retention math)
- **Nielsen Norman Group — Mobile App Onboarding research**
- **RevenueCat — State of Subscription Apps 2026** (paywall conversion data, trial benchmarks, regional patterns)
- **Apple App Store Review Guidelines (current as of authoring)** — esp. 3.1.1, 3.1.2, 4.8, 5.1.1(v)
- **Google Play Console policies** — esp. Data Safety, target API
- **GDPR, CCPA, COPPA, HIPAA** at the level of "what does this require my onboarding to do"
- **PostHog, Mixpanel, Amplitude, Eppo, ConfigCat, LaunchDarkly** documentation for feature flags + experiments
- **XState v5 documentation** for state machines
- **Mobbin / UI Sources / App Lover** for current best-in-class onboarding patterns

---

## Maintenance

This chain captures patterns and platforms current as of authoring. Things that age fastest:
- **Apple App Store rules** (the toggle-paywall ban is a recent example)
- **Pricing benchmarks** (RevenueCat re-publishes annually)
- **Tool-specific feature sets** (Stitch and Claude Design are evolving rapidly)
- **CMP / consent law** (regulators add jurisdictions yearly)

When a stage's recommendations feel stale, run that stage with a `<web_search_triggers>`-driven session — the personas are designed to web-search for current data when uncertain.

When a major platform shift happens (e.g., a new App Store rule, a new RevenueCat capability, a new design tool), update the relevant master prompt's `<core_principles>` or `<platform_specific>` sections. Don't rewrite the whole chain.

---

## Acknowledgments

This chain is part of the broader `master-prompts/` library. It depends on:

- `project-discovery-prompt.md` (SpecCraft) — produces `project_specification.md` upstream
- `mobile-master-prompt.md` (StitchCraft Mobile) — `02a` extends this
- `implementation-guide-prompt.md` (BuildCraft) — `04` extends this for onboarding
- `feature-spec-prompt.md` / `feature-implementation-prompt.md` — adjacent for non-onboarding features

If you want a similar chain for a different domain (auth, social features, gamification, real-time collab), use this folder's structure as the template.
