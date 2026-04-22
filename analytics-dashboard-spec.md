# tapthis.co Analytics Dashboard Spec

**Goal:** Answer three questions in real time without guessing.
1. **Is tapthis.co growing?** (traffic, engagement, retention)
2. **Does the site drive revenue?** (strategy call bookings, paid conversion readiness)
3. **Which features are actually working?** (stacks, search, feedback, heroes)

**Platform stack (what's already wired):**
- **Google Tag Manager** (container ID: `GTM-P6MPH7`) — already on every page
- **localStorage** state mirrors (favorites, unlocked, recents, stacks, feedback)
- **`/api/capture-email` endpoint** — already captures email + level + feedback events
- **No backend DB yet** — recommendations below include minimal infra to add one

**Dashboard tool recommendations (pick one):**
1. **Google Looker Studio** (free, connects to GA4 via GTM) — easiest, best for solo/small team
2. **Mixpanel** (paid, free tier is generous) — best for event-based product analytics
3. **Amplitude** (paid) — deeper funnel analysis, overkill right now

**Recommendation:** Start with Looker Studio connected to GA4. When you have >5K MAU, upgrade to Mixpanel.

---

## 1. THE EVENTS ALREADY WIRED

Every event below is already firing from the React code. Your job is to connect them to GA4 (or Mixpanel) via the existing GTM container. No new code required.

### Core engagement events

| Event name | Fires when | Parameters | Why it matters |
|------------|------------|------------|----------------|
| `page_view` | Any route loads | `page_path`, `page_title` | Basic traffic measure |
| `search` | User navigates via quick pick, subcategory, or subgroup | `search_query` | Category affinity — which quick pick drives most activity |
| `search_select` | User clicks a result in the new global search | `search_query`, `prompt_id` | Proves the search feature is used |
| `prompt_view` | A prompt card is expanded | `prompt_id` | Top-of-funnel interest signal |
| `prompt_copy` | A prompt is successfully copied | `prompt_id`, `prompt_category` | The single most important engagement event |
| `prompt_copy_free` | One of the free pre-gate copies | `prompt_id`, `free_copy_number` | Progressive gate validation — are users using their free copies? |

### Monetization & conversion events

| Event name | Fires when | Parameters | Why it matters |
|------------|------------|------------|----------------|
| `lead` | User submits email | `email_level` (new/mid/top/not-specified) | Email capture rate |
| `strategy_call_click` | User clicks strategy call CTA | `placement` (sticky_footer / prospecting_cta / drip_email) | The revenue event — every click is a potential booking |
| `open_in_ai` | User clicks "Run in Claude" (or switches tool) | `tool`, `platform` (ios/android/desktop), `prompt_id` | Tool preference data + mobile usage |

### Feature-specific events (stacks)

| Event name | Fires when | Parameters | Why it matters |
|------------|------------|------------|----------------|
| `stack_new_click` | User opens stack creation | — | Feature discovery |
| `stack_template_click` | User opens a starter template | `template` | Which template resonates |
| `stack_save` | User saves a stack | `stack_id`, `prompt_count` | Feature activation signal |
| `stack_run_start` | User begins run-mode for a stack | `stack_id`, `prompt_count` | The moment a stack becomes useful |
| `stack_step_copy` | User copies a prompt during run mode | `stack_id`, `prompt_id`, `step` | Step-by-step engagement |
| `stack_run_complete` | User finishes all steps | `stack_id` | Completion rate |
| `stack_delete` | User deletes a stack | `stack_id` | Negative signal on specific templates |

### Feedback events

| Event name | Fires when | Parameters | Why it matters |
|------------|------------|------------|----------------|
| `prompt_feedback` | User clicks 👍 or 👎 after copy | `prompt_id`, `rating` (up/down) | Per-prompt quality signal |

---

## 2. THE DASHBOARD — 4 SECTIONS

Build in Looker Studio with 4 tabs. Each tab answers one business question.

---

### TAB 1: THE HEALTH PULSE (daily driver)

**Question:** Is the site healthy and growing?

**Key widgets:**

1. **Daily active users (DAU) — 30-day sparkline**
   - Metric: unique users firing any event per day
   - Why: basic growth signal

2. **Weekly active users (WAU)**
   - Metric: unique users firing any event in rolling 7 days
   - Why: smoother growth signal; also WAU/MAU ratio is a stickiness proxy

3. **Prompt copies per day**
   - Metric: `prompt_copy` + `prompt_copy_free` count per day
   - Why: the single most important engagement metric — if this is flat, nothing else matters

4. **Email capture rate**
   - Metric: `lead` events / unique users per day
   - Goal: >8% after progressive gate launch
   - Why: progressive gate's success is measured here

5. **New vs. returning split**
   - Metric: new visitors / returning visitors per day
   - Why: returning % is the retention proof point

---

### TAB 2: THE REVENUE FUNNEL

**Question:** Does tapthis.co drive strategy call bookings?

**Key widgets:**

1. **Strategy call click funnel**
   - Stage 1: Unique users per day
   - Stage 2: Users who copied ≥1 prompt (`prompt_copy` fired)
   - Stage 3: Users who fired `strategy_call_click`
   - Stage 4: Users who actually booked a call (requires Calendly integration — see infra notes)
   - Display as funnel chart with drop-off % at each stage

2. **Strategy call click placement breakdown**
   - Bar chart: `strategy_call_click` count grouped by `placement` (sticky_footer / prospecting_cta / drip_email)
   - Why: tells you which CTA placement converts — budget more real estate to the winner

3. **Strategy call clicks by user segment**
   - Grouped by `email_level` (new / mid / top)
   - Why: if top producers convert 3× at new agents, that's pricing signal

4. **Strategy call bookings** (requires Calendly webhook — see infra notes)
   - Count of actual confirmed bookings per week
   - Revenue impact: bookings × average call value

5. **Drip email performance** (requires email platform integration)
   - Open rate, click rate, strategy-call click-through per email
   - Why: tells you which of the 5 drip emails is doing the heavy lifting

---

### TAB 3: FEATURE PERFORMANCE

**Question:** Which features are actually used, and which are dead weight?

**Key widgets:**

1. **Feature adoption funnel (per feature):**
   For each feature, show: % of DAU who saw it, % who used it, % who used it again within 7 days.
   - **Global search:** `page_view` → `search_select`
   - **Stacks:** `page_view` (on `/stacks`) → `stack_save` → `stack_run_start`
   - **"Run in Claude":** `prompt_view` → `open_in_ai`
   - **Feedback widget:** `prompt_copy` → `prompt_feedback`

2. **Stacks funnel (dedicated, because it's the moat feature):**
   - Users who visited `/stacks`
   - Users who opened creation
   - Users who saved a stack
   - Users who ran a stack
   - Users who completed a run
   - Users who created a 2nd stack (true product-market fit signal)

3. **"Run in Claude" tool breakdown**
   - Pie chart of `open_in_ai` events grouped by `tool`
   - Bar chart of `open_in_ai` events grouped by `platform`
   - Why: tells you Claude vs ChatGPT preference, mobile vs desktop usage

4. **Search usage**
   - Top 20 most-searched terms (from `search_query`)
   - Why: gaps in the category hierarchy — if people search "buyer rejection" and no result comes up, that's a content gap

5. **Favorites vs. Recent activity**
   - Requires a small localStorage-to-analytics bridge — see infra notes
   - Why: are users actually favoriting, or are we building graveyard features?

---

### TAB 4: PROMPT-LEVEL QUALITY

**Question:** Which prompts earn their keep, and which should be rewritten?

**Key widgets:**

1. **Top 20 most-copied prompts** (last 30 days)
   - Grouped by `prompt_id`
   - Cross-reference with actual prompt titles via a lookup (pull from `data/prompts.json`)
   - Why: this IS your "Top 10 This Week" curation, auto-updating

2. **Bottom 20 least-viewed prompts** (from `prompt_view` count)
   - Why: these are dead prompts that need rewriting or deletion

3. **Per-prompt feedback score**
   - For each prompt: `prompt_feedback` up / (up + down) = thumbs-up rate
   - Threshold: prompts below 60% thumbs-up rate should be flagged for rewrite
   - Why: quality signal the audit never had before

4. **View-to-copy conversion rate**
   - For each prompt: `prompt_copy` / `prompt_view`
   - Threshold: below 30% = prompt isn't converting curiosity to action
   - Why: "I opened it but didn't copy it" tells you the prompt's selling text (bestFor) needs work

5. **Category heatmap**
   - Matrix: categories (write/followup/coach/strategy) × difficulty (beginner/intermediate/advanced)
   - Cell value: copies per prompt
   - Why: tells you if advanced prompts are under-copied (they usually are)

---

## 3. KEY NORTH-STAR METRICS

Pick ONE north star for each of these 3 views. Display prominently on every dashboard tab:

### North-star metric (top of dashboard, giant number)
**Weekly Active Prompt Copiers (WAPC)**
= unique users who copied ≥1 prompt in the last 7 days

Why: This is the truest "is this a real thing" signal. It filters out drive-by traffic (who bounce without copying anything) and rewards only real usage.

### Supporting metrics (always visible)
- **Email capture rate** (daily %)
- **Strategy call click-through rate** (from all users, daily %)
- **Stack save rate** (from users who visited `/stacks`)

### Vanity metrics (nice to have, don't over-index on)
- Page views
- Sessions
- Social followers (track on Metricool baseline separately)

---

## 4. INFRASTRUCTURE NOTES (what you need to add)

### What's already working
- GTM is installed and firing events
- Events already have payloads

### What needs to be added for the full dashboard

**Tier 1 — this week (required for basic dashboard):**
1. **Connect GTM to GA4.** You may already have this. Verify in GTM admin that a GA4 tag is firing on every event.
2. **Create a Looker Studio project** that connects to GA4 as a data source. ~30 minutes to set up the first version.
3. **Create 4 dashboard tabs** following the spec above. ~4-6 hours to build cleanly.

**Tier 2 — this month (for strategy call funnel):**
4. **Calendly webhook integration.** When a call is booked via joinkale.com/schedule, fire a webhook that logs to either (a) a Google Sheet, (b) a simple serverless function that posts to GA4 as a `strategy_call_booked` event. ~2 hours of work.
5. **Email platform integration.** Whichever tool you wire up for the drip, make sure open/click events flow back into GA4 (most email platforms support this natively via UTM parameters).

**Tier 3 — next quarter (only when adoption justifies it):**
6. **Minimal backend database.** Right now localStorage state (favorites, stacks, feedback) is stuck on each user's device. When you want cross-device sync (required for a paid tier), add a real DB. Recommendations:
   - **Supabase** (free tier, Postgres, hosts auth) — best for this use case
   - **PlanetScale** + NextAuth for auth
   - This unlocks: cross-device stacks, team sharing, real user profiles, paid tier

---

## 5. UTM TAGGING STRATEGY

Every link you share externally should carry UTM parameters. Naming convention:

| Source | Medium | Campaign |
|--------|--------|----------|
| `podcast_<show_slug>` | `podcast` | `sizzle_feb2026` (or similar event-specific) |
| `email_drip` | `email` | `drip_email_<N>` (1-5) |
| `instagram` | `social` | varies by post |
| `talk_<event_slug>` | `keynote` | e.g., `talk_nar2026` |
| `newsletter` | `email` | `weekly_<date>` |

Example full URL:
```
https://tapthis.co/prospecting?utm_source=podcast_real_estate_rockstars&utm_medium=podcast&utm_campaign=sizzle_feb2026
```

Why it matters: you'll be able to see which podcast appearances actually drive traffic (and strategy-call clicks) vs. which are just good for ego.

---

## 6. REVIEW CADENCE

### Daily (5 min)
- Glance at Tab 1 (Health Pulse). Is DAU trending up or flat? Any anomalies?

### Weekly (30 min, Monday morning)
- Tab 2: What was the strategy call funnel last week? Any drop-off changes?
- Tab 4: Any new prompts in the top 20? Any fall out?
- Update the "Top 10 This Week" curation on the home page based on actual data (replace the static curated list with data-driven picks)

### Monthly (1 hour, first of month)
- Full review of all 4 tabs
- Pull bottom-20 prompts (Tab 4). Decide: rewrite or delete.
- Pull top-20 most-searched terms with no results (Tab 3). Decide: write those prompts next.
- Review drip email performance. Decide: A/B test which subject lines.

### Quarterly (2 hours)
- North-star metric trend over 90 days. Real growth or noise?
- Feature adoption review. Anything below 5% adoption gets cut or reinvested in.
- User cohort analysis. Do users who captured email in month 1 still come back in month 3?

---

## 7. WHAT GOOD LOOKS LIKE (benchmarks)

These are targets to aim for, not immediate expectations.

| Metric | Month 1 | Month 3 | Month 6 | Month 12 |
|--------|---------|---------|---------|----------|
| Weekly Active Prompt Copiers | 50 | 200 | 600 | 1,500 |
| Email capture rate | 4% | 8% | 10% | 12% |
| Stack save rate (of /stacks visitors) | 20% | 35% | 45% | 50% |
| Strategy call click rate (of email-captured users) | 2% | 5% | 7% | 10% |
| Strategy call booking rate (of clicks) | 10% | 15% | 20% | 25% |
| Drip email open rate | 30% | 38% | 42% | 45% |

If you're below the Month-1 targets after Month 3, something's structurally off. Revisit the audit.

If you're above the Month-6 targets in Month 3, start building for paid tier.

---

## 8. QUICK-START: BUILD THIS DASHBOARD IN 2 HOURS

If you want to ship a basic version this weekend:

1. **Hour 1:**
   - [ ] Verify GTM → GA4 connection
   - [ ] Open Looker Studio, create new report, connect GA4 as data source
   - [ ] Build Tab 1 (Health Pulse): DAU, WAU, prompt copies per day, email capture rate

2. **Hour 2:**
   - [ ] Add Tab 2 (Revenue): strategy call clicks by placement, drip email performance (if email platform connected)
   - [ ] Add Tab 3 (Features): simple `open_in_ai` tool breakdown, stacks funnel
   - [ ] Add the north-star widget (WAPC) at the top of every tab
   - [ ] Share the dashboard link with yourself so you can bookmark it

That's the minimum viable dashboard. Expand over the following weeks.

---

## 9. WHAT TO IGNORE

Don't over-engineer this. In particular, ignore:

- **Bounce rate** — meaningless for a single-page prompt vault
- **Time on page** — users who copy in 30 seconds are your best customers
- **Social media vanity metrics** (follower counts) — track in Metricool separately
- **Heatmaps** (Hotjar / FullStory) — wait until you have >500 DAU; before that, it's noise
- **Session recordings** — same as above; great later, distraction now

The 4-tab dashboard above is enough. Resist the urge to add more until you're actively using what's there.
