# Onboarding Strategy — StillWaters (EXAMPLE)

> Sample artifact showing what Stage 01 (PsychCraft v2) produces. App is hypothetical: a guided meditation + journaling app for adults dealing with anxiety. Magician/Caregiver archetype, Adaptive paywall posture. Use this as a calibration reference for what your real `onboarding_strategy.md` should look like.

## 1. App Reality
- Category: Wellness / mindfulness / journaling
- Painpoint sentence: "I want to feel less overwhelmed but I keep ending each day exhausted with no time for myself."
- Identity word: **anchored** ("I am someone who is anchored, not anxious")
- Mode: Mode C — Tightly Chained (consumed `emotional_strategy.md` + `emotional_spec.md` from v2 chain)

## 2. Emotional Reality (inherited from emotional_strategy.md)
- Primary archetype: **Magician** (transformation arc; AI Reveal IS the spell; "become" language)
- Secondary archetype: **Caregiver** (gentle pacing; never urgency-led)
- Ethical posture: **Adaptive-leaning-Calm** (hard paywall at climax, but skip-button respected, no win-back manipulation, no streak-pressure tactics)
- Anti-AI-slop ban list inherited verbatim:
  - NO Inter / Roboto / system-ui — use **Cabinet Grotesk display + Manrope body**
  - NO indigo-500 / violet-500 / purple-blue gradient — use **oklch(0.62 0.18 285)** (deep indigo-violet, NOT slop indigo-500)
  - NO rounded-xl uniformly — vary: **12px on plan cards, 0px on hero photography, 999px on chips**
  - NO Lucide cube/check/lightning trinity — use **Phosphor Duotone at 24px stroke 1.5**
  - NO emoji bullets, NO generic Lottie celebration, NO toggle paywall (Apple 3.1.2 ban 2026-01)
  - Magician-specific bans: never "just" / "simply" / "easy" — these are slop fillers that collapse the transformation voice

## 3. Aha Engineering
- Aha sentence: "User realizes they can have a 60-second guided practice that's actually about THEIR specific anxiety, not generic meditation."
- Activation event: First completed guided session (3-minute breath practice)
- Aha placement: **During onboarding via AI Plan Reveal at step 11 of 13** (not waiting for first real-world use)
- AI Plan Reveal: **YES** — the LLM generates a personalized 7-day "anchor practice" plan stitching the user's identified anxiety triggers, time-of-day preference, and identity word verbatim
- LLM choice: Claude Sonnet 4.6 (frontier reasoning needed; small models produce generic output that breaks the story)
- Stitched inputs at reveal:
  1. User's painpoint sentence (verbatim) — "Because you said you 'end each day exhausted'..."
  2. User's identity word ("anchored")
  3. User's chosen practice time-of-day (e.g., "after 8pm")
  4. User's selected anxiety trigger (e.g., "work overwhelm")
- TTV target: **AI Reveal at step 11 (~6–8 min into onboarding)** — distinct from short-onboarding TTV (<60s); this is long-onboarding-TTV, where the reveal IS the activation peak

## 4. Onboarding Pattern Pick
- Primary pattern: **Story-Onboarding (Mau-Baron 5-act)**
- Reasoning: Wellness category with strong identity component; LLM-generated personalized plan is the load-bearing payoff; story-form preserves Calm/Caregiver archetype voice while building sunk-cost investment.
- Total step count: **13 screens** (compressed from 15-min Mau-Baron canonical to ~10-min for Caregiver-pacing — wellness users tolerate gentle pace, not aggressive 15-min)
- Acts:
  1. **AFFIRM** (welcome + pain validation) → bridge: "Most people are exhausted by what they carry. We're here to help you put it down."
  2. **SOCIAL_PROOF** (testimonials + 5M users) → bridge: "Now let's see how it works."
  3. **DEMO** (live 60-second breath practice INSIDE onboarding — this is the load-bearing reciprocity move) → bridge: "Now let's make it yours."
  4. **PERSONALIZE** (4 identity questions) → bridge: "Generating your plan..."
  5. **AI_REVEAL** (theatrical 5-second loader → personalized 7-day plan reveal stitching all 4 inputs)
  6. **REVIEW_PROMPT** (mid-onboarding App Store review modal at engineered peak)
  7. **PAYWALL** (side-by-side weekly+3-day-trial / annual, framed as "lock in your anchor practice")
