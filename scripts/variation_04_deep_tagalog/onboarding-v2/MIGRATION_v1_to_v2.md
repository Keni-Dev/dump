# Migrating from Onboarding v1 to v2

> Apply this when an app's onboarding was built with `.agent/master-prompts/onboarding/` (v1) and you want to upgrade to v2 — or when auditing any existing app for 2026 compliance.

---

## Critical 2026 Audit (do this FIRST, before anything else)

Run these 4 audits on the existing app. **Each one is App Store rejection or regulatory risk if failed.**

### 🚨 Audit 1 — Apple Toggle-Paywall Ban (effective 2026-01)

**Check:** Open existing paywall. Is there a "Free trial enabled" toggle / switch above the CTA?

| Result | Action |
|---|---|
| ✅ No toggle, side-by-side cards or timeline transparency | Pass — no migration needed for 3.1.2. |
| 🚨 Toggle present | **CRITICAL:** App Store rejection on next submission, 100% probability. Migration required before any update can ship. Run Stage 06 (GateCraft v2) Audit Mode immediately. |

**Migration path:**
1. Replace toggle with side-by-side cards (Annual + 3-day-trial as default-selected "Most Popular"; Monthly as alternative).
2. OR replace with explicit timeline transparency: single CTA + sub-headline `Day 1 today: Free. Day 4: billed $79.99/yr. Cancel anytime in Settings.`
3. Update `RevenueCat Paywalls SDK` config: `compatibility.min_paywall_version = 2`; `display_options.template = 5`.
4. Test on TestFlight production-like build (NOT sandbox-only).
5. Submit with `Notes for Reviewer` calling out the 3.1.2 compliance choice.

### 🚨 Audit 2 — COPPA Compliance (deadline 2026-04-22)

**Check:** Does the app:
- (a) target users under 13?
- (b) have a "mixed audience" (general consumer with no age restriction)?
- (c) collect persistent IDs, biometric, geolocation, or behavioral/inferred data?

| Combo | Action |
|---|---|
| Pure 18+ (App Store rated 17+ or 18+) | Pass — no COPPA exposure. |
| Mixed audience + asks "Are you 13+?" boolean gate | **CRITICAL:** Non-compliant under amended COPPA Rule (April 2025). Replace with neutral birthdate gate by 2026-04-22. |
| Mixed audience + collects expanded "personal information" types | **HIGH:** All collection of behavioral/inferred data on under-13s requires verifiable parental consent (VPC). Disney $10M FTC settlement Dec 2025 sets enforcement tone. |

**Migration path:**
1. Replace boolean age gate with date-of-birth picker (neutral).
2. If under-13 detected, route to VPC flow (PRIVO / KidsXP / SuperAwesome).
3. Audit telemetry — disable behavioral profiling events for under-13 cohorts.
4. Update Play Data Safety form + App Store privacy declarations.

### 🚨 Audit 3 — FTC Click-to-Cancel Symmetry (effective 2025-07-14)

**Check:** Count taps from app launch to:
- (a) starting a paid subscription (signup path)
- (b) canceling that subscription (cancel path)

| Symmetry | Action |
|---|---|
| Cancel ≤ signup taps | Pass — symmetric. |
| Cancel > signup taps | **HIGH:** FTC + state law violation. Re-architect cancellation. |

**Migration path:**
1. Add `Settings → Subscription → Cancel` deep link (top-level).
2. Remove confirm-shaming double-confirms ("Are you sure?", "What about your streak?").
3. Email + in-app confirmation within 24h.
4. NY/CA also tightening — cover multi-state compliance.

### ⚠️ Audit 4 — EU Digital Fairness Act Pre-Audit (Q4 2026 draft)

**Check this matrix:**

| Practice | Present in your app? | Required action |
|---|---|---|
| Confirm-shaming exit ("Are you sure you want to give up on yourself?") | Y/N | Replace with neutral "Maybe later" / "Continue free". |
| Fake urgency (countdown timers) | Y/N | Real expirations only OR no countdown. |
| Asymmetric subscribe-vs-cancel | Y/N | Mirror onboarding signup flow (see Audit 3). |
| Pre-checked consent boxes | Y/N | All defaults off; explicit opt-in only. |
| Manipulative consent UIs (double-negatives) | Y/N | Plain English. |
| Streak loss-aversion targeting minors | Y/N | UK AADC + CA AADC compliance + parental controls. |

Mark items with present-pattern as `legal_requirement_pending` priority. DFA enforces ~mid-2027.

---

## Structural Differences (v1 → v2)

| Aspect | v1 | v2 | Migration |
|---|---|---|---|
| Foundation | Pattern-first (HookCraft picks pattern) | Psychology-first (PsychCraft v2 interrogates emotional reality, then patterns fall out) | Re-run Stage 01 with v2 prompts; existing outputs from v1 are partial |
| Pattern taxonomy | One "long" pattern | **Story-Onboarding (Mau-Baron)** vs **Long-Questionnaire (Cal-AI)** as distinct peers | Re-classify your existing flow; if metrics-led → keep as Long-Quiz; if identity-led → migrate to Story-Onboarding |
| Aha engineering | Implicit | Explicit AI Plan Reveal slot at step N-1 with theatrical loader spec | Add AI Plan Reveal step before paywall if absent (Cal AI / Mau Baron pattern) |
| Emotional integration | None | Requires v2 emotional chain (`emotional_strategy.md` + `emotional_spec.md`) upstream | Run `.agent/master-prompts/v2/01_emotional_discovery.md` + `02_emotional_spec.md` first; pass artifacts into onboarding-v2 |
| Anti-AI-slop ban list | Light | Aggressive per-stage (no Inter, no indigo-500, no rounded-xl, no toggle paywall) | Audit existing screens; replace defaults with archetype-locked tokens |
| 2026 currency | Up to 2024 | Toggle ban, COPPA, Click-to-Cancel, DFA, WCAG 2.2, Liquid Glass, M3 Expressive | See 4 audits above |
| Implementation prompt files | `prompts/phase_onboarding/` | Same path; v2 prompts include explicit FSM state names + telemetry events per file | Generate fresh prompts via Stage 04; existing v1 prompts work but lack 2026 currency |

