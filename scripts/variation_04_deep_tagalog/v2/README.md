# Master Prompts v2 — Emotional Design Chain

> Four master prompts that take you from **app idea → archetype-locked emotional strategy → concrete design tokens → per-screen Claude Design or Google Stitch prompts**. Each prompt is grounded in the 27-item emotional design research base in `.agent/research/emotional-design/` and aggressively enforces the 2025-2026 anti-AI-slop doctrine.

## The Chain

```
[your app idea, project_specification.md, or onboarding_strategy.md]
        │
        ▼
01 — EmotionCraft (01_emotional_discovery.md)
   produces: emotional_strategy.md
   locks: archetype, ethical posture, distinctiveness posture, platform stance, ban list
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
```

## What Each Prompt Locks

| Stage | Locks | Output | Time |
|---|---|---|---|
| 01 EmotionCraft | Archetype (1 of 12 + optional secondary), ethical posture (Calm/Adaptive/Engagement/Mix), distinctiveness posture, platform stance, anti-AI-slop ban list, prescribed alternatives, aesthetic touchstones | `emotional_strategy.md` | 20-40 min |
| 02 TokenCraft | OKLCH color ramps, typography pairing + scale, geometry/border-radius variance, motion spring physics + signature moments, haptic patterns, sound posture, microcopy voice + 8-12 locked phrasings, iconography, imagery | `emotional_spec.md` | 30-60 min |
| 03a ClaudeDesign | Per-screen XML-tagged prompt with banned/tokens/layout/motion/accessibility/archetype-voice/Claude-Code-handoff | Claude Design prompts | 2-5 min/screen |
| 03b StitchCraft | Per-screen prose prompt — exhaustive visual spec, hex+OKLCH, motion narrated verbally, archetype-translated aesthetic | Stitch prompts | 2-5 min/screen |

## Anti-AI-Slop Doctrine (enforced by every prompt)

The chain explicitly forbids these defaults across all stages:

- **Type:** Inter, Roboto, Arial, system-ui-only stacks, default Tailwind font-sans
- **Color:** indigo-500 (#6366F1), violet-500 (#8B5CF6), the from-violet-500-to-indigo-500 / from-purple-500-to-blue-500 / from-cyan-400-to-violet-500 / from-pink-500-to-purple-500 gradients
- **Geometry:** rounded-xl on every container, max-w-7xl wrapper, identical 16px/24px padding everywhere, ring-1 ring-white/10 cards
- **Layout:** centered hero with H1+subhead+CTA-pair+trust-row, three-column feature grid with icons
- **Iconography:** Lucide cube/check/lightning trinity, emoji bullets (🚀✨⚡🔥💡🎯🛡️✅)
- **Imagery:** stock-photo-of-diverse-team-on-laptops, glassy-3D-blob, AI-illustrations-with-melted-hands
- **Motion:** hover:scale-105 on every card, animate-pulse, fade-in-on-scroll uniform
- **Templates:** shadcn defaults, Tailwind UI Catalyst paste, Lovable/v0/Bolt scaffolds without customization

925studios research: AI-slop sites convert 91% lower than distinctive custom design. Every stage of this chain prescribes specific named alternatives.

## Adaptive Defaults

The prompts adapt to your project's category and ethical posture:

| Category | Distinctiveness default | Ethics default | Platform stance default |
|---|---|---|---|
| Consumer mobile (habit, fitness, journal, mindfulness, social, dating) | Distinctive-but-tasteful, lean-warm | Calm-leaning for wellness; Adaptive for habit/social | Liquid Glass extend on iOS, M3 Expressive extend on Android |
| B2B / dev-tool / productivity (Linear/Raycast/Notion territory) | Clean-minimal-high-craft (web design-engineer caliber) | Calm-leaning by default | Web-craft (Linear/Vercel/Raycast standard) |
| AI-wrapper / chat-first (most prone to slop) | AGGRESSIVE distinctive — biggest slop risk | Adaptive — varies per surface | Custom; fight platform defaults if shipping web-first |
| Marketing site | Editorial / asymmetric / opinionated | Sage/Magician archetype voice typical | Web-craft + brand-distinct |
| Other (novel category) | Web-search the category, recommend | Recommend based on user emotional reality | Recommend based on platform |

## Research Base

Each prompt is grounded in 27 deeply-researched items in `.agent/research/emotional-design/results/` covering:

- **Foundations** (7): Don Norman's Tripartite Model, Aesthetic-Usability Effect, Cognitive Load + Hick's + Gestalt, Peak-End Rule, Self-Determination Theory, Fogg + Hooked, Affective Computing
- **Platform Languages** (3): Apple Liquid Glass (WWDC25), Material 3 Expressive (I/O 25 — 18,000-participant study), Calm Technology
- **Brand & Identity** (3): 12 Jungian Brand Archetypes, Distinctive Design Languages (16 case studies), Karri Saarinen's Quality/Craft Doctrine
- **Components** (6): Color Psychology, Typography & Tone of Voice, Micro-Interactions, Haptic Feedback Architecture, Sound Design, Loading States & Perceived Performance
- **Anti-Slop & Ethics** (8): AI-Slop Tells, Anti-AI-Slop Movement, Distinctive Design Moves, Maximalism/Y2K Counter-Aesthetic, Design Engineer Role, Vibe Design / AI-Codegen Workflow, EU Digital Fairness Act, Ethical Persuasion Boundary

See `.agent/research/emotional-design/outline.yaml` and `fields.yaml` for the full research framework.

## Compatibility with Existing Prompts

These v2 prompts are GENERAL-PURPOSE (work for any app/category). They're separate from your onboarding-specific chain (`master-prompts/onboarding/`):

- **`onboarding/01_strategy.md` (HookCraft)** — onboarding strategy specifically. Compatible: pass `onboarding_strategy.md` into `01_emotional_discovery.md` (Mode C).
- **`onboarding/02_design_claude.md` / `02_design_stitch.md`** — onboarding screens specifically. Use the v2 chain for non-onboarding surfaces; use the onboarding chain for onboarding surfaces.
- **`onboarding/03_architecture.md`** (FlowCraft) — FSM architecture. Independent.
- **`mobile-master-prompt.md` / `web-master-prompt.md`** — original general-purpose Stitch prompts (no emotional design framework, no anti-slop ban list). The v2 chain is the upgrade. Old ones remain for fallback.

## Recommended Workflow

### Greenfield (new app, no spec)
1. Run `01_emotional_discovery.md` standalone → save `emotional_strategy.md`
2. Run `02_emotional_spec.md` chained → save `emotional_spec.md`
3. Run `03a_claude_design.md` (or `03b_stitch.md`) chained → generate per-screen prompts
4. (Optional) Run both `03a` and `03b` for parallel exploration
5. Hand off code via Claude Code one-liner from `03a` outputs

### Existing project (has SpecCraft/HookCraft outputs)
1. Run `01_emotional_discovery.md` chained with your existing spec → produce `emotional_strategy.md`
2. Run `02_emotional_spec.md` chained → `emotional_spec.md`
3. Run `03a` and/or `03b` chained per surface

### Quick exploration (single screen, no chain)
1. Run `03a` or `03b` standalone — they include compressed strategy + token interrogation
2. Iterate inline

### Audit (existing app needs emotional refresh)
1. Run `01_emotional_discovery.md` Mode D (Audit) with screenshots/links → revised strategy
2. Run `02_emotional_spec.md` Mode C (Audit) with current tokens → revised spec
3. Run `03a/b` for redesigned screens

## File Index

| File | Purpose | Length |
|---|---|---|
| `README.md` | This file | — |
| `01_emotional_discovery.md` | EmotionCraft — strategy interrogator | 27K |
| `02_emotional_spec.md` | TokenCraft — token interrogator | 35K |
| `03a_claude_design.md` | ClaudeDesign Emotional — code-first design prompts | 21K |
| `03b_stitch.md` | StitchCraft Emotional — visual mockup prompts | 21K |

## Related

- `.agent/research/emotional-design/` — research base (27 JSON files + outline + fields)
- `.agent/master-prompts/onboarding/` — onboarding-specific prompt chain (HookCraft → StitchCraft Onboarding / ClaudeDesign Onboarding → FlowCraft → ...)
- `.agent/master-prompts/project-discovery-prompt.md` — SpecCraft (project-level spec, predates emotional chain)
- `.agent/Emotional Design for App Development.pdf` — primary research source
