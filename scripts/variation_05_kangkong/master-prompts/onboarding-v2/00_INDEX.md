# Onboarding v2 Master Prompt Chain

A 6-stage chain of AI personas that takes a project idea (or `project_specification.md` from SpecCraft, or `emotional_strategy.md`+`emotional_spec.md` from the v2 emotional design chain) and produces a complete, **2026-current**, psychology-first, archetype-locked, anti-AI-slop mobile onboarding flow — strategy, designs, architecture, implementation prompts, telemetry, monetization, and compliance.

> **What's new in v2 vs v1?** Psychology-first (not pattern-first). Story-Onboarding Doctrine (Mau Baron) AS A FIRST-CLASS PEER to Long Questionnaire (Cal AI). AI Plan Reveal as engineered Aha. Tight integration with the v2 emotional design chain (consumes `emotional_strategy.md` + `emotional_spec.md` as required inputs). 2026 currency baked in: **Apple toggle-paywall ban (Guideline 3.1.2, effective 2026-01)**, COPPA 2026-04-22 deadline, FTC Click-to-Cancel (effective 2025-07-14), EU Digital Fairness Act (Q4 2026 draft), Liquid Glass + M3 Expressive design language alignment. All 65 onboarding research items in `.agent/research/onboarding-v2/` ground every prompt.

> Each prompt file is a **system prompt** you paste into a new AI conversation. The output of one stage becomes the input to the next.

---

## The Chain

```
[your idea, project_specification.md, OR emotional_strategy.md + emotional_spec.md]
        │
        ▼
┌──────────────────────────────────────────────────────────┐
│ 01 — PsychCraft v2 (Strategy + Psychology, psyche-first) │
│ produces: onboarding_strategy.md                         │
│ - Pattern pick (story / long-quiz / cinematic / friction)│
│ - Aha definition (cognitive realization, not 1st use)    │
│ - Hook-loop wiring (Trigger / Action / Variable / Invest)│
│ - Questionnaire spec (identity vs demographic, sequence) │
│ - AI Plan Reveal decision + theatrical loader spec       │
│ - Paywall posture (Calm / Adaptive / Engagement)         │
│ - 6+modern antipattern audit (incl. toggle ban 2026-01)  │
│ - Compliance posture (GDPR/CCPA/COPPA/DFA/Click-to-Cancel)│
│ - KPI targets (Day 0 / D7 / D30 / 12mo LTV)              │
└──────────────────────────────────────────────────────────┘
        │
        ▼
┌──────────────────────────────────────────────────────────┐
│ 02a — ClaudeDesign Onboarding v2 (code-first design)     │
│   OR                                                     │
│ 02b — StitchCraft Onboarding v2 (visual mockup design)   │
│ produces: ordered design prompts (one per onboarding screen)│
│ - Inherits emotional_spec.md tokens (OKLCH, type, motion)│
│ - Anti-AI-slop ban list enforced per screen              │
│ - Per-screen telemetry events spec'd                     │
└──────────────────────────────────────────────────────────┘
        │
        ▼
┌──────────────────────────────────────────────────────────┐
│ 03 — FlowCraft v2 (Architecture)                         │
│ produces: onboarding_architecture.md                     │
│ - XState v5 FSM blueprint (5 acts for story, N steps     │
│   for long-quiz)                                         │
│ - Persistence model (MMKV + server sync, fault tolerance,│
│   cross-device resume hydration)                         │
│ - SDUI decision (Server-Driven UI vs hardcoded)          │
│ - TS types, telemetry event taxonomy, error handling     │
│ - AI Plan Reveal endpoint contract (LLM call + cache)    │
└──────────────────────────────────────────────────────────┘
        │
        ▼
┌──────────────────────────────────────────────────────────┐
│ 04 — OnboardBuild v2 (Implementation Prompt Files)       │
│ produces: prompts/phase_onboarding/*.md                  │
│ - one prompt file per implementation step that an AI     │
│   coding agent (Claude Code/Codex/Cursor) can execute    │
│ - Wires emotional_spec tokens, FSM states, paywall SDKs  │
└──────────────────────────────────────────────────────────┘
        │
        ▼
┌──────────────────────────────────────────────────────────┐
│ 05 — FunnelCraft v2 (Telemetry + A/B + Cohorts)          │
│ produces: onboarding_telemetry.md +                      │
│   prompts/phase_onboarding_telemetry/*.md                │
│ - Step-level tracking plan (every step emits             │
│   viewed/completed/abandoned)                            │
│ - Funnel def, cohort/LTV harness                         │
│ - Experiment slate (top-quartile target = 14.7 paywall   │
│   experiments/yr per RevenueCat 2026)                    │
│ - Feature flags, kill-switches, dashboards               │
└──────────────────────────────────────────────────────────┘
        │
        ▼
┌──────────────────────────────────────────────────────────┐
│ 06 — GateCraft v2 (Paywall + Consent + Compliance)       │
│ produces: onboarding_monetization.md +                   │
│   prompts/phase_onboarding_monetization/*.md             │
│ - RevenueCat / Adapty / Superwall config                 │
│ - Paywall pattern (post-toggle-ban 2026-01:              │
│   side-by-side cards or timeline transparency)           │
│ - Win-back paywall (item 39)                             │
│ - CMP (Axeptio/OneTrust/Usercentrics) + ATT priming      │
│ - COPPA neutral age gate (deadline 2026-04-22)           │
│ - FTC Click-to-Cancel symmetry audit                     │
│ - EU DFA Q4-2026 dark-pattern pre-audit                  │
│ - App Store + Play Store compliance audit                │
└──────────────────────────────────────────────────────────┘

    Stages 05 and 06 can run in parallel after 04 (mostly disjoint files)
```

