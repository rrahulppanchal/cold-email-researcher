# Campaigns: Lists, Segments, Testing, Multi-Channel, Replies

Use when user runs outreach at volume (batch of prospects, campaign setup, sequences) or asks how to scale.

## Contents
1. List quality
2. Segmentation: volume without losing personalization
3. A/B testing and variation
4. Multi-channel sequence (6-8 touches)
5. Speed to lead: handling replies
6. Metrics and benchmarks

---

## 1. List quality - list beats copy

Bad list = great email wasted + domain burned. Never blast generic lists.

**Sources (best -> fine)**
1. **Manual build** - Google Maps "[niche] [town]", local directories, LinkedIn, Product Hunt, G2 categories. Slow, highest quality
2. **Scraping tools / software** - Google Maps scrapers (e.g. Apify), Apollo, Clay, LinkedIn Sales Navigator; then verify
3. **Bought data** - only verified, recent, compliant providers; still re-verify and spot-check; check local law first (bought lists are risky/unlawful for cold email under GDPR/PECR in EU/UK, CASL in Canada, Spam Act in Australia)

**Every row must have**
- Business name, niche, town, website (or "none"), Google rating + review count
- Contact name + role, public business email, source
- One research note / hook (even short) - no hook = not ready to email
- Fit score 1-5 (does it have a problem sender fixes?)

**Filters**
- Verify emails (NeverBounce, ZeroBounce, MillionVerifier) - bounce rate must stay under ~2%
- Remove role-based catch-alls if possible (info@ fine for small local; avoid noreply@, support@ for SaaS)
- Remove businesses that already have exactly what you sell, and ones that opted out before
- Prioritise: has a problem visible in audit > has budget signals (reviews volume, multiple locations, funding) > everyone else

When asked to build a list, this skill outputs a table with these columns and ranks by fit. It does not guess emails.

---

## 2. Segmentation - high volume, still personal

Volume comes from **many small campaigns**, not one big one. Segment by:

1. **Niche** (lawn care vs cafes - different pains, words, offers)
2. **Location** (town/city - allows local references and competitor names)
3. **Problem found** (no website / no booking / low reviews / slow site / aggregator-dependent)
4. **Size/stage** (solo owner vs multi-location; pre-seed vs Series A SaaS)

Each segment = its own campaign with its own:
- Subject lines and opener variants
- Offer + value asset
- Case study (from same niche if possible)

Inside a segment, every email still gets a **custom first line** (the hook) from research. Template body ok; first line never templated.

Example segment names: `lawn-frisco-no-quote-form`, `cafes-blr-instagram-only`, `saas-agencytools-no-comparison-pages`.

Volume guardrails: ~30-50 emails per mailbox per day, warm mailboxes, multiple mailboxes on a secondary domain for scale, SPF/DKIM/DMARC set.

---

## 3. A/B testing and variation

Test one variable at a time, ~100+ sends per variant before judging (smaller samples = noise; say so).

**Test order (biggest impact first)**
1. Offer / value asset (mockup vs audit vs loom)
2. Opener / hook type (review quote vs competitor gap vs missed-call)
3. CTA ("Want it?" vs "Worth a look?" vs "Open to a 10-min chat?")
4. Subject line family
5. Length

When generating a campaign, output **Variant A and Variant B** for opener and CTA, labelled, so the user can split-test.

**Spintax / variation**
Spintax (`{Hi|Hey|Hello} {first_name}`) keeps emails from being word-for-word identical across a campaign, which reads more human. Use it on greetings, transitions, sign-offs, and CTA phrasing - never on the personalized hook or facts. Every spun combination must read naturally; check 3 random outputs.

Spintax is not a deliverability fix. Inbox placement comes from: verified list, low daily volume, warmed authenticated domain, relevant content, real replies, easy opt-out. Don't use variation to disguise sending to people who would mark it spam.

Example:
```
{Hi|Hey} {{first_name}},

{{custom_hook}}

{Happy to|I can} {send over|share} the mockup I {made|put together} for {{business}} - {want it|want me to send it}?

{Cheers|Thanks},
{{sender_name}}
```

---

## 4. Multi-channel sequence (6-8 touches)

Most replies come after several touchpoints, not email 1. Mix channels; each touch adds something new.

Default cadence (adjust per niche):

| Day | Channel | Touch |
|---|---|---|
| 1 | Email | Email 1 - hook + value offer |
| 2 | LinkedIn / Instagram | View profile, follow, like a recent post (SaaS: LinkedIn; local: Instagram/Facebook) |
| 3 | Email | Follow-up 1 - backup finding (in thread) |
| 5 | LinkedIn DM / Instagram DM | Short, personal, no pitch dump: "Sent you an email about [x] - easier here?" |
| 7 | Email | Follow-up 2 - proof / case study / send asset preview |
| 9 | Phone call | Local: call at quiet time (cafe 3pm, contractors 7-8am or after 5pm). Script below |
| 12 | Email or DM | Follow-up 3 - new value (seasonal tip, competitor update) |
| 16 | Email | Breakup |

**Phone script (30 seconds)**
"Hi [Name], it's [you] - I'm the one who emailed about [Business]'s [specific: missed calls / Google listing]. Not selling anything on this call - I made a quick [mockup] and wanted to check you'd actually like to see it. Should I send it to this number or email?"

**SMS / WhatsApp**: only where lawful and appropriate - generally after they've engaged, given the number for this purpose, or local law permits B2B texting. In the US, marketing texts to mobiles need prior consent (TCPA); India has TRAI DND rules; WhatsApp Business has its own opt-in policy. Default: use SMS/WhatsApp only as a reply channel or after they say yes.

**Rules**
- Stop all channels the moment they reply (yes, no, or not now)
- "No" or opt-out on any channel = stop on every channel
- Don't spam: max one touch per day, never same message on two channels

---

## 5. Speed to lead - handling replies

Positive reply = respond **within minutes, ideally under 1 hour, same day at worst**. Momentum dies fast; they may also be talking to others.

When user pastes a reply, classify it and draft the response immediately:

| Reply type | Response |
|---|---|
| **Interested / "send it"** | Send the promised asset now + one-line insight + calendar link with 2 specific times ("Tue 4pm or Wed 11am?") |
| **"How much?"** | Give range or starting price honestly, tie to outcome, offer 10-min call to scope. Don't dodge |
| **"Not now / busy season"** | Thank, ask when better, note follow-up date, offer to send asset anyway |
| **"Already have someone"** | Respect it; offer the audit as a second opinion; leave door open |
| **"Who are you / how did you get my email?"** | Honest: public business email from [source], short who you are, offer to stop |
| **"Not interested" / unsubscribe** | One line: "Understood, won't contact you again. Best of luck with [business]." Mark do-not-contact across all channels |
| **Out of office** | Note return date, resume sequence after |
| **Referral ("talk to X")** | Thank, email X referencing the referrer by name |

Reply drafts: under 60 words, match their tone, one clear next step. Sending still follows the approval rule in SKILL.md.

Suggest user enables notifications for replies and keeps a "reply within the hour" habit; for scale, a simple automation (e.g. reply detected -> Slack/WhatsApp ping) helps.

---

## 6. Metrics and benchmarks (rough, vary by niche)

- Bounce < 2%, spam complaints < 0.1%
- Open rate unreliable (privacy features inflate/deflate); judge by **reply rate**
- Reply rate: ~1-3% generic; 5-15%+ for well-researched, segmented, value-first
- Positive reply -> booked call: aim 30-50%
- If replies < 2% after 200 sends: fix list first, then offer, then opener, then subject
