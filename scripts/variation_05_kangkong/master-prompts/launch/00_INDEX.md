# Launch — Master Prompt Chain

A 5-stage chain of AI personas that takes a payment-validated, designed, onboarding-architected MVP and produces a complete, **2026-current**, hybrid-doctrine (Pat Walls + Marc Lou + Adam Lyttle 2026), anti-AI-slop launch — pre-launch infrastructure, App Store + Play Store submission, waitlist activation, publicity + UGC + Spark Ads, 24-72hr war room. Hands off cleanly to the (still-to-be-built) `monetize-optimize/`, `growth-marketing/`, and `retain/` chains.

> **The Spine.** A 3-track decision tree picks the founder's launch path:
> - **Track A (Marc Lou audience-leveraged)** if founder has >1k followers in any channel — Twitter-first + PH supplement + cross-post to HN/Reddit + $6K-in-48hr benchmark.
> - **Track B (Pat Walls content-first)** if magic moment is screen-recordable + 3-word-rule passes — pretend product exists → TikTok demo until viral hit (≥50K views with build-this comments) → 5-day MVP sprint → launch (Pushscroll $30K/mo pattern, Cal AI $40M ARR pattern).
> - **Track C (Adam Lyttle 2026)** if mobile + niche keyword sweet spot + post-June-2025-ASO-nerf reality — ASO foundation + Apple Search Ads day-of-approval ($66/wk exact-match → search-suggestion-slot hijack) + viral mechanics built INTO the app + Meta paid flywheel + sustained 90-day download velocity (not 72hr burst).
>
> Kill gates between each path. Mid-cycle switch allowed if signal doesn't manifest in first 7 days.

> **2026 currency.** Apple App Review delays Mar 2026 (7-30 days vs 24-48h normal — submit binary 10+ days pre-launch). Privacy Manifests mandatory (auto-reject if missing). Cal AI April 2026 §5.4 metadata crackdown for AI-health apps. Apple Guideline 3.1.2 toggle-paywall ban (2026-01). FTC Click-to-Cancel (2025-07-14). EU DFA Q4 2026 draft dark-pattern audit. Google Play Target API 36 (Aug 31 2026 deadline). Closed Testing 12-tester / 14-day gate. RevenueCat 2026: hard paywalls 5x trial conversion (10.7% vs 2.1% by Day 35); iOS = 77% of new sub-app launches. Adapty 2026: weekly+3-day-trial = $49.27 / 12mo LTV; 636% LTV gap worst-vs-best paywall. TikTok Spark Ads 69% more conversions / 30-40% lower CPA. UGC creator rates 2026: $150-350 per video. GummySearch shutdown 2025-11-30 (Reddit API revocation reshaped pain-mining). TechCrunch impersonator surge Mar 2026.

> **Solo-dev-first.** Every prescribed pattern includes `solo_dev_feasibility` (same_day / 1_week / 1_month / requires_team). Mobile + web with explicit branching per stage.

> Each prompt file is a **system prompt** you paste into a new AI conversation. Output of one stage becomes input to the next.

> **Strict chain integration.** This chain runs AFTER validating-app-ideas/, emotional-design v2/, and onboarding-v2/ chains complete. 01 LaunchCraft Mode A requires the full upstream artifact stack. Mode B (greenfield) discovery batches replicate the missing Q&A.

---

## The Chain