- Live demo: **YES** — 60-second guided breath practice plays live in the demo act (real audio, not video; transcript visible for accessibility)

## 5. Questionnaire Spec
- Question count: **4** (PERSONALIZE act only; identity-led, not metric-led)
- Type mix:
  - 1 painpoint identification (chip selection from 4 anxiety triggers)
  - 1 identity confirmation ("Are you a [worrier / over-thinker / over-giver / perfectionist]?" — radio with 4 options)
  - 1 time-of-day commitment ("When do you want to practice?" — 4 chip options)
  - 1 frequency commitment ("How often?" — 4 options: 1×/day / 2×/day / weekdays / when needed)
- **No demographic questions** (age, gender, BMI not asked — Caregiver archetype + Magician transformation arc; data minimization per GDPR)
- Conversational pattern: one question per screen, big-button selection (96dp tall), thumb-zone bottom-anchored CTA
- Sequencing: painpoint → identity → time-of-day → frequency (low-friction → identity → behavioral commitment)
- Cross-step stitching at AI Reveal (step 11): 4 user inputs from steps 7–10 stitched verbatim into the plan reveal:
  - User's chosen anxiety trigger (e.g., "work overwhelm")
  - User's identity word (e.g., "over-thinker")
  - User's practice time-of-day
  - User's frequency commitment
- Progress indicator: **segmented sub-progress** ("Section 2 of 4 / Step 1 of 4") — reduces fatigue vs single 13-step bar

## 6. Hook Loop Wiring
- Trigger: TikTok Spark Ads (UGC creator-sourced) targeting anxiety/overwhelm hashtags. First 3 onboarding screens semantically mirror the ad creative archetype: testimonial-style intro from a real user.
- Action: per-screen single tap (chip selection, big-button CTA, no multi-field forms)
- Variable Reward: theatrical AI Plan Reveal at step 11 (5-second loader + full-bleed reveal); 70/25/5 confetti tier on session completion (small/medium/jackpot)
- Investment: **plan_id** persists as the user's home-screen anchor — "Day 1 of 7 of your Anchor Practice" remains visible on every subsequent screen
- Internal Trigger: evening anxiety (8pm reflection moment) → app. Day-2 push copy: "It's 8:14pm — your anchor practice is waiting. 60 seconds." (NOT "Don't lose your streak" — Caregiver archetype forbids loss-framed)

## 7. Paywall Posture
- Posture: **Adaptive (default)** — hard paywall at step 13 (no close button on first impression), but skip affordance on second mount; no win-back manipulation
- SKU structure (post-toggle-ban 2026-01, side-by-side cards):
  - **Annual + 3-day-trial: $79.99/yr** (Most Popular, default-selected)
  - **Monthly: $14.99/mo**
- Trial decision: **3-day trial** (Adapty 2026: weekly+3-day = $54.50 12mo LTV vs $7.40 without; for wellness category, annual+3-day matches Cal AI / Headspace 2024 pattern)
- Placement: **climax step 13** (after Mid-Onboarding Review at step 12)
- Win-back paywall: **YES** — fires once on dismiss, offers monthly @ 50% off first period. Compliant copy: "We made a more affordable option for you" (NOT confirm-shaming "Wait, don't go!")
- Persistent Buy-Now CTA: **ON** post-onboarding (~10-20% revenue lift per PDF)
- Localization plan (Day 0): **US-en, ES-419 (LATAM Spanish), JA-jp** at launch; FR-fr, DE-de at Day 30. Native copywriters per locale (NOT machine translation). LATAM aggressive monthly-equivalent anchoring; JP social-proof + verifiable trust badges.