---

## Migration Workflow (full)

For an existing app:

### Step 1 — Run the 4 critical audits above.
Stop and fix any 🚨 critical immediately. Don't proceed until all are compliant.

### Step 2 — Run v2 emotional design chain if not already done.
- Open new conversation with `.agent/master-prompts/v2/01_emotional_discovery.md` (Mode D — Audit) and existing app screenshots.
- Get `emotional_strategy.md`.
- Open new conversation with `.agent/master-prompts/v2/02_emotional_spec.md` (Mode C — Audit) and current tokens.
- Get `emotional_spec.md`.

### Step 3 — Run onboarding-v2 Stage 01 in Audit Mode.
- Paste `01_psychology.md` system prompt.
- Provide: existing onboarding screenshots, current paywall config, current age gate, existing telemetry.
- PsychCraft v2 produces a gap-analysis `onboarding_strategy_v2.md` with priorities.

### Step 4 — Decide on scope.
The audit will surface 5–15 issues. Pick a scope:

- **Minimal (compliance-only):** fix toggle paywall, COPPA gate, Click-to-Cancel symmetry. ~1 week solo dev.
- **Quality bump:** add AI Plan Reveal at step N-1, theatrical loader, cross-step personalization stitching. ~2–3 weeks.
- **Full re-do:** restructure to Story-Onboarding pattern; new design with v2 emotional spec; new architecture. ~4–6 weeks.

### Step 5 — Run remaining stages incrementally.
- Stage 02 (design) for new/modified screens.
- Stage 03 (architecture) if FSM is missing or migrating to XState v5.
- Stage 04 (implementation) for new prompt files.
- Stage 05 (telemetry) to upgrade tracking plan.
- Stage 06 (monetization+compliance) — start here if compliance is the priority.

### Step 6 — Test on TestFlight production-like build.
NOT sandbox. Sandbox masks paywall timing, receipt validation latency, deep-link return.

### Step 7 — Submit with explicit compliance notes.
Apple `Notes for Reviewer`: "Side-by-side plan selection per Guideline 3.1.2 (effective 2026-01). Neutral birthdate age gate per amended COPPA Rule (compliance deadline 2026-04-22). Click-to-Cancel symmetry verified."

---

## Common v1 Patterns Worth Preserving

If your v1 onboarding has these, KEEP them — v2 inherits:

- ✅ XState FSM (already 2026-current)
- ✅ MMKV + Supabase persistence (still default)
- ✅ RevenueCat IAP (still default; consider Adapty Pro if you need higher A/B velocity)
- ✅ PostHog telemetry (still default)
- ✅ Axeptio CMP (still default)

## Common v1 Patterns to Replace

- ❌ Toggle paywall → side-by-side or timeline transparency
- ❌ Boolean age gate ("Are you 13+?") → neutral birthdate gate
- ❌ "Don't lose your streak!" loss-framed copy → archetype-aligned gain-framed copy
- ❌ Asymmetric cancel flow → 1-click cancel from Settings
- ❌ Confirm-shaming win-back → neutral "We made a more affordable option for you"
- ❌ Fake countdown timers → real expirations or no countdown
- ❌ Inter / indigo-500 / purple-blue gradient defaults → archetype-locked tokens from emotional_spec.md
- ❌ Lucide cube/check/lightning trinity → archetype-aligned icon set (Phosphor Duotone, custom, etc.)

---

## Quick-Reference: v2 Stage Map

| If you need... | Run this stage |
|---|---|
| To pick the right pattern for your category | 01 PsychCraft v2 |
| To fix toggle paywall before App Store rejection | 06 GateCraft v2 (Audit Mode) |
| To add AI Plan Reveal | 01 (define) → 03 (endpoint contract) → 04 (implement) |
| To wire step-level analytics | 05 FunnelCraft v2 |
| To migrate to XState v5 + cross-device resume | 03 FlowCraft v2 |
| To add side-by-side paywall (post-toggle-ban) | 06 GateCraft v2 |
| To bake in COPPA + Click-to-Cancel + DFA pre-audit | 06 GateCraft v2 |
| To get archetype-locked microcopy | v2 emotional chain `01_emotional_discovery.md` first, then 02a/02b |

---

## Critical Reminders

1. **Apple 3.1.2 toggle paywall ban is real and being enforced as of January 2026.** Apps with toggle paywalls are rejected within 24–72 hours of submission. This is the #1 reason to do this migration today.

2. **COPPA 2026-04-22 compliance deadline is fixed.** Disney $10M settlement (Dec 2025) sets enforcement tone. If your app has any mixed-audience exposure, address before April 2026.

3. **EU DFA is pending but forecastable.** Pre-auditing dark patterns now (~6 months ahead of enforcement) costs near-zero and de-risks 2027.

4. **Click-to-Cancel is already enforced** (effective 2025-07-14). Asymmetric cancellation flows have already triggered FTC actions.

5. **The toggle-paywall replacement is also a conversion win.** Adapty 2026: side-by-side cards convert 1.35% (highest of any placement); toggle paywalls were ALREADY underperforming on most metrics. Compliance + conversion both win.
