# Validating App Ideas — Master Prompt Chain

A 7-stage chain of AI personas that takes a raw app idea (or `idea_landscape.md` from the recon stage) and produces a complete, **2026-current**, payment-validated, bias-audited, anti-AI-slop validation verdict — psychology audit, idea sourcing recon, customer interrogation, pretotyping + smoke tests, willingness-to-pay validation, MVP execution, and a final go/no-go verdict that hands off cleanly into the **onboarding-v2** and **emotional-design v2** chains.

> **The Spine.** Rob Walling's 2/20/200 framework provides the time-boxed staging that gates progression (2h prior art → 20h interviews + landing → 200h MVP that can charge). Pat Walls' content-first / TikTok-as-MVP doctrine and Marc Lou's payment-as-validation doctrine layer in as parallel tactical tracks. Pieter Levels' 24-72hr ugly-MVP doctrine governs Stage 3 cadence. Mom Test (Fitzpatrick), JTBD (Christensen/Ulwick/Moesta), and Pretotyping (Savoia) supply the customer-interrogation and demand-test mechanics. Anti-AI-slop discipline (forbidding Inter / indigo-500 / purple-blue gradient / Lucide trinity / emoji-bullets per .agent/feedback memory) is enforced on every landing-page and content artifact (925studios: AI-slop landings record 91% lower CR).

> **2026 currency.** RevenueCat State of Subscription Apps 2025/2026 + Adapty 2026 paywall benchmarks (5x hard-paywall trial conversion, 636% LTV gap worst-vs-best). FTC Click-to-Cancel (2025-07-14). EU Digital Fairness Act (Q4 2026 draft). Apple toggle-paywall ban (Guideline 3.1.2, 2026-01). COPPA 2026-04-22 deadline. App Store + Play Store rules. GummySearch shutdown (2025-11-30 — Reddit API revocation) and post-GummySearch pain-mining stack. AI codegen layer (Lovable / Bolt / v0 / Replit / Cursor) collapsed validation cycles in 2025-2026.

> **Solo-dev-first.** Every prescribed pattern includes `solo_dev_feasibility` (same_day / 1_week / 1_month / requires_team). Mobile + web with explicit branching per stage.

> Each prompt file is a **system prompt** you paste into a new AI conversation. Output of one stage becomes input to the next.

---

## The Chain

