# Master Prompts

A collection of 15 AI prompt templates that cover the **entire software development lifecycle** — from idea to production to maintenance. Each prompt is a self-contained system prompt you paste into a new AI conversation (Claude Opus 4.6 recommended).

---

## Prompt Catalog

### 🏗️ Build — From Idea to Working Software

| # | Prompt | Persona | What It Does |
|---|---|---|---|
| 1 | [project-discovery-prompt.md](project-discovery-prompt.md) | **SpecCraft** | Interviews you about a project idea and produces a complete `project_specification.md` — tech stack, architecture, features, data models, and a phased build plan. |
| 2 | [implementation-guide-prompt.md](implementation-guide-prompt.md) | **BuildCraft** | Takes a project spec and **creates prompt files** in `prompts/` directory — one markdown file per implementation step, organized by phase. Outputs files like `prompts/phase_00_setup/01_monorepo_init.md` that you feed to an AI coding agent. **Does NOT implement directly.** |
| 3 | [feature-spec-prompt.md](feature-spec-prompt.md) | **FeatureSpec** | Takes a feature idea + existing codebase and produces a detailed feature specification — UI states, data shapes, API contracts, acceptance criteria, edge cases. |
| 4 | [feature-implementation-prompt.md](feature-implementation-prompt.md) | **FeatureCraft** | Takes a feature spec and implements it inside an existing codebase — respecting conventions, patterns, and architecture already in place. |

### 🔧 Maintain — Keep the Codebase Healthy

| # | Prompt | Persona | What It Does |
|---|---|---|---|
| 5 | [pr-review-prompt.md](pr-review-prompt.md) | **ReviewCraft** | Reviews code changes with a 5-pass system (correctness, security, performance, patterns, maintainability). Produces severity-rated findings with a verdict. |
| 6 | [security-audit-prompt.md](security-audit-prompt.md) | **ShieldCraft** | Audits a codebase across 7 security domains (auth, authorization, input validation, data protection, infrastructure, API, client-side). OWASP-categorized findings. |
| 7 | [refactoring-prompt.md](refactoring-prompt.md) | **RefactorCraft** | Three modes: tech debt audit, targeted refactoring, or library migration. Prioritizes by impact/effort ratio. Always writes tests first. |
| 8 | [bug-investigation-prompt.md](bug-investigation-prompt.md) | **DebugCraft** | 6-stage scientific debugging: intake → reproduce → investigate → fix → verify → report. Finds root causes, not symptoms. |
| 9 | [performance-audit-prompt.md](performance-audit-prompt.md) | **PerfCraft** | Measures first, optimizes second. Profiles frontend (Core Web Vitals, bundle), backend (queries, caching), and mobile (startup, memory, animations). Before/after metrics for every fix. |
| 10 | [documentation-prompt.md](documentation-prompt.md) | **DocCraft** | Generates documentation artifacts: inline JSDoc/TSDoc, module READMEs, API docs, database schema docs, component docs, ADRs, and deployment runbooks. |

### 📚 Understand — Navigate & Learn Codebases

| # | Prompt | Persona | What It Does |
|---|---|---|---|
| 11 | [codebase-onboarding-prompt.md](codebase-onboarding-prompt.md) | **MapCraft** | Explores a codebase and produces a complete onboarding guide — architecture map, data flows, conventions, gotchas, and a recommended reading order for day one. |

### 🎨 Design — AI-Generated UI

| # | Prompt | Persona | What It Does |
|---|---|---|---|
| 12 | [mobile-master-prompt.md](mobile-master-prompt.md) | **StitchCraft Mobile** | Generates Google Stitch prompts for mobile app screens — production-quality UI from descriptions. |
| 13 | [web-master-prompt.md](web-master-prompt.md) | **StitchCraft Web** | Generates Google Stitch prompts for web pages and dashboards — responsive, accessible UI from descriptions. |

### 🖼️ Marketing — AI-Generated Images

| # | Prompt | Persona | What It Does |
|---|---|---|---|
| 14 | [upwork-thumbnail-prompt.md](upwork-thumbnail-prompt.md) | **ThumbnailCraft** | Generates Google Gemini prompts for Upwork portfolio thumbnails — mobile, web, and general software projects. |
| 15 | [appstore-screenshots-prompt.md](appstore-screenshots-prompt.md) | **StoreVision** | Generates Google Gemini prompts for App Store & Play Store screenshots — interview-based, user selects which screens. |

---

## Recommended Flows

### Flow 1: Build a New Project from Scratch

```
SpecCraft → BuildCraft → AI Agent Executes Prompts → DocCraft
```

1. **SpecCraft** — Describe your idea. Get a full project specification.
2. **BuildCraft** — Feed the spec in. Get a `prompts/` directory with step-by-step prompt files.
3. **Execute prompts** — Feed each prompt file (in order) to an AI coding agent. It builds the code.
4. **DocCraft** — Document everything that was built.

**Sample prompts:**
- → SpecCraft: *"I want to build a real-time multiplayer quiz game for students. Interview me."*
- → BuildCraft: *"Here's my project spec [paste]. Create the implementation prompt files."*
- → AI Agent: *Feed `prompts/phase_00_setup/01_monorepo_init.md` to GPT-5.3-Codex or Claude*
- → DocCraft: *"Document the entire codebase — module READMEs, API docs, and inline JSDoc for all public exports."*