---

## File Catalog

| # | File | Persona | Deliverable | Lines |
|---|---|---|---|---|
| — | [`00_INDEX.md`](./00_INDEX.md) | (this file) | Chain overview + how to use | — |
| 01 | [`01_psychology.md`](./01_psychology.md) | **PsychCraft v2** | `onboarding_strategy.md` (pattern pick, Aha, Hook wiring, questionnaire spec, paywall posture, antipattern audit, compliance posture, KPIs) | ~600 |
| 02a | [`02a_design_claude.md`](./02a_design_claude.md) | **ClaudeDesign Onboarding v2** | Claude Design prompts (XML-structured, runnable HTML/CSS/JS, per-screen) | ~500 |
| 02b | [`02b_design_stitch.md`](./02b_design_stitch.md) | **StitchCraft Onboarding v2** | Google Stitch prompts (text-only visual mockup spec, per-screen) | ~500 |
| 03 | [`03_architecture.md`](./03_architecture.md) | **FlowCraft v2** | `onboarding_architecture.md` (XState v5 FSM, persistence, types, telemetry taxonomy, AI Plan Reveal endpoint, errors) | ~550 |
| 04 | [`04_implementation.md`](./04_implementation.md) | **OnboardBuild v2** | `prompts/phase_onboarding/*.md` (step prompt files for AI coding agent) | ~450 |
| 05 | [`05_telemetry.md`](./05_telemetry.md) | **FunnelCraft v2** | `onboarding_telemetry.md` + `prompts/phase_onboarding_telemetry/*.md` | ~450 |
| 06 | [`06_monetization_compliance.md`](./06_monetization_compliance.md) | **GateCraft v2** | `onboarding_monetization.md` + `prompts/phase_onboarding_monetization/*.md` | ~550 |

---

## How v2 Differs from v1

| Aspect | v1 (`master-prompts/onboarding/`) | v2 (`master-prompts/onboarding-v2/`) |
|---|---|---|
| **Foundation** | Pattern-first (HookCraft picks a pattern) | Psychology-first (interrogates user emotional reality + archetype, then patterns fall out) |
| **Pattern taxonomy** | One "long" pattern | Two distinct long patterns: **Story-Onboarding (Mau Baron)** and **Long Questionnaire (Cal-AI)** — same family, different mechanics |
| **Aha engineering** | Implicit | Explicit AI Plan Reveal slot at step N-1, theatrical loader spec, Mid-Onboarding Review prompt |
| **Emotional integration** | None | REQUIRED inputs: `emotional_strategy.md` + `emotional_spec.md` from v2 emotional design chain |
| **Anti-AI-slop discipline** | Light | Aggressive ban list per stage (no Inter, no indigo-500, no rounded-xl, no Lucide trinity, no toggle paywalls) |
| **2026 currency** | Up to 2024 | Apple toggle-paywall ban (3.1.2 effective 2026-01), COPPA 2026-04-22 deadline, Click-to-Cancel (2025-07-14), DFA Q4 2026 draft, Liquid Glass (WWDC25), M3 Expressive (I/O 25 18k-participant study), RevenueCat 2026, Adapty 2026 benchmarks |
| **Solo-dev posture** | Generic | Calibrated to solo founder publishing apps. Each prescribed_action notes solo_dev_feasibility |
| **Research base** | PDF + practitioner sources | 65-item structured research base in `.agent/research/onboarding-v2/results/` (33 fields per item) |

