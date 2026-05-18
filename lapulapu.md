# Klee Accessory Handoff — Designer → Implementation

> Sibling of [asset_production.md](asset_production.md). This is the contract between the human designer (working in **GoPaint on Huawei MatePad**) and the Kleeve mobile codebase for delivering Klee's accessory art. The Nano Banana Pro AI pipeline in `asset_production.md` remains in force for marketing illustration; accessory character art is human-made and follows this doc instead.

---

## 1. Context

- Designer tool: **GoPaint** (Huawei native, raster-only painting app, no SVG export, no layered file export beyond its own format). Output: PNG / JPG.
- Mascot: Klee (see [CHARACTER_BIBLE.md](../apps/mobile/assets/mascot/CHARACTER_BIBLE.md) and `asset_production.md` §Workflow 1 for visual identity and cuteness lock).
- Scope: **12 accessories** are in progress, each delivered as an **8-pose set** (= 96 images at full inventory). First two reviewed: dino-hoodie and banana-leaf.

This shapes three decisions: **format**, **architecture**, and **handoff procedure**.

---

## 2. Format decision: PNG primary

We are **not** converting to SVG. Reasoning:

| Consideration | Verdict |
|---|---|
| GoPaint native SVG export | Not supported (raster app) |
| Auto-tracing PNG → SVG (Vectorizer.AI / Illustrator Image Trace) | Lossy on hand-drawn line variation; 96-image QA cost is high |
| Largest mobile display size for mascot | Splash 360pt = **1080px @3x** — well within PNG's sweet spot |
| React Native rendering | PNG renders natively; `react-native-svg` adds runtime cost and has known Android edge cases on complex paths |
| File size at 1080px PNG-24 with alpha | ~40-90KB per image — fine |
| Future runtime color variants | Preservable via silhouette mask PNG — see §10 |

**Decision: PNG-24 with alpha transparency, 1080px square canvas. SVG path retired.**

The Skia geometry in [`apps/mobile/assets/mascot/_klee-base-shape.tsx`](../apps/mobile/assets/mascot/_klee-base-shape.tsx) is **placeholder scaffolding** — to be replaced by PNG-rendering components in Phase 14.1. Skia/Reanimated stays for *motion overlays* (blink, breathe, confetti particles) only.

---

## 3. Accessory architecture (two-slot model)

| Slot | Cardinality | Examples | Storage |
|---|---|---|---|
| `outfit` | One active (mutually exclusive with `base`) | base, dino-hoodie | Whole-character — 8 PNGs per outfit |
| `hat` | One active (null = none) | sprout, banana-leaf, green-beanie, cat-beanie, frog-beanie, glasses, … | Single overlay + per-pose anchor coords |
| `stickers` | Multiple, max 3 | sparkle, heart, leaf, star, cloud, flame-cool | Corner-placement overlays (no anchor needed) |

**Outfit-vs-hat rule:** if the accessory **changes the body silhouette** (wraps the body, reshapes proportions, fully obscures the head), it's an `outfit`. If it sits *on top* of the existing body without altering the silhouette, it's a `hat`.

**Current 12-accessory inventory (preliminary — fill in as designer delivers):**

| ID | Type | Status |
|---|---|---|
| `base` | outfit (default) | ✅ delivered |
| `dino-hoodie` | outfit | ✅ delivered |
| `sprout` | hat | ✅ delivered |
| `banana-leaf` | hat | ✅ delivered |
| `green-beanie` | hat | ✅ delivered |
| `cat-beanie-white` | hat | ✅ delivered |
| `frog-beanie` | hat | ✅ delivered |
| `glasses` | hat | ✅ delivered |
| _TBD #7-12_ | hat or outfit | pending |

> 🟡 **Edge case on hat overlays that cover the ear-nubs**: green-beanie, cat-beanie-white, and frog-beanie all sit on top of Klee's ear-nubs. The designer's current art handles this correctly by painting a body-color shoulder region into the hat asset itself (the hat "consumes" the ear area visually). No mask layer required from the body side — but the QA gate confirms this is preserved across all 8 poses.

---

## 4. File structure

