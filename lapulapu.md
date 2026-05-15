# Asset Strategy: Kleeve

> Asset-level contract produced by AssetCraft Strategy (stage 04), inheriting locks from `emotional_strategy_kleeve.md` (stage 01) and `emotional_spec_kleeve.md` (stage 02). Single source-of-truth for asset inventory, mascot decision, 3D appetite, sound posture, free-tool stack, illustration style guide, and anti-slop ban list. Downstream stages — `05_asset_production.md` (per-asset workflows + prompt templates) and `06_appstore_assets.md` (store + preview video) — consume this verbatim.
>
> **AI-illustration policy (founder override, locked 2026-05-13):** Founder has Google Nano Banana Pro (Gemini 3 Pro Image, Nov 2025) — a "Thinking" image-gen model with state-of-the-art character consistency, high-fidelity text rendering, and deep prompt reasoning. The blanket AI-illustration ban from emotional_spec §9 is **LIFTED** for Kleeve, conditional on **disciplined production-brief prompting** (NOT tag-soup), explicit anti-slop counter-prompts in every generation, mandatory hand-refinement in Figma/Inkscape, and final Skia port for mascot scenes. AI is now the **moodboard + first-draft** layer; Skia + SVG remain the **production-output** layer. Generic AI-slop tells (smooth-gradient blob illustration, melted faces, six-fingered hands, AI-smile dead eyes) remain BANNED — the discipline is in the prompt, not in tool avoidance.

---

## 0. Inheritance from Upstream Specs

- **Primary Archetype:** Jester
- **Secondary Archetype:** Everyman
- **Ethical Posture:** Adaptive — Calm-Tech defaults on surveillance/notifications, Engagement-Aware with consent rails on streaks/social/real-money
- **Distinctiveness Posture:** Distinctive-but-tasteful with AGGRESSIVE anti-slop ban-list enforcement
- **Type Pairing (locked):** Bricolage Grotesque (display) · Plus Jakarta Sans (body) · JetBrains Mono (mono/timer)
- **Brand OKLCH:**
  - Primary: `oklch(0.75 0.10 25)` — `#EDA597` (warm-blush-coral, mascot-anchored)
  - Accent: `oklch(0.62 0.18 65)` — `#C2701D` (sunset-orange, milestone)
  - Paper: `oklch(0.96 0.025 85)` — `#FAF1E0` (warm-near-white)
  - Ink: `oklch(0.18 0.02 270)` — `#1F1F26` (soft warm ink)
  - Streak-break: `oklch(0.45 0.12 30)` — `#80513A` (warm-deepened-clay, NEVER red)
- **Motion Personality (locked):** soft-spring physics (damping 0.7–0.85, stiffness 100–220, mass 1.0). React Native Reanimated 3 on RN, React Native Skia for mascot scenes + particle systems, Framer Motion on web. **Lottie / Rive / GSAP are BANNED** — code-driven motion only.
- **Sound Posture (locked):** Signature-only — 3 sonic moments (start 120ms, submit 180ms, milestone 600ms). CC0-sourced + Audacity-edited at v1.0. Audio OFF by default.
- **Visual Ban List (inherited):** Inter, Roboto, Arial, Geist-as-default, indigo-500, violet-500, purple-blue gradient, default Tailwind palette as primary, pure black/white, red as urgency, `rounded-xl` everywhere, `max-w-7xl`, Lucide trinity (`Box`/`CheckCircle`/`Zap`), emoji bullets in chrome, `hover:scale-105`, `animate-pulse`, `transition-all`, stock photos (diverse-team-on-laptops, hands-on-keyboard, glassy 3D blobs), AI-generated illustration, shadcn defaults, centered-hero + three-column-feature-grid, Tailwind UI Catalyst paste, Lovable/v0/Bolt default scaffolds.
- **Load-bearing constraint:** mascot is ALREADY in the build at `apps/mobile/assets/mascot/` as hand-authored Skia primitives. The brand color was re-anchored to match mascot art, not the other way round. The mascot is the highest-leverage asset and is non-negotiable.

---

## 1. Asset Inventory

