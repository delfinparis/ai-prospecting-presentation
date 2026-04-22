# Slide Visual Design Specs — Find Your Next Client With AI

**Target tool:** Keynote (Mac) — native, ships with Mac, best live-demo reliability
**Fallback:** PowerPoint or Google Slides (specs translate cleanly)
**Design philosophy:** Dark, confident, spare. The stage is for YOU — slides are the punctuation, not the sentence.

**Brand continuity:** These specs intentionally match the tapthis.co/prospecting companion page design language, so the slides feel like an extension of the page attendees will visit after the talk.

---

## GLOBAL DESIGN TOKENS

### Colors (hex)

| Token | Hex | Use |
|-------|-----|-----|
| `navy-950` | `#0a1628` | Primary background — EVERY slide |
| `navy-900` | `#0f2140` | Card backgrounds, elevated panels |
| `navy-800` | `#162d54` | Secondary panels |
| `slate-100` | `#f1f5f9` | Primary text (almost-white, never pure white) |
| `slate-300` | `#cbd5e1` | Secondary text (body, notes) |
| `slate-500` | `#64748b` | Tertiary text (captions, timestamps) |
| `accent-cyan` | `#38bdf8` | Primary accent — call-outs, headline highlights |
| `accent-emerald` | `#10b981` | Secondary accent — success states, stats, the gradient with cyan |
| `accent-amber` | `#f59e0b` | Warning / attention — pricing anchor, objection highlights |
| `accent-red` | `#ef4444` | Negative framing (what NOT to do, strikethrough items) |
| `accent-bracket` | `#f97316` | Prompt variables (the `[BRACKETED]` highlight, matches tapthis.co) |

### The gradient (use sparingly for emphasis)
```
linear-gradient(135deg, #10b981 0%, #38bdf8 100%)
```
Use on: hero CTA buttons, "5 queries" numbered circles, important transition markers. Do NOT use on text for body content (only for headline accent spans).

### Typography

| Token | Family | Weight | Use |
|-------|--------|--------|-----|
| Display | **Space Grotesk** | 700 | All headlines, H1-H2, numbered slide markers |
| Body | **Inter** | 400 / 500 / 600 | Body text, captions, speaker notes |
| Mono | **JetBrains Mono** or **SF Mono** | 400 | Query text on screen (ROLE/CONTEXT/TASK blocks) |

Fallback: system fonts `-apple-system, BlinkMacSystemFont, sans-serif`.

### Type scale

| Level | Size (pt) | Line height | Use |
|-------|-----------|-------------|-----|
| Hero | 72 | 1.1 | Opening slide headline, Hero #5 reveal |
| H1 | 56 | 1.15 | Slide titles, Query titles |
| H2 | 44 | 1.2 | Section breaks, "What you'll get" lists |
| H3 | 32 | 1.3 | Sub-headlines, taglines |
| Body | 24 | 1.5 | Body text, speaker-visible notes |
| Caption | 18 | 1.4 | Timing, attributions |
| Mono (query text) | 20 | 1.5 | Query content — readable from back row |

**Rule of thumb:** If the back row can't read it at 40 feet, it's too small. Bias toward larger.

### Slide dimensions
**16:9, 1920×1080** — default for Keynote and most projectors. Do NOT use 4:3 unless the venue specifically requires it.

---

## LAYOUT SYSTEM

### The 8-point grid
All spacing in multiples of 8pt: 8, 16, 24, 32, 48, 64, 96, 128.

### Standard margins
- **Outer margin:** 96pt (1.25 inch / 128px)
- **Content width:** ~1728pt (90% of 1920)
- **Vertical rhythm:** 32pt between elements, 64pt between sections

### Three layout archetypes

1. **Hero layout** — centered headline, no other elements. Used for: title slide, reframe slide (Slide 2), section transitions.
2. **Split layout** — left column 40% (label/context), right column 60% (content/demo). Used for: query slides (title on left, query text on right).
3. **Full-bleed layout** — content fills nearly entire slide with minimal framing. Used for: the 82% stat slide, demo-backup screenshots.

