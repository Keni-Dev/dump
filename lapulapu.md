# Asset Production: Kleeve

> Per-asset creation walkthroughs produced by AssetCraft Production (stage 05), executing the contract locked in `asset_strategy.md` (stage 04). Each workflow gives **ready-to-paste JSON prompts for Nano Banana Pro (Gemini 3 Pro Image)**, tool-specific steps with time estimates, anti-slop verification, and Claude Code handoff lines. Sibling: `06_appstore_assets.md` for App Store + Play Store + preview video.
>
> **Reading order:** all assets in P0 → P1 → P2 priority. Start with Workflow 1 (Mascot Foundation — unblocks everything downstream). The mascot 360° character sheet from Workflow 1 is the visual identity reused via Nano Banana Pro character-reference in Workflows 2, 4, 5, 8, and 10.

---

## How Nano Banana Pro JSON Prompts Work in This Doc

Every illustration generation in this doc uses **JSON-format production briefs** pasted into Gemini app or AI Studio with Nano Banana Pro (Gemini 3 Pro Image) selected. The schema:

```json
{
  "subject": "what the image is of",
  "composition": "framing, viewpoint, layout",
  "action": "what the subject is doing",
  "setting": "background / surface / context",
  "style": "art style with specific named references",
  "lighting": "light source, mood, color temperature",
  "camera": "viewpoint, focal length, perspective",
  "colors": "exact palette with hex codes",
  "texture": "surface treatment (grain, smoothness, line quality)",
  "style_references": ["named artists / studios / cultural touchstones"],
  "avoid": ["explicit anti-slop list — paste verbatim"],
  "output": "format, resolution, transparency"
}
```

**Why JSON:** Nano Banana Pro's Thinking process parses structured input more reliably than natural language. The `"avoid"` array is load-bearing — every prompt MUST include the full anti-slop ban list verbatim.

**Standard avoid array (paste in EVERY prompt):**

```json
"avoid": [
  "default AI chibi proportions (extreme 1:1 head:body, oversized head, anime-large sparkly eyes)",
  "anime-derivative without intentional reference (no anime-large eyes, no sparkle layers, no tear-drops)",
  "Duolingo Duo derivative (green bird, similar pose, similar expression library)",
  "generic 3D blob with default Cinema 4D materials",
  "generic Pixar-cute 3D character",
  "AI smile uncanny lip curl or dead eyes",
  "melted facial features or six-fingered hands or gibberish text",
  "smooth-gradient blob illustration (we want hand-drawn flat-fill, NOT AI-rendered gradient)",
  "isometric voxel city scene",
  "glassy translucent 3D shapes floating",
  "default Storyset Humaaans unDraw Open Doodles IRA Design aesthetic",
  "purple-blue gradient or indigo-500 violet-500 anywhere",
  "Inter Roboto Geist Helvetica typography",
  "centered-text-on-gradient composition",
  "diverse-team-on-laptops or hands-on-keyboard photography",
  "Lucide Box CheckCircle Zap feature-trinity icons",
  "emoji bullet section headers",
  "skipping the cheek blush (the blush is the load-bearing cuteness mechanic — MANDATORY)",
  "making the character a specific real animal (Klee is its own creature — NOT a bird, NOT a fox, NOT a cat)",
  "tag-soup quality descriptors like '4k trending on artstation masterpiece'"
]
```

**Standard colors array (paste in EVERY illustration prompt):**

```json
"colors": {
  "primary": "#EDA597 (warm-blush-coral, mascot body anchor)",
  "primary_darker": "#EE9A8A (primary-400, one-tone-darker — used for mascot cheek blush at 40% opacity)",
  "accent": "#C2701D (sunset-orange, milestone)",
  "paper": "#FAF1E0 (warm-near-white background)",
  "paper_elevated": "#F4E4C2 (mascot-spotlight surface)",
  "ink": "#1F1F26 (soft warm ink, outline + body text)",
  "streak_break": "#80513A (warm-deepened-clay, NEVER red)",
  "rule": "use ONLY these hex codes; no gradients; flat fills with optional 6-8% risograph grain overlay; mascot cheek blush at 40% opacity is mandatory in all character scenes"
}
```

**Standard style_references array (paste in EVERY illustration prompt with Klee in it):**

```json
"style_references": [
  "Molang — Hye-ji Yoon 2010, Korean white-rabbit pillow simplicity with subtle blush (MAIN cuteness reference)",
  "Pusheen — tubby rounded silhouette, expressive-through-pose-not-face",
  "Studio Ghibli Soot Sprites / Susuwatari — simple round bodies with wide expressive eyes",
  "Tarepanda — San-X melted-relaxed cute character economy",
  "Adventure Time circa 2014 character economy and proportion",
  "Mirror Studio Mexico City risograph zine print texture",
  "Tom Froese editorial vector line quality (for the hand-drawn outline character)",
  "1.2-1.6px hand-drawn outline stroke (NOT computer-perfect Bezier)",
  "slight 1px CMYK-misregistration offset on accent overlays"
]
```

**Cuteness mechanics (paste into every Klee-character prompt):**

```json
"cuteness_mechanics": {
  "body_ratio": "head-to-body 1:1.2 — pillow proportion, NOT AI-chibi 1:1, NOT realistic 1:7",
  "silhouette": "pebble / clover-tuft / pillow shape, taller-than-wide oval, two small ear-nubs or hair-tufts on top (rounded soft bumps, NOT pointed animal ears)",
  "eyes": "soft bean-oval shapes ~8% of face height, ONE tiny highlight dot upper-left of each iris (single catch-light, ~15% of eye size). NOT anime-large, NO sparkle layers, NO tear-drops",
  "mouth": "gentle simple curve in neutral, soft ':3' or 'ω' cat-style mouth in expressive scenes (submit / confetti / celebration). NEVER 'AI smile' lip curl",
  "cheek_blush": "MANDATORY two small peach ovals (#EE9A8A at 40% opacity, ~12% of face width each, lower-outer cheek area). DO NOT SKIP — this is the load-bearing cuteness mechanic",
  "paws": "short rounded mitten-shapes with three subtle toe-bump indentations along bottom edge (no individual fingers — anti-six-fingered-AI preserved)",
  "anti_animal": "Klee is its own creature, NOT a bird, NOT a fox, NOT a cat, NOT any specific real animal"
}
```

---

# ─────────────────────────────────────────────────────────
# WORKFLOW 1: MASCOT FOUNDATION (360° character sheet + 6 scene states)
# Priority: P0 — UNBLOCKS EVERYTHING
# Estimated time: 2–2.5 days (Nano Banana Pro accelerated)
# ─────────────────────────────────────────────────────────

## Step 1.1 — Lock the character bible (30 min)

Before any Nano Banana Pro generation, the mascot character bible must be written down once and referenced verbatim across every subsequent prompt. Create `apps/mobile/assets/mascot/CHARACTER_BIBLE.md` with:

```markdown
# Klee — Kleeve Mascot Character Bible

## Identity
- Name: **Klee** (derived from the "Kleeve" stem; also German for "clover", carrying a small luck/friendship association — incidental, not load-bearing)
- Species: a soft warm-coral creature, pebble / clover-tuft / pillow silhouette, friendly hug-able shape, NOT a specific real animal
- Body ratio: head-to-body **1:1.2** (cute pillow proportion — NOT default AI chibi 1:1, NOT realistic 1:7)
- Silhouette: taller-than-wide oval with two small ear-nubs or hair-tufts on top
- Height in scene: 60-70% of frame on portrait, 40-50% on square

## Personality (5 traits)
1. Warm — never sharp or judgmental
2. Dryly-honest — acknowledges the miss without guilt-tripping
3. Curious-not-coach — looks with you, never at you
4. Tactile — has hand-drawn imperfection
5. Quietly-celebratory — small joy on submit, never over-celebratory

## Visual identity (load-bearing — tasteful-cute, NOT AI-cute)
- **Body color:** warm-blush-coral #EDA597 (OKLCH 0.75 0.10 25)
- **Outline:** soft-ink #1F1F26 at 1.2-1.6px stroke, hand-drawn quality (NOT computer-perfect Bezier)
- **Eyes:** soft bean-oval shapes (~8% of face height), each with one tiny highlight dot in upper-left of iris. NOT anime-large. NO sparkle layers. NO tear-drops. ONE highlight only.
- **Mouth:** simple gentle curve in neutral states. Small soft `:3` or `ω` cat-style mouth in expressive scenes (submit / confetti / celebration). NEVER "AI smile" uncanny lip curl.
- **Cheek blush:** subtle peach blush — small oval, color #EE9A8A (primary-400, one tone darker than body), opacity ~40%, positioned on the lower outer portion of each cheek. Sanrio/Tarepanda signature. DO NOT skip — this is the load-bearing cuteness mechanic.
- **Paws:** short rounded mitten-shapes with three subtle toe-bumps each (no individual fingers — anti-six-fingered-AI tell preserved)
- **Four-color palette max per scene:** body coral / outline ink / blush peach / one accent (sticker only)

## Style siblings (tasteful-cute lineage — paste into every Nano Banana Pro prompt)
- **Molang** (Hye-ji Yoon 2010 — Korean white-rabbit, pillow simplicity, subtle blush)
- **Pusheen** (tubby rounded silhouette, expressive-through-pose-not-face)
- **Studio Ghibli Soot Sprites / Susuwatari** (simple round bodies with wide expressive eyes)
- **Tarepanda** (San-X melted-relaxed cute)
- **Adventure Time circa 2014** (character economy and proportion)
- **Mirror Studio Mexico City risograph zine** (texture treatment)

## Accessories
- Sticker overlays (hat, journal items, small badges) earned via streaks
- Slight 1px CMYK-misregistration offset on sticker overlay (deliberate imperfection)

## Voice in copy (when speaking)
- Dryly-honest, friend-text-message-cadence
- Occasional dry joke
- NEVER coach-voice, NEVER motivational-poster, NEVER passive-aggressive
- Sample: "Day done. Bea and Alex already submitted — Mira's still cooking."
```