```
apps/mobile/assets/mascot/
├── CHARACTER_BIBLE.md
├── outfits/
│   ├── base/
│   │   ├── pose-1-front.png
│   │   ├── pose-2-three-quarter.png
│   │   ├── pose-3-profile.png
│   │   ├── pose-4-back.png
│   │   ├── expr-submit.png
│   │   ├── expr-confetti.png
│   │   ├── expr-celebration.png
│   │   └── expr-wave.png
│   └── dino-hoodie/
│       └── (same 8 files)
├── hats/
│   ├── sprout/
│   │   ├── overlay.png         ← the hat alone, transparent bg
│   │   └── anchors.json        ← per-pose anchor coords
│   ├── banana-leaf/
│   ├── green-beanie/
│   ├── cat-beanie-white/
│   ├── frog-beanie/
│   ├── glasses/
│   └── … (12 total)
├── stickers/                   ← already exists
└── masks/                      ← optional, for future color variants
    └── base/
        └── pose-1-front-body-mask.png
        └── …
```

---

## 5. PNG export specs (paste this to the designer verbatim)

| Spec | Value |
|---|---|
| Format | PNG-24 with alpha transparency (8-bit per channel + alpha) |
| Canvas | 1080 × 1080 px, square |
| Background | Fully transparent (alpha = 0 everywhere outside Klee) |
| Color profile | **sRGB** (NOT Display P3 — sRGB renders predictably on all Android/iOS devices) |
| DPI metadata | Not required (mobile uses pixel dimensions) |
| Klee placement | Body centered horizontally; vertically positioned with paws/feet at ~88% canvas height (leaves ~12% headroom for bounce animations and ~12% footroom for shadow) |
| Klee height in canvas | 60-70% of canvas height (for portrait poses); 50-60% for back/three-quarter |
| Compression | PNG-24 lossless. No web-optimized 8-bit palette quantization (loses anti-aliasing on the hand-drawn outline) |
| Anti-aliasing | On (default GoPaint behavior — do not disable) |

**Naming convention** (case-sensitive, kebab-case): `{outfit-or-hat-id}/{pose-id}.png` or `{hat-id}/overlay.png`.

---

## 6. The 8 poses (canonical list)

Each outfit and the base set must contain **all 8**, in this exact order/naming:

| # | Pose ID | What it is | Use cases |
|---|---|---|---|
| 1 | `pose-1-front` | Standing, facing camera, neutral mouth | Default rest, lockscreen, home |
| 2 | `pose-2-three-quarter` | ¾ left-facing, waving paw subtle | Group screen, profile |
| 3 | `pose-3-profile` | Side-on right-facing | Streak detail, walking transitions |
| 4 | `pose-4-back` | Facing away (back of head + body) | Loading, "going somewhere" moments |
| 5 | `expr-submit` | Holding green check ✓ with sparkle | Habit submitted, daily ritual complete |
| 6 | `expr-confetti` | Paws out, confetti ring | Streak milestone (7d, 30d, 100d) |
| 7 | `expr-celebration` | Arms up, sparkles around | Group milestone, ransom paid |
| 8 | `expr-wave` | One paw up, waving | First-launch greeting, onboarding hello |

Front, ¾, profile, back form a continuous turnaround. The 4 expressions break canonical face direction in favor of expression clarity.

---

## 7. Cuteness lock QA gates

These are checked on **every pose** before acceptance. The lock comes from [klee_cuteness_mechanics.md](../packages/shared/) (memory artifact) and `asset_production.md` §Workflow 1.

- [ ] **Body color** `#EDA597` (warm-blush-coral) — eyedrop to confirm
- [ ] **Outline color** `#1F1F26` (soft ink) — not pure black
- [ ] **Outline weight** 1.2-1.6px hand-drawn quality (slight variation OK, computer-perfect Bezier is NOT)
- [ ] **Cheek blush** `#EE9A8A` at ~40% opacity — TWO small ovals, lower-outer cheek, mandatory on all face-visible poses (poses 1, 2, 5, 6, 7, 8)
  - Exception: `pose-4-back` (no face visible) — blush absent is correct
  - Exception: `pose-3-profile` shows only one blush oval — correct
- [ ] **Eyes** bean-oval shape, height ≈ 1.4 × width — NOT anime-large, NO sparkle layers, NO tear-drops
- [ ] **Mouth** simple curve in poses 1-4; soft `:3` / `ω` in poses 5-8
- [ ] **Paws** rounded mitten shapes with 3 subtle toe-bumps (no individual fingers)
- [ ] **Ear-nubs** visible on base outfit, all poses; on hat overlays that cover the ears, the hat fills in the body color seamlessly
- [ ] **Background** fully transparent (no white edges, no JPEG-artifact fringe)
- [ ] **Klee centered** within the canvas tolerances above (§5)

**Reject conditions** (zero-tolerance):
- AI-large anime eyes
- Default AI chibi 1:1 head-body proportion (correct ratio is 1:1.2)
- Klee styled as a specific real animal (bird, cat, fox — Klee is its own creature)
- Purple-blue gradient anywhere
- Saved as JPEG (alpha loss)
- Saved with white background instead of transparent

