# Compliance Review — Find Your Next Client With AI

**Reviewed:** Gameplan, Speaker Notes, 5 Hero Queries, 21-Query Swipe File, Drip Emails
**Regulatory surfaces:** Fair Housing Act, TCPA, state DNC, CAN-SPAM, NAR Code of Ethics, state license law
**Reviewer disclaimer:** This is a structured flag-check, not legal advice. Have a real estate attorney or your broker's compliance officer sign off before stage.

---

## TL;DR

**Green light:** The talk's core architecture (research + outreach targeting behavior signals, not protected classes) is compliance-defensible. The 5 hero queries are clean.

**Yellow flags requiring stage-level language adjustments:** 3 items (listed below) — small tweaks, no structural changes.

**Already removed (not on stage):** Obituary/pre-probate cross-reference, divorce docket mining, pre-foreclosure outreach. These were cut early for NAR-influencer reasons. Do NOT bring them back without a formal compliance sign-off.

---

## FAIR HOUSING ACT (FHA)

### What it prohibits
Discrimination in housing-related services based on 7 protected classes (federal): race, color, religion, sex, national origin, familial status, disability. Many states and localities add more (source of income, sexual orientation, gender identity, age, marital status, veteran status, etc.).

### What it applies to
YOUR MARKETING, ADVERTISING, and SERVICE DECISIONS — including:
- Who you target with advertising
- Who you agree to represent (buyer/seller)
- How you treat clients during a transaction
- What neighborhoods you steer clients toward (or away from)
- Language in MLS descriptions (can't describe neighborhoods by demographic makeup)

### What it does NOT prohibit
- Researching a prospective client using publicly available information
- Using behavior-based signals (years in home, equity position, life events, referral history) to prioritize outreach
- Niche marketing based on profession, life stage, or interest (first-time buyers, military, medical — these are NOT protected classes)

### Query-by-query audit

| # | Query | FHA Risk | Notes |
|---|-------|----------|-------|
| 1 | Pre-Listing Dossier | ✅ Clean | Research on a named prospect already expressing intent |
| 2 | Database Triage | ✅ Clean | Scoring weights are behavioral (tenure, equity, notes) — NOT protected classes |
| 3 | Ghost Notes | ✅ Clean | Re-engaging existing CRM — no discrimination vector |
| 4 | LLC Unmasking | ✅ Clean | B2B — FHA does not apply to business-to-business real estate |
| 5 | Become the Agent AI Recommends | ✅ Clean | Self-marketing positioning |

### Swipe file audit — FHA flags

**🟡 Query 3 (Empty Nester Reverse Lookup):**
Targets "owners 55+" which is AGE-ADJACENT. Age is not a federal protected class for housing, BUT it's protected in some states. And the Housing for Older Persons Act only covers dedicated senior communities, not general marketing.
- **Stage language:** Introduce it as "tenure + life-stage signal (18+ year owners with graduating kids)" rather than "owners 55+." Keep the query mechanics identical but frame the targeting as life-event-based, not age-based. 
- **Recommended edit:** In the query's CONSTRAINTS section, add: "Do NOT include or exclude candidates based on owner age as a primary filter — use tenure and the presence of publicly documented life events (graduations, kids leaving home) as the signal."

**🟡 Query 10 (Medical Residency Match Day):**
Occupation-based targeting of medical residents. Occupation is not a protected class, but some state Fair Housing laws cover "source of income" — residents have fixed salaries that might trigger scrutiny in narrow interpretations.
- **Stage language:** Frame as a "relocation cycle" play, not a "medical demographic" play. The distinction matters.
- **Query edit:** Already clean as written. No changes required.

**🟡 Query 11 (PCS Season Military Farming):**
Military is a protected class in some states (veteran status). VA loan use is a factor but NOT a discrimination vector — you're HELPING veterans access housing, which is the opposite of discrimination.
- **Query edit:** Already acknowledges OPSEC concerns. Add: "If asked, acknowledge that any agent can serve any client regardless of military status. Your specialization is relocation logistics, not exclusion."

---

## TCPA (Telephone Consumer Protection Act)

### What it prohibits
Unsolicited calls/texts to personal phones without prior express written consent for marketing purposes. **$500-$1,500 per violation.** This is the real risk.

### What triggers TCPA
- Sending a marketing text to anyone without their prior express written consent
- Calling a cell phone using an autodialer or pre-recorded voice without consent
- Texting past 9pm or before 8am (in recipient's local time)
- Continuing to text after an opt-out request

### What does NOT trigger TCPA
- Manual, human-dialed, one-to-one calls (though state DNC laws may still apply)
- Response to a direct inbound inquiry (transactional, not marketing)
- Contact with existing clients/past clients with an established business relationship (EBR exemption — but this is narrower than most agents think)

### Query-by-query audit — TCPA risk

| # | Query | TCPA Risk | Notes |
|---|-------|-----------|-------|
| 1 | Pre-Listing Dossier | ✅ Clean | Research only, no outreach method implied |
| 2 | Database Triage | 🟡 Yellow | Output includes "suggested opening line" — if the agent sends those as texts to leads who haven't opted in, that's a TCPA violation |
| 3 | Ghost Notes | 🟡 Yellow | 4-touch sequence includes TEXT as Touch 1 — past clients generally fit EBR, but cold/dead leads without prior opt-in are risky |
| 4 | LLC Unmasking | ✅ Clean | B2B outreach, TCPA carve-out for most business numbers |
| 5 | Become the Agent AI Recommends | ✅ Clean | No direct outreach mechanic |

### Stage language recommendation — TCPA

**On stage, during the Ghost Notes demo, add ONE sentence:**
> "One compliance note — if these are cold leads you haven't texted before and who didn't explicitly opt in to your texts, send the email first (Touch 2), not the text. The text is for people with a prior relationship."

This is a ~5-second addition that covers you and teaches the audience a real rule.

**On the companion page**, add a compliance footer to Hero #3:
> *"Before using the text template with any lead: verify you have prior express written consent for marketing texts, or use the email version as Touch 1 instead. TCPA violations are $500–$1,500 per text."*

---

## STATE DO-NOT-CALL (DNC) LISTS

The National DNC Registry + state DNC lists. Same principle as TCPA but applies to voice calls.

### Query-by-query audit

| # | Query | DNC Risk | Notes |
|---|-------|----------|-------|
| 2 | Database Triage | 🟡 Yellow | "Who to call Monday" — if any of those contacts are on DNC and you don't have an EBR, that's a violation |
| 3 | Ghost Notes | 🟡 Yellow | Touch 3 is a voice memo (which goes via text/messenger, not DNC-covered) — but if an agent converts it to a direct call, DNC applies |

### Stage language recommendation — DNC

Already baked into Query #2's CONSTRAINTS: "Penalize anyone flagged 'do not contact' or 'DNC' in any column." Good. But add a footnote to the speaker notes for Slide 12:

> *"One quick callout — if your CRM doesn't already tag DNC status, check the National DNC Registry on your top 10 before calling. It's free at donotcall.gov."*

---

## CAN-SPAM (Commercial Email)

### What it requires
- Don't use false/misleading From or Subject lines
- Identify the email as an ad (unless relationship-based)
- Include a physical postal address
- Honor opt-outs within 10 business days
- Include a functioning unsubscribe mechanism

### Query audit — CAN-SPAM
All queries involving email output should produce material that is CAN-SPAM compatible. The queries themselves are compliant in structure; the agent is responsible for ensuring the actual sends include unsubscribe + address.

**Recommended edit to Hero #3 (Ghost Notes):** In the email template constraints, add: "Ensure the email includes my firm's physical address and an unsubscribe link — CAN-SPAM requires both for any marketing email."

---

## NAR CODE OF ETHICS

### Most relevant articles
- **Article 1:** Protect the best interests of the client
- **Article 3:** Cooperate with other agents honestly
- **Article 12:** Present a true picture in advertising and other public communications
- **Article 15:** Do not knowingly make false or misleading statements about competitors

### Query-by-query audit

| # | Query | NAR Risk | Notes |
|---|-------|----------|-------|
| 4 | LLC Unmasking | 🟡 Yellow | The "suggested opener" must NOT misrepresent how you found them — "Saw you picked up [address]" is honest; "A mutual friend mentioned you" would not be |
| 13 | Competitor Agent Weakness Audit | 🟡 Yellow | Output includes positioning statements "exploiting competitor gaps." The QUERY already prohibits naming competitors in the positioning — good. But agents could abuse this. |

### Stage language — NAR

During Hero #4 demo, the sentence *"I would never put a stranger's name on this screen without their written consent"* is gold — it's also NAR-Article-12-defensible framing. Keep it exactly as written in the speaker notes.

For the swipe file Query #13 (Competitor Weakness Audit), add a CONSTRAINTS line: "Do NOT publicly name the competitor in any content you create from this output. Article 15 prohibits knowingly false or misleading statements about competitors. Positioning statements are for your own marketing; they must stand on their own merit, not denigrate."

---

## STATE REAL ESTATE LICENSE LAW

### What it applies to
Varies by state. Common restrictions relevant to this talk:
- **Dual agency / undisclosed representation:** Stage is fine (no active representation)
- **Net listings / secret commission arrangements:** Not relevant
- **Advertising disclosure:** Most states require agent license number + brokerage name on marketing. The companion page (tapthis.co/prospecting) includes D.J.'s bio + Kale Realty — confirm that's in the page footer too.

### Recommended edit — companion page

Add a small footer on `tapthis.co/prospecting`:
> *D.J. Paris is a licensed real estate broker in the State of Illinois at Kale Realty, Chicago. License info on request.*

This is belt-and-suspenders for any state that requires it. The speaker notes already mention Kale Realty.

---

## AI-SPECIFIC COMPLIANCE CONCERNS

### Hallucination liability
If an agent repeats an AI-generated "fact" to a client and it's wrong, the agent is liable — not the AI tool.

**Already addressed:** Every hero query has VERIFIED/INFERRED tagging. Emphasized in the speaker notes at Slides 8, 9, 20.

**Stage reinforcement:** During Hero #1 demo, the line *"Verified-versus-inferred tagging is the reason this is safe to actually use"* is the single most important compliance sentence in the talk. Say it slowly. Repeat it.

### Data handling
Agents uploading CRM exports to Claude, ChatGPT, etc. should understand:
- Claude does NOT train on API or paid consumer tier conversations (Anthropic policy as of this writing)
- ChatGPT has similar opt-out for paid tiers
- Free tiers often DO use data for training
- Client PII uploaded to any external AI should be considered "disclosed" for practical purposes

**Recommendation:** Add one slide OR one talking point between Slide 12 (CSV Triage demo) and Slide 13 (takeaway):

> **SAY:** "One thing worth saying out loud — when you upload a CSV with real client data to any AI tool, treat that data as if you've disclosed it. Claude and ChatGPT paid tiers don't train on your conversations, but it's still good hygiene to anonymize names or use a separate scratch account for client work. Your brokerage may also have a specific policy. Know it."

One sentence. Costs 10 seconds. Saves lawsuits.

### Disclosure to clients
If AI-generated content is used in client communications (listing descriptions, market updates, buyer letters), some states are considering disclosure requirements. None are federal law yet, but the direction is clear.

**Recommendation:** No change to the talk needed right now, but add to the post-talk drip Email 5 (the "three things I wish someone had told me" email): include a line about checking your brokerage's AI-disclosure policy.

---

## RECOMMENDED STAGE EDITS — SUMMARY

1. **Hero #3 narration, after the Touch 1 text reveal:**
   > "One compliance note — if these are cold leads without prior consent, send the email first (Touch 2), not the text. TCPA applies."

2. **Hero #2 narration, before the 'call these 10 Monday' closing line:**
   > "Quick callout — if your CRM doesn't tag DNC status, check donotcall.gov on your top 10 before calling. Free. Thirty seconds."

3. **Between Slide 12 and 13 (or baked into Slide 13 narration):**
   > "One thing worth saying out loud — treat any CSV you upload as disclosed data. Paid Claude and ChatGPT tiers don't train on your conversations, but your brokerage may have a policy. Know it."

4. **Hero #1 narration (already exists, just emphasize):**
   > "Verified-versus-inferred tagging is the reason this is safe to actually use." (Say slowly.)

---

## RECOMMENDED QUERY EDITS — SUMMARY

1. **Swipe Query #3 (Empty Nester):** Add CONSTRAINTS line: "Do NOT use owner age as a primary filter — use tenure and publicly documented life events instead."

2. **Hero #3 (Ghost Notes) email template:** Add CONSTRAINT: "Email output must be CAN-SPAM compliant — include firm physical address and unsubscribe link."

3. **Swipe Query #13 (Competitor Audit):** Add CONSTRAINT: "Do NOT publicly name the competitor in any content derived from this output. NAR Article 15 prohibits false/misleading statements about competitors."

---

## RECOMMENDED COMPANION PAGE EDITS

1. Add license/brokerage footer: "D.J. Paris is a licensed real estate broker at Kale Realty, Chicago IL. License info on request."
2. Add compliance note to Hero #3 expanded view:
   > *"Before using the text template with a lead: verify you have prior express written consent for marketing texts, or use the email version as Touch 1. TCPA violations are $500–$1,500 per text."*

---

## WHAT WAS ALREADY REMOVED (GOOD CALL — KEEP REMOVED)

| Technique | Why removed |
|-----------|-------------|
| Obituary → pre-probate cross-reference | Targets grieving families. Compliance risk (vulnerable-population consumer protection), reputational risk on NAR stage, practical risk of media backlash |
| Divorce docket mining | Similar vulnerability concerns + some states restrict use of divorce filings for commercial solicitation |
| Pre-foreclosure outreach | Heavily regulated — many states require specific disclosures and cooling-off periods. "Foreclosure rescue" statutes apply |

These three techniques exist and are legal in many jurisdictions, but require specialized compliance setup that's not appropriate for a general national audience. The decision to cut them was correct. Do not bring them back on any stage without a formal legal review.

---

## FINAL PRE-STAGE CHECKLIST

- [ ] Have a Kale Realty compliance officer read this document and the speaker notes
- [ ] Add the 4 stage narration edits above to your speaker notes
- [ ] Add the 3 query constraint edits above to the swipe file and companion page
- [ ] Add the 2 companion page edits above to `/prospecting` page
- [ ] Confirm your brokerage's AI data-handling policy and reference it on stage if applicable
- [ ] Memorize the TCPA line (point #1) — it will come up in Q&A regardless
- [ ] Memorize the CSV-is-disclosed line (point #3) — someone always asks

**Bottom line:** The talk is compliance-defensible as written. The edits above are belt-and-suspenders — they turn "defensible" into "bulletproof" without changing the substance of a single demo.
