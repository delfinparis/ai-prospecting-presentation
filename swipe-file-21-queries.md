# The Swipe File — 21 Production-Ready AI Prospecting Queries

**Companion library to:** Find Your Next Client With AI
**Primary tool:** Claude Pro ($20/mo) — all queries tested against Claude. Most also work in ChatGPT Plus with light adjustments.
**Framework:** Every query uses the same 6-part structure: ROLE / CONTEXT / TASK / CONSTRAINTS / RULES / EXPECTED OUTPUT.
**Usage:** Copy the query, paste into Claude, replace `[BRACKETED]` fields with your specifics, send. Edit the output in your voice.

---

## INDEX

**COLD — Hyperlocal Farm & Public Records**
1. Permit-Flip Predictor
2. Absentee Owner Targeting
3. Empty Nester Reverse Lookup
4. Pre-Listing Micro-Signal Sweep

**COLD — Investor & Landlord Sourcing**
5. Tired Landlord Signal Mining
6. Rental Portfolio Mapping
7. Short-Term Rental Operator Outreach
8. REIA Meetup Intel Brief

**COLD — Niche Verticals**
9. Relocating Executive LinkedIn Query Builder
10. Medical Residency Match Day Calendar
11. PCS Season Military Farming
12. Corporate Relocation Pipeline

**COLD — Positioning & Visibility**
13. Competitor Agent Weakness Audit
14. LLM-Quotable Content Generator
15. Local Business & Institution Mapping

**WARM — Sphere Intelligence**
16. Hidden Referral Connector Mapping
17. Life-Event Screenshot Scanning
18. Equity Position Personalized Video Scripts
19. Anniversary Stack
20. Relationship-Tuned Referral Ask
21. Reverse ICP from Last 20 Closings

---

## 1. Permit-Flip Predictor

**Category:** Cold / Hyperlocal Farm
**Best for:** Listing agents farming an active flip market. Finds flippers 60–90 days BEFORE they list.
**Run frequency:** Monthly per farm
**Why it works:** Flippers pull permits in their LLC name, not the current owner's name. A permit-holder/owner mismatch is a leading indicator of an upcoming listing that nobody else is watching.

```
ROLE:
You are a real estate market intelligence analyst. You specialize in identifying properties likely to list in the next 60–90 days by analyzing public building permit data and cross-referencing it with ownership records.

CONTEXT:
I farm [ZIP CODE / NEIGHBORHOOD], [CITY, STATE]. In this area, flippers commonly pull permits to renovate a property they've recently acquired, complete the work in 4–6 months, then list for resale. Because flippers typically hold title in an LLC and pull permits under that same LLC or a related contractor entity, I can identify these flips before they hit the market by looking for mismatches between the current tax-record owner and the permit holder — or by identifying permits pulled by known flipper entities on properties they recently acquired.

TASK:
Research public building permit data for [NEIGHBORHOOD / ZIP] filed in the last 18 months. For each permit over $25,000 in value, cross-reference:
1. The permit holder / applicant name
2. The current tax-record owner name for that property
3. The date the current owner acquired the property
4. Whether the current owner is a business entity (LLC, Inc, LP) or individual

Flag properties where ALL of the following are true:
- The permit value is over $25,000 (suggesting substantial renovation, not minor repair)
- The permit was pulled within 12 months of the current owner acquiring the property
- The current owner is a business entity, not an individual
- The permit is for scope consistent with a flip (kitchen remodel, bath addition, whole-house renovation, demo/rebuild) — NOT routine maintenance (roof, water heater, fence)

CONSTRAINTS:
- Use only publicly available municipal permit data and county assessor records.
- Flag every data point as VERIFIED (with source) or INFERRED.
- Do NOT include owner-occupied properties where the homeowner is clearly renovating for personal use.
- Do NOT include properties owned by individuals with long tenure (5+ years) who pulled a permit — those are likely lifestyle upgrades, not flips.

RULES FOR OUTPUT:
For each flagged property, return:
- Property Address
- Current Owner (entity name)
- Acquisition Date and Price
- Permit Type and Value
- Permit Date
- Contractor name (if listed)
- "Likely list timing" estimate (based on typical flip timeline from permit date)
- Suggested outreach: who to contact (LLC principal via Query #5 in the hero set) and a one-sentence opener

EXPECTED OUTPUT:
A table, ranked by "likely list timing" with the soonest at the top. Below the table: a summary count of total flips detected and the average acquisition-to-permit gap in the market (a useful number to know).
```

---

## 2. Absentee Owner Targeting

**Category:** Cold / Hyperlocal Farm
**Best for:** Any listing agent. Absentee owners are the largest under-targeted group in most markets.
**Run frequency:** Quarterly per farm
**Why it works:** Out-of-state mailing addresses on tax rolls identify owners who don't live in the property. They're harder to reach by door-knock or postcard but easier to reach by email/LinkedIn — and they often want to sell or need property oversight they're not getting.

```
ROLE:
You are a real estate research analyst specializing in absentee owner outreach. You identify property owners whose mailing address on the tax roll differs from the property address, which indicates they do not reside in the property.

CONTEXT:
I serve [CITY, STATE] and want to build a pipeline of absentee owners in [NEIGHBORHOOD / ZIP]. These are people who own property in my market but live elsewhere. They may be landlords, inheritors, former residents who relocated, or investors who never intended to occupy. They are underserved by traditional agent marketing (postcards arrive at their investment property, not at them) and are statistically more likely to sell than owner-occupants over any given 12-month window.

INPUT:
[Paste a list of absentee owners from the county assessor's database. Columns: Property Address | Owner Name | Owner Mailing Address | Assessed Value | Year Acquired | Tax Delinquency Status]

TASK:
For each absentee owner in the list:
1. Determine if the mailing address is in-state, out-of-state, or international
2. Identify whether the owner is an individual or an entity (LLC, trust, estate)
3. For individuals, estimate life stage from name patterns and mailing-address location (retired snowbird in FL, adult child in another metro, professional relocated for work)
4. For entities, note the entity type and whether it warrants a Query #5 (LLC Unmasking) follow-up
5. Classify likely seller motivation: "inherited and out of state," "retired and downsized," "landlord exiting," "relocated for work — kept the old house," "tax-delinquent distressed"
6. Rank each owner on outreach priority 1–10 based on: tenure in the property, tax delinquency signals, geographic distance (further = more likely to sell), and entity complexity (simple = easier outreach)

CONSTRAINTS:
- Use only publicly available data.
- Do not speculate about an owner's financial distress beyond what tax records reveal.
- If classification is ambiguous, mark it UNCLEAR and move on.
- Do not include owners whose mailing address and property address are both in the same metro (likely second-home situations that need different messaging).

RULES FOR OUTPUT:
For each owner: Property Address | Owner Name | Mailing City/State | Owner Type (Individual/Entity) | Likely Motivation | Priority Score | Suggested outreach channel (letter / LinkedIn / phone) | One-sentence opener customized to the motivation (e.g., out-of-state inheritor gets "managing a property from [their city] is a hassle — happy to be eyes-on-the-ground if you ever want to explore options").

Group the output into three sections: "Reach out this month" (priority 8–10), "Nurture — 6-month cycle" (priority 5–7), "Pass" (priority 1–4).

EXPECTED OUTPUT:
Three tables plus a one-line summary: "X high-priority absentees, Y nurture, Z pass."
```

---

## 3. Empty Nester Reverse Lookup

**Category:** Cold / Hyperlocal Farm
**Best for:** Listing agents in suburban or family-oriented neighborhoods. Empty nesters are the highest-probability sellers nobody is targeting on purpose.
**Run frequency:** Annually per farm (timed to May–August, post-graduation)
**Why it works:** Owners 55+ with 18+ years of tenure often sell within 2–3 years of their youngest child leaving home. Cross-referencing tenure with publicly reported graduation news identifies this transition before anyone else.