---

## 8. Anchor coords for hats

Each hat needs per-pose anchor coords so the overlay lands correctly across all 8 poses. The anchor point is **the pixel on Klee's head where the hat's anchor point should sit** (typically a fixed point on the hat's brim or base).

**Format** (`hats/{hat-id}/anchors.json`):

```json
{
  "anchor_point_on_hat": { "x": 540, "y": 980, "comment": "center of hat brim" },
  "poses": {
    "pose-1-front":          { "x": 540, "y": 240, "rotation":   0, "scale": 1.0 },
    "pose-2-three-quarter":  { "x": 560, "y": 245, "rotation":  -5, "scale": 1.0 },
    "pose-3-profile":        { "x": 590, "y": 260, "rotation": -10, "scale": 0.95 },
    "pose-4-back":           { "x": 540, "y": 250, "rotation":   0, "scale": 1.0 },
    "expr-submit":           { "x": 540, "y": 250, "rotation":   2, "scale": 1.0 },
    "expr-confetti":         { "x": 540, "y": 245, "rotation":  -3, "scale": 1.0 },
    "expr-celebration":      { "x": 540, "y": 240, "rotation":   0, "scale": 1.0 },
    "expr-wave":             { "x": 545, "y": 245, "rotation":   2, "scale": 1.0 }
  }
}
```

Designer can deliver anchors as **annotated reference images** instead (a single PNG per hat with dots painted at each anchor point + a screenshot of each pose with the hat positioned correctly). I/we convert to JSON in code review.

---

## 9. Future: runtime color variants without re-export

Goal: let users tint Klee's body color (e.g., as a future premium customization) without re-shipping every outfit.

Approach: ask the designer to additionally export a **body silhouette mask** per pose of the base outfit only:

- Same 1080×1080 canvas
- Klee's body shape filled flat with pure `#EDA597`
- No outline, no blush, no facial features, no shadows
- Same transparent background
- Filename: `masks/base/pose-1-front-body-mask.png`

At runtime: render `mask` (tinted via shader/blend mode) BELOW the main outfit PNG. The mask supplies the body color; the outfit PNG supplies outline, face, and texture on top.

This is **deferred** — not part of the v1 ship. But asking the designer to deliver masks alongside the base set now is much cheaper than coming back to her in 6 months.

---

## 10. Handoff procedure (per accessory)

Designer side — what she delivers per accessory:

1. The 8 pose PNGs (or 1 overlay PNG for hats)
2. The source GoPaint file (preserved for future edits)
3. For hats: an annotated reference image showing where the hat sits on each of the 8 base poses (8 mini screenshots is fine)
4. A 1-line tag: `outfit` or `hat`

Engineering side — what we do per accessory:

1. Drop PNGs into the correct `outfits/{id}/` or `hats/{id}/` directory
2. For hats: convert annotated references to `anchors.json`
3. Add the new ID to the literal union type in `packages/shared/src/mascot-state.ts`
4. Run QA gates (§7) before merging
5. Optionally update `apps/mobile/assets/mascot/inventory.ts` (the asset loader)

---

## 11. What does NOT need to be redelivered

- The **existing 6 mascot states** in `apps/mobile/assets/mascot/mascot-*.tsx` are Skia placeholders. They get **replaced**, not augmented. Once base outfit PNGs land, those Skia files are deleted (except where Skia is used for motion overlays).
- The web SVG assets in `apps/web/public/mascot/` stay as-is for now (web mascot use is minor — marketing-only). Phase 14.1 will decide whether to swap web to PNG too.

---

## 12. Open questions for the designer

- [ ] Confirm: 12 accessories total, all 8-pose sets? Or some single-pose only?
- [ ] List the remaining 6 accessory IDs (we've seen 6 so far)
- [ ] Source file format from GoPaint — `.gpaint`? Are layered exports possible?
- [ ] Willing to do silhouette masks for the base outfit (§9)? +8 PNGs total, ~30 min work
- [ ] Color profile: confirm she's working in sRGB (not P3) inside GoPaint settings

---

## Related docs

- [asset_production.md](asset_production.md) — Nano Banana Pro pipeline (marketing illustration only after this doc)
- [emotional_spec_kleeve.md](emotional_spec_kleeve.md) — when each mascot pose is triggered
- [CHARACTER_BIBLE.md](../apps/mobile/assets/mascot/CHARACTER_BIBLE.md) — visual identity reference
- [`packages/shared/src/mascot-state.ts`](../packages/shared/src/mascot-state.ts) — persisted state schema
