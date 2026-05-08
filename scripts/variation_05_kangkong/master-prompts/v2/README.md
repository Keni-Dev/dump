# Master Prompts v2 — Emotional Design + Asset Creation Chain

> Seven master prompts that take you from **app idea → archetype-locked emotional strategy → concrete design tokens → per-screen design prompts → asset library → App Store / Play Store submission**. Each prompt is grounded in the 27-item emotional design research base in `.agent/research/emotional-design/` and the 25-item asset creation research base in `.agent/research/asset-creation/`, aggressively enforcing the 2025-2026 anti-AI-slop doctrine.

## The Full Chain

```
[your app idea, project_specification.md, or onboarding_strategy.md]
        │
        ▼
01 — EmotionCraft (01_emotional_discovery.md)
   produces: emotional_strategy.md
   locks: archetype, ethical posture, distinctiveness posture, platform stance, visual ban list
        │
        ▼
02 — TokenCraft (02_emotional_spec.md)
   produces: emotional_spec.md
   locks: 9 token categories — color (OKLCH), typography, geometry,
          motion (spring physics), haptic, sound, microcopy, iconography, imagery
        │
        ▼
        ┌─────────────────────────────┴─────────────────────────────┐
        ▼                                                           ▼
03a — ClaudeDesign Emotional                            03b — StitchCraft Emotional
   (03a_claude_design.md)                                 (03b_stitch.md)
   produces: Claude Design prompts                        produces: Google Stitch prompts
   output: runnable HTML/CSS/JS                           output: visual mockup
   handoff: 1-line Claude Code instruction                handoff: Firebase Studio export
   best for: production fidelity                          best for: greenfield velocity
        │                                                           │
        └─────────────────────────────┬─────────────────────────────┘
                                      ▼
04 — AssetCraft Strategy (04_asset_strategy.md)
   produces: asset_strategy.md
   locks: asset inventory, mascot Y/N, 3D Y/N, sound posture,
          free tool stack (5-9 tools), style guide extensions, ban list (asset-specific)
                                      │
                                      ▼
05 — AssetCraft Production (05_asset_production.md)
   produces: per-asset walkthroughs + ready-to-paste AI prompts + Claude Code handoff
   covers: app icon, splash, mascot (5-step bible), illustrations,
           Lottie/Rive animations, UI motion, sound, 3D
                                      │
                                      ▼
06 — AppStoreCraft Emotional (06_appstore_assets.md)
   produces: appstore_assets.md
   covers: per-device screenshots, 30s app preview video, feature graphic,
           OG/social cards, full ASO copy, localization plan
   replaces: legacy appstore-screenshots-prompt.md
```

Use `03a` and `03b` in parallel for fastest exploration: Stitch for visual A/B, Claude Design for code-bound production.

## Quick Start

### Standalone (single prompt, fast iteration)
Each prompt works alone. Paste it as the system prompt + describe your need; the prompt interrogates you inline.

```
You: [paste 01_emotional_discovery.md]
You: I want to build a habit-tracking app with social accountability.
EmotionCraft: [walks you through 10 discovery categories in batches]
EmotionCraft: [produces emotional_strategy.md]
```

### Chained (production-grade rigor)
Outputs of each stage feed the next. This is the path for serious projects.

```
01 → emotional_strategy.md (saved to docs/design/)
02 → consume strategy → produce emotional_spec.md
03a → consume spec → produce Claude Design prompts per screen
   AND/OR
03b → consume spec → produce Stitch prompts per screen
04 → consume emotional spec → produce asset_strategy.md
05 → consume asset_strategy → walk through per-asset production
06 → consume asset_strategy + emotional_spec → produce appstore_assets.md
```

## What Each Prompt Locks