```
ROLE:
You are a demographic research analyst specializing in real estate seller pipelines. You identify homeowners approaching the empty-nester transition by cross-referencing property tenure data with publicly available life-stage signals.

CONTEXT:
I farm [NEIGHBORHOOD / ZIP]. Based on county assessor data, I have a list of homeowners who have owned their property for 18+ years and are 55 years or older. Many of these families are approaching or in the empty-nester phase, which is a statistically reliable 24-month sell window. I want to identify WHICH of these families have had a child graduate high school or college in the last 24 months, because those are the highest-probability sellers in my farm this year.

INPUT:
[Paste a list of long-tenure owners. Columns: Property Address | Owner Name(s) | Estimated Age | Years Owned | Household Size from public sources if available]

TASK:
For each owner in the list:
1. Search publicly indexed sources for any mention of a graduation, college acceptance, or "off-to-college" life event involving a child of the household in the last 24 months. Sources: local newspaper honor rolls, high school graduation programs, sports team rosters, college announcements, faculty/coach social posts that name graduates, church bulletins, civic award announcements.
2. If a graduation is found, capture: child's name (if public), graduating institution, date.
3. If no direct evidence is found, note whether the parents' publicly visible social media shows older teens in the household 2+ years ago (informing a likely-graduated estimate).
4. Classify each household: CONFIRMED EMPTY NESTER (recent graduation), LIKELY EMPTY NESTER (tenure + age match the pattern, no direct evidence), UNCLEAR (insufficient data), NOT A FIT (evidence of younger children still at home).

CONSTRAINTS:
- Use only publicly available information. No paid databases.
- Never assume children's existence or absence without evidence.
- Respect privacy — if the only "evidence" would require piecing together social media in a way that feels invasive, mark the household UNCLEAR and move on.
- Do not include any details about minor children beyond the fact of graduation itself.

RULES FOR OUTPUT:
For each household: Address | Owner Name | Classification (Confirmed / Likely / Unclear / Not A Fit) | Evidence (2 sentences max, with source if VERIFIED) | Recommended outreach timing (confirmed = immediate; likely = 60-day follow-up; unclear = quarterly nurture) | Suggested opener for confirmed empty nesters only (warm, not transactional — "noticed [institution] had a beautiful graduation ceremony this year — if the house is starting to feel big, I'd love to help you think through what's next someday").

EXPECTED OUTPUT:
A table ranked by classification priority (Confirmed first). Below the table: total counts by category.
```

---

## 4. Pre-Listing Micro-Signal Sweep

**Category:** Cold / Hyperlocal Farm
**Best for:** Farm agents who want to know what's happening in their neighborhood before it hits MLS.
**Run frequency:** Monthly per farm
**Why it works:** Most agents rely on MLS for market intelligence. MLS is lagging data. Building permits, HOA minutes, business license changes, school boundary discussions, and civic news are leading indicators that compound into listing activity 30–120 days later.

```
ROLE:
You are a hyperlocal real estate intelligence analyst. You aggregate leading indicators from non-MLS sources to predict which neighborhoods will see the most listing activity in the next 30–120 days.

CONTEXT:
I farm [NEIGHBORHOOD / ZIP / SUBDIVISION] in [CITY, STATE]. I want a single monthly briefing that tells me what's happening in my farm that will translate into listing activity in the coming quarter, pulled from sources most agents never check.

TASK:
For [NEIGHBORHOOD] in the last 60 days, research and summarize:

1. BUILDING PERMITS — filed over $10,000 in value. Flag especially: demolitions, major additions, pools/ADUs, and any permits on long-tenure owner properties (potential "renovate to sell" signal).

2. HOA / CONDO ASSOCIATION ACTIVITY — published meeting minutes, announced special assessments, major capital projects, any dispute or lawsuit mentions. Special assessments often trigger cash-strapped owners to sell.

3. LOCAL BUSINESS LICENSE CHANGES — any new businesses opening or closing that significantly change the neighborhood's character or foot traffic.

4. SCHOOL BOUNDARY CHANGES — any ongoing discussions at the school board about redistricting, new school construction, or program changes that would affect families' school assignment.

5. CIVIC NEWS — zoning change applications, variance requests, development proposals, major infrastructure projects (road work, transit), commercial property changes.

6. EMPLOYER NEWS — any large employer in the immediate area announcing layoffs, relocations, hiring sprees, or office opens/closures.

7. CRIME / SAFETY TRENDS — any material shifts in local police beat reports or community forums.

CONSTRAINTS:
- Use only publicly available sources: municipal permit portals, HOA public minutes, local news, school board agendas, civic forums (Nextdoor public posts only), news archives.
- Do not fabricate data. If a source wasn't checkable, say "not checked" and list the source I should check manually.
- Stay neutral and analytical — this is intelligence, not opinion. Do not speculate on whether changes are "good" or "bad."

RULES FOR OUTPUT:
A one-page briefing organized by the seven sections above. For each section, 3–5 bullet points max, each with a source citation. End the briefing with:
- "TOP 3 LISTING-TRIGGER SIGNALS THIS MONTH" — the specific items most likely to convert to a listing in the next 90 days
- "RECOMMENDED OUTREACH" — 2–3 concrete actions this week (e.g., "send a 'thinking of you' letter to the 12 owners in the 200 block of Oak — their street is about to get 18 months of construction")

EXPECTED OUTPUT:
One-page briefing as described.
```

---

## 5. Tired Landlord Signal Mining

**Category:** Cold / Investor & Landlord Sourcing
**Best for:** Agents who want to work with small portfolio landlords exiting 1–3 properties.
**Run frequency:** Monthly per market
**Why it works:** Small landlords vent publicly about tenant issues, maintenance costs, and property taxes long before they decide to sell. Their rental listings themselves often signal burnout — frequent re-lists, rent drops, maintenance complaints in the description.

```
ROLE:
You are a real estate market intelligence analyst specializing in identifying small-portfolio landlords who are approaching the decision to sell.

CONTEXT:
I serve [METRO AREA]. Small landlords (1–5 properties) often decide to exit one or more properties after months or years of quiet frustration. The signals appear publicly in two places: their rental listings (on Zillow, Craigslist, Apartments.com, Facebook Marketplace) and in public forums where they vent (Reddit, local landlord groups, X). I want to identify the landlords in my market showing these signals NOW so I can offer them a conversation about an exit strategy before they list themselves or call a competitor.

TASK:
Research public rental listings in [METRO AREA] active in the last 45 days on Zillow, Craigslist, Apartments.com, and Facebook Marketplace. For each listing, analyze:

1. RE-LIST FREQUENCY — has this unit been listed multiple times in the last 12 months?
2. RENT DROPS — has the listed rent decreased from an earlier listing?
3. LANGUAGE SIGNALS — does the description contain phrases suggesting burnout: "no pets this time," "NO smoking, NO exceptions," "tenant responsible for ALL utilities," "landlord will NOT negotiate," "quiet tenants only," "previous tenant damage being repaired," or similar language that indicates friction from prior tenants?
4. TIME-ON-MARKET — how long has the listing been active without renting?
5. OWNER DETAILS — is the owner identifiable from the listing (direct landlord, not property management company)? If so, is it the same person listing multiple properties?

Flag listings that show 2 or more burnout signals. For each flagged listing, if the owner is identifiable, cross-reference the property address against tax records to determine the full portfolio size.

CONSTRAINTS:
- Public rental listings only. No scraping of private platforms.
- Do not include listings managed by large property management companies — those are not the target audience.
- Do not include listings with fewer than 2 signals — one signal alone is noise.
- Respect honest listings — don't pathologize a landlord who simply wants responsible tenants.

RULES FOR OUTPUT:
For each flagged listing:
- Property Address
- Listed Rent and any drop history
- Re-list count (12 months)
- Burnout signals detected (quoted from the listing)
- Owner name (if identifiable)
- Portfolio size (if determinable)
- Suggested outreach: a letter or DM that acknowledges the reality without pitching a sale. Something like "I noticed the [address] listing. If being a landlord has gotten harder in the last year or two, happy to share how some of my clients have transitioned out without giving up the income — no pressure."

EXPECTED OUTPUT:
A priority-ranked table. Below it, a note on the top 3 portfolios worth a follow-up outreach, ranked by portfolio size × signal strength.
```