```
[raw idea, problem journal entry, OR audit of partially-validated idea]
        │
        ▼
┌──────────────────────────────────────────────────────────┐
│ 01 — BiasCraft (Founder Psychology + Bias Audit)         │
│ produces: bias_audit.md                                  │
│ - Confirmation bias / sunk cost / IKEA / wishful audit   │
│ - Pre-registered kill criteria (load-bearing)            │
│ - Polite-lie defense protocol                            │
│ - Founder archetype alignment (Magician/Jester/Caregiver │
│   default per user memory; avoid Sage/Ruler default)     │
└──────────────────────────────────────────────────────────┘
        │
        ▼
┌──────────────────────────────────────────────────────────┐
│ 02 — ScoutCraft (Idea Sourcing + Macro Recon)            │
│ produces: idea_landscape.md (+ 1-3 candidate idea cards) │
│ - Problem journal review / niche mining                  │
│ - App marketplace mining (Flippa, Acquire, MicroAcquire) │
│ - Mobile: ASO keyword-volume gate (Adam Lyttle)          │
│   + Sensor Tower / AppFigures / Apptweak intelligence    │
│ - Web: Google Trends velocity + Lean SEO                 │
│ - Reverse-engineering competitors (MitaBoost 1k-paying)  │
│ - Reddit/TikTok/X organic signal mining                  │
│   (post-GummySearch stack)                               │
│ - Greg Isenberg ACP (Audience → Community → Product)     │
└──────────────────────────────────────────────────────────┘
        │
        ▼
┌──────────────────────────────────────────────────────────┐
│ 03 — MomCraft (Mom Test + JTBD Interrogation)            │
│ produces: interview_brief.md + jtbd_synthesis.md         │
│ - Mom Test interview script (gold-standard questions)    │
│ - Past-behavior anchoring + alternatives probe           │
│ - JTBD Switch Interview (forces of progress: push/pull/  │
│   anxiety/habit)                                         │
│ - Hard-commitment currency ladder (LOI / prepay / intro) │
│ - 10-interview synthesis → forces-of-progress diagram    │
│ - LLM-assisted synthesis (Otter.ai → Claude)             │
└──────────────────────────────────────────────────────────┘
        │
        ▼
┌──────────────────────────────────────────────────────────┐
│ 04 — SmokeCraft (Pretotyping + Smoke Tests + Content-1st)│
│ produces: pretotype_plan.md + landing_brief.md           │
│           + content_test_brief.md                        │
│ - Pretotype pick (Fake Door / Impersonator / Provincial  │
│   / Pinocchio / YouTube / Onesie / Mechanical Turk)      │
│ - Asset stack 2026 (Carrd / Lovable / Bolt / v0)         │
│   with mandatory anti-AI-slop discipline                 │
│ - Traffic mix (fake AdWords + organic Reddit + TikTok)   │
│ - Pat Walls content-first / 3-word rule / TikTok hooks   │
│ - Pushscroll / Cal AI / Mau Baron exemplar patterns      │
│ - Conversion thresholds (36% install CR = green light)   │
└──────────────────────────────────────────────────────────┘
        │
        ▼
┌──────────────────────────────────────────────────────────┐
│ 05 — PayCraft (WTP Validation + Stripe Smoke Checkout)   │
│ produces: wtp_validation.md + checkout_brief.md          │
│ - Van Westendorp PSM (directional)                       │
│ - A/B pricing tests on landing (Intercom $50/$100/$150)  │
│ - Pre-sales / deposits / founding-member discounts       │
│ - Stripe sandbox + serverless smoke checkout             │
│   (4242 4242 4242 4242 + refund-the-real-purchase)       │
│ - Marc Lou's "validate with payments, not praise"        │
│ - Hard paywall at install (RevenueCat 2025: 5x conv)     │
│   vs freemium decision matrix                            │
└──────────────────────────────────────────────────────────┘
        │
        ▼
┌──────────────────────────────────────────────────────────┐
│ 06 — ShipCraft (MVP Execution: Concierge/Wizard/NoCode/  │
│                  AI-Codegen/Levels 24-72hr Ugly)         │
│ produces: mvp_blueprint.md + execution_prompts/*.md      │
│ - Value Hypothesis (Concierge) vs Growth Hypothesis      │
│   (Wizard of Oz) decision                                │
│ - No-code stack (Bubble/Adalo/Glide/Softr)               │
│ - AI codegen stack ranked (Lovable→Bolt/v0→Replit/Tempo  │
│   →Cursor cleanup pass)                                  │
│ - Pieter Levels 24-72hr ugly MVP doctrine                │
│ - 200-hour scope discipline (forbid feature lists)       │
│ - Single-screen magic-moment spec (<60s)                 │
│ - Hand-off prompts for AI coding agents (Claude Code,    │
│   Codex, Cursor)                                         │
└──────────────────────────────────────────────────────────┘
        │
        ▼
┌──────────────────────────────────────────────────────────┐
│ 07 — VerdictCraft (Metrics + Kill Criteria + Hand-Off)   │
│ produces: validation_verdict.md                          │
│ - Vanity vs actionable metric audit                      │
│ - Day-zero retention as magic-moment proxy               │
│ - 10-item anti-pattern audit (Building-While-Validating, │
│   Audience-of-Friends, Praise-Mining, Waitlist-as-Proof, │
│   AI-Wrapper-Only-Moat, Vanity-Anchoring, Lost-in-       │
│   Thoughtland, Premature-MVP, Skipping-Review-Mining,    │
│   Ignoring-Day-Zero-Retention)                           │
│ - AI SaaS challenges audit (Data Gravity / API           │
│   Brittleness / Silent Churn)                            │
│ - Technical feasibility vs viability final gate          │
│ - Compliance audit (Click-to-Cancel, FTC pre-sale,       │
│   GDPR/CCPA waitlist email)                              │
│ - GO / NO-GO verdict with rationale                      │
│ - Hand-off package: onboarding-v2 chain + emotional-     │
│   design v2 chain (if GO)                                │
└──────────────────────────────────────────────────────────┘

    Stages 02 and 04 can run partial-parallel (Stage 02 outputs
    candidate ideas; Stage 04 begins pretotype design once
    Stage 03 confirms one of those ideas survives interviews).

    Stage 06 and Stage 05 can run partial-parallel (Stripe
    smoke checkout can be wired while MVP scope is finalized).
```

---

## File Catalog