---

## SLIDE-BY-SLIDE VISUAL DIRECTIONS

Based on the 28+ slides in `ai-prospecting-speaker-notes.md`. For each: layout type, specific treatment, and "if there's one thing" guidance.

---

### SLIDE 1 — Title
- **Layout:** Hero
- **Background:** Pure `navy-950`. NO gradient on the background.
- **Content:**
  - `FIND YOUR NEXT CLIENT` in Space Grotesk 72pt, `slate-100`, centered, top-aligned at 35% from top
  - `WITH AI` in Space Grotesk 72pt, with the "AI" span as `linear-gradient(135deg, #10b981, #38bdf8)` applied to text fill
  - `D.J. Paris  |  tapthis.co/prospecting` in Inter 24pt, `slate-500`, centered, 72pt below the headline
- **No decoration, no logo, no date.** This slide is for the first 90 seconds of silence.
- **If there's one thing:** The word AI is the only colored word. Everything else is in slate.

---

### SLIDE 2 — The Reframe
- **Layout:** Hero
- **Background:** `navy-950`
- **Content:**
  - Top line: `AI is not a content tool.` in Inter 56pt 600 weight, `slate-500` (muted, because this is what they already think)
  - Bottom line: `It is a prospecting intelligence tool.` in Space Grotesk 72pt 700 weight, `slate-100`, with "prospecting intelligence" highlighted in the gradient
  - 64pt vertical gap between lines
- **Animation:** Top line appears on slide-in. 2-second pause. Bottom line appears with a quick fade + slight upward motion (transform: translateY(12px) → 0).
- **If there's one thing:** The muted top line + gradient bottom line IS the visual storytelling. The slide literally shows the reframe happening.

---

### SLIDE 3 — The Stakes (82%)
- **Layout:** Full-bleed
- **Background:** `navy-950`
- **Content:**
  - **`82%`** in Space Grotesk 256pt (intentionally absurd), with the gradient applied. Centered vertically.
  - Below the big number, in Inter 28pt `slate-300`:
    > `of Americans use AI to research real estate decisions`
    > `67% use ChatGPT specifically`
  - Attribution: `Source: Inman, Oct 2025` in Inter 16pt `slate-500` at the bottom
- **Animation:** The `82%` number counts up from 0 to 82 over 1.5 seconds on entry. Use built-in Keynote "Number Increment" build.
- **If there's one thing:** That number has to take over the screen. Make it bigger than you think is reasonable.

---

### SLIDE 3a — Before/After Reframe
- **Layout:** Split (50/50 vertical split)
- **Background:** `navy-950`
- **Left column (red-tinted):**
  - Header: `What 99% of agents type:` in Inter 20pt, `accent-red` letterspacing 2
  - Body: `"Write me a listing description for a 3-bed 2-bath in Lincoln Park"` in Inter 28pt italic `slate-300`, with 10 words shown
  - Visual cue: Small red `❌` icon above the quote
- **Right column (green-tinted):**
  - Header: `What the top 1% type:` in Inter 20pt, `accent-emerald` letterspacing 2
  - Body: The full 6-part query structure, with each part (ROLE, CONTEXT, TASK, CONSTRAINTS, RULES, EXPECTED OUTPUT) shown as a stacked label. Use Mono 18pt.
  - Visual cue: Small green `✓` icon above the query
- **Divider:** 1pt `slate-500` vertical line between columns
- **If there's one thing:** The left side feels short and bare. The right side feels dense and professional. The visual weight does the teaching.

---

### SLIDE 4 — Agenda (5 queries)
- **Layout:** Hero with a 5-item grid below
- **Content:**
  - Headline: `Five queries.` in Space Grotesk 56pt `slate-100`
  - Subhead: `Each one ends with a name, a reason, and an opening line.` in Inter 28pt `slate-500`
  - Below: 5 pills in a row, each one:
    - Circle number (1-5) in the gradient, 64pt diameter
    - Query title next to it in Space Grotesk 24pt `slate-300`