---

## 6. Rental Portfolio Mapping

**Category:** Cold / Investor & Landlord Sourcing
**Best for:** Agents targeting an existing known investor for repeat business.
**Run frequency:** Before any investor conversation — run it as prep.
**Why it works:** When you know one property an investor owns, you can find the rest by searching county assessor records for all properties with the same mailing address. Knowing their full portfolio before a conversation makes you look like a professional, not a prospector.

```
ROLE:
You are a real estate research analyst. You help agents map a known investor's full property portfolio by cross-referencing county assessor data on mailing addresses.

CONTEXT:
I know an investor in [COUNTY / METRO AREA] owns at least one property at [KNOWN PROPERTY ADDRESS]. The investor's mailing address on the tax record is [MAILING ADDRESS — extract from assessor]. I want to find every other property in the same county (or adjacent counties I also serve) that lists this same mailing address, because those are almost certainly other properties in the same portfolio.

TASK:
1. Search the county assessor database(s) for all property records where the mailing address matches [MAILING ADDRESS]. Include minor variations (suite vs ste, road vs rd, etc.).
2. For each matching property, pull: property address, assessed value, year acquired, property type (SFR / 2-4 unit / 5+ unit / commercial / land), and current tenancy status if available.
3. Map the portfolio:
   - Total property count
   - Total assessed value
   - Geographic concentration (map by zip or neighborhood)
   - Property type mix
   - Acquisition timeline (when they started buying, when they stopped, any gaps)
4. Identify the investor's apparent STRATEGY based on the portfolio: BRRRR accumulator, buy-and-hold cash flow, house hacker, STR operator, flipper (short hold times), value-add multifamily, etc.
5. Flag any properties where the investor may be over-concentrated or under-utilizing (e.g., an older property never renovated, or a property acquired 10+ years ago that has appreciated dramatically).

CONSTRAINTS:
- Public assessor data only.
- If the mailing address is a PO Box, flag it — the search will be less complete because PO Box matching may not surface all properties.
- Do not include properties in counties you can't serve — stay focused on actionable geography.

RULES FOR OUTPUT:
1. An INVESTOR PROFILE paragraph summarizing portfolio size, strategy, and concentration.
2. A TABLE of all properties: Address | Type | Assessed Value | Year Acquired | Notes.
3. A section called "CONVERSATION STARTERS" with 3 specific, informed opening lines you could use in a call or meeting with this investor, referencing specific portfolio details without being creepy (e.g., "Noticed you've been focused on the [neighborhood] market since [year] — the 2BR multifamily space there has been moving differently this year, wanted to compare notes").
4. A "BEST OPPORTUNITY" callout: based on the portfolio, what transaction is this investor most likely to do in the next 12 months, and what should I bring them?

EXPECTED OUTPUT:
As described above, in that order.
```

---

## 7. Short-Term Rental Operator Outreach

**Category:** Cold / Investor & Landlord Sourcing
**Best for:** Agents in markets with significant STR activity (tourist destinations, major metros, college towns).
**Run frequency:** Quarterly per market
**Why it works:** STR operators are a specific investor subclass with volatile economics — regulation changes, occupancy drops, and cash-flow pressure push them to exit. Public Airbnb/VRBO listings cross-referenced to assessor records identify them.

```
ROLE:
You are a real estate market analyst who specializes in identifying short-term rental operators and the market conditions affecting their decision to continue, expand, or exit.

CONTEXT:
I serve [METRO AREA / COUNTY]. STR regulation, occupancy rates, and operating costs have shifted in my market. I want to identify STR operators in my area who may be candidates for: (a) selling the STR property and re-deploying capital, (b) converting to long-term rental, or (c) expanding their portfolio and needing an agent partner.

INPUT:
[Paste a list of publicly visible STR listings in your market. Source: Airbnb or VRBO, filtered to your geography. Include: Listing URL, property type, approximate address or neighborhood, host name, number of listings by this host.]

TASK:
For each STR operator represented in the list:
1. Cross-reference the listing's approximate location and description against the county assessor to identify the actual property address (where possible from public data).
2. Determine from assessor records: when did the current owner acquire the property? What was the purchase price? What's the estimated current value?
3. Look at the STR listing itself: review count, rating trend, recent availability (frequent open weeks suggest occupancy decline), listed nightly rate vs. market average.
4. Check for any local regulatory actions that affect this host (new STR caps, permit requirements, HOA restrictions) and flag properties likely affected.
5. Classify each operator: THRIVING (strong reviews, high occupancy, growing) | STEADY (maintaining) | STRUGGLING (occupancy slipping, rates dropping, recent negative reviews) | REGULATORY PRESSURE (caught by new rules).

CONSTRAINTS:
- Public STR listings and public assessor data only.
- Do not include listings hosted by large property managers (they're not making the sell/hold decision).
- Do not make claims about occupancy without review-count-based evidence.

RULES FOR OUTPUT:
For each operator:
- Host Name (from STR listing)
- Property Address (if identifiable)
- STR Performance: review count / rating / recent occupancy signal
- Ownership: acquisition date / price / likely equity
- Classification (Thriving / Steady / Struggling / Regulatory Pressure)
- Recommended conversation: "Sell the property now" (struggling + high equity), "Convert to LTR and refi" (steady + regulatory pressure), "Buy another one" (thriving + appreciating capital)
- One-sentence opener tuned to the classification

EXPECTED OUTPUT:
A priority-ranked table (Struggling and Regulatory Pressure at top). Below the table: a "Market Summary" paragraph on the overall health of STR operations in the area.
```

---

## 8. REIA Meetup Intel Brief

**Category:** Cold / Investor & Landlord Sourcing
**Best for:** Agents attending a local real estate investor association (REIA) meetup to prospect for investor clients.
**Run frequency:** Before each meetup you attend
**Why it works:** Walking into a REIA meetup cold is networking roulette. Walking in with a briefing on the 20 people most likely to be there, what they're working on, and what you can offer each one converts the room from strangers to warm leads.

```
ROLE:
You are a real estate networking strategist. You brief agents before they attend investor meetups so they can walk in with a specific game plan, not as a generic networker.

CONTEXT:
I'm attending the [MEETUP NAME] at [VENUE] on [DATE] in [CITY]. Based on the meetup's public website, social media, and past attendee mentions, I want a briefing on: who typically attends, what investor archetypes are represented, who the 2–3 speakers or organizers are, and which attendees are most likely to be valuable for me to meet tonight.

TASK:
Research the following publicly:

1. MEETUP BACKGROUND
- How long has this group been running?
- What's the stated focus (BRRRR, short-term rentals, commercial, wholesaling, etc.)?
- Who are the organizers / regular speakers?
- What's the typical attendance?

2. ATTENDEE ARCHETYPES
- Based on past event recaps, Facebook group activity, and LinkedIn mentions of the meetup, what types of investors show up?
- Are there known individuals who attend regularly? List them with one-sentence bios.

3. TONIGHT'S SPEAKER (if known)
- Name, background, known portfolio, social presence
- What topics are they likely to cover based on their public writing or podcasts
- One thoughtful question I could ask them during Q&A that would make them remember me

4. CONVERSATION STRATEGY
- Two "openers" I can use to start a conversation with a stranger at a meetup
- Two offer I can make to investors that is specific and useful, not generic (e.g., "I just pulled a list of LLCs that bought in [neighborhood] in 2024 — happy to share if you're looking for private-money lending opportunities")
- One landmine to avoid (a topic or approach that will get me dismissed)

5. FOLLOW-UP PLAN
- A template DM or email to send to anyone I meet tonight, within 24 hours
- A plan for a second-touch in 7 days if they don't respond

CONSTRAINTS:
- Public data only. Do not scrape meetup member lists.
- Do not fabricate past attendees. If I can't verify, say so.
- Be realistic about my value proposition — as an agent, what I offer investors is different from what another investor offers them.

RULES FOR OUTPUT:
A one-page briefing in the five sections above. Each section tight (no fluff).

EXPECTED OUTPUT:
As described above.
```