| Asset Type | Required? | Priority | Format | Source / Tool | Anti-Slop Notes |
|---|---|---|---|---|---|
| **App icon (iOS)** | Yes | P0 | PNG 1024×1024, alpha-free (iOS) + alternate icons set | Figma (compose) → export PNG | Mascot-anchored portrait at warm-paper background. NOT generic AI face. NOT initials-on-gradient. Liquid Glass icon variant: layered specular highlight (see §10 platform note). |
| **App icon (Android)** | Yes | P0 | Adaptive icon: foreground PNG 432×432 (108dp safe area) + background color or PNG | Figma → export adaptive layers | M3 adaptive themable monochrome variant (Android 13+) also exported. |
| **Splash / Launch** | Yes | P0 | iOS Storyboard (`SplashScreen.storyboard` via `expo-splash-screen`) + Android 12+ system splash (`SplashScreen` API with icon + window background) | Native + mascot blink animation (Skia, runtime) | NOT a static centered-logo-on-white. Mascot blinks-and-waves within 320ms of cold start (Reanimated 3 + Skia). Background = `--c-paper` `#FAF1E0`. |
| **Mascot Skia primitives** | Yes | **P0** | TypeScript `.tsx` files exporting `@shopify/react-native-skia` scenes | Figma (pose authoring) → Inkscape (path cleanup) → manual port to Skia primitives | Six states: `mascot-base.tsx`, `mascot-submit.tsx` (with checkmark-draw path), `mascot-shrug.tsx`, `mascot-confetti.tsx`, `mascot-celebration.tsx`, `mascot-streak-break.tsx`. NO chibi proportions, NO Duo-derivative, NO 3D, NO AI-generated. |
| **8 preset mascot avatars** | Yes | P0 | Skia composable scenes (avatar variant series) | Figma variants → Skia ports | Hue + texture variation across the 8 avatars. If avatars span beyond coral, extend palette with `--c-mascot-avatar-{1..8}` tokens (Open Question §11.2 in spec). |
| **Sticker / accessory layer** | Yes | P1 | Skia primitives composed per `profiles.mascot_state` JSON column | Figma authoring → Skia | Hats, journal items, small badges earned via streaks. Composited at render time — no extra image assets bundled. |
| **Web mascot hero (SVG)** | Yes (marketing site) | P1 | SVG (single hero pose at v1.0) | Inkscape OR Figma → SVG export, hand-optimized | Asymmetric editorial hero, ~520px scale on desktop. Optimized via SVGO (no metadata bloat). |
| **Empty state illustrations** | Yes | P1 | SVG | Inkscape / Figma → SVG | Each empty state is a mascot-pose variant (NOT generic Storyset character). States: no-group-yet, group-thread-day-1, empty-history, no-friends-online. |
| **Error state illustration** | Yes | P2 | SVG | Inkscape / Figma → SVG | Single mascot-shrug variant covers all error states. Pairs with dryly-honest microcopy. |
| **Onboarding visuals** | Yes | P1 | SVG + Skia (boot-loaded) | Inkscape / Figma → SVG export; Skia for animated moments | Numerical hierarchy `01.` `02.` `03.` replaces icons. Mascot pose per step (4 steps). NO three-step-with-icon-grid. |
| **Achievement / celebration scenes** | Yes | P1 | Skia particle system (NOT Lottie file) | Code-authored in React Native Skia | 24-particle confetti, `accent-400/500/600` + `primary-300/400`, gravity 0.8, lifetime 800ms, staggered emit (per emotional_spec §4 signature move #1). |
| **Streak-break recovery illustration** | Yes | P1 | Skia scene | Code-authored | Mascot-streak-break state + soft-wave gesture, warm-deepened-clay surface texture. |
| **Phosphor Duotone icon set** | Yes | P0 | `@phosphor-icons/react`, `phosphor-react-native` packages | Imported via npm | Duotone weight only — NOT regular/bold. Size scale 16/20/24/32. NOT Lucide. |
| **3D hero element** | **NO** | — | — | — | **Locked NO.** Banned in spec §9 (glassy 3D blobs forbidden). 2D-only commitment. |
| **Sonic logo (`kleeve_start.mp3`)** | Yes | P2 | MP3 128kbps mono, 120ms, <8KB | Pixabay/Freesound CC0 source → Audacity edit | Soft warm bell-ping, single ~G4. Original or CC0 — NOT default ElevenLabs voice, NOT stock cinematic. |
| **Submit chime (`kleeve_submit.mp3`)** | Yes | P2 | MP3 128kbps mono, 180ms, <8KB | CC0 source → Audacity | Two-note ascending ~C5→E5, soft attack. |
| **Milestone chime (`kleeve_milestone.mp3`)** | Yes | P2 | MP3 128kbps mono, 600ms, <8KB | CC0 source → Audacity | Three-note ascending ~C5→E5→G5 + brief sparkle layer. NOT generic uplifting lo-fi. |
| **Milestone haptic (`kleeve_milestone.ahap`)** | Yes | P2 | AHAP JSON (Core Haptics) | Hand-authored JSON (per emotional_spec §5) | Custom 3-event transient pattern with rising intensity (0.6 → 0.8 → 1.0). Android fallback via `VibrationEffect.createWaveform`. |
| **App Store screenshots (iOS)** | Yes | P0 (pre-submit) | PNG per iPhone screen-class (6.7", 6.1", 5.5") + iPad (12.9") | Figma device-frame mockups → exported screen recordings + brand-layer composite | Mascot-led narrative. NOT generic-feature-grid screenshot pattern. Warm-paper background, dryly-honest copy overlay in Bricolage Grotesque. See 06. |
| **Play Store screenshots (Android)** | Yes | P0 (pre-submit) | PNG 1080×1920 (phone) + 1080×1920 (tablet) | Figma + screen recordings | Same mascot-led narrative, M3 Expressive chrome respected in frames. |
| **App preview video (iOS)** | Optional | P1 | MP4, 15–30s, per Apple App Preview specs (1080×1920 portrait) | iOS Simulator screen recording → DaVinci Resolve edit + mascot-as-end-card | NO centered-text-with-cinematic-music cliché. NO stock cinematic riser. End card uses the milestone chime. |
| **Promo video (Play)** | Optional | P2 | YouTube link (per Play Console spec), 30s | Same source as iOS preview, CapCut compose | — |
| **Marketing landing hero (web)** | Yes | P1 | SVG mascot + warm-paper background | Inkscape → Next.js `public/illustrations/` | Asymmetric 60/40 split, mascot left, copy right. Risograph grain via SVG `<feTurbulence>` at 6% opacity. |
| **OG / social cards** | Yes (marketing) | P2 | PNG 1200×630 (Open Graph) + 1200×600 (Twitter/X) | Figma → PNG export | Asymmetric mascot left + dryly-honest copy right. NOT centered-logo-on-gradient. |
| **Risograph grain texture (web)** | Yes | P2 | SVG `<feTurbulence>` filter inline | Hand-authored SVG filter | 5–8% opacity overlay on `paper-elevated` surfaces and streak-break surfaces only. NOT on body-text surfaces (legibility kill). |
| **Favicon set** | Yes | P1 | 16/32/48/180 ICO/PNG, plus `apple-touch-icon` 180×180, plus `safari-pinned-tab.svg` | Figma → favicon generator (RealFaviconGenerator self-hosted) | Mascot bust crop, same warm-paper background. |

**Out of scope at v1.0:**
- AI-generated illustration of any kind (mascot, hero, supporting art, marketing photography) — banned in spec §9.
- 3D hero element of any kind — 2D-only commitment.
- Lottie / Rive animation files — code-driven motion only.
- Stock photography (including diverse-team-on-laptops, hands-on-keyboard, etc.) — zero photography across product + marketing.
- Curated content bundle illustrations (deferred to v1.1+ if introduced).

---

## 2. Mascot Decision

### Decision: **LOCKED YES**

### Mascot Name: **Klee**

Derived from the "Kleeve" stem (Klee + ve); also German for "clover" — a small incidental association with luck/friendship that maps cleanly onto the friend-group-accountability product premise without being load-bearing. Short, easy to say aloud in friend-text-message cadence ("Klee did the thing"), one syllable, no ESL pronunciation friction. Use the name consistently in microcopy where the mascot speaks, in dialogue bubbles, in character-bible references, and as the character anchor in every Nano Banana Pro generation prompt.

- **Justification:** Mascot is already load-bearing in the build (Skia primitives shipping in `apps/mobile/assets/mascot/`), the brand-anchor color was sampled from the mascot art (`oklch(0.75 0.10 25)`, not the other way around), and Jester+Everyman archetype is a strong-fit mascot pair (mascot is the highest-leverage Jester signal). The three signature motion moves all depend on the mascot existing — removing it would collapse the brand strategy. Spec §13.3 explicitly locks this.
- **Personality (5 traits):**
  1. **Warm** — never sharp, never owl-judgmental; soft posture even when delivering a streak-break shrug
  2. **Dryly-honest** — acknowledges the miss (`"shake it off"`) without guilt-tripping
  3. **Curious-not-coach** — looks-with-you, never coaches-at-you
  4. **Tactile** — has hand-drawn imperfection (deliberate 1px CMYK-misregistration on sticker overlay)
  5. **Quietly-celebratory** — small joy on submit (~480ms checkmark-draw), bigger joy on milestone (confetti) — never over-celebrates
- **Archetype embodiment:** Jester (primary, in expression range) + Everyman (in body proportion — accessible, not idealized, not aspirational)
- **Body proportions (cuteness-tuned 2026-05-13):** Head-to-body ratio approximately **1:1.2** — pillow-shaped silhouette, taller-than-wide oval with two small ear-nubs or hair-tufts on top. Slightly rounder than the original 1:1.4 spec to read as cute/huggable, still NOT default-AI-chibi 1:1, still NOT realistic 1:7. Think Molang's pillow proportion or Pusheen's tubby silhouette.
- **Cuteness mechanics (locked):**
  - **Eyes:** Soft bean-oval shapes (~8% of face height), each with a single tiny highlight dot in the upper-left of the iris. NOT anime-large. NOT multi-layer sparkle. NOT tear-drops. One highlight only.
  - **Mouth:** Simple gentle curve in neutral states. Small soft ":3" or "ω" cat-style mouth in expressive scenes (mascot-submit, mascot-confetti, mascot-celebration). NEVER "AI smile" uncanny lip curl.
  - **Cheek blush:** Subtle peach blush (small oval shape, one tone darker than body — `#E08E70` against `#EDA597` body — at ~40% opacity). Lifted from original NO-blush spec; the subtle blush is the single biggest tasteful-cute upgrade and a Sanrio/Tarepanda signature.
  - **Paws:** Short rounded mitten-shapes with three subtle toe-bumps each (no individual fingers — anti-six-fingered-AI tell preserved).
  - **Silhouette:** Pebble / clover-tuft / pillow body, soft rounded silhouette, vaguely creature-like but NOT a specific real animal (NOT a bird, NOT a fox, NOT a cat).
- **Color palette (mascot core):** `--c-primary-500 #EDA597` (body), `--c-primary-400 #EE9A8A` (one-tone-darker for blush), `--c-paper-elevated #F4E4C2` (highlight), `--c-ink-900 #1F1F26` (outline at 1.2–1.6px stroke), `--c-accent-500 #C2701D` (sticker accents only). Four colors max per scene.
- **Style descriptor (verbatim — paste into every reference / brief):**
  > "Klee is a soft pebble-shaped warm-coral creature mascot. Pillow / clover-tuft silhouette, taller-than-wide oval with two small ear-nubs on top. Head-to-body ratio 1:1.2 (cute pillow proportion, NOT default AI chibi 1:1, NOT realistic 1:7). Eyes: soft bean-oval shapes with one tiny highlight dot upper-left, NOT anime-large, NO sparkle layers, NO tears. Mouth: gentle simple curve in neutral, soft ':3' or 'ω' cat-style curve in expressive scenes. Cheeks: subtle peach blush (one-tone-darker oval, 40% opacity). Paws: short rounded mittens with three subtle toe-bumps. Outline: 1.2–1.6px hand-drawn ink, deliberately imperfect (NOT computer-perfect Bezier). Slight 1px CMYK-misregistration on sticker overlays. Risograph-zine grain at 6% opacity. Style siblings: Molang (Hye-ji Yoon 2010 — pillow simplicity, subtle blush), Pusheen (tubby rounded silhouette, expressive-through-pose), Studio Ghibli Soot Sprites Susuwatari (simple round bodies with wide expressive eyes), Tarepanda (San-X melted-relaxed cute), Adventure Time circa 2014 character economy, Mirror Studio Mexico City risograph texture. Tasteful-cute, NOT AI-cute. NOT 3D. NOT anime-derivative. NOT Duolingo Duo derivative. NOT generic Pixar-cute 3D. NOT 'AI smile' uncanny lip curl. NO gradient meshes. NO photorealism."
- **Voice (in copy):** Jester-dry, friend-text-message-cadence, occasional dry joke, NEVER coach-voice. Microcopy patterns locked in emotional_spec §7.
- **Expression range needed (v1.0):** 6 scene states (base / submit / shrug / confetti / celebration / streak-break) + 8 preset avatar variants + 4–6 sticker accessories earned via streaks.
- **Hand-off to 05 (AssetCraft Production):** Klee character bible — pose library (8 expressions, do/don't reference sheet), JSON-format Nano Banana Pro prompts using `Klee` as the explicit character-name anchor in every prompt's `subject` field (Nano Banana Pro's Thinking model uses the name as additional identity anchor across the 360° character sheet methodology — generate front + 3/4 + side + back, lock visual identity, reuse refs across all subsequent scenes/avatars), Figma/Inkscape vector refinement, final Skia primitive port for production runtime. 8-avatar variants via Nano Banana Pro character-reference reuse (same Klee identity, body-hue variants).

**Risk surfaced:** if the production mascot art (as committed in `apps/mobile/assets/mascot/`) deviates from the sampled body color, the entire brand-primary ramp re-tunes (per emotional_spec §11.1). TokenCraft owns this loop; AssetCraft confirms the mascot is the anchor, not the palette.

---

## 3. 3D Decision

### Decision: **LOCKED NO**

- **Justification:** Spec §9 explicitly bans glassy 3D blobs, AI-illustration-with-smooth-gradients, and any photographic imagery. The brand language is risograph zine + Adventure Time + Studio Ghibli — all 2D-character disciplines. 3D would introduce slop risk (default Cinema 4D cute-character look) without earning distinctiveness. Mascot-as-2D-Skia-character is the distinctive lever.
- **Tool:** N/A (no Spline / Bezi / Blender in stack)
- **Anti-slop note:** explicitly NOT isometric voxel scene, NOT glassy translucent 3D blob, NOT default Cinema 4D-style 3D character. The brand commits to 2D vector + risograph texture, period.

---

## 4. Sound Posture

### Posture: **SIGNATURE-ONLY (locked)**

Three sonic moments, no ambient sound, no UI clicks beyond the three signature sounds, no notification stings. Audio OFF by default — user opts in via Settings → Sound.

- **Sonic logo (`kleeve_start.mp3`):**
  - **Trigger:** Timer start tap (`Start timer` button)
  - **Duration:** 120ms
  - **Description:** Soft warm bell-ping, single note ~G4, slight reverb tail
  - **Tool:** Pixabay/Freesound CC0 hand-curated, OR ElevenLabs Sound Effects free tier prompt `"warm soft bell ping, single note G4, brief, 120ms, slight reverb"` — Audacity edit for exact-millisecond trim + 5ms fade-in/out + normalize to -3dB peak
- **Submit chime (`kleeve_submit.mp3`):**
  - **Trigger:** Submit confirmed (paired with `.impact(.medium)` haptic + mascot checkmark-draw)
  - **Duration:** 180ms
  - **Description:** Two-note ascending chime ~C5→E5, soft attack
  - **Tool:** Same workflow as sonic logo
- **Milestone chime (`kleeve_milestone.mp3`):**
  - **Trigger:** 7d / 30d / 100d streak milestone (paired with custom AHAP haptic + Skia confetti burst)
  - **Duration:** 600ms
  - **Description:** Three-note ascending chord ~C5→E5→G5 with brief sparkle layer
  - **Tool:** Same workflow

**Default-mute respected:** Audio OFF at install — opt-in via Settings → Sound. Auto-pause when iOS in silent mode (`AVAudioSession.Category.ambient`), Android in DND, or media volume = 0. Never plays during system audio (music, calls, voice memos).

**Anti-slop note:** explicitly NOT generic "ding" notification, NOT stock cinematic riser/whoosh, NOT AI-music with time-loop artifacts, NOT default ElevenLabs voice. CC0-sourced and hand-edited; license documented in `apps/mobile/assets/sounds/LICENSES.md` (source URL + license confirmation per chime).

**Roadmap (v1.1+, if budget):** commission sound designer to produce branded versions in single musical key (recommend C major or G major, soft synth + bell timbre) — currently the three CC0 sources are not musically related. Spec §6 Roadmap lock.

---

## 5. Free Tool Stack Commitment

**10 committed tools. Nano Banana Pro is now the PRIMARY illustration tool — first-draft generation, mood exploration, character variants — with mandatory hand-refinement in Figma/Inkscape before Skia port.** All illustration prompts MUST be JSON-format production briefs (NOT tag-soup) with explicit anti-slop counter-prompts.

| Tool | Free Tier | Purpose | Anti-Slop Discipline |
|---|---|---|---|
| **Nano Banana Pro (Gemini 3 Pro Image)** | Unlimited via Gemini Pro subscription (founder confirmed) | **PRIMARY illustration tool.** Mascot scenes (first-draft generation before vector port), 8 preset mascot avatars (via 360° character-sheet methodology + character-reference reuse), empty/error/onboarding illustrations, web hero illustration, OG card composition, App Store screenshot background composition, palette mood exploration. | **JSON-format prompts only** (production-brief style — subject + composition + style + colors + lighting + camera + style siblings + counter-prompts). NEVER tag-soup. Every prompt includes explicit `"avoid"` array with full anti-slop ban list (§8). Always generate 4–8 variants, pick least-AI-looking, hand-refine in Figma. |
| **Figma free** | 3 files (unlimited drafts inside each) | Mascot pose authoring + Nano Banana Pro output cleanup, sticker variants, screen composition for App Store mockups, app icon export, character bible reference sheet, OG card composition | Use plugins selectively (Iconify, SVG Export, Image Trace via Vectornator-style). Disable Figma AI / Adobe Firefly plugins — we control AI generation through Nano Banana Pro JSON prompts, not implicit Figma assists. |
| **Inkscape** | Free (open-source) | Path cleanup of Nano Banana Pro raster output → SVG vectorization, path simplification before Skia port, web hero SVG, empty/error/onboarding SVGs | Vector-precision tool; the bridge between AI raster output and Skia production. Trace Bitmap with edge-detection + manual node cleanup. |
| **Penpot** | Free (open-source, git-trackable) | Backup design source-of-truth if Figma 3-file limit is hit; team handoff if collaborators added | Open-source = no vendor lock; git-tracked design files survive. |
| **React Native Skia** (production runtime, in-stack) | Free | Final mascot scene primitives + confetti particle system + animations at runtime | NOT a "design tool" but the final output target. Mascot ports from refined SVG to Skia paths via `react-native-svg-transformer` or manual `<Path>` definitions. |
| **Audacity** | Free (open-source) | Sound editing — millisecond trim, fade-in/out, normalize-to-peak | Use for ALL 3 chime edits + license-audit metadata. |
| **Pixabay / Freesound (CC0)** | Free | CC0 sound sourcing (warm bell, soft chime, sparkle layers) | Source-of-truth for sound; document URL + license in `LICENSES.md`. |
| **ElevenLabs Sound Effects** | Free 10k chars/mo | Text-to-SFX fallback if CC0 sources can't deliver exact tone for any of the 3 chimes | NOT for voice (we don't use voice). NOT for music. |
| **DaVinci Resolve** | Free (professional grade) | App preview video edit (iOS preview 15–30s) + audio sync to milestone chime | NOT centered-text-with-cinematic-music cliché — narrative-driven, mascot end-card. |
| **CapCut** | Free | Quick social/marketing video, Play Store promo video, mobile-friendly export | Customize templates aggressively — NO TikTok-default trending-effect signature. |

**Why Nano Banana Pro specifically (not Imagen 4 / Midjourney / Recraft):**

- **"Thinking" reasoning model** — Gemini 3 Pro Image processes the JSON brief before generation, fixing logic errors that tag-soup prompts produce (six-fingered hands, melted features, gibberish text).
- **Character consistency via 360° sheet** — generate front + 3/4 + side + back of mascot once, then use those as character references for every subsequent pose / expression / avatar variant. Closest free-tier equivalent to LoRA training.
- **High-fidelity text rendering** — relevant for OG cards, App Store screenshots, marketing hero with overlaid copy in Bricolage Grotesque.
- **JSON prompt acceptance** — structured prompts (subject, composition, style, lighting, camera, colors, style_references, avoid) outperform natural-language prompts for consistency.
- **Founder already has Gemini Pro** — zero incremental cost.

**Tools explicitly NOT in the stack (and why):**

- **Midjourney** — paid ($10/mo), and Nano Banana Pro matches it for character consistency via 360° sheet methodology. Skip the subscription.
- **Recraft / Microsoft Designer / DALL-E** — Nano Banana Pro is the locked AI generator; multiple AI tools introduces style drift across the asset library.
- **Lottielab / LottieFiles** — Lottie format is banned (code-driven motion only per emotional_spec §4).
- **Rive editor** — banned (overkill for v1.0, code-driven motion ethic).
- **Spline / Bezi / Blender** — banned (3D-NO commitment).
- **Suno** — generic uplifting lo-fi is a slop signature; CC0 + Audacity covers the 3-chime need.
- **After Effects + Bodymovin pipeline** — produces Lottie; banned.

---

## 6. Paid Threshold

### Decision: **STAY FREE at v1.0** (Gemini Pro subscription is pre-existing, not incremental)

The stack above covers the v1.0 asset library entirely. Nano Banana Pro access via existing Gemini Pro subscription = no incremental cost. No additional subscription tools enter the budget.

**Explicit paid considerations DEFERRED to v1.1+ (one-time commissions, not subscriptions):**

| Possible Paid Item | Cost | Trigger to Reconsider | Why one-time, not subscription |
|---|---|---|---|
| **Sound designer commission** (3 branded chimes in single musical key + bonus 2 sounds for v1.1 features) | $300–800 one-time | If CC0 sources produce musically-disjointed chimes that users flag in feedback | Branded sonic identity; CC0 patchwork has a ceiling. |
| **Photography commission** (founder's friend group, candid documentary style, for marketing site only) | $200–500 one-time | If marketing site needs human imagery beyond mascot at v1.2+ | One-time; documentary not staged; mascot remains primary imagery. |
| **Illustrator commission for mascot extensions** (only if Nano Banana Pro can't deliver consistency at >24 character variants in v1.2+) | $400–800 one-time | If character consistency degrades past 24 variants and founder needs reliable extensions | Backup, not primary — Nano Banana Pro 360° sheet methodology is locked first. |

**What we DO NOT pay for:**
- ❌ Midjourney Basic ($10/mo) — Nano Banana Pro covers it via 360° character-sheet consistency
- ❌ Recraft Pro ($12/mo) — Figma + Inkscape + Skia handles vector consistency
- ❌ Adobe single-app ($23/mo) — Lottie/After Effects pipeline is banned
- ❌ Spline Pro ($9/mo) — 3D-NO commitment
- ❌ Figma Pro / team plan — 3 free files is sufficient with disciplined file architecture
- ❌ Suno / ElevenLabs paid tiers — free tier covers signature-only sound posture

**Threshold trigger:** if Nano Banana Pro JSON prompts consistently produce slop tells (six-fingered hands across 8+ generations, melted faces, smooth-gradient bodies) after 2 weeks of disciplined prompt iteration, escalate to illustrator commission ($400–800 one-time) rather than switching AI tools. The discipline is in the JSON prompt, not the tool.

---

## 7. Style Guide Extensions (asset-level)

Extends emotional_spec.md tokens with asset-specific descriptors. These paste verbatim into every brief, reference doc, and (where applicable) AI-reference exploration prompt.

### 7.1 Illustration Style Descriptor (for ALL illustration briefs)

> "Hand-drawn vector illustrations with warm risograph-zine grain texture. Color palette strictly limited to: warm-coral primary `#EDA597`, sunset-accent `#C2701D`, warm-paper `#FAF1E0` background, warm-paper-elevated `#F4E4C2` highlight surface, soft-ink `#1F1F26` outline + body text, warm-clay-deepened `#80513A` for streak-break / regret surfaces. Outline stroke width 1.2–1.6px, deliberately hand-drawn (NOT computer-perfect Bezier). Slight 1px CMYK-misregistration offset on accent overlays. Risograph grain via SVG `<feTurbulence>` at 5–8% opacity. Asymmetric composition — NEVER centered-symmetrical. Style siblings: Adventure Time circa 2014 character economy, Studio Ghibli warm pastel discipline, risograph zine print culture (Mirror Studio Mexico City reference). FORBIDDEN: gradient meshes, 3D shapes, photorealism, AI-generated faces, glassy translucent blobs, Cinema 4D-style cute characters, Storyset/unDraw/Humaaans/Open Doodles aesthetic, isometric voxel scenes, smooth-gradient AI illustration tells."

### 7.2 Mascot Style Descriptor (for mascot-specific work)

> "Soft-edge vector character. Body ratio ~1:1.4 head-to-body (NOT chibi 1:1, NOT realistic 1:7). Warm-coral `#EDA597` body, soft-ink `#1F1F26` outline at 1.2–1.6px stroke (hand-drawn, NOT computer-perfect), three-color palette per scene max. Slight 1px CMYK-misregistration on sticker/accessory overlays. Expression vocabulary: warm-curious base, quiet-celebratory submit (checkmark-draw across chest), apologetic shrug (NOT sad, NOT defeated), confetti-joy (small, contained, never over-celebratory), milestone-bigger-joy (still under control), soft-wave on streak-break (acknowledging, NOT shaming). Voice in copy: dryly-honest friend-text-message-cadence, occasional dry joke. FORBIDDEN: chibi proportions, anime-derivative (without intentional reference), Duo-derivative (green-bird-equivalent), generic 3D blob, AI-faces-with-melted-features, 'AI smile' uncanny lip curl, dead eyes."

### 7.3 Animation Easing Doctrine (extends emotional_spec §4 motion section)

- **Mascot character animation (Skia):** spring profile damping 0.70, stiffness 140, mass 1.0 → ~480ms perceived. Checkmark-draw path uses `--ease-content-enter` `cubic-bezier(0.16, 1, 0.3, 1)` (ease-out-expo).
- **Confetti particle burst (Skia):** spring damping 0.60, stiffness 160, mass 0.8 → ~800ms staggered. 24 particles, gravity 0.8, lifetime 800ms.
- **UI motion (Reanimated 3):** spring damping 0.80–0.85, stiffness 180–220, mass 1.0 per surface (full matrix in emotional_spec §4).
- **Web motion (Framer Motion):** matching spring profiles to mobile Reanimated 3 values.
- **Reduced-motion:** crossfade (200–240ms opacity) replaces spring slides; static fallback icons replace character animation; confetti suppressed entirely (per emotional_spec §4 reduced-motion table).
- **LINEAR easing is FORBIDDEN** except indeterminate progress (not present in v1.0).
- **NO Lottie, NO Rive, NO GSAP** — code-driven motion only.

### 7.4 Sound Aesthetic Descriptor

> "Warm analog-bell timbre, soft attack, slight reverb tail. Single-note or simple ascending chord progressions only. ~80–100 BPM equivalent feel. Sonic logo `kleeve_start` is the brand 'inhale' — a 120ms warm bell-ping at ~G4 that feels like 'beginning, gently.' Submit chime is a quiet confirmation, not a triumph. Milestone chime is the only sound that approaches celebration, and even then it's contained. FORBIDDEN: cinematic riser/whoosh, generic notification 'ding', AI-music with time-loop artifacts, default ElevenLabs voice, dubstep / EDM / aggressive synth stabs, default UI 'pop' / 'tap' / 'click' sounds."

### 7.5 Texture Treatment (web + spotlight surfaces only)

- Risograph-style grain noise via SVG `<feTurbulence>` filter at **5–8% opacity** (verified threshold from emotional_spec §9)
- Applied to `paper-elevated` surfaces and `streak-break` surfaces only — **NOT on body-text surfaces** (legibility kill)
- Slight 1px CMYK-misregistration offset on mascot sticker overlay (deliberate imperfection, character-coded)
- Implementation: inline SVG filter in web; on mobile, baked-in to Skia mascot scenes (not a runtime filter for performance)

---

## 8. Asset-Specific Anti-AI-Slop Ban List

Inherited from emotional_spec §0 visual ban list **PLUS** asset-specific bans below. Every brief, every reference exploration, every production prompt MUST include `"AVOID — [list]"` verbatim.

### 8.1 Illustration BANS (asset-specific)

- ❌ Generic gradient mesh hero (purple/pink/cyan blur)
- ❌ Isometric voxel city scene
- ❌ Storyset / unDraw / Humaaans / Open Doodles / IRA Design default styles (recognizable on sight)
- ✅ AI-generated illustration via Nano Banana Pro IS now permitted as first-draft layer, conditional on: JSON-format production-brief prompts (NOT tag-soup), explicit `"avoid"` array enforcing the full ban list, mandatory hand-refinement in Figma/Inkscape, mandatory Skia port for mascot scenes
- ❌ Tag-soup AI prompts ("warm cute mascot, vector style, 4k, trending on artstation") — Nano Banana Pro is a Thinking model, it rewards production-brief detail
- ❌ Shipping raw Nano Banana Pro output without Figma/Inkscape refinement — AI is moodboard + first draft, vector tools are lock-in
- ❌ AI faces with melted features / six-fingered hands / gibberish text — re-prompt with stricter `"avoid"` array, never ship
- ❌ AI illustration from non-locked tools (Midjourney / DALL-E / Stable Diffusion / Imagen 4 / Recraft / Firefly) — Nano Banana Pro is the single locked AI generator to avoid cross-tool style drift
- ❌ Glassy translucent 3D shapes
- ❌ Generic 3D blobby cute characters (Pixar-derivative without the craft)
- ❌ Smooth-gradient AI illustration tell — soft uniform blur across illustration body
- ❌ Diverse-team-on-laptops stock photography
- ❌ Hands-on-keyboard-overhead stock photography
- ❌ "Happy people using phones" Unsplash hero composition

### 8.2 Mascot BANS

- ❌ Default chibi proportions (1:1 head:body)
- ❌ Duolingo Duo derivative (green bird, similar pose, expression library)
- ❌ Generic 3D blob with default Cinema 4D materials
- ❌ Anime-derivative without intentional reference
- ❌ "AI smile" — uncanny lip curl, dead eyes
- ❌ Mascot color drifting from `#EDA597` anchor (palette is anchored TO mascot)
- ❌ Mascot expressions that read as guilt-tripping / coach-voice / passive-aggressive (Duolingo owl 2023 cautionary tale)

### 8.3 Animation BANS

- ❌ Lottie / Rive / GSAP — code-driven motion only (Reanimated 3 + Skia + Framer Motion)
- ❌ Default LottieFiles "loading dots" download
- ❌ Default LottieFiles "confetti burst" — we use Skia particle system with custom emit
- ❌ Default LottieFiles celebration / star-burst / heart-pulse
- ❌ Stock cinematic riser / whoosh on app preview video
- ❌ Fade-in-on-scroll uniformly applied (web)
- ❌ `hover:scale-105` on any card
- ❌ `animate-pulse` on any loading state — use mascot breathing loop instead
- ❌ `transition-all` — named springs per surface

### 8.4 Sound BANS

- ❌ Generic "ding" notification
- ❌ Stock cinematic riser / whoosh
- ❌ AI-music with time-loop artifacts (Suno default uplifting lo-fi)
- ❌ Default ElevenLabs voice without character
- ❌ Dubstep / EDM / aggressive synth stab
- ❌ Default UI "pop" / "tap" / "click" — sound is signature-only, NOT ambient UI feedback

### 8.5 Iconography BANS (reinforced from emotional_spec)

- ❌ Lucide `Box` / `CheckCircle` / `Zap` trinity — banned everywhere, especially marketing
- ❌ Heroicons as primary
- ❌ Phosphor non-Duotone weights (regular / bold) — Duotone only
- ❌ Emoji bullet section headers (🚀 ✨ ⚡ 🔥 💡 🎯 🛡️ ✅ 🎨 🤖 ❤️)

### 8.6 App Store / Marketing BANS

- ❌ Centered-text-with-cinematic-music app preview cliché
- ❌ Logo cloud "trusted by 1000+ teams" (we don't have those teams and the pattern IS the signature)
- ❌ Three-column feature grid with icons + headlines + subcopy
- ❌ Generic gradient background OG/social cards
- ❌ Stock-photo App Store screenshot frames
- ❌ Vercel-clone / Linear-clone / shadcn-default marketing landing

---

## 9. Workflow Sequencing & Time Budget

### Recommended order (P0 first, P2 last):

**Week 1 — Foundation (P0 unblocks everything downstream)**
1. **Mascot Skia primitives (6 scene states)** — Figma pose authoring → Inkscape SVG cleanup → manual Skia path port. *2.5–3 days.*
2. **8 preset mascot avatars** — Figma variants → Skia ports. Re-tune palette ramp if avatars span beyond coral. *1.5–2 days.*
3. **Sticker / accessory layer** — Figma authoring → Skia primitives composed per `profiles.mascot_state`. *1 day.*
4. **App icon (iOS + Android adaptive)** — mascot bust crop, Figma compose, export. *0.5 day.*
5. **Splash screen** — iOS Storyboard + Android 12+ system splash + mascot blink animation (Skia at runtime). *0.5 day.*

**Week 2 — Surface assets (P1)**
6. **Empty state SVGs (4 states)** — Inkscape, mascot-pose-variant per state. *1 day.*
7. **Error state SVG** — mascot-shrug, single asset, reused. *0.5 day.*
8. **Onboarding visuals (4 steps)** — numerical hierarchy + mascot pose per step. *1 day.*
9. **Streak-break recovery scene (Skia)** — mascot-streak-break + soft-wave + warm-clay texture. *0.5 day.*
10. **Phosphor Duotone integration + size scale** — npm install + tokenize sizes (16/20/24/32). *0.25 day.*

**Week 3 — Signature moments & sound (P1–P2)**
11. **Confetti particle system (Skia)** — 24 particles, accent + primary colors, staggered emit. *1 day.*
12. **Checkmark-draw path animation (Skia)** — path-drawing across mascot chest, ease-out-expo. *1 day.*
13. **Group thread presence pulse (Reanimated 3)** — radial coral pulse, 1200ms breathing cycle. *0.5 day.*
14. **3 sonic chimes** — Pixabay/Freesound CC0 sourcing + Audacity edit + LICENSES.md audit. *1 day.*
15. **Milestone AHAP haptic** — hand-authored JSON + Android fallback waveform. *0.25 day.*

**Week 4 — Store + marketing (P0 store, P1–P2 marketing)**
16. **App Store screenshots (iOS, 5–8 per device class)** — Figma device frames + screen recordings + brand-layer composite. *2 days. Forward to 06.*
17. **Play Store screenshots (Android)** — same source, M3 frames. *0.5 day.*
18. **App preview video (iOS)** — Simulator screen recording → DaVinci Resolve edit + milestone chime end-card. *1.5 days.*
19. **Marketing landing hero (web SVG mascot)** — Inkscape → SVG export → Next.js public folder. *0.5 day.*
20. **OG / social cards** — Figma → PNG 1200×630. *0.5 day.*
21. **Favicon set** — Figma → favicon generator → multi-size export. *0.25 day.*

**Total estimated time budget (solo dev, zero design skill, full v1.0 asset library, Nano Banana Pro accelerated):**

- **Mascot YES (locked) + 8 avatars + sticker layer + risograph illustration discipline:** ~**2–2.5 weeks** of focused asset work (Nano Banana Pro 360° sheet generation cuts mascot foundation from 5 days to 2 days; vectorization + Skia port unchanged)
- **Plus app store + preview video:** +0.5 week
- **Plus marketing landing assets:** +0.5 week
- **Realistic total: 3–3.5 weeks** if asset work is the only thing happening
- **Realistic total: 6–7 weeks** if asset work parallels feature development (the actual case)

**Time-budget red flags:**
- If Nano Banana Pro consistently produces slop tells (six-fingered hands, melted faces) after 8+ disciplined-JSON-prompt iterations, escalate `"avoid"` array stricter OR fall back to manual Figma authoring (slower but reliable).
- If mascot Skia port is taking >0.5 day per scene after vectorization, consider shipping SVG-rendered (`react-native-svg`) instead of native Skia primitives for non-critical scenes (mascot-base + mascot-submit stay native Skia for performance; shrug/streak-break can be SVG).
- If sonic chimes are taking >1.5 days because CC0 sources don't deliver, escalate to ElevenLabs Sound Effects free tier with explicit prompt (NOT generic stock-cinematic).
- If app preview video is taking >2 days, simplify to single-screen mascot end-card with chime — the Apple App Preview spec doesn't require a narrative.

### Maintenance plan (post-launch, ongoing)

- **Asset additions** for new features (v1.1+) follow the same workflow: Figma → Inkscape → Skia port for mascot work; Figma → SVG export for illustrations; CC0 source → Audacity for new sounds.
- **Style guide governance:** §7 above is the contract. Every new asset is reviewed against §7.1 and §7.2 verbatim before commit.
- **Naming convention:** `<asset_type>-<purpose>-<state>-<format>.ext` (e.g., `mascot-celebration-7d-skia.tsx`, `illustration-empty_state-no_group-svg.svg`, `sound-chime-milestone-mp3.mp3`)
- **Folder structure (mobile):**
  - `apps/mobile/assets/mascot/` — Skia primitives + sticker layer
  - `apps/mobile/assets/illustrations/` — SVG empty/error/onboarding
  - `apps/mobile/assets/sounds/` + `LICENSES.md`
  - `apps/mobile/assets/haptics/` — AHAP files
  - `apps/mobile/assets/icons/` — app icon variants
- **Folder structure (web):**
  - `apps/web/public/illustrations/` — SVG hero + OG cards
  - `apps/web/public/sounds/` — (none at v1.0, web is silent)
  - `apps/web/public/favicons/`
- **Reference folder (NEVER ship):** `references/` at repo root — AI mood exploration, palette references, character bible reference sheets. `.gitignore` if size-prohibitive; otherwise track but NEVER import from `apps/`.

---

## 10. Hand-Off Notes

### For 05 (AssetCraft Production)

- **Locked tool stack** (§5 above) — production workflows use these tools by name. AI tools in production prompts are explicitly REFERENCE-ONLY.
- **Mascot decision:** LOCKED YES. Character bible inputs per §2:
  - 5-trait personality
  - Body ratio 1:1.4
  - 3-color palette per scene
  - 6 scene states + 8 avatar variants + 4–6 sticker accessories
  - Voice = dryly-honest friend-text-message-cadence
  - Workflow: Figma pose → Inkscape clean → Skia port (NO AI generation for final)
- **3D decision:** LOCKED NO. Skip 3D production workflow entirely.
- **Sound posture:** SIGNATURE-ONLY (3 chimes locked in emotional_spec §6). Workflow: CC0 source → Audacity edit → license-audit → MP3 128kbps mono.
- **Style descriptors** (§7) are the verbatim paste-in for every brief. Especially §7.1 illustration descriptor and §7.2 mascot descriptor.
- **Anti-slop ban list** (§8) MUST appear at top of every production prompt as `"AVOID — [list]"`.
- **Reference-only AI tools:** Imagen 4 / Whisk / NotebookLM are mood-exploration ONLY. Output stays in `references/`, never enters `apps/`.

### For 06 (AppStoreCraft)

- **Asset inventory for store / preview:**
  - iOS App Store screenshots: 5–8 per device class (6.7", 6.1", 5.5", 12.9" iPad)
  - Play Store screenshots: phone + tablet
  - iOS App Preview video: 15–30s, 1080×1920 portrait
  - Play promo video: 30s, YouTube-hosted link
- **Hero illustration source for screenshots:** mascot Skia scenes (composited via Figma device frames over screen recordings)
- **Mascot pose library available for screenshots:** all 6 scene states + 8 avatar variants
- **Sonic logo for preview video end-card:** `kleeve_milestone.mp3` (3-note ascending chord)
- **Microcopy for screenshots:** must use Bricolage Grotesque, locked phrasings from emotional_spec §7 (e.g., `"Day one. You're in."`, `"7 days. The squad held it down with you."`)
- **Screenshot anti-slop notes:**
  - NO three-screenshot feature-grid pattern
  - NO generic-glassy-3D-background
  - NO centered-text-overlay cliché
  - YES mascot-led narrative across 5–8 frames
  - YES asymmetric composition, warm-paper background, dryly-honest copy

---

## 11. Open Questions & Risks

### Unresolved tool / production decisions

1. **Mascot Figma → Skia port methodology** — manual path port is slow (~2.5–3 days for 6 scenes). Founder should validate one mascot scene end-to-end (Figma authoring → SVG export → Inkscape clean → Skia primitive code) BEFORE committing to all 6 in week 1. If port time exceeds 0.5 day per scene, escalate to illustrator commission ($400–800 one-time) rather than AI generation (ban is load-bearing).
2. **8 preset mascot avatars — palette implication.** If avatars span beyond coral hue (e.g., a moss-green avatar, a sky-blue avatar), the primary color ramp re-tunes and `--c-mascot-avatar-{1..8}` token series must be defined (per emotional_spec §11.2). TokenCraft owns this; AssetCraft flags it.
3. **CC0 sonic source availability** — if Pixabay/Freesound don't yield a usable warm-bell-ping at ~G4, fallback is ElevenLabs Sound Effects free tier with prompt `"warm soft bell ping, single note G4, brief, slight reverb"`. If still insufficient, defer milestone chime to v1.1 sound-designer commission rather than shipping a generic ding.

### Style references requiring validation

4. **Risograph grain texture at 5–8% opacity** — verified threshold from emotional_spec §9, but real-device testing on iPhone OLED (warm-yellow tint) and Android LCD/AMOLED variations recommended pre-launch. If grain reads as "noisy" rather than "warm imperfection," tune down to 4% or apply only on `paper-elevated`.
5. **Mascot CMYK-misregistration offset (1px)** — deliberate imperfection. Confirm with a 5-user qualitative test that this reads as "characterful" rather than "broken / visual bug" before locking into all sticker overlays.

### Time-budget realism

6. **Asset work parallels feature development.** 4–5 weeks of focused asset work translates to 8–10 weeks in calendar time if features are also being built. Founder should explicitly sequence asset weeks BEFORE feature-heavy weeks (Week 1 mascot foundation BEFORE any screen built with mascot dependency).
7. **App preview video is highest-skill-required asset.** DaVinci Resolve has a learning curve. Time-budget assumes 1.5 days; in practice may take 3 days for a solo dev. Mitigation: simplify to single-screen mascot end-card with chime (Apple App Preview spec allows this).

### Cross-platform consistency

8. **iOS 26 Liquid Glass app icon variant** — Apple introduced layered specular highlight in iOS 26. Founder should export both classic icon and Liquid Glass layered variant (foreground + middleground + background layers per Apple spec) to ensure forward compatibility. Effort: +0.5 day to icon work.
9. **Android M3 Expressive themable monochrome icon variant** — Android 13+ supports user-tinted monochrome icons. Export single-color silhouette mascot variant. Effort: +0.25 day.

### Hand-off risks

10. **Stage 05 (AssetCraft Production) must respect AI-illustration ban.** The default AssetCraft Production prompts will recommend AI workflows (LoRAs, Recraft style references, Midjourney `--cref`). Founder must override these in 05 and substitute with the Figma → Inkscape → Skia port workflow. Flag this at the very top of the 05 session opening message.
11. **Stage 06 (AppStoreCraft) screenshot mockup tools** — if 06 recommends AI-illustration-based screenshot backgrounds, decline. Use Figma device frames + screen recordings only.

---

**Status:** v1.0 asset strategy, locked. Mascot YES, 3D NO, Sound SIGNATURE-ONLY, 9 free tools committed (vector-craft-first, AI demoted to reference-only), paid threshold = stay free (one-time commissions deferred to v1.1+). Feed forward to `05_asset_production.md` for per-asset workflows + AI-reference-only prompt templates, and `06_appstore_assets.md` for App Store + Play Store + preview video. After downstream stages run, this document remains the asset-level source-of-truth; per-asset drift back into AI-generation defaults or Lottie/Rive motion is to be flagged against this spec at code review.