| # | File | Persona | Deliverable | Lines |
|---|---|---|---|---|
| — | `00_INDEX.md` | (this file) | Chain overview + how to use | — |
| 01 | `01_psychology_biases.md` | **BiasCraft** | `bias_audit.md` (founder cognitive audit, pre-registered kill criteria, polite-lie defense, archetype alignment) | ~450 |
| 02 | `02_idea_sourcing_recon.md` | **ScoutCraft** | `idea_landscape.md` + candidate idea cards (problem journal, marketplace mining, ASO gate, Lean SEO, reverse-engineering, ACP) | ~500 |
| 03 | `03_interrogation_jtbd.md` | **MomCraft** | `interview_brief.md` + `jtbd_synthesis.md` (Mom Test script, Switch Interview, hard-commitment ladder, 10-interview synthesis) | ~500 |
| 04 | `04_pretotyping_smoke_tests.md` | **SmokeCraft** | `pretotype_plan.md` + `landing_brief.md` + `content_test_brief.md` (pretotype pick, asset stack, traffic mix, Pat Walls content-first, 3-word rule) | ~550 |
| 05 | `05_wtp_payment.md` | **PayCraft** | `wtp_validation.md` + `checkout_brief.md` (Van Westendorp, A/B pricing, pre-sales, Stripe smoke, Lou doctrine, hard paywall vs freemium) | ~450 |
| 06 | `06_mvp_execution.md` | **ShipCraft** | `mvp_blueprint.md` + `execution_prompts/*.md` (Concierge/Wizard/no-code/AI-codegen/Levels 24-72hr, 200h scope discipline, magic-moment spec) | ~550 |
| 07 | `07_metrics_kill_criteria.md` | **VerdictCraft** | `validation_verdict.md` (metrics audit, anti-pattern audit, AI SaaS challenges, compliance, GO/NO-GO + hand-off to onboarding-v2 + emotional-design v2) | ~500 |

---

## How to Use

**Sequential (default).** Run 01 → 02 → 03 → 04 → 05 → 06 → 07 in order. Each stage produces a load-bearing markdown document that the next stage consumes.

**Audit mode.** If you have a partially-validated idea, jump to whichever stage's gate you haven't met, then proceed forward. Stage 07 can audit any prior stage's output.

**Parallel option.** Stages 02 + 04 + 05 can partially overlap once Stage 01's bias audit passes and Stage 03 confirms at least one candidate idea survives interview gating.

**Hand-off downstream.** Stage 07's `validation_verdict.md` is the input to:
- `.agent/master-prompts/v2/01_emotional_discovery.md` (emotional-design v2 chain) — for the GO verdicts
- `.agent/master-prompts/onboarding-v2/01_psychology.md` (PsychCraft v2) — runs after emotional-design v2 outputs `emotional_strategy.md` + `emotional_spec.md`

So the full pipeline from raw idea to shipping app:

```
[raw idea]
  → BiasCraft 01 → ScoutCraft 02 → MomCraft 03 → SmokeCraft 04
  → PayCraft 05 → ShipCraft 06 → VerdictCraft 07
  → [if GO]
    → ClaudeDesign Onboarding v2 / StitchCraft v2 (visual design)
    → PsychCraft v2 → ClaudeDesign v2 / StitchCraft v2 → FlowCraft v2
      → OnboardBuild v2 → FunnelCraft v2 → GateCraft v2
    → Ship the app
```

---

## Research Base

All 67 research items are stored in `.agent/research/validating-app-ideas/results/*.json`. Each prompt cites items by id (e.g., "per item 21 (Walling 2/20/200)"). The research is grounded in:

- **PDF:** *Comprehensive Frameworks for App Idea Validation* (21 pages, 59 citations) — `.agent/Validating App Ideas_ A Deep Dive.pdf`
- **Videos:** Rob Walling 2/20/200 (canonical source); Pat Walls / Starter Story Build Pushscroll case study; MitaBoost 2024-2025-2026 evolution
- **Practitioners:** Marc Lou, Pieter Levels, Greg Isenberg, Justin Welsh, Adam Lyttle, Pat Walls
- **Reports:** RevenueCat State of Subs 2025/2026, Adapty State of In-App Subscriptions 2026
- **Books:** The Mom Test (Fitzpatrick), Pretotype It (Savoia 10-year anniversary), Lean Startup (Ries)
- **Frameworks:** JTBD (Christensen/Ulwick/Moesta), Van Westendorp PSM, 5PM, Forces of Progress
- **Tooling 2026:** Lovable / Bolt / v0 / Replit / Tempo / Cursor; Carrd / Tally / GetWaitlist / Beehiiv; Stripe / Stripe Atlas / Paddle / Lemon Squeezy; Sensor Tower / AppFigures / Apptweak / Mobbin / Refero