```
[VerdictCraft GO from validating-app-ideas/07]
  ↓ emotional-design v2 chain
  ↓ onboarding-v2 chain (PsychCraft → ClaudeDesign/Stitch → FlowCraft → OnboardBuild → FunnelCraft → GateCraft)
  ↓
┌──────────────────────────────────────────────────────────┐
│ 01 — LaunchCraft (Overall Strategy + 3-Track Decision)   │
│ produces: launch_strategy.md                             │
│ - 3-track pick (Marc Lou / Pat Walls / Adam Lyttle 2026) │
│ - Channel sequencing (PH + HN + Reddit + TikTok + X +    │
│   press + UGC + Spark Ads)                               │
│ - Timeline: T-minus-30d, T-minus-10d (binary submit),    │
│   T-minus-1d, launch hour 0, hours 1-6, 6-24, 24-72,     │
│   T-plus-7d, T-plus-30d                                  │
│ - Mid-cycle switch criteria (when to change tracks)      │
│ - Solo-dev calibration + founder archetype voice         │
└──────────────────────────────────────────────────────────┘
        │
        ▼
┌──────────────────────────────────────────────────────────┐
│ 02 — StoreCraft (App Store + Play Store Submission)      │
│ produces: store_listing.md                               │
│ - Apple: ASO title+subtitle+100-char keywords (Lyttle    │
│   90/10 rule), Privacy Manifests audit, Mar 2026 review  │
│   queue (10-day buffer), Custom Product Pages per        │
│   acquisition source, In-App Events for keyword ranking, │
│   Apple Search Ads exact-match day-of-approval campaign  │
│ - Play: Target API 36 (Aug 31 2026), Closed Testing      │
│   12-tester/14-day gate, Listing Experiments, Data       │
│   Safety, content rating                                 │
│ - Apple §5.4 AI-health metadata audit (Cal AI Apr 2026   │
│   crackdown precedent)                                   │
│ - iOS-first vs Android+14d sequencing                    │
└──────────────────────────────────────────────────────────┘
        │
        ▼
┌──────────────────────────────────────────────────────────┐
│ 03 — WaitlistConvertCraft (Stage 04/05 → Launch-Day)     │
│ produces: waitlist_activation.md                         │
│ - Pre-built waitlist as 60%+ of PH launch-day traffic    │
│ - 200+ first-hour supporters queued                      │
│ - Stage 05 PayCraft paying-cohort onboarding sequence    │
│ - Email retention (Loops 5-emails-2-weeks, Day-0 trial   │
│   cancellation <55%)                                     │
│ - Discord + Tally Day-Zero demand capture                │
│ - Founding-member discount activation                    │
└──────────────────────────────────────────────────────────┘
        │
        ▼
┌──────────────────────────────────────────────────────────┐
│ 04 — PublicityCraft (Press + Podcast + Newsletter + UGC) │
│ produces: publicity_plan.md                              │
│ - Cold press email discipline (TechCrunch impersonator   │
│   defense Mar 2026)                                      │
│ - Podcast outreach (My First Million, Indie Hackers,     │
│   Starter Story, Lenny's, Build Your SaaS)               │
│ - Niche newsletter sponsorships (Beehiiv + SparkLoop,    │
│   sub-$500 single-blast, 5K-20K subs > 100K generalist)  │
│ - Influencer/Micro-creator UGC pipeline (Mau Baron       │
│   pattern: $150-350/video, 10-30 creators, top 10%       │
│   → Spark Ads)                                           │
│ - TikTok Spark Ads (69% more conversions, 30-40% lower   │
│   CPA)                                                   │
│ - Marc Lou Twitter-first launch thread                   │
└──────────────────────────────────────────────────────────┘
        │
        ▼
┌──────────────────────────────────────────────────────────┐
│ 05 — LaunchDayWarRoomCraft (24-72hr Runbook + Dashboards)│
│ produces: launch_day_runbook.md                          │
│ - Stack: Sentry + Crashlytics + LaunchDarkly/Unleash     │
│   killswitch + RevenueCat live + PostHog + PocketHog     │
│ - 24-72hr runbook: <30min comment reply, hotfix templ.,  │
│   double-shift schedule (US PST + EU/IN co-pilot)        │
│ - Real-time dashboard: signups/min, source breakdown,    │
│   AI_plan_reveal_completed, paywall_views, crash-free %, │
│   1-star alerts                                          │
│ - Negative-feedback playbook (acknowledge → DM → fix     │
│   → public reply with screenshot)                        │
│ - 10-item launch anti-pattern audit (constitutional      │
│   refusal list — item 53)                                │
│ - Founder burnout mitigation                             │
│ - Hand-off to monetize-optimize/, growth-marketing/,     │
│   retain/ chains                                         │
└──────────────────────────────────────────────────────────┘

Stages 02, 03, 04 can run partial-parallel after 01 locks
the track. Stage 05 is the launch-day execution layer that
inherits from all prior stages.
```

---

## File Catalog

| # | File | Persona | Deliverable | Lines |
|---|---|---|---|---|
| — | `00_INDEX.md` | (this file) | Chain overview + diagram + research base | — |
| 01 | `01_launch_strategy.md` | **LaunchCraft** | `launch_strategy.md` (3-track decision tree, channel sequencing, timeline, mid-cycle switch) | ~500 |
| 02 | `02_store_listing.md` | **StoreCraft** | `store_listing.md` (Apple 2026 + Play 2026 + Privacy Manifests + ASO + Apple Search Ads + Custom Product Pages + Apple §5.4 audit + iOS-first sequencing) | ~550 |
| 03 | `03_waitlist_activation.md` | **WaitlistConvertCraft** | `waitlist_activation.md` (Stage 04/05 → launch-day, 200+ first-hour supporters, email retention, Day-Zero demand capture) | ~400 |
| 04 | `04_publicity_outreach.md` | **PublicityCraft** | `publicity_plan.md` (press + podcast + newsletter + influencer/UGC + Spark Ads + Marc Lou Twitter-first) | ~500 |
| 05 | `05_war_room_runbook.md` | **LaunchDayWarRoomCraft** | `launch_day_runbook.md` (war-room stack, 24-72hr runbook, real-time dashboard, negative-feedback playbook, 10-item anti-pattern audit, founder burnout mitigation, downstream hand-off) | ~600 |

---

## How to Use

**Sequential (default).** Run 01 → 02 → 03 → 04 → 05 in order. Each stage produces a load-bearing markdown document that the next stage consumes.