- **If there's one thing:** The 5 pills should all fit on one horizontal row. If your query titles are too long, abbreviate in the pill and use full titles on the query's dedicated slide.

---

### SLIDE 5 — Avatar Fork
- **Layout:** 4-column grid
- **Content per column (column width: ~416pt, gaps of 24pt):**
  - Icon (SVG): a simple silhouette differing per avatar
  - Label: `NEW` / `STRUGGLING` / `PART-TIME` / `TOP 1%` in Inter 20pt 700 weight, letterspacing 2, colored by severity:
    - NEW: `accent-emerald`
    - STRUGGLING: `accent-amber`
    - PART-TIME: `accent-cyan`
    - TOP 1%: `slate-100` (white-hot)
  - Name + stats: "Marcus, 6 months, zero sales" in Inter 24pt `slate-100`
  - Which query they should focus on: 1-line hint in Inter 18pt `slate-500`
- **If there's one thing:** Color-coding by avatar means when you reference "Renee" again later, the audience can match the color visually.

---

### SLIDE 5a — What This Talk Is NOT
- **Layout:** Hero-style list with strikethrough
- **Content:**
  - Headline (muted): `This talk is NOT about:` in Inter 32pt `slate-500`
  - 5 items, each appearing one at a time with strikethrough:
    - `Writing listing descriptions` (strikethrough in `accent-red`)
    - `Social media captions` (strikethrough)
    - `Chatbots on your website` (strikethrough)
    - `Email templates` (strikethrough)
    - `Market reports` (strikethrough)
  - Below, 48pt gap, in Space Grotesk 44pt `slate-100`:
    > `This talk is about one thing:`
    > `Finding your next client.` (with "Finding" in the gradient)
- **Animation:** Build the 5 items one at a time with strikethrough, 0.3s each. Pause 0.8s. Then reveal the punch line.
- **If there's one thing:** The pacing of the build IS the point.

---

### SLIDES 6, 10, 14, 18, 22 — Hero Query Titles
- **Layout:** Hero, but with a giant numbered marker
- **Content:**
  - Top-left corner: big `QUERY #1` marker in Space Grotesk 72pt `slate-500` (deliberately muted — the number is reference, not the main event)
  - Centered main headline: the query title, in Space Grotesk 80pt `slate-100`
  - Subtitle: the tagline ("Walk in like you've known the seller for a year.") in Inter 32pt italic `slate-300`
  - Bottom-right corner: "For [AVATAR]" line in Inter 20pt `accent-cyan`, referencing which avatar this is built for
- **If there's one thing:** The number is muted on purpose. The TITLE is the hero.

---

### SLIDES 7, 11, 15, 19, 23 — Query Text Slides
- **Layout:** Full-bleed with monospace content
- **Content:**
  - Small label top-left: `QUERY #[N]` in Mono 16pt `slate-500`
  - Main content area (centered horizontally, ~1600pt wide):
    - The 6 sections of the query in Mono 20pt
    - Each section header (`ROLE:`, `CONTEXT:`, etc.) in `accent-cyan` bold
    - Section body in `slate-300`
    - Between sections: 24pt vertical gap
  - Bracketed variables (like `[ADDRESS]`) highlighted with `accent-bracket` background