---

## 9. Relocating Executive LinkedIn Query Builder

**Category:** Cold / Niche Verticals
**Best for:** Agents in markets with major employer concentrations (finance, tech, healthcare, manufacturing).
**Run frequency:** Monthly per target company
**Why it works:** Most agents try to "use LinkedIn" and fail because they don't know how to build search queries that surface relocating executives. This query teaches Claude to generate the exact Boolean search string you paste into LinkedIn (or Sales Navigator).

```
ROLE:
You are a LinkedIn sourcing strategist. You build advanced Boolean search strings that identify executives who have recently relocated or will soon relocate to a specific metro area.

CONTEXT:
I'm a listing and buyer's agent in [METRO AREA, STATE]. I want to build a weekly prospect list of C-suite, VP-level, and Director-level executives who have recently taken jobs in my metro or announced relocations. These are high-income professionals with time constraints, often handling a home sale in their departure city simultaneously with a home purchase here. They are underserved by standard agent prospecting because they don't live here yet.

TASK:
Build 5 distinct LinkedIn search queries I can paste into LinkedIn standard search and LinkedIn Sales Navigator (if I have access). Each query should target a slightly different segment so I can run them weekly and compare:

1. QUERY A: Executives who announced a new role in [METRO] in the last 30 days
2. QUERY B: Executives whose previous employer was based 500+ miles from [METRO], now at a [METRO] employer
3. QUERY C: Specific target companies in [METRO] (research and list the top 10 employers by size) — people who joined any of them in the last 60 days at Director level or above
4. QUERY D: Medical executives (for healthcare metros) — hospital administrators, department chairs, practice owners who relocated
5. QUERY E: Tech executives — VP and above at companies with [METRO] offices

For each query, provide:
- The exact Boolean search string
- The filters to apply in LinkedIn Sales Navigator (geography, title, past company, tenure, function)
- The approximate result count I should expect (so I know if the query is too narrow or too wide)
- What to do with the results: connection request template (one sentence, non-salesy) and follow-up sequence

CONSTRAINTS:
- LinkedIn standard search has fewer filters than Sales Navigator. Provide BOTH versions of each query.
- Respect LinkedIn's terms of service — no scraping, no mass connection requests, no automation tools.
- The connection requests should be genuine and relevant; no "networking" spam.

RULES FOR OUTPUT:
For each of the 5 queries: a clear labeled section with the Boolean string in a code block, the filter list, the expected result count, and the connection request template.

Also include a section called "TOP 10 TARGET EMPLOYERS IN [METRO]" listing the companies you researched for Query C, with each company's approximate size and why it's a high-value target.

EXPECTED OUTPUT:
As described.
```

---

## 10. Medical Residency Match Day Calendar

**Category:** Cold / Niche Verticals
**Best for:** Agents in cities with major teaching hospitals. A massive, predictable, underserved seller/buyer cohort.
**Run frequency:** Annually (prepare in February, execute April–July)
**Why it works:** Medical residency Match Day happens every March. Matched residents move to their training city in June–July. Every major teaching hospital publishes incoming resident class announcements. This is a known, date-certain pipeline of 100–500 new residents per hospital per year, and almost no agent works it deliberately.

```
ROLE:
You are a real estate market intelligence analyst specializing in the medical relocation cycle. You help agents build structured outreach around the annual Match Day / residency relocation pattern.

CONTEXT:
I serve [METRO AREA]. Every year in March, medical students nationwide are matched to residency programs. The ones matched to hospitals in my metro will physically relocate here in June or July. Each hospital's incoming class is publicly announced — often with names, medical schools of origin, and specialty. I want to build a 12-month calendar and outreach playbook around this predictable cohort.

TASK:
For [METRO AREA], research:

1. TEACHING HOSPITALS — list every major teaching hospital with residency programs. For each, estimate incoming class size annually.

2. MATCH DAY TO MOVE TIMELINE — specifically, for each hospital:
- When does the hospital publish its incoming class list? (Usually April)
- When do residents typically begin housing searches?
- When do they sign leases or make purchases?
- What's the typical housing budget and neighborhood preference for this hospital's residents?

3. OUTREACH CHANNELS — for each hospital:
- Is there an incoming-resident welcome coordinator or housing resource contact?
- Are there alumni social groups or class-year Facebook groups?
- Do current residents have a social presence that would let me offer help via existing residents referring incoming ones?

4. MONTH-BY-MONTH CALENDAR — for the next 12 months, what should I be doing each month to build relationships with the incoming class:
- FEBRUARY: pre-Match Day prep (build hospital-specific landing page)
- MARCH: post-Match Day (name scraping, LinkedIn outreach)
- APRIL-MAY: intro messaging
- JUNE-JULY: showing/signing phase
- AUGUST-SEPTEMBER: follow-up with those who signed leases (future buyers)
- OCTOBER-FEBRUARY: nurture

5. OUTREACH MESSAGING — 3 templates tuned to the resident cohort:
- Initial intro (LinkedIn or hospital welcome packet insert)
- Neighborhood guide delivery (an actual valuable resource, not a sales pitch)
- Check-in 60 days after arrival (their honeymoon with the hospital is wearing off)

CONSTRAINTS:
- Respect medical-school privacy norms. Publicly announced incoming residents are fair game. Do NOT scrape match-list databases or enter private group spaces.
- Do not exploit the fact that residents are often cash-strapped — your messaging should be genuinely helpful, not predatory.

RULES FOR OUTPUT:
A 5-section playbook as described. The month-by-month calendar should be in a table format. The outreach messaging should be in full template form (ready to edit for voice).

EXPECTED OUTPUT:
As described.
```

---

## 11. PCS Season Military Farming

**Category:** Cold / Niche Verticals
**Best for:** Agents within 60 miles of any active military installation.
**Run frequency:** Annually (peak PCS May–August)
**Why it works:** PCS (Permanent Change of Station) moves are a military-specific relocation cycle. Every base has a predictable rotation pattern, and military families are well-served when their agent genuinely understands BAH rates, VA loans, and the 30-day-notice reality.

```
ROLE:
You are a real estate market strategist specializing in the military PCS (Permanent Change of Station) relocation cycle. You help agents build structured outreach around the annual PCS season at a specific military installation.

CONTEXT:
I serve [METRO AREA], which is within [X MILES] of [BASE NAME] ([BRANCH OF SERVICE]). PCS season peaks May–August every year. Military families have specific needs: BAH-constrained budgets, VA loan use, 30-day notice timelines, spouse-employment considerations, and preference for agents who genuinely understand military life.

TASK:
For [BASE NAME], research and build:

1. BASE INTELLIGENCE
- Total active-duty personnel assigned to the base
- Approximate number of PCS moves IN per year (arrivals)
- Approximate number of PCS moves OUT per year (departures)
- Current BAH rates for this metro by rank (E-5 with dependents, O-3 with dependents, etc.)
- Typical housing patterns (on-base vs off-base percentage, preferred neighborhoods, renting vs buying split)

2. PCS CYCLE CALENDAR
- When are PCS orders typically issued (3–4 months before the move)?
- What's the process a service member goes through — from orders, to house hunting trip, to lease/purchase decision?
- What's the "sponsor" system and how can I plug into it?

3. MILITARY-SPECIFIC AGENT CREDENTIALS
- Is MRP (Military Relocation Professional) certification worth getting?
- What other certifications do military families look for?
- Which local VA-approved lenders should I partner with?

4. OUTREACH CHANNELS
- Base housing office or command sponsor program — how do I engage as a resource?
- Spouse Facebook groups (PCS to [base name]) — are they open to agents posting, or do they require a different approach?
- Military-specific sites (AHRN, MilitaryByOwner, USAA real estate agent network)

5. MESSAGING (3 TEMPLATES)
- Inbound inquiry response tuned to a military family: acknowledge BAH, timeline, VA loan, and the reality that they might not have time to visit before signing
- Sponsor-family outreach: how to be helpful to a family in the "orders just came" phase
- Post-move check-in: 60 days after move, when friction with on-base housing is highest

CONSTRAINTS:
- Respect OPSEC (operational security). Do not ask service members about deployment schedules, unit assignments, or any sensitive topics.
- Be honest about the agent commission reality in a BAH-constrained market.
- Military families are often relocation veterans — treat them as sophisticated, not rookies.

RULES FOR OUTPUT:
A 5-section briefing. BAH data should be a table by rank.

EXPECTED OUTPUT:
As described.
```

