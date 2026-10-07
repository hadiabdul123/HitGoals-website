# HitGoals — Design System

> The design system for **HitGoals**, a personal AI assistant that helps people
> hit their goals faster and live more organized, productive lives.

HitGoals has a conversation with each new user to learn their whole life — goals,
work, studies, hobbies, routines, deadlines, habits — then builds a personalized
daily schedule, tracks progress, and acts as an always-on coach and accountability
partner that reshapes the plan as life changes.

This system captures the brand: a friendly, **Duolingo-style** look built around the
**red arrow mascot**, warm cream paper, chunky pressable UI, and pastel accents.

---

## Sources provided
- **Company brief** — product description (see top of this file).
- **Mascot & illustration set** — ~30 PNG/MP4 assets of the red arrow character in
  many poses & emotions (uploaded to `uploads/`, curated copies in `assets/mascot/`).
- **Reference UI screenshot** — `uploads/just reference of ui...png`. NOTE: the user
  explicitly said this dark/purple theme **should NOT be used** — it was reference for
  *screen types only* (Today, Plan, Goals, Coach, Habits, Insights, Profile…). The
  visual direction here is the mascot-derived cream+red system, not that screenshot.
- No logo/wordmark file, codebase, or Figma was provided. See "Iconography" & "Logo".

---

## Brand at a glance
- **Mascot** — a rounded red character whose "hair" is an upward → arrow (growth /
  hitting goals). White belly-face, black eyes, pink cheeks, bold dark-brown outline.
  It is the soul of the brand — use it generously (empty states, loading,
  celebration, onboarding, the AI coach). Poses live in `assets/mascot/`.
- **Primary color** — HitGoals Red `#F23B2E`, sampled from the mascot body.
- **Surfaces** — warm cream paper (`#FBF5EB`) with white cards.
- **Accents** — pastel gold, green, teal, sky — taken from the mascot's toy blocks.
- **Fonts** — Onest (display) + Nunito (body).

---

## CONTENT FUNDAMENTALS
How HitGoals writes.

- **Voice: a warm, upbeat coach.** Supportive, never corporate, never a nag. It talks
  like a friend who's rooting for you.
- **Person:** Second person — "you", "your day", "let's". The AI refers to itself as
  "I" ("I've moved Workout to 6 PM"). Warm and personal, not a faceless system.