| Stage | Persona | Locks | Output | Time |
|---|---|---|---|---|
| 01 | EmotionCraft | Archetype (1 of 12 + optional secondary), ethical posture, distinctiveness, platform stance, anti-AI-slop ban list, prescribed alternatives, aesthetic touchstones | `emotional_strategy.md` | 20-40 min |
| 02 | TokenCraft | OKLCH color ramps, typography pairing + scale, geometry/border-radius variance, motion spring physics + signature moments, haptic patterns, sound posture, microcopy voice + 8-12 locked phrasings, iconography, imagery | `emotional_spec.md` | 30-60 min |
| 03a | ClaudeDesign | Per-screen XML-tagged prompt with banned/tokens/layout/motion/accessibility/archetype-voice/Claude-Code-handoff | Claude Design prompts | 2-5 min/screen |
| 03b | StitchCraft | Per-screen prose prompt — exhaustive visual spec, hex+OKLCH, motion narrated verbally, archetype-translated aesthetic | Stitch prompts | 2-5 min/screen |
| 04 | AssetCraft Strategy | Asset inventory, mascot Y/N, 3D Y/N, sound posture, committed free tool stack, style guide extensions, asset-specific ban list, time budget | `asset_strategy.md` | 20-40 min |
| 05 | AssetCraft Production | Per-asset walkthroughs (icon, mascot, illustrations, animations, sound, 3D), ready-to-paste AI prompt templates, Claude Code repo integration | Per-asset bundles | 30 min - 2-4 weeks/asset |
| 06 | AppStoreCraft | Per-device screenshots, 30s app preview video script, feature graphic, OG/social cards, full ASO copy + keywords, localization plan, submission checklist | `appstore_assets.md` | 8-20 hours per launch |

## Anti-AI-Slop Doctrine (enforced by every prompt)

The chain explicitly forbids these defaults across all stages:

### Web/UI design slop
- **Type:** Inter, Roboto, Arial, system-ui-only stacks, default Tailwind font-sans
- **Color:** indigo-500 (#6366F1), violet-500 (#8B5CF6), the from-violet-500-to-indigo-500 / from-purple-500-to-blue-500 / from-cyan-400-to-violet-500 / from-pink-500-to-purple-500 gradients
- **Geometry:** rounded-xl on every container, max-w-7xl wrapper, identical 16px/24px padding, ring-1 ring-white/10 cards
- **Layout:** centered hero with H1+subhead+CTA-pair+trust-row, three-column feature grid with icons
- **Iconography:** Lucide cube/check/lightning trinity, emoji bullets (🚀✨⚡🔥💡🎯🛡️✅)
- **Motion:** hover:scale-105 on every card, animate-pulse, fade-in-on-scroll uniform
- **Templates:** shadcn defaults, Tailwind UI Catalyst paste, Lovable/v0/Bolt scaffolds without customization

### Asset slop (asset_strategy + production add)
- **Illustrations:** generic gradient blob mesh hero, isometric voxel city, AI faces with melted features / six-fingered hands / gibberish text, default Storyset / unDraw / Open Doodles / Humaaans / IRA Design styles, glassy translucent 3D shapes, generic 3D blobby cute characters
- **Mascots:** default chibi proportions, Duolingo Duo derivative, generic 3D blob with default Cinema 4D materials, anime-derivative without intent, "AI smile" with melted features
- **Animation:** default LottieFiles "loading dots" / "confetti burst" downloads without customization, stock cinematic riser / whoosh
- **Sound:** generic "ding" notification, stock cinematic riser, AI music with time-loop artifacts, default ElevenLabs voice
- **App store screenshots:** generic gradient mesh background, glassy 3D blob backdrop, "Trusted by 1000+ teams" without proof, "The #1 [category] app" hero copy, centered-text-on-purple-gradient, AI-faces-on-laptops-stock-photo
- **Preview videos:** centered-text-on-gradient with cinematic-riser music, generic stock footage, AI-voice generic narration, 30 seconds of UI screen recording with no narrative

925studios research: AI-slop sites convert 91% lower than distinctive custom design. Every stage prescribes specific named alternatives.

## Adaptive Defaults

The prompts adapt to your project's category and ethical posture:

| Category | Distinctiveness default | Ethics default | Mascot default | 3D default | Platform stance default |
|---|---|---|---|---|---|
| Consumer mobile (habit, fitness, journal, mindfulness, social, dating) | Distinctive-but-tasteful, lean-warm | Calm-leaning for wellness; Adaptive for habit/social | Recommend YES if archetype supports (Caregiver/Jester/Innocent) | Selectively NO | Liquid Glass extend on iOS, M3 Expressive extend on Android |
| B2B / dev-tool / productivity (Linear/Raycast/Notion territory) | Clean-minimal-high-craft | Calm-leaning by default | Usually NO (dilutes premium) | NO | Web-craft (Linear/Vercel/Raycast standard) |
| AI-wrapper / chat-first (most prone to slop) | AGGRESSIVE distinctive — biggest slop risk | Adaptive — varies per surface | Usually NO (face logo = slop) | YES selectively for hero brand moment | Custom; fight platform defaults if shipping web-first |
| Marketing site | Editorial / asymmetric / opinionated | Sage/Magician archetype voice typical | NO unless brand-led | Selectively | Web-craft + brand-distinct |
| Other (novel category) | Web-search the category, recommend | Recommend based on user emotional reality | Decide per discovery | Decide per discovery | Recommend based on platform |

## Free-Tools-First Tool Stack (committed in stage 04)

For solo devs on $0 budget:
1. **Imagen 4 (Gemini Pro)** — illustrations, mascot refs, mood iteration (UNLIMITED via Pro)
2. **Recraft (free 50 credits/day)** — vector output, brand-consistent style refs
3. **Microsoft Designer / Bing Image Creator** — DALL-E 3 free with MS account, hero illustrations
4. **Figma free (3 files)** — composition, refinement, character variants, code handoff
5. **Lottielab freemium** — Lottie creation without After Effects
6. **Rive editor (free, $14/mo Pro for advanced)** — interactive state machine animations
7. **DaVinci Resolve / CapCut (free)** — app preview video editing
8. **ElevenLabs (10k chars/mo free)** — voice + Sound Effects
9. **Suno (10 songs/day free)** — sonic logo, music
10. **Spline (free tier — only if 3D in scope)** — 3D hero elements

Paid only at named thresholds: Recraft Pro ($12/mo) for 50+ vector assets, Midjourney Basic ($10/mo) for brand-critical mascot, Adobe single-app ($23/mo) for AE+Bodymovin Lottie pipeline.

## Research Base

The chain is grounded in two research bases:

### Emotional Design (27 items in `.agent/research/emotional-design/`)
- **Foundations** (7): Don Norman's Tripartite Model, Aesthetic-Usability Effect, Cognitive Load + Hick's + Gestalt, Peak-End Rule, Self-Determination Theory, Fogg + Hooked, Affective Computing
- **Platform Languages** (3): Apple Liquid Glass (WWDC25), Material 3 Expressive (I/O 25 — 18,000-participant study), Calm Technology
- **Brand & Identity** (3): 12 Jungian Brand Archetypes, Distinctive Design Languages (16 case studies), Karri Saarinen's Quality/Craft Doctrine
- **Components** (6): Color Psychology, Typography & Tone of Voice, Micro-Interactions, Haptic Feedback Architecture, Sound Design, Loading States & Perceived Performance
- **Anti-Slop & Ethics** (8): AI-Slop Tells, Anti-AI-Slop Movement, Distinctive Design Moves, Maximalism/Y2K, Design Engineer Role, Vibe Design / AI-Codegen Workflow, EU Digital Fairness Act, Ethical Persuasion Boundary

### Asset Creation (25 items in `.agent/research/asset-creation/`)
- **Asset Inventory** (5): App Icon/Splash, Mascot Fundamentals, Illustration Set, Icon System, App Store/Marketing
- **Format Decisions** (3): SVG/PNG/WebP/Lottie/Rive/MP4 Framework, Lottie Deep Dive, Rive Deep Dive
- **AI Tools** (5): Free AI Image Tools 2026, Gemini Pro / Imagen 4 / Veo / Whisk, AI Vector / SVG Generation, Paid AI Tools Comparison, AI Video Generation
- **Production Tools** (4): Figma Free Tier, Free Creative Suite (Krita/Inkscape/GIMP/Photopea/Blender/DaVinci/CapCut), Lottie Creation Tools, Spline / 3D
- **Deep Dives** (4): Mascot Creation Workflow, Mascot Animation, Animation Principles for App UX, Sound + Voice Asset Creation
- **Workflow & Anti-Slop** (4): Asset Choice as Archetype Signal, Anti-AI-Slop in Illustrations/3D/Mascots, Asset Library Consistency, End-to-End Workflow

## Compatibility with Existing Prompts

These v2 prompts are GENERAL-PURPOSE (work for any app/category). They're separate from your onboarding-specific chain (`master-prompts/onboarding-v2/`):

- **`onboarding-v2/01_psychology.md` (PsychCraft v2)** — onboarding strategy specifically. Compatible: pass `onboarding_strategy.md` into `01_emotional_discovery.md` (Mode C).
- **`onboarding-v2/02a_design_claude.md` / `02b_design_stitch.md`** — onboarding screens specifically. Use the v2 main chain (03a/b) for non-onboarding surfaces; use the onboarding-v2 chain for onboarding surfaces.
- **`onboarding-v2/03_architecture.md`** (FlowCraft v2) — XState v5 FSM for onboarding. Independent.
- **`mobile-master-prompt.md` / `web-master-prompt.md`** — original general-purpose Stitch prompts (no emotional design framework, no anti-slop ban list). The v2 chain is the upgrade. Old ones remain for fallback.
- **`appstore-screenshots-prompt.md`** — legacy app store prompt. **Superseded by `v2/06_appstore_assets.md`** which integrates emotional design + anti-slop.
- **`project-discovery-prompt.md`** (SpecCraft) — project-level scope. Runs BEFORE the v2 chain.

## Recommended Workflow (Greenfield)

### Full chain
1. Run `project-discovery-prompt.md` (SpecCraft) → save `project_specification.md`
2. Run `v2/01_emotional_discovery.md` (Mode B with project spec) → `emotional_strategy.md`
3. Run `onboarding-v2/01_psychology.md` (PsychCraft v2, with project spec + emotional strategy) → `onboarding_strategy.md` [if onboarding scope warrants]
4. Run `v2/02_emotional_spec.md` (chained) → `emotional_spec.md`
5. Run `onboarding-v2/03_architecture.md` (FlowCraft v2) → onboarding FSM [if onboarding]
6. Run `v2/03a_claude_design.md` AND/OR `v2/03b_stitch.md` (chained) → per-screen design prompts
   - Use `onboarding-v2/02a_design_claude.md` for onboarding screens specifically
7. Run `v2/04_asset_strategy.md` (chained) → `asset_strategy.md`
8. Run `v2/05_asset_production.md` (chained) → produce in-app assets (icon, mascot, illustrations, animations, sound)
9. Run `v2/06_appstore_assets.md` (chained) → produce App Store + Play Store + preview video
10. Hand off to Claude Code (`feature-implementation-prompt.md`) for actual code with assets wired

### Quick exploration (single screen / asset)
Each v2 prompt works standalone. Paste the prompt + your idea + answer compressed inline questions.

### Audit
Each v2 prompt has Mode C (audit) — paste existing artifacts + get a revised plan.

## File Index

| File | Purpose | Length |
|---|---|---|
| `README.md` | This file | ~12K |
| `01_emotional_discovery.md` | EmotionCraft — strategy interrogator | 40K |
| `02_emotional_spec.md` | TokenCraft — token interrogator | 39K |
| `03a_claude_design.md` | ClaudeDesign Emotional — code-first design prompts | 26K |
| `03b_stitch.md` | StitchCraft Emotional — visual mockup prompts | 25K |
| `04_asset_strategy.md` | AssetCraft Strategy — inventory + tool stack | ~33K |
| `05_asset_production.md` | AssetCraft Production — per-asset walkthroughs | ~45K |
| `06_appstore_assets.md` | AppStoreCraft — App Store + Play Store + preview video | ~37K |

## Related

- `.agent/research/emotional-design/` — research base for stages 01-03 (27 items, 17 fields each)
- `.agent/research/asset-creation/` — research base for stages 04-06 (25 items, 17 fields each)
- `.agent/master-prompts/onboarding-v2/` — onboarding-specific chain
- `.agent/master-prompts/project-discovery-prompt.md` — SpecCraft (project-level spec, predates emotional chain)
- `.agent/Emotional Design for App Development.pdf` — primary research source (emotional design)