---

## 12. Corporate Relocation Pipeline

**Category:** Cold / Niche Verticals
**Best for:** Agents in metros with major employer expansion or new headquarters openings.
**Run frequency:** Quarterly per metro
**Why it works:** When a Fortune 1000 company announces a new office, HQ relocation, or 50+ hire plan, there's a 6–18 month relocation wave that follows. Most agents find out about it 12 months late, after the relocated employees have already chosen their agent.

```
ROLE:
You are a corporate relocation intelligence analyst. You identify employers in a metro area that are about to generate relocation activity, and you build an outreach plan for the real estate agent who wants to be the preferred agent on their relocation list.

CONTEXT:
I serve [METRO AREA]. I want a quarterly briefing on every major employer announcement in the last 90 days that signals incoming relocation activity: new HQ announcements, new office openings, 50+ hiring plans, economic development incentive deals, or M&A with workforce implications.

TASK:
For [METRO AREA] in the last 90 days, research:

1. RELOCATION TRIGGER ANNOUNCEMENTS
- Companies announcing new offices or HQ moves TO [metro]
- Companies announcing 50+ new hires
- Economic development incentive packages announced by state/local government (these are often public and name the company)
- Major M&A where the acquirer's workforce will expand in [metro]
- Research university or hospital expansions with hiring implications

2. FOR EACH ANNOUNCEMENT:
- Company name
- Announcement date and source
- Size of workforce impact (# of hires, relocation count if disclosed)
- Timing of actual hiring / relocation
- Relocation policy (if known) — do they offer relocation services to employees? Who's their provider (Cartus, SIRVA, Graebel)?
- HR / relocation contact person if publicly identifiable (LinkedIn)

3. RELATIVE RANKING
- Rank the announcements by: total workforce impact × timing (sooner = higher priority) × accessibility (easier to reach HR = higher).

4. OUTREACH STRATEGY FOR TOP 3
- For the top 3, build a specific outreach plan: who to reach, through which channel, with what offer (preferred agent status? relocation tours? buyer education session for their HR team?)
- Draft a specific outreach email tuned to each

5. ALSO CHECK
- Are there relocation management companies (RMCs) actively hiring agents in [metro]? How do I get on their preferred agent lists?

CONSTRAINTS:
- Public sources only.
- Do not contact HR contacts cold without a warm angle (usually you need to offer something useful first — a market report for their relocating employees, for example).
- Do not speculate on unannounced relocations.

RULES FOR OUTPUT:
Four sections plus the RMC appendix. Announcements in a table, ranked by priority. Outreach plans for top 3 as full mini-strategies (not one-liners).

EXPECTED OUTPUT:
As described.
```

---

## 13. Competitor Agent Weakness Audit

**Category:** Cold / Positioning & Visibility
**Best for:** Solo agents and small teams trying to break into a farm where one dominant agent owns the market.
**Run frequency:** Annually per competitor, or before major marketing pushes.
**Why it works:** Dominant competitors have patterns you can exploit — they neglect certain neighborhoods, certain buyer types, certain price bands. A structured audit of their 24-month public footprint reveals the gaps.

```
ROLE:
You are a competitive intelligence analyst for the real estate industry. You analyze a dominant competitor agent's public footprint and identify specific, exploitable gaps that a smaller competitor can capture.

CONTEXT:
I am an agent in [MARKET]. The dominant agent in my farm is [COMPETITOR NAME] at [THEIR BROKERAGE]. I want a clear-eyed audit of what they're doing well, where their coverage is thin, and how I can position myself to win business they can't or won't serve.

TASK:
Research [COMPETITOR NAME]'s public footprint for the last 24 months across:

1. LISTING PORTFOLIO (what they're actually closing)
- Total closed transactions (if published anywhere)
- Price band distribution (luxury, mid-market, entry-level)
- Neighborhood concentration (which areas they dominate vs. which they ignore)
- Property types (SFR, condo, multifamily, new construction)
- Listing side vs. buyer side split (if determinable)
- Average days on market compared to the market overall

2. MARKETING & BRAND
- Website (strengths, gaps, content cadence)
- YouTube / video presence
- Podcast appearances or own podcast
- Instagram, LinkedIn, Facebook — content style and consistency
- Press coverage (Inman, HousingWire, local magazines, local TV)
- Awards, rankings, "top 100" list appearances

3. REVIEWS
- Total review count across Google, Zillow, Realtor.com
- Star average
- Common themes in 5-star reviews (what do clients love?)
- Common themes in 3-star and lower reviews (what do clients complain about — this is gold)

4. WEAKNESSES & GAPS
For each of these, give me a specific finding:
- A price band they underserve
- A neighborhood they don't market to
- A buyer type they don't speak to (first-time, luxury, investor, downsizer, etc.)
- A communication channel where they're absent or weak
- A review complaint that repeats — something I can explicitly counter-position against

5. POSITIONING STATEMENTS
- 5 positioning statements I can use in my own marketing that exploit their gaps without naming them. Example: "For first-time buyers who want an agent who texts back within 10 minutes, not 10 hours" (if the complaint theme is slow response).
- Each statement should be specific, sharp, and defensible based on the audit findings.

CONSTRAINTS:
- Public data only. No scraping, no paid databases.
- Do not name [COMPETITOR] in any of the 5 positioning statements. The audit is for me; the positioning is public.
- Be rigorous — don't manufacture weaknesses. If they're genuinely strong, say so.

RULES FOR OUTPUT:
Five sections as described. Audit findings in bullets with sources. Positioning statements clearly numbered.

EXPECTED OUTPUT:
As described.
```

---

## 14. LLM-Quotable Content Generator