- **Treatment:** Add a subtle "scroll indicator" bar on the right that shows the query is longer than the slide (so the audience understands it's a full prompt, not a fragment).
- **If there's one thing:** The query text has to be legible from the back row. 20pt Mono is the minimum. If your room is large, bump to 22pt and cut/abbreviate.

---

### SLIDES 8, 12, 16, 20, 24 — DEMO BREAK slides
- **Layout:** Hero, minimal
- **Content:**
  - Headline: `LIVE DEMO` in Inter 32pt `accent-emerald`, letterspacing 4
  - Subhead: what we're about to run, in Inter 24pt `slate-300`
  - No other content — you're switching to Claude, not looking at the slide
- **Why minimal:** This slide is only visible for 2-3 seconds before you Cmd+Tab to Claude. Don't over-design.
- **Behind the scenes:** Set this slide's animation so that if you come back to it, there's a subtle animated "breathing" glow on the emerald text — signals "we're in demo mode" to you and the audience when you return mid-demo.

---

### SLIDES 8a, 12a, 16a, 20a, 24a — Demo Backup Screenshots
- **Layout:** Full-bleed screenshot
- **Content:**
  - The actual Claude output from a successful rehearsal run, screenshotted at 2x resolution
  - Small `BACKUP VIEW` watermark in the corner in `slate-500` 14pt (invisible to audience but reminds you)
- **Purpose:** If the live demo fails, Cmd+Right arrow to this slide. Continue narrating the output as if it were live. Nobody in the audience will know.
- **If there's one thing:** These are the most important slides in the deck. Without them, one demo failure kills the talk.

---

### SLIDES 9, 13, 17, 21, 25 — Hero Takeaway Slides
- **Layout:** 3-bullet emphasis
- **Content:**
  - Headline (short): `The takeaway.` in Space Grotesk 44pt `slate-500`
  - 3 bullets, each in Inter 36pt `slate-100`, with 32pt vertical gaps
  - Each bullet starts with a mini-icon (check / number / arrow) in the gradient
- **If there's one thing:** Bullets should be full sentences, not fragments. They need to work as spoken phrases for the room.

---

### SLIDE 13a — Audience Interaction (Phone Out)
- **Layout:** Hero with giant CTA
- **Content:**
  - Headline: `Pull out your phone.` in Space Grotesk 72pt `slate-100`
  - Subhead: `Open your CRM.` in Space Grotesk 56pt `slate-300`
  - Supporting instruction: `Google: "[your CRM name] export contacts CSV"` in Mono 28pt `accent-cyan`
  - Timer visual (optional): a 30-second countdown ring in the corner, auto-starting when the slide appears
  - Bottom: list of common CRMs in Inter 18pt `slate-500`
- **If there's one thing:** The timer is optional but effective. When it's ticking down, the room FEELS the pause.

---

### SLIDE 25 — Tool Reality Check
- **Layout:** 4-column comparison grid
- **Content per column:**
  - Tool name in Space Grotesk 28pt (Claude, ChatGPT, Gemini, Grok)
  - Price in Inter 24pt `accent-emerald` ($20, $20, $20, $30)
  - One-line positioning in Inter 20pt `slate-300`
  - Small accent bar at the top of each column in a different brand-inspired color
- **If there's one thing:** All four columns are equal width. You're not pitching one over the others.

---

### SLIDE 26 — Monday Morning Checklist
- **Layout:** Literal checklist, 2-column if needed
- **Content:**
  - Headline: `Your Monday morning.` in Space Grotesk 44pt `slate-100`
  - 7 checkbox items, each in Inter 24pt `slate-300`, with actual unchecked checkbox squares in front
  - Below: `Take a photo of this slide.` in Inter 20pt `accent-emerald`, pulsing subtly
- **If there's one thing:** The checklist has to be photographable from anywhere in the room. Use dark backgrounds and high-contrast white text.

---

### SLIDE 27 — Companion Page QR
- **Layout:** Hero with QR code as the hero element
- **Content:**
  - Top: `All 5 queries + 21 more` in Inter 32pt `slate-300`
  - Center: QR code, 600pt × 600pt, black on white (required for scanning contrast)
  - Below QR: `tapthis.co/prospecting` in Mono 32pt `accent-cyan`
- **QR code technical requirement:** Generate at 1024×1024 PNG minimum. Test-scan from 40 feet before stage day.
- **If there's one thing:** The QR code has to be big enough that the back row can scan it. Error correction level should be H (30% recovery).

---

### SLIDE 28 — CTA (Book + Follow)
- **Layout:** Two side-by-side buttons
- **Content per button:**
  - Button 1: `BOOK AN AI STRATEGY CALL` in Space Grotesk 28pt, on the gradient, rounded 16pt
  - Below: `joinkale.com/schedule` in Mono 20pt `slate-500`
  - Gap: 48pt
  - Button 2: `FOLLOW ON INSTAGRAM` in Space Grotesk 28pt, on a darker tile, rounded 16pt
  - Below: `@delfin.paris` in Mono 20pt `slate-500`
- **If there's one thing:** The primary CTA (strategy call) is gradient-filled. The secondary (IG) is outlined. The visual hierarchy teaches which action matters more.

---

### SLIDE 29 — Q&A
- **Layout:** Hero, minimal
- **Content:**
  - `QUESTIONS?` in Space Grotesk 144pt `slate-100`, centered
  - Below: `tapthis.co/prospecting  |  @delfin.paris` in Inter 24pt `slate-500`
- **If there's one thing:** The "?" mark should be huge. It invites.

---

## REUSABLE COMPONENTS

Build these as Keynote master slides so you can drop them into the deck without re-designing.

### Gradient hero circle (for the numbered "QUERY #N" markers)
- Circle 160pt diameter
- Fill: `linear-gradient(135deg, #10b981, #38bdf8)`
- Number inside: Space Grotesk 80pt `navy-950` (dark text on light gradient)

### Card container (for quotes, stats, rapport hooks)
- Background: `rgba(255,255,255,0.03)`
- Border: 1pt `rgba(255,255,255,0.08)`
- Border-radius: 12pt
- Padding: 32pt

### Highlighted variable tag (for query content)
- Background: `rgba(249, 115, 22, 0.15)` (the bracket orange at 15% opacity)
- Text: `accent-bracket`
- Border-radius: 4pt
- Padding: 2pt 6pt

### Demo backup screenshot frame
- Outer border: 2pt `slate-500`
- Inner shadow: `0 0 0 1pt rgba(255,255,255,0.05)` (subtle inset)
- Top-left sticker: "LIVE DEMO (backup)" in Inter 14pt `slate-500`

---

## ANIMATION PRINCIPLES

Less is more. Over-animated slides scream "I made this in 2013."

**Use animation for:**
- Building lists one item at a time (when pacing matters)
- The "reveal" of a stat (82% counter)
- The "strikethrough" build on Slide 5a
- Demo back-and-forth (subtle breathing glow on demo-mode indicators)

**Do NOT use:**
- Slide transitions other than the default crossfade
- Bouncing, spinning, or "flash" effects
- Text that flies in from off-screen
- Anything that draws attention to itself rather than the content

Keep all animations 200-400ms. Longer feels sluggish on stage.

---

## TIMING REFERENCE (printed in your speaker notes but not on slides)

Add a subtle `SPEAKER NOTES` overlay (Keynote's built-in) with a countdown per slide, matching the timing in the speaker notes doc. The overlay appears ONLY on your laptop display, not on the projected output.

---

## PRE-PRODUCTION CHECKLIST

Hand these specs to your designer (or yourself if DIY) along with these assets:

- [ ] **Headshot** — high-res, landscape crop, neutral background
- [ ] **Logo (tapthis.co)** — vector if possible, for footer use
- [ ] **QR code** — generated at 1024×1024 minimum, pointing to tapthis.co/prospecting
- [ ] **Avatar silhouettes** — 4 simple SVG silhouettes for Slide 5
- [ ] **Tool logos** — Claude, ChatGPT, Gemini, Grok (use each tool's official brand asset pack)
- [ ] **Icon set** — check, arrow, number, sparkle, star (use Lucide Icons or similar open-source set)

---

## EXPORTABILITY

Final deck should export cleanly to:
- PDF (1-up and handout 4-up) for attendees who ask for notes
- PNG slides (for social media clips post-talk)
- Video export (MP4, 1080p, for highlights reel if recorded)

Keep fonts EMBEDDED in the exported PDF. If the deck is opened on a non-Mac without Space Grotesk installed, it should fall back gracefully.

---

## THE ONE-LINE BRAND MEMORY AID

If a designer forgets everything else, this is the sentence that preserves brand continuity:

> Dark navy, gradient cyan-to-emerald, Space Grotesk on display text, Inter on body. Punctuation over decoration.

Tape it above their monitor.