- **Tone:** Encouraging and momentum-focused. Celebrate small wins ("Nice — 3 done
  today!"). When things slip, be kind and solution-first ("No worries, life happens —
  here's the new plan."). Never shame ("You failed to…" is banned).
- **Casing:** Sentence case for everything (titles, buttons, labels). Micro labels
  (tab bars, section eyebrows) may be UPPERCASE with wide tracking (`--ls-caps`).
- **Length:** Short. Punchy card titles ("Today's Focus"), one-line coach messages,
  verbs on buttons ("Start Focus", "Adjust Plan", "Apply Plan").
- **Numbers as motivation:** Progress %, streak days, days-left, completion rate,
  "3 wins today". Data always framed as encouragement, not judgement.
- **Emoji:** Used sparingly as warmth/flavor (a 🎯 or 🔥 beside a goal), never as the
  primary UI language and never in error/serious contexts. Prefer the mascot and real
  icons over emoji for actual UI.
- **Examples:**
  - Greeting: *"Good morning, Abdul 👋 Here's your plan for today."*
  - Nudge: *"You're most productive 9 AM–12 PM. Let's protect this time for deep work."*
  - Recovery: *"Plan updated — shortened Read to 20 min to keep your day on track."*

---

## VISUAL FOUNDATIONS

**Color.** Red-dominant, warm, optimistic. Red (`--red-500`) is reserved for primary
actions, the mascot, active states and key emphasis — used with restraint so it stays
special. Backgrounds are cream (`--cream-100`); cards are white. Pastel accents
(gold=streaks/rewards, green=done/success, teal=focus/insights, sky=info) give the
Duolingo multi-color feel without competing with red. Text/outlines are a warm
near-black brown (`--ink-900`) — **never pure black**, echoing the mascot's outline.

**Type.** Two families. **Onest** (rounded geometric) for display, headings, big
numbers and buttons — it mirrors the mascot's bouncy, pillowy shapes. **Nunito** for
body, labels and UI text — friendly and highly legible. Headings 600–700; body 600–800
(the brand runs body weight heavy for a confident, chunky feel). Tight tracking on
large display; wide uppercase tracking on micro labels.

**Spacing & layout.** 4px base grid. Generous padding inside cards (16–20px). Mobile-
first: the app frame is ~390–420px wide with a fixed bottom tab bar (`--nav-height`
68px) and a `--tap-target` minimum of 48px. Comfortable, uncramped, breathable.

**Backgrounds.** Flat warm cream — **no aggressive gradients**. Depth comes from
white cards on cream, not from gradient washes. Full-bleed mascot illustrations
(which carry their own cream/pink backdrop) anchor onboarding, empty and celebration
states. Subtle red-tinted radial glow is acceptable behind a hero mascot only.

**Corners.** Only slightly rounded — crisp, not pillowy: inputs/buttons/small cards
`--radius-md` (7px), cards `--radius-lg` (10px), hero cards/sheets `--radius-xl`
(14px). Fully-round `--radius-pill` is reserved for circular controls (avatars,
switch knob, streak pill).

**Shadows & the signature "chunky edge".** Two elevation ideas:
1. **Soft ambient shadows** — low-blur, warm-tinted (`--shadow-sm/md/lg`) for cards.
2. **Solid press-down edges** — the signature toy look. Primary buttons carry a solid
   darker bottom edge (`--edge-brand` = `0 4px 0 var(--red-700)`); pressing translates
   the button down by the edge height so it physically "clicks". Green/gold variants
   have matching edges. This chunky, tactile feel is core to the brand — prefer it on
   commit actions over flat buttons.

**Borders.** Cards use a 1.5px warm hairline (`--border-default`). Emphasis / mascot-
style outlines use `--border-strong` (ink). Inputs get a 2px border that turns red on
focus with a soft red glow ring.

**Animation.** Playful and springy. Easing `--ease-bounce`/`--ease-spring` (overshoot)
for anything that appears, toggles, or celebrates; `--ease-out` for movement. Buttons
press down, toggles bounce, tab icons pop, the mascot floats/jumps. Use the mascot
MP4s (`assets/mascot/*.mp4`) for loading and celebration moments. Respect reduced-
motion for essential flows.

**Hover / press states.**
- Buttons: hover → darker shade (`--red-600`); press → translateY down onto the edge.
- Cards (interactive): hover → lift 2px + `--shadow-md`.
- Icon buttons / tab icons: press → scale 0.92 / active → pop scale 1.06.
- Chips/segments: active → filled red (chip) or white pill on cream track (segmented).

**Imagery vibe.** Warm, hand-drawn, cel-shaded cartoon with thick dark outlines, soft
highlights, pink-cream backdrops. Rounded, huggable, optimistic. No photography in
brand illustration; user avatars may be photos.

**Transparency / blur.** Used minimally. Occasional translucent sheet backdrops; not a
glassmorphism system. Keep surfaces opaque and warm.

---

## ICONOGRAPHY
- **No icon assets, icon font, or SVG sprite were provided** with the brand. The mascot
  set is illustration, not an icon system.
- **Substitution (FLAGGED):** this system uses **Lucide** (https://lucide.dev) as the
  icon set — rounded caps/joins, ~2px stroke, which matches the friendly, rounded
  brand feel. Cards & UI kit load it from CDN
  (`https://unpkg.com/lucide@0.454.0`). Recommended defaults: stroke width 2,
  `stroke="currentColor"`, size 20–24. Common glyphs: Sun/Today, Target/Goals,
  CalendarDays/Plan, MessageCircle/Coach, User/You, Flame/streaks, Rocket/Sparkles,
  Bell, Check. **If you have or want a bespoke icon set, please share it and we'll
  swap Lucide out.**
- **Emoji** appear occasionally as warm flavor next to goals/labels (🎯🔥📚💪), not as
  functional UI icons.
- **The mascot** is used where most apps would use a big illustrative icon (empty
  states, loading, celebration).

## Logo
- **No logotype/wordmark file was provided.** The brand mark is rendered as: the mascot
  (`assets/mascot/mascot-proud.png` / `mascot-wave.png`) + the word **HitGoals** set in
  Onest 700 ("Hit" in red, "Goals" in ink). See `guidelines/brand-logo.card.html`.
  If you have an official logotype, share it and we'll replace the type treatment.

---

## Fonts — substitution note (FLAGGED)
No font files were supplied. This system uses the closest friendly, rounded matches on
**Google Fonts**, imported in `tokens/typography.css`:
- **Onest** (display) — rounded geometric, echoes the mascot's arrow/shape language.
- **Nunito** (body) — rounded, warm, highly legible.
- **DM Mono** (data/mono) — occasional numeric/metadata use.
Because they load from Google Fonts (not bundled `@font-face` binaries), the compiler
reports **0 fonts**; that's expected. **If HitGoals has official brand fonts, please
send the files and we'll self-host them.**

---

## INDEX / Manifest

**Root**
- `styles.css` — global entry (import this one file). Imports all tokens.
- `thumbnail.html` — homepage tile.
- `readme.md` — this file.
- `SKILL.md` — Agent-Skills-compatible entry.

**`tokens/`** — `colors.css`, `typography.css`, `spacing.css`, `radius.css`,
`shadows.css`, `motion.css` (CSS custom properties: base values + semantic aliases).

**`assets/mascot/`** — curated mascot poses (PNG) & animations (MP4): wave, proud,
determined, thinking, sad, stressed, studying, typing, running, run-hero, blocks,
search, envelope, jump + `mascot-jump/run/writing/envelope.mp4`.

**Components** (`components/<group>/`, namespace `window.HitGoalsDesignSystem_8b4e00`):
- **forms/** — `Button`, `IconButton`, `Input`, `Checkbox`, `Switch`, `SegmentedControl`
- **display/** — `Card`, `Badge`, `Chip`, `StatTile`, `Avatar`
- **progress/** — `ProgressBar`, `ProgressRing`, `StreakFlame`
- **app/** — `Mascot`, `TopBar`, `BottomNav`, `ListRow`, `GoalCard`, `HabitRow`,
  `CoachBubble`

**Guidelines / specimen cards** (`guidelines/`) — Colors (red, cream, ink, accents,
semantic), Type (display, body, scale), Spacing (scale, radius, elevation), Brand
(logo, voice).

**UI kit** (`ui_kits/hitgoals-app/`) — interactive mobile app recreation: Today,
Goals, AI Coach, Habits. See its `README.md`.

### Intentional additions
- **Mascot** component — not a "standard" primitive, but the mascot is the brand's
  defining element, so a first-class wrapper is essential.
- **GoalCard / HabitRow / CoachBubble / StreakFlame** — app-domain compositions that
  recur across every HitGoals surface; included so screens compose from real parts.
- **Lucide icons** — substituted for a missing icon set (see Iconography).