## Step 1.2 — Generate 360° character sheet via Nano Banana Pro (3-4 hours)

Goal: 4 reference images (front, 3-quarter-right, side-right, back) that lock the mascot's visual identity. These 4 images are reused as character references for EVERY subsequent generation.

### Prompt 1A — Front view

Paste into Gemini app with Nano Banana Pro / Gemini 3 Pro Image model:

```json
{
  "subject": "Klee — the warm-coral creature mascot for an app called Kleeve. Klee is a tasteful-cute, pillow-shaped, huggable character with a clover-tuft / pebble silhouette and two small ear-nubs on top. NOT a specific real animal. The cuteness target is Molang × Pusheen × Studio Ghibli Soot Sprites, NOT AI-chibi and NOT anime.",
  "composition": "full-body portrait, centered, front view facing camera directly, isolated on flat warm-paper background, no shadow under the character",
  "action": "standing relaxed in a tiny soft pose, gentle warm expression, short rounded paw-arms slightly out at sides, looking warmly forward — a friendly 'oh hi' moment, hug-able and approachable",
  "setting": "flat warm-paper #FAF1E0 background, no environment, no other objects",
  "style": "hand-drawn vector illustration with risograph-zine print texture, 1.2-1.6px ink outline that has a deliberate hand-drawn quality (NOT computer-perfect Bezier curves), flat color fills, 6% grain texture overlay, slight 1px CMYK-misregistration on accent areas. Tasteful-cute, NOT AI-cute.",
  "lighting": "flat editorial lighting, no shadow, no specular highlight, even warm illumination",
  "camera": "straight-on portrait, eye-level, no perspective distortion",
  "colors": {
    "body": "#EDA597 (warm-blush-coral)",
    "outline": "#1F1F26 (soft warm ink, 1.2-1.6px stroke)",
    "blush": "#EE9A8A (primary-400, one-tone-darker than body, 40% opacity, small oval on lower outer cheek area)",
    "highlight_cheeks": "#F4E4C2 (paper-elevated, subtle catch-light if any)",
    "background": "#FAF1E0 (warm-paper)",
    "rule": "four colors max on the character (body / outline / blush / one optional accent), flat fills only, NO gradients"
  },
  "character_identity": {
    "body_ratio": "head-to-body 1:1.2 — cute pillow proportion, slightly chibier than human but NOT default AI chibi 1:1, NOT realistic 1:7",
    "silhouette": "pebble / clover-tuft / pillow shape, taller-than-wide oval, two small ear-nubs or hair-tufts on top (rounded soft bumps, NOT pointed animal ears, NOT specific to any real animal — these are clover-tuft suggestions). Hug-able huggable form factor.",
    "eyes": "soft bean-oval shapes, about 8% of face height (NOT anime-large, NOT realistic-small). Each eye has ONE tiny highlight dot in the upper-left of the iris (a single round catch-light, ~15% of the eye size). NO sparkle layers. NO multi-highlight. NO tear-drops. Eyes positioned slightly wider than center, low on the face, conveying warm-curious.",
    "mouth": "small soft gentle curve in this neutral pose, positioned slightly below center of lower face. NEVER an 'AI smile' uncanny lip curl. The curve has hand-drawn imperfection, NOT a computer-perfect arc.",
    "cheek_blush": "MANDATORY — two subtle peach blush ovals, color #EE9A8A at 40% opacity, small (~12% of face width each), positioned on lower-outer cheek area, slightly tilted toward the eyes. This is the load-bearing cuteness mechanic — DO NOT skip the blush.",
    "limbs": "two short rounded paw-mitten arms at the sides (no individual fingers — mitten silhouette only, with three subtle toe-bump indentations along the bottom edge to suggest soft padded paws). Feet are NOT visible (body sits low, pillow-style, no legs OR very short stubby feet).",
    "tail_or_other": "no tail (or optionally a tiny soft round nub-tail visible from front), keep simple"
  },
  "style_references": [
    "Molang — Hye-ji Yoon 2010, Korean white-rabbit pillow simplicity with subtle blush, MAIN reference for proportion and cuteness mechanic",
    "Pusheen — tubby rounded silhouette, expressive-through-pose-not-face",
    "Studio Ghibli Soot Sprites / Susuwatari — simple round bodies with wide expressive eyes",
    "Tarepanda — San-X melted-relaxed cute character economy",
    "Adventure Time circa 2014 character economy and proportion",
    "Mirror Studio Mexico City risograph zine print texture",
    "Tom Froese editorial vector line quality (for the hand-drawn outline character)"
  ],
  "avoid": [
    "default AI chibi proportions (extreme 1:1 head:body, oversized head, anime-large sparkly eyes)",
    "anime-derivative without intentional reference (no anime-large eyes, no sparkle layers, no tear-drops)",
    "Duolingo Duo derivative (green bird, similar pose, similar expression library)",
    "generic 3D blob with default Cinema 4D materials",
    "generic Pixar-cute 3D character",
    "AI smile uncanny lip curl or dead eyes",
    "melted facial features",
    "six-fingered hands or defined individual fingers (mitten-only)",
    "gibberish text on the body or background",
    "smooth-gradient blob illustration (we want hand-drawn flat-fill, NOT AI-rendered gradient)",
    "isometric perspective",
    "glassy translucent 3D shapes",
    "default Storyset Humaaans unDraw Open Doodles aesthetic",
    "purple-blue gradient or indigo-500 violet-500 anywhere",
    "centered-text-on-gradient composition",
    "skipping the cheek blush (the blush is mandatory for cuteness)",
    "making the character a specific real animal (NOT a bird, NOT a fox, NOT a cat — it is its own creature)",
    "tag-soup quality descriptors like '4k trending on artstation masterpiece'"
  ],
  "output": {
    "format": "PNG with transparent background preferred, otherwise flat warm-paper #FAF1E0 background",
    "resolution": "2048x2048 square",
    "aspect_ratio": "1:1"
  }
}
```

Generate 4–8 variants. **Pick the LEAST-AI-looking** — the one with the most hand-drawn outline character, no AI smile, no melted features. Save best variant as `references/mascot/360/01-front.png`.

### Prompt 1B — Three-quarter right view

Same JSON as Prompt 1A with two changes:

```json
{
  "...all fields identical to 1A except...": "",
  "composition": "full-body portrait, centered, three-quarter view turned 45 degrees right, isolated on flat warm-paper background, no shadow under the character",
  "character_reference": "MUST match the character generated in the front-view reference image: same body color #EDA597, same head-to-body ratio 1:1.4, same eye style (simple dot or short-line), same outline weight 1.2-1.6px, same cheek highlight, same mitten-style limbs"
}
```

**In Gemini app:** attach the front-view image from Prompt 1A as a reference image (use the image-upload feature in the prompt input). Nano Banana Pro's character consistency works by referencing prior images.

Save best variant as `references/mascot/360/02-three-quarter-right.png`.

### Prompt 1C — Side view

Same approach with `"composition": "full-body portrait, centered, pure side profile facing right..."` and attach BOTH 1A and 1B as references. Save as `references/mascot/360/03-side-right.png`.

### Prompt 1D — Back view

Same approach with `"composition": "full-body portrait, centered, back view (showing the character from behind)..."` and attach 1A + 1B + 1C as references. Save as `references/mascot/360/04-back.png`.

**Verification before proceeding:**
- All 4 views show the same body color, outline weight, eye style, head ratio
- Hand-drawn outline character is visible (NOT computer-perfect Bezier)
- No AI smile, no melted features, no six-fingered hands, no gibberish text
- Risograph grain texture is visible at ~6% opacity

If any view drifts, regenerate that view with the prior views as references and the `"character_reference"` field strengthened.

## Step 1.3 — Generate 6 scene states (4-5 hours)

Each scene state is generated with the 4 reference images attached PLUS the specific scene prompt. Save outputs to `references/mascot/scenes/`.

### Scene 1 — mascot-base (idle / hero pose)

Use Prompt 1A as the base (already generated). This IS mascot-base. Save as `references/mascot/scenes/mascot-base.png`.

### Scene 2 — mascot-submit (with checkmark draw)

```json
{
  "subject": "Klee — the same Kleeve mascot character from the reference images, in a quietly-celebratory submit pose",
  "composition": "full-body portrait, three-quarter view, isolated on warm-paper background",
  "action": "the character is making a gentle pleased gesture — one short paw-mitten arm slightly raised in soft pride, eyes warm and content (preserving the bean-oval shape with single highlight dot from reference), mouth in a small soft ':3' or 'ω' cat-style curve (quietly pleased, NOT exaggerated, NOT AI-uncanny), cheek blush preserved. A soft-success green #5FA77A checkmark is being drawn across the character's chest area as a separate compositional element (the checkmark looks like a hand-drawn stroke being inked in real-time)",
  "setting": "flat warm-paper #FAF1E0 background",
  "style": "[same as mascot-base, character identity inherited from references]",
  "character_reference": "MUST exactly match the 4 reference images attached: body color #EDA597, head:body 1:1.4, eye style, outline weight 1.2-1.6px, mitten-style limbs",
  "colors": {
    "body": "#EDA597",
    "outline": "#1F1F26",
    "checkmark_stroke": "#5FA77A (success green, 4px stroke)",
    "background": "#FAF1E0",
    "rule": "checkmark is the ONLY accent color; body remains coral with ink outline"
  },
  "style_references": ["...same as mascot-base..."],
  "avoid": ["...standard avoid array..."],
  "output": {"format": "PNG transparent background", "resolution": "2048x2048", "aspect_ratio": "1:1"}
}
```