**Strict chain integration.** Mode A requires the full upstream artifact stack from validating-app-ideas + emotional-design v2 + onboarding-v2 chains:
- `bias_audit.md` (Stage 01 BiasCraft)
- `idea_landscape.md` (Stage 02 ScoutCraft)
- `jtbd_synthesis.md` (Stage 03 MomCraft)
- `pretotype_plan.md` + `landing_brief.md` + `content_test_brief.md` (Stage 04 SmokeCraft)
- `wtp_validation.md` + `checkout_brief.md` (Stage 05 PayCraft)
- `mvp_blueprint.md` + `execution_prompts/*.md` (Stage 06 ShipCraft)
- `validation_verdict.md` (Stage 07 VerdictCraft — must be GO)
- `emotional_strategy.md` + `emotional_spec.md` (v2 emotional-design chain)
- `onboarding_strategy.md` + `onboarding_architecture.md` + `onboarding_telemetry.md` + `onboarding_monetization.md` (onboarding-v2 chain)

**Mode A/B/C/D operating modes** (mirroring validating-app-ideas):
- **Mode A — Chained from full upstream** (best signal, fewest batches)
- **Mode B — Greenfield** (discovery batches replicate needed upstream Q&A)
- **Mode C — Audit existing launch** (diagnose what's missing)
- **Mode D — Post-flop autopsy** (Marc Lou doctrine + harvest)

**Hand-off downstream.** Stage 05's `launch_day_runbook.md` + first-72hr metrics flow into:
- `monetize-optimize/` chain (paywall A/B, pricing power, win-back, cohort monetization)
- `growth-marketing/` chain (audience, content, ads, UGC, viral, sustained ASO)
- `retain/` chain (push, email, in-app, loyalty)

So the full pipeline from raw idea to sustained revenue:

```
[raw idea]
  → BiasCraft → ScoutCraft → MomCraft → SmokeCraft → PayCraft → ShipCraft → VerdictCraft
  → [if GO]
    → emotional-design v2 chain
    → onboarding-v2 chain
    → LAUNCH CHAIN (this)
    → monetize-optimize chain
    → growth-marketing chain
    → retain chain
```

---

## Research Base

All 60 research items are stored in `.agent/research/launching-apps/results/*.json`. Each prompt cites items by id (e.g., "per item 21 (PH 12:01 AM PST timing)"). The research is grounded in:

- **YouTube sources:** Chris Raroque "Things I ALWAYS Do Before Launching New Apps" (item 1-7 infrastructure playbook); Adam Lyttle "$1.19M App Process Part 3" + "The app store is changing in 2026" (item 8-15 + 34 ASO doctrine + viral pivot); Tuomas Kivioja "My App Failed - Brutal 6 Months" (item 52 failure post-mortem genre)
- **Practitioners:** Marc Lou (ShipFast $6K/48h + Maker of the Year 2026 — items 38, 46, 58); Pieter Levels (Photo AI 0→$132K MRR — Track A reference); Pat Walls (Pushscroll $30K/mo from 1 TikTok — items 32, 59); Mau Baron (3-day AI app + UGC + Spark Ads ₹17L/mo — items 35, 42); Adam Lyttle ($1.19M App Store, 1.7M+ downloads, 2026 ASO-nerf pivot — items 8-15, 34, 54); Greg Isenberg (Late Checkout, ACP); Justin Welsh (5-12-3 audience building); Chris Raroque (4-apps 100% profitable infrastructure)
- **Case studies:** Marc Lou ShipFast (item 58); Pushscroll (item 59); Cal AI → MyFitnessPal Mar 2026 exit (item 60); Lovable $20M ARR in 2 months
- **Platform docs:** Apple Developer / App Review Guidelines / WWDC, Google Play Console, Product Hunt 2026 launch playbooks (LaunchList, innmind, dev.to iris1031, Marc Lou newsletter), Hacker News Show HN documentation
- **Reports:** RevenueCat State of Subscription Apps 2025/2026, Adapty State of In-App Subscriptions 2026, AppFigures / Apptweak / Sensor Tower / Phiture 2026
- **Compliance:** FTC Click-to-Cancel rule (2025-07-14), EU Digital Fairness Act Q4 2026 draft, Apple Guideline 3.1.2 toggle-paywall ban (2026-01), Apple §5.4 (Cal AI April 2026 crackdown), COPPA 2026-04-22 deadline, Apple Privacy Manifests, TestFlight paid-ad ban
- **Tooling 2026:** Framer + Formspark / Carrd / Lovable / Bolt / v0 (landing); PostHog / Plausible / Fathom (analytics); Canny / FeedBear (feedback); Loops / Resend / Postmark / Beehiiv (email); Sentry + Crashlytics + LaunchDarkly/Unleash (war room); RevenueCat / Adapty (mobile subscription); PocketHog (mobile dashboard); AppFigures / Apptweak / Sensor Tower / Mobbin / Refero / App Radar / ASOMobile / Astro (ASO + competitor intel); Apple Search Ads / Meta Ads / TikTok Ads / Google Ads (paid acquisition); TikTok Spark Ads (UGC scaling)