## 8. Permission Ladder & Notification Schedule
- Ladder order: **push primer screen** (step 12.5 — between Review and Paywall) → soft-ask sheet → native dialog. THEN ATT (iOS, post-paywall). THEN feature-gated permissions (none required for v1).
- Push primer copy: "We'll send a single gentle reminder at your chosen time. No pressure, no streaks. You can pause anytime." (Caregiver archetype voice — NEVER use "Don't miss out!")
- Day 0 / Day 1 / Day 2 / Day 7 push schedule:
  - **Day 0**: opt-in moment after AI Reveal — "Want a single gentle reminder at [chosen time]?"
  - **Day 1** (within 24h, at user's chosen time): "It's [time] — your anchor practice is waiting. 60 seconds."
  - **Day 2** (chosen time): "Day 2 of your anchor practice. Same gentle pace."
  - **Day 7** (chosen time): "You've practiced 7 days. Your plan continues." (NOT "DON'T LOSE YOUR STREAK!")
- iOS opt-in target: 65% (vs 25% baseline without primer)
- Android opt-in target: 82%

## 9. Antipattern Audit
| # | Antipattern | Risk in this strategy | Counter |
|---|---|---|---|
| 1 | Wall-of-Text + Cognitive Overload | None — conversational pattern, one question/screen | Progressive disclosure throughout |
| 2 | Premature Authentication | None — auth deferred to post-paywall (Magic Link via Supabase) | Sign-up wall after value demonstrated |
| 3 | No-Escape Room | "Maybe later" link visible on paywall (second mount) | Persistent skip per Adaptive posture |
| 4 | Contextless Permissions | None — push primer at step 12.5 | Pre-permission soft-ask screen |
| 5 | Wasted Loading Screens | None — AI Reveal loader is theatrical | Cycling copy: "Reading your responses... Crafting your plan... Almost there..." |
| 6 | Ignored Error States | Mitigated by FSM error handling in Stage 03 | Network-flap recovery + offline fallback plan |
| 7 | Decision Paralysis | None — only 2 paywall plans (Annual / Monthly) | Hick's Law respected |
| 8 | Generic Celebration | None — Magician archetype celebration uses "transformation" language; warm OKLCH colors | Archetype-locked motion + copy |
| 9 | Toggle Paywall (BANNED 2026-01) | **CONFIRMED ABSENT** | Side-by-side card selection |
| 10 | Confirm-Shaming Close | Win-back uses "We made a more affordable option" framing | DFA-compliant |

## 10. Compliance Posture
- GDPR/CCPA data minimization: PASS — no demographic data collected; no health data beyond user-stated anxiety triggers
- COPPA (2026-04-22 deadline): App targets 18+ explicitly (mental-health adult category); App Store rating 17+. **Neutral birthdate gate at step 1**: date-of-birth picker; under-18 routes to "Sorry, this app is for adults" terminal screen (not VPC required since app excludes minors entirely).
- ATT framework (iOS): pre-permission soft-ask after paywall (Day 0 post-purchase) — "Allow tracking so we can show you the right plan options at the right time" (CMP-aligned copy)
- CMP: **Axeptio** (free tier, geo-aware) — fires on first app launch; GDPR opt-in for EU, CCPA opt-out for US-CA, "no banner" for jurisdictions without legislation
- Click-to-Cancel (effective 2025-07-14): cancellation flow: Settings → Subscription → Cancel (3 taps, mirroring 3-tap signup at paywall). Email confirmation within 24h.
- DFA Q4 2026 pre-audit:
  - Confirm-shaming: ABSENT (win-back uses neutral framing)
  - Fake urgency: ABSENT (no countdown timers)
  - Asymmetric subscribe-vs-cancel: PASS (3 taps both directions)
  - Pre-checked consent boxes: ABSENT (Axeptio enforces explicit opt-in)
  - Manipulative consent UIs: ABSENT (plain English consent copy)
  - Addictive design: streak presence — flagged minor risk; mitigated by Caregiver archetype voice ("Your plan continues" not "Don't lose your streak")
  - Dark patterns targeting minors: N/A (18+ app)

## 11. KPI Targets

| Metric | Target | Source benchmark |
|---|---|---|
| Day 0 onboarding completion | **65%** | Story-onboarding category 60–70% (Headspace 2024) |
| Day 0 paywall_viewed (% of installs) | **45%** | Adapty 2026 wellness category |
| Day 0 trial_started | **5–7%** of installs | Adapty 2026: 1.35% baseline; wellness premium |
| Day 1 retention | **48%** | Mobbin wellness benchmarks |
| Day 7 retention | **22%** | Wellness category D7 baseline |
| Day 30 retention | **14%** | Wellness category D30 |
| 12-month cohort LTV | **$32–48** | Adapty 2026 weekly+trial range; calibrated for wellness |
| Honest-signal test metric | **D30 retention WITHOUT push notifications** | Distinguishes intrinsic motivation from Hook-burnout |

## 12. Downstream Handoffs
- → **Stage 02 (design)**: 13 screen names with FSM state mapping:
  1. `affirm` (welcome + pain headline)
  2. `social_proof` (5M-user testimonial wall)
  3. `demo` (live breath practice — 60-sec audio + transcript)
  4. `personalize_q_1` (anxiety trigger chip selection)
  5. `personalize_q_2` (identity confirmation)
  6. `personalize_q_3` (time-of-day chips)
  7. `personalize_q_4` (frequency commitment)
  8. (transition) `endowed_progress` ("Crafting your anchor practice...")
  9. `ai_reveal_loader` (5-second theatrical wait)
  10. `ai_reveal_reveal` (full-bleed personalized plan)
  11. `review_prompt` (mid-onboarding review modal)
  12. `push_primer` (gentle permission soft-ask)
  13. `paywall` (side-by-side annual/monthly)
  14. `winback_paywall` (conditional, on dismiss)
  15. `home_intro` (empty-state with Day 1 of 7 anchor)
- → **Stage 03 (architecture)**: FSM state names from §6 (frozen); types per §5 stitching list
- → **Stage 06 (monetization)**: paywall posture from §7 (Adaptive); compliance posture from §10
- → **Stage 05 (telemetry)**: KPI targets from §11; experiment slate priorities (localization at Day 30)

## 13. Open Questions / Risks
- **R1 (Medium):** AI Plan Reveal cost at scale (~$0.04/user × 100K MAU = $4K/mo). Mitigation: cache by similar profiles (anxiety-trigger × identity × locale combo); reduces ~40%.
- **R2 (Medium):** Caregiver archetype voice may underperform Magician aggressive transformation framing on conversion. **Recommendation:** A/B test post-launch (Stage 05 experiment slate priority 6).
- **R3 (Low):** Streak surface in Day-7 push could feel like guilt mechanic. **Mitigation:** explicit copy review with archetype voice check; emphasize "Your plan continues" framing.
- **R4 (High):** WCAG 2.2 audit for live audio breath practice (demo act) — must include synced transcript + skippable affordance. Stage 02 design prompts must enforce.
- **R5 (Low):** App Store review may flag "anxiety" terminology — mental-health apps face elevated review scrutiny. Add `Notes for Reviewer` calling out 18+ adult target + clinical-disclaimer copy.

---

> Generated 2026-05-08 via PsychCraft v2 (onboarding-v2 chain stage 01).
> Inputs: emotional_strategy.md (Magician/Caregiver archetype, Adaptive-leaning-Calm posture, anti-AI-slop ban list), emotional_spec.md (OKLCH ramps, Cabinet Grotesk + Manrope, spring 200/18/1 motion).
> Next: Stage 02 (design) → Stage 03 (architecture) → Stage 04 (implementation) → Stage 05 (telemetry) + Stage 06 (monetization+compliance) in parallel.