**Category:** Cold / Positioning & Visibility
**Best for:** Every agent who wants to be recommended by AI (the Hero #5 playbook made tactical).
**Run frequency:** Monthly — pick one piece per month and actually write it.
**Why it works:** Not all content is equal in an LLM's eyes. Structured, specific, locally-grounded content gets cited. Generic blog posts don't. This query generates specific titles that are structurally likely to get quoted.

```
ROLE:
You are a generative engine optimization (GEO) content strategist. You generate content ideas that are structurally likely to be cited by an LLM when a consumer asks a real estate question in a specific market or niche.

CONTEXT:
I want my website or blog content to be cited when ChatGPT, Claude, Gemini, and Grok answer consumer questions like "best neighborhood in [city] for first-time buyers" or "how much is my home worth in [neighborhood]." LLMs tend to cite content that: has specific data, uses clear question-and-answer structure, is hosted on an authoritative domain, is updated with a recent timestamp, and answers a narrow, specific question.

MY NICHE: [e.g., "Listing agent for owner-occupied single-family in Avondale, Logan Square, and Lincoln Park, Chicago"]
MY CURRENT CONTENT: [Briefly describe what you already publish — website, blog, YouTube, podcast]

TASK:
Generate 10 content ideas that are structurally LLM-quotable for my niche. For each idea:

1. A specific, long-tail title that mirrors a real question a consumer would type into an LLM
2. The intent behind the query (what problem is the consumer actually trying to solve?)
3. A suggested outline (5–8 sections) that answers the question with specific data and minimal fluff
4. The types of data or citations the piece should include (e.g., "last 90 days of median sale price in Avondale, pulled quarterly from MRED")
5. The ideal hosting location (personal agent site, brokerage site, Medium, LinkedIn Article, YouTube)
6. An LLM-quote-worthiness score 1–10 (based on specificity, data density, and query-match potential)
7. A 90-day promotion plan — where to distribute the piece so LLMs actually crawl it

Also identify 3 CATEGORIES OF CONTENT I should commit to for the next 12 months, with the expected LLM citation impact of each.

CONSTRAINTS:
- Ideas must be specific to my niche. "Tips for home buyers" = score 1/10. "How long does a home take to sell in Avondale in the 2026 spring market?" = score 8/10.
- Do not recommend content I can't actually research with public data.
- Do not recommend paid content or ad-driven strategies.

RULES FOR OUTPUT:
A table for the 10 content ideas (columns: Title | Intent | LLM Score | Host | Promotion). Below the table, a bulleted outline for the top 3 ideas (the ones I should write first). Below that, the 3 content categories with reasoning.

EXPECTED OUTPUT:
As described.
```

---

## 15. Local Business & Institution Mapping

**Category:** Cold / Positioning & Visibility
**Best for:** Agents who want to build partnerships with the 30 most influential non-agent businesses in their farm.
**Run frequency:** Annually per farm
**Why it works:** The local florist, pediatric dentist, CrossFit owner, and coffee shop proprietor all have hundreds of relationships each in your farm. Becoming the agent they refer to is a compounding, durable advantage.

```
ROLE:
You are a local business network mapping strategist. You identify the most influential non-agent businesses in a neighborhood and build a prioritized partnership plan for a real estate agent who wants to be the preferred referral agent for those businesses.

CONTEXT:
I serve [NEIGHBORHOOD / ZIP CODE] in [CITY, STATE]. I want to build a list of the 30 most influential local businesses and institutions whose owners/operators have networks of 100+ local customers, so I can build one-to-one referral relationships with them over the next 12 months.

TASK:
Research public sources for [NEIGHBORHOOD]:

1. BUSINESSES TO MAP (categories)
- Independent coffee shops, bakeries, local restaurants (especially family-owned)
- Pediatric dentists, family practices, OB/GYNs (high-touch, recurring relationships with families)
- CrossFit / yoga / pilates / martial arts studios (weekly relationships with hundreds)
- Daycares, preschools, music schools, tutoring centers
- Independent pet groomers, veterinarians
- Boutique fitness, salons and barbershops (weekly/monthly relationships)
- Independent financial advisors (especially those serving <$1M AUM)
- Estate attorneys, divorce attorneys (transaction-adjacent)
- Youth sports coaches (soccer, baseball, swim)
- Real estate photographers, stagers, contractors (professional adjacencies)
- Independent insurance agents
- Church, synagogue, mosque community leaders (if appropriate for your market)
- Independent bookstore, toy store, specialty grocery (community hubs)

2. FOR EACH BUSINESS
- Name
- Owner / operator name (if identifiable)
- Size of customer base (estimate from public signals)
- Social media presence (following)
- Community reputation (reviews, press)
- Likely "referral potential" score 1–10 based on: customer relationship depth, owner visibility, community embeddedness

3. TOP 30 — build the list ranked by referral potential

4. PARTNERSHIP TIERS
- Tier 1 (top 10): build a genuine relationship this year. One coffee per month with each. Bring them clients.
- Tier 2 (11–20): quarterly check-in. Send them occasional referrals. Invite to events.
- Tier 3 (21–30): annual touch. Holiday card. Open invitation.

5. FIRST-MEETING FRAMEWORK
- A script for the initial coffee/intro meeting with a Tier 1 partner
- The "value first" offer I can make (refer THEM clients before asking for referrals in return)
- How to set up a formal referral relationship without it feeling transactional

CONSTRAINTS:
- Public data only.
- Do not rank by revenue alone — community embeddedness matters more.
- Skip businesses that are part of large chains; focus on independents and owner-operators.

RULES FOR OUTPUT:
The Top 30 as a ranked table. Tier assignments clearly marked. First-meeting framework as a separate section with full script.

EXPECTED OUTPUT:
As described.
```

---

## 16. Hidden Referral Connector Mapping

**Category:** Warm / Sphere Intelligence
**Best for:** Agents with 200+ sphere contacts who want to find the 20% driving 80% of referrals.
**Run frequency:** Annually
**Why it works:** Most agents have no idea which people in their sphere are network "connectors" in the Malcolm Gladwell sense. AI can analyze occupation, community role, and social signals to identify the 25 people in your sphere whose introductions would move your business most.

```
ROLE:
You are a social network analyst specializing in real estate referral networks. You identify which people in an agent's sphere are statistical "connectors" — the 20% who are naturally positioned to drive 80% of referrals.

CONTEXT:
Attached is my sphere CSV. Columns: name, occupation, employer, neighborhood, kids' ages (if known), spouse name, hobbies/interests, last_contact_date, past_referrals_sent, notes. I want to identify the top 25 people in my sphere whose job, social role, or life stage puts them in contact with the most potential home buyers or sellers per month — even if they haven't referred me yet.

INPUT:
[Paste sphere CSV]

TASK:
For each contact:

1. Calculate a CONNECTOR POTENTIAL SCORE (1–10) based on:
- Occupation: does their job put them in repeated contact with people going through housing transitions? (Pediatric dentist = 10. Remote software engineer = 3.)
- Social role: are they involved in visible community roles — school board, church lay leader, youth sports coach, HOA board, small-business owner, charity board?
- Life stage: are they in a life phase where they're surrounded by others in similar phases (new parents, recently-relocated, pre-retirement)?
- Track record: have they referred to me before?
- Relationship depth: how well do I know them (based on notes and last-contact recency)?

2. Identify specific CONNECTOR ARCHETYPES represented in my sphere. Archetypes to look for:
- Pediatric dentists and family physicians (40+ annual families in transition)
- HR professionals at mid-to-large employers (handle new-hire relocations)
- Divorce and estate attorneys (transaction-adjacent)
- Financial advisors with <$1M AUM clients (first-home-buyer clientele)
- Daycare directors and preschool owners
- CrossFit owners and independent fitness studio owners
- Youth sports coaches (especially travel-league)
- Relocation coordinators and Chamber of Commerce staff
- Church / synagogue / mosque community leaders
- Small-business owners (100+ customers themselves)

3. Rank the top 25 by connector potential.

4. For each of the top 25, generate a SPECIFIC REFERRAL-PARTNERSHIP PITCH — the value I can offer THEM (a relocation resource for HR? A client pipeline for the financial advisor? Content for their newsletter?) in exchange for a formal referral relationship.

CONSTRAINTS:
- Do not invent occupations or details not in the notes.
- Score 10 is reserved for people whose job provides repeat exposure to housing transitions AND who have referred before.
- If the sphere notes are too thin to score someone, mark them UNSCORED rather than guessing.

RULES FOR OUTPUT:
Three sections:
1. TOP 25 CONNECTORS — table with name, occupation, connector archetype, score, pitch
2. ARCHETYPE COUNT — how many of each type appear in my sphere (reveals my own network shape)
3. WEAK SPOTS — archetypes underrepresented in my sphere that I should deliberately add this year

EXPECTED OUTPUT:
As described.
```

---

## 17. Life-Event Screenshot Scanning

**Category:** Warm / Sphere Intelligence
**Best for:** Agents who want to monitor their own sphere's social feeds for move signals without becoming social-media-obsessed.
**Run frequency:** Monthly — during one focused 30-minute session
**Why it works:** You can't legally scrape LinkedIn/FB/IG. But you CAN screenshot your own feed of people you already follow and paste those screenshots into Claude's vision mode. This lets you surface move signals from 100+ friends in 10 minutes instead of scrolling mindlessly for an hour.

```
ROLE:
You are a social-signal analyst specializing in detecting real-estate-relevant life events from public social media posts.

CONTEXT:
I'm pasting screenshots of my own Facebook, Instagram, and LinkedIn feeds. These are posts from people I already follow or am connected to — people in my sphere. I want you to extract, from their public posts, any life event that correlates with a housing transition.

INPUT:
[Attach screenshots of your social feeds. Include 10–30 screenshots covering recent posts from sphere contacts.]

TASK:
For each post visible in the screenshots:

1. EXTRACT:
- Person's name (as shown in the post)
- Post date (approximate if not visible)
- Post content summary (one sentence)
- Platform (FB / IG / LinkedIn)

2. CLASSIFY the life event signal, if any:
- MOVE SIGNAL — job change, new city, engagement/wedding, baby, divorce, graduation, retirement, aging parent moving in, kids moving out, major promotion
- ADJACENT SIGNAL — home renovation, tenant complaint, commute complaint, space complaint, "dream home" post, new pet, new hobby requiring space
- SOCIAL CAPITAL — their friend's post about a life event (could be a referral opportunity)
- NO SIGNAL — everyday life content

3. PRIORITIZE:
- High priority: direct move signals in the last 30 days
- Medium priority: adjacent signals or move signals older than 60 days
- Low priority: background signals to note but not act on

4. For each HIGH PRIORITY signal, draft a specific outreach message that references the post naturally, without being creepy (never say "I saw your post," just reference the content as if a friend would): "Hey — just heard about [event]! How are things settling in?"

CONSTRAINTS:
- Only analyze what's visible in the screenshots. Do not speculate beyond the post content.
- Respect privacy — if a post is about a sensitive event (illness, death, divorce), flag it for a PERSONAL HUMAN TOUCH only, not a sales message.
- Do not draft outreach for anyone whose post shows obvious grief or distress. Those need a condolence, not a business outreach.

RULES FOR OUTPUT:
Three sections:
1. HIGH PRIORITY (immediate outreach) — table with name, event, suggested message
2. MEDIUM PRIORITY (30-day follow-up) — table with name, event, timing note
3. DO NOT CONTACT FOR BUSINESS — table of names whose posts deserve a human response only (condolence, congratulations on non-business event, etc.)

EXPECTED OUTPUT:
As described.
```

---

## 18. Equity Position Personalized Video Scripts

**Category:** Warm / Sphere Intelligence
**Best for:** Agents with a sphere of past clients who bought in 2017–2020 and are now sitting on significant equity.
**Run frequency:** Quarterly per cohort
**Why it works:** Generic "your home is worth X" postcards get ignored. A 45-second personalized video script per household — referencing their specific purchase year, current equity, and a life-stage-matched scenario — gets replies. AI lets you do 50 of these in a morning.

```
ROLE:
You are a real estate video script writer specializing in personalized equity-position messaging. You write short, conversational video scripts that a listing agent can record directly to a past client, referencing their specific financial situation and life stage.

CONTEXT:
Attached is a CSV of my past clients. Columns: name, purchase_date, purchase_price, loan_type (30yr fixed / ARM / VA / FHA / other), current_estimated_value, spouse_name, kids_ages_if_known, neighborhood, notes_on_current_life_stage. I want to send each of them a personalized 45-second video this quarter. The video will show them their specific equity gain and suggest one life-stage-matched scenario (upsizing, investing, second home, cash-out for renovation).

INPUT:
[Paste CSV]

TASK:
For each client:

1. CALCULATE:
- Equity gain (current_estimated_value minus purchase_price)
- Approximate equity percentage (equity gain / purchase price)
- Approximate principal paydown (assume 30yr fixed at the average rate for the purchase year; if loan_type is other, note limitation)
- Total estimated equity position (appreciation + principal paydown)

2. MATCH A SCENARIO to their life stage from the notes:
- Young family with kids now 6+ → "equity could be the down payment on the next-step home"
- Empty nester → "equity could fund a downsizer + a second home"
- DINK professional → "equity could fund an investment property"
- Recently promoted → "equity + new income could unlock the next bracket"
- Renovation-minded → "cash-out refi could fund the kitchen you've been talking about"

3. WRITE a 45-second conversational video script that:
- Opens with their first name
- States their specific equity number ("Jessica, your home's been doing some quiet work — looks like you've built up around $195K in equity since you bought in 2019")
- References one specific detail from their notes (their spouse's name, their kids' names/ages, a hobby, a life event)
- Proposes one scenario matched to their life stage
- Ends with a soft question, not a CTA ("No rush on this — but worth a 15-minute conversation sometime?")

CONSTRAINTS:
- Exactly 45 seconds of speaking time per script (approximately 130 words).
- Tone: trusted advisor, not salesperson. Warm, not hyped.
- Do not use "crazy market," "interest rates are," or any market-condition opener.
- Do not repeat the word "equity" more than twice per script.
- If notes are too thin to personalize, mark the client "USE GENERIC VARIANT" and generate a lighter script that references purchase year and neighborhood only.

RULES FOR OUTPUT:
For each client, output:
- Name
- Equity calculation summary (1 line)
- Matched scenario (1 phrase)
- The full 45-second script in quoted script format, ready to record

EXPECTED OUTPUT:
A clean list, one client per section, ready to record with a HeyGen or Loom tool the same morning.
```

---

## 19. Anniversary Stack

**Category:** Warm / Sphere Intelligence
**Best for:** Agents with past clients whose home-purchase anniversary is coming up.
**Run frequency:** Monthly (for clients with anniversaries in the next 30 days)
**Why it works:** A generic "happy anniversary of your home purchase" card is table stakes. A message that includes the 30-year mortgage rate that week, a news headline from that month, their approximate appreciation, and what that equity could buy today is personal, specific, and impossible to ignore.

```
ROLE:
You are a real estate anniversary content writer. You write warm, specific, nostalgic home-purchase-anniversary messages that include historical data, making the message impossible to ignore and unlikely to be deleted.

CONTEXT:
Attached is a list of past clients whose home-purchase anniversaries are in the next 30 days. Columns: name, purchase_date, purchase_price, current_estimated_value, purchase_neighborhood, kid_names_and_ages_at_purchase (if known), notes. I want a unique anniversary message for each that blends nostalgia, specific historical data, and a quiet equity update.

INPUT:
[Paste CSV]

TASK:
For each client, research:
1. The 30-year fixed mortgage rate the week they purchased
2. One major news headline from the month they purchased (national or local, something evocative — don't pick anything dark)
3. One cultural moment from that month (movie opening, album release, sports event) that would evoke nostalgia
4. Their approximate home appreciation (current estimated value minus purchase price)
5. What that equity-gain dollar amount could buy them today (e.g., "enough for a year in a European city" or "a downpayment on the mountain cabin we always joked about" — tuned to their notes)

Then WRITE a 100–150 word anniversary message that weaves these elements naturally. The message should be:
- Warm, not salesy
- Specific, not generic
- Nostalgic, not business-like
- End with a soft "if you ever want to talk through what this equity could do, happy to sit down" — but ONLY as an optional P.S., not a CTA in the main message.

CONSTRAINTS:
- Do not fabricate historical data. If you can't verify a rate or headline, use a different angle (e.g., a headline from later that year, or skip that element).
- Do not reference dark or traumatic news headlines, even if they were in that month.
- Do not mention specific political events that could feel partisan.
- Keep the tone personal. This should feel like a handwritten note, not a newsletter.

RULES FOR OUTPUT:
For each client:
- Name
- Purchase date / rate that week / one headline / one cultural moment (cited for verification)
- Equity-gain number and "could-buy-today" scenario
- The full 100–150 word message, ready to send as a text, email, or handwritten card

EXPECTED OUTPUT:
One client per block, cleanly separated.
```

---

## 20. Relationship-Tuned Referral Ask

**Category:** Warm / Sphere Intelligence
**Best for:** Agents who want to ask for referrals without using the generic "who do you know" script that everyone ignores.
**Run frequency:** Annually (or whenever you rebuild your sphere outreach plan)
**Why it works:** A college roommate and a past client deserve completely different referral asks. The generic "who do you know who's looking" script is dead because it treats every relationship the same. AI tunes the ask to each specific relationship type.

```
ROLE:
You are a referral-ask scriptwriter specializing in relationship-appropriate messaging. You write referral asks that feel like they came from the specific relationship you have with each person — not a script.

CONTEXT:
Attached is a list of sphere contacts I want to ask for referrals over the next 60 days. Columns: name, relationship_type, how_we_met, last_interaction_summary, shared_context (kids in same school / hobby / past work), past_referrals_sent, notes. I want a completely different referral ask for each person, tuned to our actual relationship — not a template.

INPUT:
[Paste contact list]

TASK:
For each contact:

1. CLASSIFY the relationship type:
- Close friend / family
- Old friend (rare contact, warm history)
- Past client (warm but transactional)
- Professional peer (may refer peer-to-peer)
- Community connection (school parent, neighbor)
- Referral partner (reciprocal)
- Distant acquaintance

2. WRITE a referral ask that:
- Opens with something specific about our relationship ("I was just thinking about the time we [specific shared moment]")
- Does NOT use "who do you know" — ever
- Acknowledges the ask as an ask, without grovelling
- Frames my value proposition in a way that resonates with THIS person specifically (a tech peer cares about different qualities than a school mom)
- Ends with a specific, easy action ("If anyone comes to mind this week, just forward them this note" rather than "please let me know")

CONSTRAINTS:
- No "who do you know."
- No "I'd appreciate any referrals."
- No "my business grows through referrals."
- No weather openings, no "hope you're well."
- Match the tone of our relationship. A college roommate gets casual. A professional peer gets focused. A past client gets warm-transactional.

RULES FOR OUTPUT:
For each contact: name, relationship_type (confirmed or re-classified), and the full referral-ask message (3–6 sentences, ready to send as text, email, or DM).

Group the output by relationship type so I can batch-send by message style.

EXPECTED OUTPUT:
Grouped by relationship type, with each contact's customized ask underneath.
```

---

## 21. Reverse ICP from Last 20 Closings

**Category:** Warm / Sphere Intelligence
**Best for:** Agents who have closed 20+ deals but don't have a crisp Ideal Client Profile.
**Run frequency:** Once a year, after you close the current year
**Why it works:** Most agents can describe "a good client" in general terms but can't describe the next 50 perfect-fit leads in specific terms. Feeding your best 20 past clients into Claude reveals pattern you can't see yourself.

```
ROLE:
You are a real estate client-archetype analyst. You analyze an agent's best past clients and reverse-engineer a detailed Ideal Client Profile (ICP), plus a targeting map for finding the next 50 like them.

CONTEXT:
Attached is a list of my 20 best past clients — the ones I'd most like to clone. Columns: name, transaction_type (buy/sell/both), closing_date, price_point, neighborhood, property_type, referral_source, occupation, family_situation_at_closing, communication_style (from memory), why_they_were_a_great_client_in_one_sentence, total_referrals_they_sent_back.

INPUT:
[Paste the list]

TASK:

1. ANALYZE PATTERNS across the 20 clients:
- Price point distribution
- Neighborhood concentration
- Occupation clusters
- Family stage (first-time, move-up, downsize, investor)
- Referral source origin (where did they come from?)
- Communication style preferences (high-touch vs. low-touch?)
- What made them great? (common themes across the "why they were great" column)

2. SYNTHESIZE THE ICP
Write a 200-word Ideal Client Profile paragraph that captures the essence of my best clients. Specific. Concrete. Not "someone who values good service."

3. BUILD THE TARGETING MAP
For the next 50 clients who fit this ICP, where are they found?
- Specific neighborhoods (5–10 to farm)
- Specific referral channels (5–10 to cultivate)
- Specific content topics they'd care about
- Specific life events that trigger their transactions
- Specific businesses they frequent (for the Local Business Mapping query, #15)

4. FLAG EXCEPTIONS
Which of the 20 clients don't fit the pattern? What can I learn from the outliers (either to double down on or deliberately avoid)?

5. IDENTIFY MY WEAK ZONES
Based on the analysis, what client type am I UNDERSERVED by? Where should I deliberately expand?

CONSTRAINTS:
- Use only the data I provided.
- Be specific — "busy professional" is not an ICP. "Dual-income couples with kids 5–12 in the Lakeview North Side of Chicago, household income $200–400K, first-or-second-home-buyer, referred by a prior client or their pediatric dentist" IS an ICP.
- Do not recommend pivoting to client types that aren't already working for me.

RULES FOR OUTPUT:
Five sections as described. ICP should be quotable. Targeting map should be immediately actionable (I should be able to schedule next week's outreach from it).

EXPECTED OUTPUT:
As described.
```

---

## BONUS — 22. The 90-Second Pre-Call Brief

**Category:** Warm / The Habit
**Best for:** Every agent who makes sphere calls regularly. Turns a random call into a prepared conversation.
**Run frequency:** Before every sphere call you make
**Why it works:** Ricky Carruth built a career on consistent short calls to past clients. AI makes each of those calls 10x sharper with 90 seconds of prep. This is the daily habit that compounds.

```
ROLE:
You are a real estate pre-call briefing writer. You produce 90-second briefings that an agent reads right before picking up the phone to call a sphere contact.

CONTEXT:
I'm about to call [CONTACT NAME]. Below is everything I know about them: CRM notes, last 5 interactions, any social posts I've captured, any referral history. I need a 90-second brief that gets me ready for a warm, informed, non-awkward call.

INPUT:
[Paste everything you know about the contact]

TASK:
Produce a brief with four tight sections:

1. HUMAN CONTEXT (3 sentences)
- Who they are beyond the transaction — their family, job, what matters to them right now

2. LAST INTERACTION SUMMARY (2 sentences)
- What we talked about last
- Anything I promised to follow up on (and haven't yet — flag it)

3. LIKELY CURRENT HEADSPACE (2 sentences)
- Based on life stage, time of year, and any public signals, what's probably top of mind for them today
- What NOT to open with (anything that would feel off given their current phase)

4. THREE OPENERS (one phrase each)
- A genuine, non-real-estate opener referencing something specific
- A natural segue to check in on how life is
- An optional real estate segue ONLY if it's appropriate (if not, leave blank and say "skip real estate this call")

CONSTRAINTS:
- Maximum 180 words total across all four sections.
- Do NOT include a "CTA" or a sales pitch — this is a relationship call, not a pitch call.
- Match the tone of the notes — if I'm informal with this person, keep the brief informal.

RULES FOR OUTPUT:
Four clearly labeled sections. No preamble. No closing summary. Just the brief.

EXPECTED OUTPUT:
A 90-second read, nothing more.
```

---

## APPENDIX: THE QUERY FRAMEWORK

Every query in this file follows the same six-part structure. Memorize this and you can build your own queries for any prospecting scenario:

1. **ROLE** — Who is Claude pretending to be?
2. **CONTEXT** — What's the situation? What do I know?
3. **TASK** — What do I want done, specifically?
4. **CONSTRAINTS** — What should Claude NOT do?
5. **RULES** — How should the output be structured?
6. **EXPECTED OUTPUT** — What does the final result look like?

**The rule:** Short question = short answer. Detailed question = detailed answer.
**The shortcut:** Start with the output. What does the perfect result look like? Work backward to the role.

All queries live at **tapthis.co/prospecting**.