---

## How to Use the Chain

### Quick path (greenfield project, ~3–5 hours focused work):

1. **Run v2 emotional design chain first** if you don't have `emotional_strategy.md` + `emotional_spec.md`:
   - `.agent/master-prompts/v2/01_emotional_discovery.md` → `emotional_strategy.md`
   - `.agent/master-prompts/v2/02_emotional_spec.md` → `emotional_spec.md`
2. **Stage 01 (PsychCraft v2).** Open a new AI conversation. Paste `01_psychology.md`. Pass the emotional artifacts + your app idea. Get `onboarding_strategy.md`. Save it.
3. **Stage 02 (ClaudeDesign OR StitchCraft).** Paste `02a_design_claude.md` (or `02b_design_stitch.md`). Pass `emotional_spec.md` + `onboarding_strategy.md`. Get a sequence of design prompts. Generate the screens. Save the screen list.
4. **Stage 03 (FlowCraft v2).** Paste `03_architecture.md`. Pass strategy + screen list. Get `onboarding_architecture.md`. Save.
5. **Stage 04 (OnboardBuild v2).** Paste `04_implementation.md`. Pass strategy + screens + architecture. Get a directory of step prompt files. Hand each to your AI coding agent.
6. **Stage 05 (FunnelCraft v2).** Paste `05_telemetry.md`. Pass strategy + architecture. Get telemetry doc + implementation prompts.
7. **Stage 06 (GateCraft v2).** Paste `06_monetization_compliance.md`. Pass strategy + architecture + telemetry. Get monetization doc + implementation prompts.

### Stages 05 + 06 can run in parallel after 04
Telemetry events wire on top of FSM transitions; paywall + CMP wire new screens at specific FSM states.

### Audit / Refactor Path
Each stage supports an "audit mode" — paste your existing onboarding artifacts (current strategy / screens / code / paywall) and the persona produces a gap analysis + redesign brief. **Most apps shipped before 2026-01 will have a toggle paywall — Stage 06's audit mode flags this immediately.**

---

## When NOT to Use This Chain

- **Single-purpose utility apps** (calculator, color picker, level) — use Cinematic 4-Screen pattern (item 25 of research base); run only Stage 01 + minimal Stage 02 + Stage 04.
- **Internal tools** — onboarding antipatterns aren't the bottleneck; just write the spec.
- **APIs / backend-only** — there's no onboarding flow.
- **Apps already in production with strong onboarding** — use audit mode of individual stages, not the whole chain.

---

## Stack Defaults (interrogated per project — Stage 01 will ask)

| Layer | Default | Why |
|---|---|---|
| Mobile framework | Expo + React Native + TypeScript | Fast iteration, OTA updates, single codebase |
| State machine | XState v5 | TS-first, persistence helpers, devtools |
| Persistence (durable, fast) | MMKV | Synchronous, faster than AsyncStorage |
| Persistence (server) | Supabase | Generous free tier, RLS, edge functions |
| Subscriptions / IAP | RevenueCat (with Adapty as A/B-velocity alt) | RevenueCat near-universal in 2026; Adapty Pro for high-velocity paywall A/B |
| Telemetry + flags + experiments | PostHog | Single platform; EU/US hosting |
| Error tracking | Sentry | Standard mobile + web |
| CMP (consent) | Axeptio | Generous free tier, geo-aware |
| LLM (for AI Plan Reveal) | Claude Sonnet 4.6 (or GPT-4o) | Frontier-class reasoning needed for personalization quality; Haiku/small-model insufficient |
| Web (if applicable) | Next.js | SSR/SSG, Vercel deploy |

If your stack differs, declare it at the start of each stage's conversation. The personas adapt.

---

## What You End Up With

After running the full v2 chain on a new project:

- `emotional_strategy.md` + `emotional_spec.md` (~5,000 words combined) — archetype, OKLCH, motion, microcopy, ban list
- `onboarding_strategy.md` (~3,500 words) — psychology + pattern pick + Aha + KPIs + questionnaire spec + paywall posture + compliance posture
- 8–20 design prompts (Stitch or Claude Design) — one per onboarding screen
- `onboarding_architecture.md` (~5,000 words) — XState FSM, types, persistence, telemetry taxonomy, AI Plan Reveal endpoint, error handling
- `prompts/phase_onboarding/` — 10–25 step files for AI coding agent
- `onboarding_telemetry.md` — step-level tracking plan, funnel, experiment slate, dashboards
- `prompts/phase_onboarding_telemetry/` — 7–9 step files for telemetry wiring
- `onboarding_monetization.md` — paywall (post-toggle-ban), RevenueCat config, win-back, CMP, COPPA, Click-to-Cancel + DFA audit
- `prompts/phase_onboarding_monetization/` — 9–12 step files for paywall + consent

That's ~55–80 artifacts total. They self-reference and dovetail. The downstream stages quote upstream stages by section number, so changing strategy ripples to architecture to implementation in coordinated fashion.

---

## 2026 Currency Notes (baked into stages)

- **Apple App Store Guideline 3.1.2 (effective 2026-01)** — toggle paywalls BANNED. Stage 06 enforces side-by-side card selection or explicit timeline transparency. Stage 02's design prompts forbid toggle paywall mockups.
- **FTC Click-to-Cancel Rule (effective 2025-07-14)** — cancellation must be as easy as signup. Stage 06's compliance audit checks symmetry.
- **Amended COPPA Rule (compliance deadline 2026-04-22)** — neutral birthdate gates required (NOT "Are you 13+?"); under-13s route to verifiable parental consent. Stage 06 enforces. Disney $10M settlement Dec 2025 sets enforcement tone.
- **EU Digital Fairness Act (Q4 2026 draft expected)** — dark patterns, addictive design, manipulative consent UIs targeted. Stage 06 pre-audits.
- **WCAG 2.2 (ratified Oct 2023)** — 24×24 px target size minimum, dragging alternatives, focus appearance, redundant entry. Stage 02's design prompts and Stage 04's implementation enforce.
- **Liquid Glass (WWDC25, iOS 26+)** — translucent material, bolder left-aligned alert typography, dynamic morphing controls. Stage 02 aligns design tokens.
- **Material 3 Expressive (Google I/O 2025, 18k-participant study)** — 4× faster element discovery in eye-tracking; removes age-effect on usability speed for users 45+. Stage 02 leverages.
- **RevenueCat State of Subscription Apps 2025/2026** — hard paywalls 21% higher LTV; soft paywalls 50% higher first-impression conversion; 35% of apps now hybrid (sub + consumable + lifetime); 90% of trial starts on Day 0. Stage 06 calibrates.
- **Adapty High-Performing Paywall 2026** — onboarding paywall converts 1.35% (highest of any placement); weekly+3-day-trial = $54.50 12mo LTV vs $7.40 without (636% lift); localization = 62.3% LTV win rate; top performers run 14.7 experiments/yr. Stage 05 + 06 calibrate.

---

## Anti-AI-Slop Doctrine (enforced at every stage)

Every stage's prompt explicitly forbids these defaults:

- **Type:** Inter, Roboto, Arial, system-ui-only stacks, default Tailwind font-sans
- **Color:** indigo-500 (#6366F1), violet-500 (#8B5CF6), the from-violet-500-to-indigo-500 / from-purple-500-to-blue-500 / from-cyan-400-to-violet-500 / from-pink-500-to-purple-500 gradients
- **Geometry:** rounded-xl on every container, max-w-7xl wrapper, identical 16px/24px padding everywhere, ring-1 ring-white/10 cards
- **Layout:** centered hero with H1+subhead+CTA-pair+trust-row, three-column feature grid with icons
- **Iconography:** Lucide cube/check/lightning trinity, emoji bullets (🚀✨⚡🔥💡🎯🛡️✅)
- **Imagery:** stock-photo-of-diverse-team-on-laptops, glassy-3D-blob, AI-illustrations-with-melted-hands
- **Motion:** hover:scale-105 on every card, animate-pulse, fade-in-on-scroll uniform
- **Templates:** shadcn defaults, Tailwind UI Catalyst paste, Lovable/v0/Bolt scaffolds without customization
- **Onboarding-specific:** toggle paywalls (BANNED 2026-01), confirm-shaming close buttons, generic loading spinners, fake countdown timers, demographic-heavy first questions ("What's your age?" before "What brings you here?")

Each stage prescribes specific named alternatives. 925studios research: AI-slop sites convert 91% lower than distinctive custom design.

---

## Research Base

Each prompt is grounded in 65 deeply-researched items in `.agent/research/onboarding-v2/results/` covering:

- **A. Psychology Foundations** (8): Hook Model, Cognitive Load, First Impression Anchoring, Sunk Cost / IKEA, Self-Determination, Peak-End, Goal-Gradient, Hick's Law
- **B. Aha & Activation** (7): Aha vs Activation, TTV, Cohort Analysis, AI Plan Reveal, Theatrical Loader, Cross-Step Personalization, Mid-Onboarding Review
- **C. Patterns** (10): Progressive Disclosure, Long Questionnaire (Cal-AI), Story-Onboarding (Mau-Baron), Frictionless, Benefits-led, Empty State + Data Seeding, Coach Marks, Walkthroughs, Permission Priming, Cinematic 4-Screen
- **D. Questionnaire** (4): Sequencing, Type Taxonomy, Conversational vs Form, Progress Indicators
- **E. Architecture** (4): FSM, Server-Driven UI, Persistence + Fault Tolerance, Cross-Device Resume
- **F. Monetization** (9): Hard Paywall (incl. Toggle Ban), Trial vs Direct, Localization, Persistent CTA, Plan Selection, Win-Back, Web-Checkout Parallel, Hybrid Monetization, UGC↔Onboarding Alignment
- **G. Telemetry** (3): Tracking Plan, Funnel + Cohort/LTV, Feature Flags + A/B
- **H. Compliance** (5): GDPR/CCPA + Data Min, CMP + ATT, COPPA + VPC, DFA Audit, Click-to-Cancel
- **I. Anti-Patterns** (1): Six-Antipattern Audit + Modern Extensions
- **J. Emotional Integration** (2): Archetype Voice, Onboarding-as-Peak-Moment
- **K. Category-Specific** (4): Wellness, Productivity/B2B, Fintech, AI-Wrapper
- **L. Notification** (2): Push Priming + Internal Trigger, Notification Ladder
- **M. Modern Auth** (3): Magic Link, Biometric/Passkeys, Social Graph Import
- **N. Contextual** (1): Time-of-Day-Aware
- **O. Accessibility** (1): Accessibility-First Onboarding
- **P. Pre-Permission** (1): Soft-Ask Screen Pattern

Plus a supplementary file `Top_App_Categories_By_Revenue_2026.json` for default category routing.

See `.agent/research/onboarding-v2/outline.yaml` and `fields.yaml` for the full research framework.

---

## Compatibility with Other Master-Prompt Libraries

- **`.agent/master-prompts/v2/`** (Emotional Design v2 chain) — REQUIRED upstream input. Provides `emotional_strategy.md` (archetype, ban list) + `emotional_spec.md` (OKLCH, type, motion, microcopy).
- **`.agent/master-prompts/onboarding/`** (v1 onboarding chain) — superseded by v2. v1 remains for fallback or for projects that don't run the v2 emotional chain.
- **`.agent/master-prompts/project-discovery-prompt.md`** (SpecCraft) — optional upstream. Provides `project_specification.md`.
- **`.agent/master-prompts/feature-spec-prompt.md` / `feature-implementation-prompt.md`** — adjacent for non-onboarding features.

---

## Maintenance

This chain captures patterns, regulations, and platforms current as of **2026-05-08**. Things that age fastest:

- **Apple App Store rules** (3.1.2 toggle ban is 2026-01 — expect more rules as DFA enforcement begins)
- **Pricing benchmarks** (RevenueCat / Adapty re-publish annually; Adapty 2026 figures will be superseded)
- **Tool-specific feature sets** (Stitch, Claude Design, Plotline, Superwall evolving rapidly)
- **CMP / consent law** (regulators add jurisdictions yearly; DFA Q4 2026 draft will become enforced rule mid-2027)
- **Material 3 Expressive + Liquid Glass** (Apple/Google ship updates each WWDC/I/O — expect drift)

When a stage's recommendations feel stale, run that stage with web-search-on triggers — the personas search for current data when uncertain.

When a major shift happens (new App Store rule, new RevenueCat capability, new design tool), update the relevant master prompt's `<core_principles>` or `<platform_specific>` sections. Don't rewrite the whole chain.