---

### Flow 2: Add a Feature to an Existing Codebase

```
FeatureSpec → FeatureCraft → ReviewCraft → DocCraft
```

1. **FeatureSpec** — Describe the feature. AI reads your codebase and writes a detailed spec.
2. **FeatureCraft** — Feed the spec in. AI implements it respecting your existing patterns.
3. **ReviewCraft** — Review the AI-generated code before merging.
4. **DocCraft** — Update docs for the new feature.

**Sample prompts:**
- → FeatureSpec: *"I want to add a friends leaderboard feature. Spec it out based on our codebase."*
- → FeatureCraft: *"Here's the feature spec [paste]. Implement it in our codebase."*
- → ReviewCraft: *"Review the changes I made to add the friends leaderboard feature."*
- → DocCraft: *"Add JSDoc to all new exports in common/friends/ and document the new API endpoints."*

---

### Flow 3: Join a New Team / Onboard to Unfamiliar Code

```
MapCraft → DocCraft (optional)
```

1. **MapCraft** — Point it at the codebase. Get a complete onboarding guide.
2. **DocCraft** (optional) — Generate detailed reference docs if they're missing.

**Sample prompts:**
- → MapCraft: *"I just joined this team. Explore the entire codebase and create an onboarding guide."*
- → MapCraft: *"Map just the battle-backend/ service — I need to make changes there this week."*
- → DocCraft: *"The API endpoints have no documentation. Generate complete API docs for app/api/."*

---

### Flow 4: Codebase Health Check (Quarterly)

```
SecurityAudit → PerfCraft → RefactorCraft
```

1. **ShieldCraft** — Find security vulnerabilities.
2. **PerfCraft** — Find performance bottlenecks.
3. **RefactorCraft** — Audit tech debt and prioritize cleanup.

**Sample prompts:**
- → ShieldCraft: *"Run a full security audit on our codebase. Focus on auth, API security, and data protection."*
- → PerfCraft: *"The app feels slow on Android. Do a full performance audit — start with mobile startup time and API response times."*
- → RefactorCraft: *"Audit tech debt across the entire codebase. Categorize and prioritize by impact/effort."*

---

### Flow 5: Debug a Production Issue

```
DebugCraft → (fix) → ReviewCraft
```

1. **DebugCraft** — Investigate the bug systematically.
2. **Fix** — Apply the root-cause fix (DebugCraft will suggest it).
3. **ReviewCraft** — Review the fix before shipping.

**Sample prompts:**
- → DebugCraft: *"Users report that the battle screen freezes after answering question 5. It only happens on iOS. Investigate."*
- → DebugCraft: *"The leaderboard API returns 500 errors intermittently — about 10% of requests. Find the root cause."*
- → ReviewCraft: *"Review my fix for the battle screen freeze — I changed the timer cleanup logic."*

---

### Flow 6: Review a Teammate's PR

```
ReviewCraft (standalone)
```

**Sample prompts:**
- → ReviewCraft: *"Review this PR. Focus on correctness and security — it touches the payment flow."*
- → ReviewCraft: *"Review the diff in these files: [list]. This adds push notification support."*
- → ReviewCraft: *"Review this PR from a junior dev. Be thorough but educational — explain the why behind each suggestion."*

---

### Flow 7: Generate UI Screens with Google Stitch

```
StitchCraft Mobile or StitchCraft Web (standalone)
```

**Sample prompts:**
- → StitchCraft Mobile: *"Generate a Stitch prompt for a battle results screen showing score, XP earned, correct/wrong breakdown, and a rematch button."*
- → StitchCraft Web: *"Generate a Stitch prompt for an admin dashboard with user stats, revenue chart, and a recent battles table."*

---

## Quick Reference: Which Prompt Do I Need?

| I want to... | Use |
|---|---|
| Plan a new project from an idea | **SpecCraft** |
| Get step-by-step prompt files for building | **BuildCraft** |
| Spec out a new feature | **FeatureSpec** |
| Implement a feature in existing code | **FeatureCraft** |
| Review code changes / a PR | **ReviewCraft** |
| Find security vulnerabilities | **ShieldCraft** |
| Clean up tech debt / refactor | **RefactorCraft** |
| Debug a tricky bug | **DebugCraft** |
| Fix performance problems | **PerfCraft** |
| Generate documentation | **DocCraft** |
| Understand an unfamiliar codebase | **MapCraft** |
| Generate mobile UI with Stitch | **StitchCraft Mobile** |
| Generate web UI with Stitch | **StitchCraft Web** |
| Create Upwork portfolio thumbnail | **ThumbnailCraft** |
| Create App Store / Play Store screenshots | **StoreVision** |

---

## How to Use Any Prompt

1. Open a new AI conversation (Claude Opus 4.6 recommended).
2. Open the prompt file and copy everything below the `---` line.
3. Paste it as the **system prompt** or first message.
4. Give the AI your task and let it work.

> **Tip:** Every prompt works best with **full codebase access** (file system + terminal). The AI reads your actual code, not just descriptions of it.