Attach the 4 reference images. Generate 4-6 variants. Pick best, save as `references/mascot/scenes/mascot-submit.png`.

### Scene 3 — mascot-shrug (gentle apologetic, NEVER sad)

```json
{
  "subject": "Klee — the same Kleeve mascot character from the reference images",
  "composition": "full-body portrait, three-quarter view, isolated on warm-paper background",
  "action": "the character is doing a small soft shrug — both arms slightly raised at the sides with palms up (mitten-style, no defined fingers), eyes warm and gently apologetic but NOT sad, NOT defeated, NOT crying. Expression is 'oh well, shake it off' not 'I let you down'. The shrug is gentle and contained, not dramatic.",
  "setting": "flat warm-paper #FAF1E0 background",
  "character_reference": "MUST exactly match the 4 reference images attached",
  "style": "[same as mascot-base]",
  "colors": "[same as mascot-base, body coral with ink outline only]",
  "style_references": ["...standard array..."],
  "avoid": [
    "...standard avoid array...",
    "sad facial expression with tears or downturned mouth",
    "defeated body posture or slumped shoulders that read as despair",
    "guilt-tripping expression",
    "Duolingo passive-aggressive owl 2023 energy"
  ],
  "output": {"format": "PNG transparent background", "resolution": "2048x2048", "aspect_ratio": "1:1"}
}
```

Save as `references/mascot/scenes/mascot-shrug.png`.

### Scene 4 — mascot-confetti (small joy on first-time submit)

```json
{
  "subject": "Klee — the same Kleeve mascot character from the reference images, in a small quietly-joyful pose",
  "composition": "full-body portrait, three-quarter view, isolated on warm-paper background, character is the central focal point with a small contained confetti element around them",
  "action": "the character has a soft ':3' or 'ω' cat-style mouth (small quiet joy, NOT exaggerated), bean-oval eyes preserved with single highlight, cheek blush preserved and slightly more visible, both short paw-mitten arms slightly raised, with about 12-16 small confetti pieces gently floating around them in warm accent colors. The confetti is CONTAINED close to the character (not spread across the whole frame), it's a small intimate moment of joy, NOT an over-the-top celebration",
  "setting": "flat warm-paper #FAF1E0 background, no environment",
  "character_reference": "MUST exactly match the 4 reference images attached",
  "style": "[same as mascot-base], confetti pieces are simple flat geometric shapes (small rectangles, simple stars), hand-drawn quality, NOT photorealistic",
  "colors": {
    "body": "#EDA597",
    "outline": "#1F1F26",
    "confetti_palette": ["#C2701D (sunset-accent)", "#ECA13F (accent-300)", "#F2BC7B (accent-200)", "#EDA89B (primary-300)", "#EE9A8A (primary-400)"],
    "background": "#FAF1E0",
    "rule": "confetti uses ONLY the listed warm accent + primary tones; no cool colors, no neon"
  },
  "style_references": ["...standard array..."],
  "avoid": [
    "...standard avoid array...",
    "over-the-top celebration with confetti filling the entire frame",
    "generic emoji-style party-popper aesthetic",
    "rainbow confetti or cool-color confetti (must stay in warm palette)",
    "default LottieFiles confetti-burst aesthetic"
  ],
  "output": {"format": "PNG transparent background", "resolution": "2048x2048", "aspect_ratio": "1:1"}
}
```

Save as `references/mascot/scenes/mascot-confetti.png`.

### Scene 5 — mascot-celebration (milestone bigger joy, still contained)

Same approach as `mascot-confetti` but action is a slightly larger gesture — both arms raised, soft smile a little more expressed, and a small banner or simple garland element with text "30" or "7" rendered in Bricolage Grotesque-style typography (Nano Banana Pro renders text well at this level). Save as `references/mascot/scenes/mascot-celebration.png`.

### Scene 6 — mascot-streak-break (acknowledging, soft wave)

```json
{
  "subject": "Klee — the same Kleeve mascot character from the reference images, in a gentle acknowledging pose for a streak-break moment",
  "composition": "full-body portrait, three-quarter view, isolated on warm-deepened-clay textured surface",
  "action": "the character is doing a soft gentle wave with one arm, eyes warm and understanding, mouth in a calm slight smile that says 'it's okay, we'll pick it up tomorrow'. The pose communicates acknowledgment WITHOUT shame, WITHOUT defeat, WITHOUT guilt-tripping.",
  "setting": "flat warm-deepened-clay #80513A surface with subtle risograph grain at 6% opacity, edges fading to warm-paper #FAF1E0 (vignette transition)",
  "character_reference": "MUST exactly match the 4 reference images attached, body color #EDA597 is preserved (the streak-break surface is the SURROUNDING surface, not the body)",
  "style": "[same as mascot-base], with a slightly more pronounced grain texture on the surface around the character",
  "colors": {
    "body": "#EDA597 (preserved coral)",
    "outline": "#1F1F26",
    "background_surface": "#80513A (warm-clay-deepened)",
    "background_edge": "#FAF1E0 (vignette to warm-paper)",
    "rule": "warm-clay is in the SURFACE, never on the body; the body stays warm-coral"
  },
  "style_references": ["...standard array..."],
  "avoid": [
    "...standard avoid array...",
    "red color anywhere (warm-clay-deepened is NOT red)",
    "tears, sad downturned mouth, defeated posture",
    "alarm-coded surface treatment",
    "harsh shaming aesthetic"
  ],
  "output": {"format": "PNG transparent body on warm-clay surface", "resolution": "2048x2048", "aspect_ratio": "1:1"}
}
```

Save as `references/mascot/scenes/mascot-streak-break.png`.

## Step 1.4 — Vectorize the 6 scene states (4-6 hours)

For each PNG saved to `references/mascot/scenes/`:

1. **Open in Inkscape** (`File → Open → [scene].png`)
2. **Trace bitmap** (`Path → Trace Bitmap → Edge detection mode → Threshold 0.65 → Apply`)
3. **Hand-clean** — delete background paths, fix any AI artifacts (jagged outline edges, melted features, six-fingered hand artifacts if any slipped through)
4. **Lock colors** — select each filled region, set fill to exact OKLCH/hex from `emotional_spec_kleeve.md` §1 (NOT whatever color Inkscape's trace picked)
5. **Simplify paths** (`Path → Simplify` Ctrl+L, multiple passes — reduce node count by 60-80%)
6. **Add grain texture** — apply SVG `<feTurbulence>` filter at 6% opacity (manually edit XML or use Inkscape filter dialog)
7. **Export SVG** — save to `apps/mobile/assets/mascot/svg/mascot-{state}.svg`
8. **Optimize:** `npx svgo --multipass apps/mobile/assets/mascot/svg/*.svg`

Target file size per SVG: <30KB after optimization.

## Step 1.5 — Port to React Native Skia primitives (6-8 hours)

For each cleaned SVG in `apps/mobile/assets/mascot/svg/`, build a Skia TSX component in `apps/mobile/assets/mascot/`:

```tsx
// apps/mobile/assets/mascot/mascot-base.tsx
import React from 'react'
import { Canvas, Path, Group, Skia, Fill } from '@shopify/react-native-skia'

const MASCOT_BASE_OUTLINE = Skia.Path.MakeFromSVGString(`
  M120,200 C100,180 ... [paste SVG path data from optimized SVG, body outline]
`)
const MASCOT_BASE_FILL = Skia.Path.MakeFromSVGString(`
  M120,200 C100,180 ... [body fill region]
`)

export const MascotBase: React.FC<{ size?: number }> = ({ size = 200 }) => (
  <Canvas style={{ width: size, height: size }}>
    <Group>
      <Path path={MASCOT_BASE_FILL!} color="#EDA597" />
      <Path path={MASCOT_BASE_OUTLINE!} color="#1F1F26" style="stroke" strokeWidth={1.4} />
      {/* additional path layers: eyes, cheek highlight, mouth */}
    </Group>
  </Canvas>
)
```

**Alternative (faster, slightly less performant):** ship SVG directly via `react-native-svg` for non-critical scenes (mascot-shrug, mascot-streak-break, mascot-confetti). Reserve native Skia primitives for mascot-base (every screen) and mascot-submit (highest-frequency animation).

```tsx
// apps/mobile/assets/mascot/mascot-shrug.tsx (SVG fallback)
import React from 'react'
import { SvgXml } from 'react-native-svg'
import shrugXml from './svg/mascot-shrug.svg'  // via react-native-svg-transformer

export const MascotShrug: React.FC<{ size?: number }> = ({ size = 200 }) => (
  <SvgXml xml={shrugXml} width={size} height={size} />
)
```

## Step 1.6 — Anti-slop + cuteness verification (15 min)

For each of the 6 scene states, verify side-by-side against BOTH the anti-slop bans AND the cuteness mechanics:

**Anti-slop:**
- ✅ Body color is exactly `#EDA597` (not "coral-ish")
- ✅ Outline weight 1.2-1.6px, hand-drawn quality (not computer-perfect Bezier)
- ✅ No "AI smile" uncanny lip curl
- ✅ No six-fingered hands (mitten-style with three toe-bumps only)
- ✅ Same character across all 6 scenes (identity consistency)
- ✅ Risograph grain visible at ~6% opacity
- ✅ NOT default AI chibi (head ratio 1:1.2, not 1:1)
- ✅ NOT Duolingo Duo derivative
- ✅ NOT anime-derivative (no sparkle eyes, no tear-drops)

**Cuteness mechanics (NEW — load-bearing):**
- ✅ Bean-oval eye shape with ONE highlight dot upper-left of each iris
- ✅ Cheek blush is visible (two small peach ovals at ~40% opacity, color `#EE9A8A`)
- ✅ Soft `:3` or `ω` cat-style mouth in expressive scenes (submit / confetti / celebration); simple gentle curve in neutral/shrug/streak-break
- ✅ Pillow / pebble / clover-tuft silhouette with two small ear-nubs on top
- ✅ Reads as TASTEFULLY CUTE on first glance (sibling-test: would fit alongside Molang and Pusheen in a Sanrio lineup)
- ✅ Four colors max per scene (body / outline / blush / one optional accent)

If ANY scene fails verification, regenerate that scene with stricter `"avoid"` array and attach the 4 reference images PLUS the passing scenes as additional character references.

## Claude Code Handoff

```text
I've placed mascot Skia primitives at `apps/mobile/assets/mascot/mascot-{base,submit,shrug,confetti,celebration,streak-break}.tsx`, with SVG source-of-truth at `apps/mobile/assets/mascot/svg/`. Set up `react-native-svg-transformer` in `metro.config.js` for SVG imports. Build a `<Mascot state={MascotState} size={number} />` dispatcher component that maps the 6 scene states to the right primitive. Wire `mascot-submit` to the signature move #1 in `emotional_spec_kleeve.md` §4 (Skia path-drawing checkmark + Reanimated spring damping 18 stiffness 200). Wire `mascot-base` to splash screen blink animation. Reserve native Skia for mascot-base and mascot-submit (high-frequency); SVG-via-react-native-svg is acceptable for the other 4 scenes.
```

---

# ─────────────────────────────────────────────────────────
# WORKFLOW 2: 8 PRESET MASCOT AVATARS
# Priority: P0
# Estimated time: 1.5-2 days
# ─────────────────────────────────────────────────────────

8 avatar variants where the same character identity is preserved but body hue + texture varies. Founder can offer these as user-selectable avatars (per spec F-1.0.10).

## Step 2.1 — Lock the 8 hue variants (15 min)

Pick 8 hues in OKLCH lightness 0.72-0.78, chroma 0.08-0.12:

| Avatar # | OKLCH | Hex | Tone Name |
|---|---|---|---|
| 1 | `oklch(0.75 0.10 25)` | `#EDA597` | Warm-blush-coral (base mascot) |
| 2 | `oklch(0.78 0.10 60)` | `#F0BA7F` | Warm-peach |
| 3 | `oklch(0.74 0.10 90)` | `#D9B864` | Warm-buttercream |
| 4 | `oklch(0.72 0.09 140)` | `#9BC192` | Soft-sage |
| 5 | `oklch(0.74 0.09 210)` | `#90BFCD` | Soft-sky |
| 6 | `oklch(0.72 0.10 270)` | `#A8A6D0` | Soft-violet (use carefully — must NOT read indigo-500-slop; keep chroma low) |
| 7 | `oklch(0.74 0.10 340)` | `#DBA3B5` | Soft-rose |
| 8 | `oklch(0.55 0.04 80)` | `#90897A` | Warm-stone (neutral / non-color) |

If avatars 6 (soft-violet) reads too close to indigo-slop, drop to `oklch(0.72 0.08 295)` for a warmer purple, or swap out the avatar entirely.

## Step 2.2 — Generate avatar variants via Nano Banana Pro (4-6 hours)

For each avatar number, paste this prompt with the 4 reference images from Workflow 1 Step 1.2 attached:

```json
{
  "subject": "Klee — the same Kleeve mascot character from the reference images, but with body color changed to a different warm tone — avatar variant #2 warm-peach",
  "composition": "full-body portrait, three-quarter view, isolated on flat warm-paper background, identical pose and proportions to the base mascot reference",
  "action": "standing relaxed, neutral expression, looking warmly forward — identical to the front-view reference",
  "setting": "flat warm-paper #FAF1E0 background",
  "character_reference": "MUST exactly match the 4 reference images attached for: head-to-body ratio 1:1.4, eye style (simple dot or short-line), outline weight 1.2-1.6px ink, mitten-style limbs, three-quarter pose, hand-drawn outline quality. ONLY the body color changes — everything else is preserved.",
  "style": "[same as mascot-base]",
  "colors": {
    "body": "#F0BA7F (warm-peach for THIS avatar variant)",
    "outline": "#1F1F26 (preserved)",
    "highlight_cheeks": "#F4E4C2 (preserved)",
    "background": "#FAF1E0 (preserved)",
    "rule": "ONLY the body fill color changes; all other colors and elements identical to the base reference"
  },
  "style_references": ["...standard array..."],
  "avoid": [
    "...standard avoid array...",
    "drift in character identity (eyes, outline, proportion) — only body color should change"
  ],
  "output": {"format": "PNG transparent background", "resolution": "2048x2048", "aspect_ratio": "1:1"}
}
```

Replace `"body"` hex and avatar number for each of avatars 2-8 (avatar 1 is the base mascot, already done in Workflow 1).

Generate 4 variants per avatar, pick best, save as `references/mascot/avatars/avatar-{1-8}.png`.

## Step 2.3 — Vectorize + Skia port (4-6 hours)

Same workflow as Step 1.4 + 1.5 for each avatar. Since the character identity is preserved, you can clone the `mascot-base.tsx` Skia primitive and just swap the body fill color:

```tsx
// apps/mobile/assets/mascot/avatars/avatar-1.tsx
import { MascotBase } from '../mascot-base'
export const Avatar1: React.FC<{ size?: number }> = (props) => (
  <MascotBase {...props} bodyColor="#EDA597" />
)
// ... avatar-2.tsx through avatar-8.tsx with respective hex codes
```

Refactor `MascotBase` to accept `bodyColor` prop for this to work cleanly.

## Step 2.4 — Anti-slop verification

For all 8 avatars side-by-side:
- ✅ Identical character identity (only body color varies)
- ✅ All 8 hues are in OKLCH lightness 0.72-0.78 range (no jarring lightness shifts)
- ✅ Avatar 6 (soft-violet) does NOT read as indigo-500-slop
- ✅ Each avatar maintains the hand-drawn outline quality

## Claude Code Handoff

```text
I've placed 8 preset mascot avatars at `apps/mobile/assets/mascot/avatars/avatar-{1-8}.tsx`. Each is a thin wrapper around `MascotBase` with the body color overridden. Update the `profiles` table schema to add `mascot_avatar_id INTEGER CHECK (mascot_avatar_id BETWEEN 1 AND 8) DEFAULT 1`. Build an `<AvatarPicker />` component in onboarding that lets the user select one. Update `<Mascot state={...} />` to read avatar_id from profile context and render the corresponding Avatar component.
```

---

# ─────────────────────────────────────────────────────────
# WORKFLOW 3: APP ICON (iOS + Android adaptive)
# Priority: P0
# Estimated time: 4-6 hours
# ─────────────────────────────────────────────────────────

## Step 3.1 — Concept anchor (15 min)

The app icon is a **mascot bust crop** — head + upper torso of the base mascot on warm-paper background. NOT initials-on-gradient, NOT abstract geometric mark. The mascot IS the brand signal at icon scale.

## Step 3.2 — Generate via Nano Banana Pro (1 hour)

Attach the 4 reference images from Workflow 1 plus `mascot-base.png` and paste:

```json
{
  "subject": "an iOS app icon for Kleeve, featuring Klee (the Kleeve mascot character) from the reference images — the icon must read as TASTEFULLY CUTE at small sizes (60x60 px on home screen) without losing the hand-drawn risograph character",
  "composition": "square 1024x1024 app icon format, Klee's head and upper-torso bust filling 70-80% of the icon canvas, centered, no logotype, no text. Composition leans slightly into the bean-oval eyes and cheek blush so the cute reads at icon scale.",
  "action": "Klee is in a warm welcoming expression, soft ':3' or 'ω' cat-style mouth (quietly inviting, NOT neutral-flat, NOT exaggerated), bean-oval eyes with single highlight dots looking slightly toward camera, cheek blush clearly visible (this is what makes the icon read as cute at small size), head and shoulders only visible",
  "setting": "flat warm-paper-elevated #F4E4C2 background fills the entire icon canvas; soft subtle risograph grain at 5% opacity",
  "character_reference": "MUST exactly match the 4 reference images for character identity",
  "style": "hand-drawn vector quality with 1.2-1.6px ink outline, flat color fills, slight grain texture, NO 3D rendering, NO gradient",
  "lighting": "flat editorial, no shadow, no specular",
  "camera": "straight-on bust crop, slightly above eye-level to give the mascot a welcoming feel",
  "colors": {
    "body": "#EDA597",
    "outline": "#1F1F26",
    "cheek_highlight": "#F4E4C2 (subtle)",
    "background": "#F4E4C2 (paper-elevated, warmer than base paper for icon distinction)",
    "rule": "three colors max, flat fills, no gradients"
  },
  "style_references": ["...standard array..."],
  "avoid": [
    "...standard avoid array...",
    "initials-on-gradient app icon aesthetic",
    "centered-text-on-gradient SaaS app icon signature",
    "shadow under the mascot (icon is flat)",
    "any logotype or wordmark in the icon (mascot-only)",
    "iOS-default rounded-square treatment (Apple handles the mask, we don't bake it in)"
  ],
  "output": {
    "format": "PNG opaque background (no transparency for iOS icon)",
    "resolution": "2048x2048 (we'll downsample to 1024)",
    "aspect_ratio": "1:1"
  }
}
```

Generate 6-8 variants, pick best.

## Step 3.3 — Refine in Figma (1.5 hours)

1. Import best variant into Figma (1024×1024 frame)
2. Vectorize via Image Trace plugin OR Inkscape Trace Bitmap (export back to Figma)
3. Lock all colors to exact hex codes
4. Verify at small size — Figma's preview at 60×60 px should still read as "Klee" (the Kleeve mascot identity intact)
5. Export iOS variant:
   - 1024×1024 PNG (App Store submission)
   - No transparency
   - `apps/mobile/assets/icons/app-icon-1024.png`

## Step 3.4 — Android adaptive icon (1 hour)

Android needs separate foreground (mascot) + background (warm-paper-elevated solid):

1. **Foreground:** mascot bust on transparent background, 432×432 PNG, 108×108dp safe zone (mascot fits within center 66% to avoid edge clipping under various device masks)
   - Export from Figma at 432×432
   - Save to `apps/mobile/assets/icons/adaptive-foreground.png`
2. **Background:** solid `#F4E4C2` warm-paper-elevated
   - Either as XML color resource `<color name="ic_launcher_background">#F4E4C2</color>` in `colors.xml`
   - Or as 432×432 PNG `apps/mobile/assets/icons/adaptive-background.png`
3. **Monochrome (Android 13+ themed icon):** silhouette-only mascot for user-tinted icons
   - Export mascot outline as solid `#1F1F26` on transparent at 432×432
   - Save to `apps/mobile/assets/icons/adaptive-monochrome.png`

## Step 3.5 — iOS 26 Liquid Glass variant (0.5 hour, optional but recommended)

iOS 26 supports layered specular highlight icons (foreground + middleground + background):

1. **Foreground layer:** mascot outline + facial features (the "darkest" elements)
2. **Middleground layer:** mascot body fill (the warm-coral)
3. **Background layer:** warm-paper-elevated solid

Export each as 1024×1024 PNG. Place in `apps/mobile/assets/icons/liquid-glass/{foreground,middleground,background}.png`. Configure in `app.json` Expo config plugin or `Info.plist` for iOS 26+ adaptive icon.

## Step 3.6 — Favicon set (0.5 hour)

For web (`apps/web/public/favicons/`):
1. Export from Figma as 16×16, 32×32, 48×48, 180×180 PNG
2. Generate `favicon.ico` via RealFaviconGenerator OR `npx png-to-ico`
3. Export `safari-pinned-tab.svg` (mascot silhouette in `#1F1F26`)
4. Update `app/layout.tsx` with proper favicon `<link>` tags

## Claude Code Handoff

```text
I've placed app icon assets at `apps/mobile/assets/icons/`:
- iOS: app-icon-1024.png (opaque, no transparency)
- Android adaptive: adaptive-foreground.png + adaptive-background.png (or colors.xml entry) + adaptive-monochrome.png
- iOS 26 Liquid Glass: liquid-glass/{foreground,middleground,background}.png

And web favicons at `apps/web/public/favicons/`: 16/32/48/180.png + favicon.ico + safari-pinned-tab.svg.

Update `app.json` Expo config:
- `expo.icon: "./assets/icons/app-icon-1024.png"`
- `expo.ios.icon.dark` / `expo.ios.icon.light` for iOS 26+ variants
- `expo.android.adaptiveIcon.foregroundImage: "./assets/icons/adaptive-foreground.png"`
- `expo.android.adaptiveIcon.backgroundColor: "#F4E4C2"`
- `expo.android.adaptiveIcon.monochromeImage: "./assets/icons/adaptive-monochrome.png"`

Build and verify on iPhone 15 Pro simulator (iOS 26+) and Pixel 8 simulator (Android 14+).
```

---

# ─────────────────────────────────────────────────────────
# WORKFLOW 4: SPLASH SCREEN
# Priority: P0
# Estimated time: 2-3 hours
# ─────────────────────────────────────────────────────────

Splash is the mascot blink-and-wave from emotional_spec §3 visceral first paint. NOT a static centered logo.

## Step 4.1 — Static splash frame (1 hour)

For native iOS Storyboard + Android 12+ system splash, we need a static fallback PNG (the system shows this before Skia/Reanimated wake up):

Static splash = mascot-base centered on warm-paper `#FAF1E0`, no animation, no text.

Generate via Nano Banana Pro:

```json
{
  "subject": "a static splash screen for the Kleeve mobile app",
  "composition": "vertical 1284x2778 (iPhone Pro Max ratio), Kleeve mascot centered horizontally at 40% vertical position, mascot scale at 30% of canvas width, isolated against flat warm-paper background, no text, no logotype",
  "action": "the mascot is in a calm neutral standing pose with a soft warm smile, ready for a blink animation to begin",
  "setting": "flat warm-paper #FAF1E0 background fills the entire canvas, no other elements",
  "character_reference": "MUST exactly match the 4 reference images of Klee (the Kleeve mascot)",
  "style": "[same as mascot-base]",
  "colors": {
    "body": "#EDA597",
    "outline": "#1F1F26",
    "background": "#FAF1E0 (flat warm-paper, edge-to-edge)",
    "rule": "no gradient, no shadow, no text — pure flat splash"
  },
  "style_references": ["...standard array..."],
  "avoid": [
    "...standard avoid array...",
    "any text or logotype",
    "centered-logo-on-white SaaS splash",
    "gradient backgrounds",
    "loading spinner or progress indicator",
    "shadow under the mascot"
  ],
  "output": {
    "format": "PNG opaque",
    "resolution": "1284x2778 (iPhone Pro Max) plus 2732x2048 (iPad Pro), 1080x2400 (Android phone)",
    "aspect_ratio": "varies per output"
  }
}
```

Export 3 device variants from the same Figma frame: iPhone Pro Max (1284×2778), iPad Pro (2732×2048), Android phone (1080×2400). Use `expo-splash-screen` config to map them.

## Step 4.2 — Mascot blink animation (Skia at runtime, 1.5 hours)

The system splash hands off to the Skia mascot scene which performs the blink + small wave (per emotional_spec §3 visceral). Implement in `apps/mobile/components/SplashTransition.tsx`:

```tsx
import { useEffect } from 'react'
import { Canvas, Path, Group } from '@shopify/react-native-skia'
import Animated, { useSharedValue, withSequence, withSpring, withTiming, runOnJS } from 'react-native-reanimated'
import { MascotBase } from '@/assets/mascot/mascot-base'

export const SplashTransition: React.FC<{ onComplete: () => void }> = ({ onComplete }) => {
  const eyeScale = useSharedValue(1)
  const armRotation = useSharedValue(0)

  useEffect(() => {
    // Blink: eyes scale 1 → 0.05 → 1 over 240ms
    eyeScale.value = withSequence(
      withTiming(0.05, { duration: 80 }),
      withTiming(1, { duration: 160 })
    )
    // Small wave: arm rotates 0 → 15° → 0 over 480ms, then hands off
    armRotation.value = withSequence(
      withTiming(15, { duration: 240 }),
      withSpring(0, { damping: 18, stiffness: 200 }, () => runOnJS(onComplete)())
    )
  }, [])

  return <MascotBase eyeScale={eyeScale} armRotation={armRotation} />
}
```

The `MascotBase` Skia primitive accepts `eyeScale` and `armRotation` as animated props that drive the Skia Path transforms.

## Step 4.3 — Configure expo-splash-screen (0.5 hour)

Update `app.json`:

```json
{
  "expo": {
    "plugins": [
      ["expo-splash-screen", {
        "image": "./assets/icons/splash-mascot.png",
        "backgroundColor": "#FAF1E0",
        "resizeMode": "contain",
        "dark": {
          "image": "./assets/icons/splash-mascot-dark.png",
          "backgroundColor": "#2B221E"
        }
      }]
    ]
  }
}
```

Generate the dark-mode splash variant via the same Nano Banana Pro prompt but with `"background": "#2B221E (warm-charcoal dark mode base)"` and `"body": "#EDA597 (preserved — primary stays at L0.75 on dark BG for 13.5:1 contrast)"`.

## Claude Code Handoff

```text
I've placed splash assets at `apps/mobile/assets/icons/splash-mascot.png` (light) and `splash-mascot-dark.png` (dark) at 1284x2778 / 2732x2048 / 1080x2400 device variants. Wire `expo-splash-screen` per `app.json` config above. Implement `<SplashTransition>` in `apps/mobile/app/_layout.tsx` to run the Skia blink + wave animation between cold-start and home-screen mount, with a max-duration safety timeout of 1200ms. Total cold-start to mascot-blink-complete budget: 800ms per emotional_strategy §3.
```

---

# ─────────────────────────────────────────────────────────
# WORKFLOW 5: ILLUSTRATIONS (empty states, error state, onboarding)
# Priority: P1
# Estimated time: 4-6 hours total
# ─────────────────────────────────────────────────────────

## Step 5.1 — Empty state: no group yet (1 hour)

```json
{
  "subject": "an empty-state illustration for the Kleeve app, showing a moment when the user has no group yet",
  "composition": "vertical portrait composition 600x800, Kleeve mascot centered slightly low in the frame, with a small empty thought-bubble or speech-bubble shape gently floating above and to one side, asymmetric layout (not centered-symmetric), warm-paper background with subtle grain",
  "action": "the mascot is in a soft curious neutral pose, looking slightly upward toward the empty bubble, with one arm raised as if gesturing 'who should be here?', expression is invitational and warm — NOT lonely, NOT sad, NOT shaming the user for not having a group",
  "setting": "flat warm-paper #FAF1E0 background with 6% risograph grain texture overlay, asymmetric arrangement",
  "character_reference": "MUST exactly match the 4 reference images for character identity",
  "style": "hand-drawn vector with risograph grain, 1.2-1.6px ink outline, flat color fills",
  "colors": {
    "mascot_body": "#EDA597",
    "outline": "#1F1F26",
    "bubble_outline": "#1F1F26 (same ink color, dashed or dotted stroke style)",
    "background": "#FAF1E0",
    "rule": "two-color illustration: warm-coral mascot + ink outline + dotted bubble; no other colors"
  },
  "style_references": ["...standard array..."],
  "avoid": [
    "...standard avoid array...",
    "generic 'person scratching head' empty-state cliché",
    "404 robot character cliché",
    "broken plug or unplugged-cord cliché",
    "empty cardboard box cliché",
    "shameful or lonely emotional read",
    "exclamation mark or question mark as graphic element"
  ],
  "output": {"format": "PNG transparent background", "resolution": "1200x1600", "aspect_ratio": "3:4"}
}
```

Variants to produce (same prompt template, change `"action"` and bubble content):

| State | Action description | Bubble content |
|---|---|---|
| No group yet | Mascot curious, gesturing at empty space | Empty dotted-outline speech bubble |
| Group thread day 1, no submissions | Mascot patient, looking at empty thread | Small "..." dotted bubble |
| Empty history | Mascot relaxed, looking at empty timeline | Empty horizontal dotted line |
| No friends online | Mascot calm, alone but not lonely | No bubble, just mascot with subtle "presence pulse" radial dot |

Vectorize each in Inkscape, save to `apps/mobile/assets/illustrations/empty-states/{state}.svg`.

## Step 5.2 — Error state illustration (0.5 hour)

```json
{
  "subject": "a gentle error-state illustration for the Kleeve app, used when network is down or an operation failed",
  "composition": "vertical portrait 600x800, mascot centered, doing the soft-shrug pose from the reference scene state",
  "action": "the mascot is doing the apologetic shrug from the mascot-shrug reference scene — arms slightly raised, mitten palms up, warm understanding expression, NOT sad, NOT alarming the user",
  "setting": "flat warm-paper #FAF1E0 background",
  "character_reference": "MUST exactly match the mascot-shrug scene reference",
  "style": "[same as empty-states]",
  "colors": "[same as mascot-shrug — warm-coral body, ink outline, no error-red anywhere]",
  "style_references": ["...standard array..."],
  "avoid": [
    "...standard avoid array...",
    "red color anywhere",
    "exclamation mark triangle alert sign",
    "broken connection wires illustration",
    "generic 404 robot",
    "frowning face on mascot"
  ],
  "output": {"format": "PNG transparent background", "resolution": "1200x1600", "aspect_ratio": "3:4"}
}
```

Single illustration reused across all error states. Save to `apps/mobile/assets/illustrations/error-state.svg`.

## Step 5.3 — Onboarding visuals (4 steps, 2 hours)

Per emotional_spec §3 onboarding: numerical hierarchy `01. 02. 03. 04.` replaces icons; mascot pose per step.

| Step | Mascot pose | Numerical hierarchy |
|---|---|---|
| 01. Pick your habit | Mascot pointing toward an empty habit-name field | `01.` in Bricolage Grotesque, large |
| 02. Invite 2-4 friends | Mascot gesturing with 2-3 small avatar shapes nearby | `02.` |
| 03. Show up for 5 minutes a day | Mascot next to a soft timer-ring visual | `03.` |
| 04. (optional) Real-money mode? | Mascot calm/neutral, money-neutral surface tone | `04.` |

Generate each via Nano Banana Pro with the standard prompt template + step-specific action + numerical hierarchy in Bricolage Grotesque (Nano Banana Pro renders text well — explicitly request font and styling).

Save to `apps/mobile/assets/illustrations/onboarding/step-{1-4}.svg`.

## Claude Code Handoff

```text
I've placed empty-state illustrations at `apps/mobile/assets/illustrations/empty-states/{no-group,thread-day-1,empty-history,no-friends}.svg`, the error-state illustration at `apps/mobile/assets/illustrations/error-state.svg`, and onboarding illustrations at `apps/mobile/assets/illustrations/onboarding/step-{1-4}.svg`. Build a `<EmptyState illustration="no-group" headline="No squad yet." description="Make one or paste an invite code." cta={...} />` component that renders the SVG via `react-native-svg` (set up `react-native-svg-transformer` in metro.config.js). Reuse the same pattern for `<ErrorState />` and `<OnboardingStep step={1-4} />`.
```

---

# ─────────────────────────────────────────────────────────
# WORKFLOW 6: ACHIEVEMENT / CELEBRATION ANIMATIONS (Skia particle system)
# Priority: P1
# Estimated time: 2-3 hours
# ─────────────────────────────────────────────────────────

**NOT Lottie. NOT Rive.** Code-driven Skia particle system per emotional_spec §4.

## Step 6.1 — Build the confetti particle system

`apps/mobile/components/ConfettiBurst.tsx`:

```tsx
import { Canvas, Group, Rect, Skia, useValue, useComputedValue, runTiming } from '@shopify/react-native-skia'
import { useEffect, useMemo } from 'react'

const PARTICLE_COUNT = 24
const PARTICLE_COLORS = ['#C2701D', '#ECA13F', '#F2BC7B', '#EDA89B', '#EE9A8A'] // accent + primary tones
const GRAVITY = 0.8
const LIFETIME_MS = 800

export const ConfettiBurst: React.FC<{ trigger: boolean }> = ({ trigger }) => {
  const particles = useMemo(() => Array.from({ length: PARTICLE_COUNT }, (_, i) => ({
    id: i,
    startX: 200 + (Math.random() - 0.5) * 40,  // emit from center with slight spread
    startY: 200,
    velX: (Math.random() - 0.5) * 200,
    velY: -300 - Math.random() * 100,
    color: PARTICLE_COLORS[i % PARTICLE_COLORS.length],
    rotation: Math.random() * Math.PI,
    emitDelay: Math.random() * 200,  // staggered emit
  })), [])

  // ... animation logic using useValue + useComputedValue with elapsed time, gravity, lifetime fade ...

  return (
    <Canvas style={{ position: 'absolute', inset: 0, pointerEvents: 'none' }}>
      <Group>
        {particles.map(p => <Rect key={p.id} {...particleProps(p)} color={p.color} />)}
      </Group>
    </Canvas>
  )
}
```

## Step 6.2 — Wire to signature move #1

Hook `<ConfettiBurst trigger={isFirstSubmit || isMilestoneDay} />` into the timer-submit flow per emotional_spec §4 signature move #1. Confetti fires at 680ms after submit (overlapping with the tail of the mascot checkmark-draw).

## Anti-slop verification
- ✅ NOT a Lottie file
- ✅ Particles use warm accent + primary palette only (no cool colors)
- ✅ 24 particles, contained spread, NOT screen-filling
- ✅ Reduced-motion fallback suppresses entirely (per emotional_spec §4 table)

## Claude Code Handoff

```text
I've built the Skia confetti particle system at `apps/mobile/components/ConfettiBurst.tsx`. Wire it into the submit flow (`apps/mobile/screens/Timer.tsx` or wherever submit is handled): fire `<ConfettiBurst trigger={...} />` at 680ms after submit on first-time-ever AND milestone days (7/30/100). Suppress on `useReducedMotion()` per emotional_spec §4 reduced-motion table — render a static `<MilestoneBadge>` instead.
```

---

# ─────────────────────────────────────────────────────────
# WORKFLOW 7: SOUND (3 chimes + milestone AHAP)
# Priority: P2
# Estimated time: 4-6 hours
# ─────────────────────────────────────────────────────────

## Step 7.1 — Source 3 base sounds from CC0 libraries (1 hour)

1. **Pixabay** (pixabay.com/sound-effects) — search "warm bell", "soft chime", "ascending chime"
2. **Freesound** (freesound.org) — filter to CC0 only, search same terms
3. Download 4-6 candidates for each chime

## Step 7.2 — Edit in Audacity (2 hours)

Per emotional_spec §6 specs:

### `kleeve_start.mp3` (120ms, sonic logo)

1. Import candidate WAV/MP3
2. Select 120ms section (use Selection Toolbar, set length to `0.120s`)
3. **Fade In** (Effect → Fade In, first 5ms)
4. **Fade Out** (Effect → Fade Out, last 5ms)
5. **Normalize** (Effect → Normalize → -3dB peak)
6. **Export** as MP3 128kbps mono (File → Export → Export as MP3)
7. Save to `apps/mobile/assets/sounds/kleeve_start.mp3` — verify file size <8KB

### `kleeve_submit.mp3` (180ms, two-note ascending)

Same workflow, 180ms target. If a single CC0 source can't produce a clean ascending two-note, splice two single-note sources in Audacity (cut, position, crossfade).

### `kleeve_milestone.mp3` (600ms, three-note ascending chord)

Same workflow, 600ms target. Layer 3 notes in 3 Audacity tracks (Edit → Duplicate, shift by 80ms each), mix down to mono.

## Step 7.3 — Fallback: ElevenLabs Sound Effects (1 hour, if CC0 insufficient)

If CC0 sources don't deliver, generate via ElevenLabs Sound Effects free tier:

```text
A short, warm bell-ping sound effect, 120 milliseconds duration. Single soft note around G4 frequency. Slight reverb tail. Soft attack, gentle decay. Mono. Like the gentle 'ping' of starting a meditation timer. NO percussion, NO drums.
```

Variations for each chime:
- **Start chime:** `"warm soft bell ping, single note G4, brief, slight reverb"`
- **Submit chime:** `"two-note ascending chime C5 to E5, soft attack, 180ms"`
- **Milestone chime:** `"three-note ascending chord C5 E5 G5 with brief sparkle layer, 600ms, warm bell timbre"`

Generate 4-6 variants per chime, edit in Audacity for exact length + normalize.

## Step 7.4 — License audit (15 min)

Create `apps/mobile/assets/sounds/LICENSES.md`:

```markdown
# Kleeve Sound Asset Licenses

## kleeve_start.mp3
- Source: [Pixabay URL / Freesound URL / ElevenLabs prompt]
- License: CC0 / Public Domain / ElevenLabs Free Tier Commercial Use
- Sourced: 2026-05-XX
- Editor: Founder via Audacity (trim, fade, normalize)

## kleeve_submit.mp3
[...]

## kleeve_milestone.mp3
[...]
```

## Step 7.5 — Milestone AHAP haptic (0.5 hour)

Already specified in emotional_spec §5. Save the JSON to `apps/mobile/assets/haptics/kleeve_milestone.ahap` verbatim from spec.

## Claude Code Handoff

```text
I've placed 3 sound files at `apps/mobile/assets/sounds/kleeve_{start,submit,milestone}.mp3` (MP3 128kbps mono, <8KB each), the license audit at `apps/mobile/assets/sounds/LICENSES.md`, and the milestone AHAP at `apps/mobile/assets/haptics/kleeve_milestone.ahap`. Install `expo-audio` (NOT deprecated `expo-av`). Wire:
- `kleeve_start.mp3` to Timer.tsx start tap (also `Haptics.impactAsync(Light)`)
- `kleeve_submit.mp3` to Timer.tsx submit confirmed (`Haptics.impactAsync(Medium)` at 0ms, `Haptics.notificationAsync(Success)` at 480ms)
- `kleeve_milestone.mp3` to milestone-broadcast component on 7d/30d/100d (paired with AHAP via expo-haptics)
Audio OFF by default — read `settings.soundEnabled` before playback. Respect `AVAudioSession.Category.ambient` on iOS and DND on Android.
```

---

# ─────────────────────────────────────────────────────────
# WORKFLOW 8: WEB MARKETING HERO ILLUSTRATION
# Priority: P1
# Estimated time: 2-3 hours
# ─────────────────────────────────────────────────────────

Asymmetric 60/40 hero per emotional_spec §9 — mascot left, copy right.

## Step 8.1 — Generate via Nano Banana Pro

```json
{
  "subject": "a marketing landing page hero illustration for the Kleeve mobile app, featuring Klee (the Kleeve mascot) in a scene that suggests friend-group accountability",
  "composition": "horizontal landscape 1200x800, asymmetric 60/40 split — the LEFT 60% contains a large hero scene of Klee at approximately 520px scale doing a warm greeting wave, with 2-3 smaller floating Klee-avatar shapes (different warm tones, same character identity) in soft conversation nearby; the RIGHT 40% is INTENTIONALLY LEFT VISUALLY EMPTY (no decoration, no abstract shapes) — it will be filled with copy in the web layout. Background is flat warm-paper-elevated with subtle 6% grain.",
  "action": "Klee is mid-wave, looking warmly toward the implied reader, while smaller floating Klee-avatar shapes (the friend variants) float at slight rotations as if mid-conversation; the scene communicates 'this is a thing my friends and I are doing together'",
  "setting": "flat warm-paper-elevated #F4E4C2 background with 6% risograph grain overlay, no environment details, no objects beyond the mascots",
  "character_reference": "MUST exactly match the 4 reference images for character identity for ALL mascots in the scene; the smaller floating friend mascots use 3 different body hues from the 8-avatar palette (peach #F0BA7F, sage #9BC192, rose #DBA3B5) but otherwise identical character identity",
  "style": "[same as mascot-base], slight 1px CMYK-misregistration offset on the smaller floating mascots for character",
  "lighting": "flat editorial, no shadow, no rim light",
  "camera": "head-on, eye-level on primary mascot, smaller mascots at slight angles around it",
  "colors": {
    "primary_mascot_body": "#EDA597",
    "friend_mascots": ["#F0BA7F", "#9BC192", "#DBA3B5"],
    "outline": "#1F1F26",
    "background": "#F4E4C2 (paper-elevated)",
    "rule": "no cool colors, no purple, no blue; warm palette only"
  },
  "style_references": ["...standard array..."],
  "avoid": [
    "...standard avoid array...",
    "centered hero composition (we explicitly want asymmetric 60/40)",
    "filling the right 40% with anything",
    "diverse-team-on-laptops stock photography",
    "hands-on-keyboard photography",
    "abstract gradient blobs as background decoration",
    "any text or logotype (copy is layered in the web layout, not in the illustration)"
  ],
  "output": {"format": "PNG transparent background", "resolution": "2400x1600", "aspect_ratio": "3:2"}
}
```

## Step 8.2 — Vectorize + optimize (1 hour)

Inkscape Trace Bitmap → SVG → SVGO. Target <80KB after optimization (web hero has slightly looser budget than mobile illustrations).

Save to `apps/web/public/illustrations/hero.svg`.

## Claude Code Handoff

```text
I've placed the marketing hero illustration at `apps/web/public/illustrations/hero.svg`. Build the asymmetric hero in `apps/web/app/page.tsx`:
- Grid: 60% / 40% (CSS grid template columns)
- Left column: <img src="/illustrations/hero.svg" alt="Kleeve mascot greeting friend avatars" />
- Right column: H1 + subhead + CTA pair, Bricolage Grotesque display, Plus Jakarta Sans body, copy from emotional_spec §7 microcopy patterns
- Background: --c-paper-elevated #F4E4C2 with SVG <feTurbulence> grain overlay at 6%
- NO three-column feature grid below the hero; numerical hierarchy 01./02./03. for sections
```

---

# ─────────────────────────────────────────────────────────
# WORKFLOW 9: OG / SOCIAL CARDS
# Priority: P2
# Estimated time: 1 hour
# ─────────────────────────────────────────────────────────

## Step 9.1 — Generate via Nano Banana Pro

```json
{
  "subject": "an Open Graph social card for Kleeve, featuring Klee (the Kleeve mascot) and brand copy",
  "composition": "horizontal 1200x630 social card, asymmetric layout — left 45% contains Klee doing a warm wave at ~340px scale; right 55% contains brand copy in two lines: a large headline in Bricolage Grotesque and a smaller subhead in Plus Jakarta Sans; copy and mascot are visually balanced but NOT centered-symmetric",
  "action": "Klee in warm welcoming wave, copy reads 'Build habits with your actual friends.' as headline and 'Invite-only group accountability. Show up for 5 minutes a day.' as subhead",
  "setting": "flat warm-paper-elevated #F4E4C2 background with 6% risograph grain",
  "character_reference": "MUST exactly match the 4 reference images of Klee (the Kleeve mascot)",
  "style": "hand-drawn vector mascot + crisp legible typography (Nano Banana Pro renders text well at this scale — use Bricolage Grotesque-style display for headline and a friendly sans like Plus Jakarta Sans for subhead)",
  "colors": {
    "mascot_body": "#EDA597",
    "outline": "#1F1F26",
    "headline_text": "#1F1F26 (soft warm ink)",
    "subhead_text": "#4A4A52 (mid-ink)",
    "background": "#F4E4C2 (paper-elevated)",
    "rule": "no gradient, no accent colors, just mascot + ink type on warm-paper-elevated"
  },
  "typography": {
    "headline_font_style": "geometric humanist sans-serif similar to Bricolage Grotesque, weight 600, slight letter-spacing tight",
    "subhead_font_style": "warm humanist sans-serif similar to Plus Jakarta Sans, weight 400, line-height 1.5"
  },
  "style_references": ["...standard array..."],
  "avoid": [
    "...standard avoid array...",
    "centered-text-on-gradient OG card aesthetic",
    "stock-app-screenshot composition",
    "logo cloud or feature-bullet aesthetic",
    "Twitter-default sans-serif typography rendering"
  ],
  "output": {"format": "PNG opaque", "resolution": "1200x630", "aspect_ratio": "1.91:1"}
}
```

Save to `apps/web/public/og-card.png`.

## Step 9.2 — Twitter/X variant

Same prompt with `"resolution": "1200x600"` and `"aspect_ratio": "2:1"`. Save to `apps/web/public/twitter-card.png`.

## Claude Code Handoff

```text
I've placed OG cards at `apps/web/public/og-card.png` (1200x630) and `apps/web/public/twitter-card.png` (1200x600). Update `apps/web/app/layout.tsx` metadata:

export const metadata = {
  title: 'Kleeve — Build habits with your actual friends',
  description: 'Invite-only group accountability. Show up for 5 minutes a day.',
  openGraph: { images: ['/og-card.png'] },
  twitter: { card: 'summary_large_image', images: ['/twitter-card.png'] },
}
```

---

# ─────────────────────────────────────────────────────────
# WORKFLOW 10: GROUP THREAD PRESENCE PULSE
# Priority: P1 (signature move #2 from emotional_spec §4)
# Estimated time: 1 hour
# ─────────────────────────────────────────────────────────

Pure code, no asset — included here for completeness. Per emotional_spec §4 signature move #2.

`apps/mobile/components/PresencePulse.tsx`:

```tsx
import Animated, { useSharedValue, useAnimatedStyle, withRepeat, withTiming, Easing } from 'react-native-reanimated'
import { useEffect } from 'react'
import { useReducedMotion } from 'react-native-accessibility-info'  // or hook

export const PresencePulse: React.FC<{ active: boolean }> = ({ active }) => {
  const opacity = useSharedValue(0.4)
  const scale = useSharedValue(1)
  const reduceMotion = useReducedMotion()

  useEffect(() => {
    if (!active) return
    if (reduceMotion) {
      opacity.value = 0.4
      return
    }
    opacity.value = withRepeat(
      withTiming(0, { duration: 600, easing: Easing.in(Easing.ease) }),
      -1, true
    )
    scale.value = withRepeat(
      withTiming(1.6, { duration: 600, easing: Easing.out(Easing.ease) }),
      -1, true
    )
  }, [active, reduceMotion])

  const animatedStyle = useAnimatedStyle(() => ({
    opacity: opacity.value,
    transform: [{ scale: scale.value }],
  }))

  return <Animated.View style={[styles.pulse, animatedStyle]} />
}

const styles = {
  pulse: {
    position: 'absolute',
    width: 16, height: 16, borderRadius: 8,
    backgroundColor: '#EE9A8A',  // primary-400 at 0.4 opacity via opacity prop
  }
}
```

Wire to Supabase Realtime presence channel — fires `active=true` when friend's device is connected.

## Claude Code Handoff

```text
I've built `<PresencePulse active={isFriendOnline} />` at `apps/mobile/components/PresencePulse.tsx`. Wire to Supabase Realtime presence channel — subscribe per friend in the active group, set `isFriendOnline={true}` when their device emits a presence-state event. Render as an absolute-positioned overlay on the friend's avatar in the group thread (`apps/mobile/screens/GroupThread.tsx`). Honor reduced-motion fallback (static 0.4-opacity dot).
```

---

# ─────────────────────────────────────────────────────────
# WORKFLOW 11: REPO STRUCTURE & OPTIMIZATION CHECKLIST
# ─────────────────────────────────────────────────────────

## Final folder layout

```
apps/
  mobile/
    assets/
      mascot/
        CHARACTER_BIBLE.md
        mascot-base.tsx                 (native Skia primitive)
        mascot-submit.tsx               (native Skia primitive)
        mascot-shrug.tsx                (SVG via react-native-svg)
        mascot-confetti.tsx             (SVG via react-native-svg)
        mascot-celebration.tsx          (SVG via react-native-svg)
        mascot-streak-break.tsx         (SVG via react-native-svg)
        svg/
          mascot-{base,submit,shrug,confetti,celebration,streak-break}.svg
        avatars/
          avatar-{1-8}.tsx
        stickers/
          {hat,journal,badge-7d,badge-30d,badge-100d}.svg
      illustrations/
        empty-states/
          {no-group,thread-day-1,empty-history,no-friends}.svg
        error-state.svg
        onboarding/
          step-{1-4}.svg
      icons/
        app-icon-1024.png
        adaptive-foreground.png
        adaptive-monochrome.png
        liquid-glass/{foreground,middleground,background}.png
        splash-mascot.png
        splash-mascot-dark.png
      sounds/
        kleeve_start.mp3
        kleeve_submit.mp3
        kleeve_milestone.mp3
        LICENSES.md
      haptics/
        kleeve_milestone.ahap
  web/
    public/
      illustrations/hero.svg
      og-card.png
      twitter-card.png
      favicons/{16,32,48,180}.png + favicon.ico + safari-pinned-tab.svg

references/                              (NEVER ship — Nano Banana Pro raw outputs)
  mascot/
    360/{01-front,02-three-quarter-right,03-side-right,04-back}.png
    scenes/{mascot-base,mascot-submit,...}.png
    avatars/{avatar-1...avatar-8}.png
```

## Optimization commands

```bash
# SVG optimization (run after every Inkscape export)
npx svgo --multipass apps/mobile/assets/mascot/svg/*.svg
npx svgo --multipass apps/mobile/assets/illustrations/**/*.svg
npx svgo --multipass apps/web/public/illustrations/*.svg

# PNG optimization (run before commit on every PNG)
npx @squoosh/cli --webp '{"quality":85}' apps/mobile/assets/icons/*.png
# Or use squoosh.app GUI for one-offs

# Audio (already MP3 128kbps from Audacity export — no further compression)

# Verify file sizes
find apps/mobile/assets -name '*.png' -size +100k -exec ls -lh {} \;
find apps/mobile/assets -name '*.svg' -size +50k -exec ls -lh {} \;
```

## Per-asset size budgets

| Asset Class | Target Size | Hard Limit |
|---|---|---|
| Mascot SVG (per scene) | <30KB | 60KB |
| Empty/error/onboarding SVG | <40KB | 80KB |
| App icon PNG 1024 | <80KB | 200KB |
| Adaptive foreground PNG 432 | <30KB | 60KB |
| Splash mascot PNG (per device) | <120KB | 300KB |
| Sound MP3 (per chime) | <8KB | 15KB |
| Web hero SVG | <80KB | 150KB |
| OG card PNG 1200x630 | <100KB | 200KB |

---

# ─────────────────────────────────────────────────────────
# ANTI-SLOP VERIFICATION CHECKLIST (apply to EVERY generated asset)
# ─────────────────────────────────────────────────────────

Before committing any AI-generated → vectorized → ported asset to the repo, run this checklist:

- [ ] Character identity matches the 360° reference sheet (consistency check)
- [ ] Body color is exactly `#EDA597` (or correct avatar hex for variants)
- [ ] Outline weight is 1.2-1.6px, hand-drawn quality (not computer-perfect Bezier)
- [ ] **Bean-oval eye shape preserved, ONE highlight dot upper-left of each iris** (not anime-large, no sparkle layers, no tear-drops)
- [ ] **Cheek blush visible — two small peach ovals (#EE9A8A at 40% opacity)** — load-bearing cuteness, MUST NOT be missing
- [ ] **Mouth treatment correct for the scene** — `:3` / `ω` in expressive scenes (submit/confetti/celebration), simple gentle curve in neutral/shrug/streak-break, NEVER "AI smile" uncanny lip curl
- [ ] **Pillow / clover-tuft silhouette preserved** — head:body 1:1.2, two small ear-nubs on top
- [ ] **Tastefully-cute on first glance** — would sit comfortably alongside Molang / Pusheen / Soot Sprites in a Sanrio lineup
- [ ] No six-fingered hands — mitten-style with three toe-bumps preserved
- [ ] No melted facial features
- [ ] No gibberish text on body / clothing / background
- [ ] No purple-blue gradient anywhere
- [ ] No indigo-500, violet-500, or default Tailwind palette
- [ ] No `rounded-xl` everywhere look (radius varies per system)
- [ ] No Lucide trinity (cube/check/lightning) in any asset
- [ ] No emoji bullets in any composition
- [ ] No isometric voxel scene
- [ ] No glassy translucent 3D shapes
- [ ] No smooth-gradient blob illustration
- [ ] No default Storyset/Humaaans/unDraw/Open Doodles signature
- [ ] No `hover:scale-105` or `animate-pulse` baked into illustration
- [ ] No Lottie/Rive references (code-driven motion only)
- [ ] Colors match emotional_spec_kleeve.md §1 exact hex codes
- [ ] Risograph grain texture visible at 5-8% opacity (where applicable)
- [ ] File size within per-asset budget (§Workflow 11)
- [ ] SVG optimized via `npx svgo --multipass`
- [ ] PNG compressed via Squoosh

If ANY check fails → regenerate with stricter `"avoid"` array. Never ship.

---

# ─────────────────────────────────────────────────────────
# TIME BUDGET SUMMARY
# ─────────────────────────────────────────────────────────

| Workflow | P | Time | Cumulative |
|---|---|---|---|
| 1. Mascot Foundation (360° sheet + 6 scenes) | P0 | 2-2.5 days | 2.5 days |
| 2. 8 Preset Mascot Avatars | P0 | 1.5-2 days | 4.5 days |
| 3. App Icon (iOS + Android + web favicons) | P0 | 4-6 hours | 5 days |
| 4. Splash Screen | P0 | 2-3 hours | 5.5 days |
| 5. Illustrations (empty/error/onboarding) | P1 | 4-6 hours | 6 days |
| 6. Achievement / Celebration (Skia confetti) | P1 | 2-3 hours | 6.5 days |
| 7. Sound (3 chimes + AHAP) | P2 | 4-6 hours | 7.5 days |
| 8. Web Marketing Hero | P1 | 2-3 hours | 8 days |
| 9. OG / Social Cards | P2 | 1 hour | 8 days |
| 10. Presence Pulse (code, no asset) | P1 | 1 hour | 8 days |
| 11. App Store + Preview Video (forward to 06) | P0 | 2 days | 10 days |

**Realistic total: 10-12 working days** of focused asset production (Nano Banana Pro accelerated). In calendar time parallel to feature development: ~3-4 weeks.

---

# ─────────────────────────────────────────────────────────
# OPEN QUESTIONS & RISKS
# ─────────────────────────────────────────────────────────

1. **Nano Banana Pro character consistency across 14+ scenes (6 base + 8 avatars).** If consistency drift starts past ~10 generations, founder should regenerate the 4 reference images at higher fidelity and re-anchor subsequent scenes to those. Worst case: commission illustrator for the last 4 avatars only ($200-300 one-time).

2. **Skia primitive port time per scene.** Estimate is 0.5-1 day per scene; if real-world port time is significantly higher, fall back to `react-native-svg` for non-critical scenes. Performance test mascot-base + mascot-submit at 60fps before locking native Skia commitment.

3. **CC0 sound source availability for warm-bell-ping at G4.** If Pixabay/Freesound don't deliver, fall back to ElevenLabs Sound Effects (free tier) with explicit prompt. If still insufficient at v1.0, defer milestone chime to v1.1 sound-designer commission rather than shipping generic ding.

4. **Nano Banana Pro text rendering quality on OG cards.** If headline typography reads as "AI-rendered text" rather than crisp display type, render copy as actual web `<h1>` over the illustration in Next.js layout — generate OG cards with empty copy zones and overlay text dynamically via @vercel/og at build time.

5. **iOS 26 Liquid Glass icon variant.** Apple's three-layer specular highlight spec is new (Nov 2025); verify against current `expo.ios.icon` config plugin support before locking. May need to bake the layered variant as a single composed PNG until Expo SDK catches up.

6. **Risograph grain rendering on real devices.** SVG `<feTurbulence>` performance is acceptable on web but heavy on mobile WebView. For mobile illustrations, bake grain into the PNG during Inkscape export rather than applying as runtime SVG filter.

---

**Status:** v1.0 asset production walkthrough. Mascot Foundation (Workflow 1) is the unblocker — execute that first, then everything downstream depends on the 4 reference images + 6 scene states. Forward to `06_appstore_assets.md` for App Store + Play Store + preview video after Workflows 1-10 are complete.
