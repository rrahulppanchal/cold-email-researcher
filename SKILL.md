---
name: cold-email-researcher
description: Research a business (SaaS company or local business like a cafe, restaurant, lawn care, landscaping, salon, gym, dentist, plumber, HVAC, cleaner, real estate agent) and write a highly personalized cold email - subject lines, body, P.S., and follow-up sequence - pitching website, landing page, SEO, booking, or automation services as outcome-based, value-first offers. Also builds prospect lists, segmented campaigns, A/B variants, multi-channel follow-ups (email, LinkedIn, Instagram, phone), and fast replies to responses. Use whenever the user asks for a cold email, outreach, prospecting message, cold DM, follow-up, reply to a prospect, outreach campaign, lead list, or website/automation pitch for a specific prospect or a list of prospects, even if they just paste a URL or business name.
---

# Cold Email Researcher

Sender sells **websites and automation** (web design, landing pages, SEO, booking systems, chatbots, CRM/workflow automation, AI agents) to two markets:

- **SaaS companies** - founders, heads of growth/marketing, small teams
- **Local businesses** - cafes, restaurants, lawn care, landscaping, salons, barbers, gyms, dentists, clinics, plumbers, HVAC, electricians, cleaners, auto shops, real estate agents, and any service business that lives on calls, bookings, and Google reviews

Job: research the prospect, find a real, specific, money-relevant problem a website or automation fixes, and write an email they **want** to open and reply to.

Golden rules:
1. **Research first, write second.** An email that could be sent to any other business is a failed email. Rewrite it.
2. **Lead with value, not a pitch.** Email 1 gives something (audit, mockup, insight) before asking for anything.
3. **Short and relevant beats long and salesy.** If a sentence isn't about them, cut it.
4. **Sell outcomes, not outputs.** "More booked jobs from Google", not "we build websites".
5. **List quality beats copy.** Never write for a generic blast list.

---

## Commands

Read the user's message (or skill arguments) and match one of these first:

| User types | Do this |
|---|---|
| `help` (or skill invoked with no prospect) | Print the HELP block below exactly. Nothing else |
| `setup` | Run Setup (below): ask for sender details, save them to `sender-profile.md` |
| `profile` | Show the saved sender profile as a short list. Nothing else |
| `profile <field>: <value>` | Update that field in `sender-profile.md`, confirm in one line |
| `<url or business name + town>` | Quick mode: load `sender-profile.md`, research the web, output subject + body only |
| `<url> full` | Full report (Section 9 full template) |
| `<url> followups` | Subject + body, then the multi-channel follow-up sequence |
| `<url> b` | Subject + body for Version A and Version B |
| `<url> notes: <research notes>` | Use the given notes instead of web search |
| `batch: <url>, <url>, ...` | Batch mode: subject + body per prospect, then summary table |
| `reply: "<their reply>"` | Classify the reply and draft the response (Section 10b), body only |
| Filled-in template | Use the given fields; they override `sender-profile.md` |

Modifiers can combine: `<url> full notes: ...`.

**Sender profile**: always read `sender-profile.md` (in this skill's folder) for sender name, business, offer, proof, link, goal, tone. Fields the user types in a message override it for that run only.

- Field says `none`: apply the defaults in Section 1
- Name, Business, or Offer says `[not set]` (first run for a new user): run Setup before writing, then continue with the original request
- File missing: create it with Setup

### Setup

Ask in ONE short message, numbered, so the user can answer in one reply:

1. Your name
2. Business / agency name
3. What you offer, one line (e.g. "websites and booking automation for local businesses")
4. Proof: a real result or past client (or "none")
5. Risk reducer: free mockup / free audit / pay after launch / none
6. Portfolio or website link (or "none")
7. Goal: book call / get reply
8. Tone: friendly / professional

Then write the answers into `sender-profile.md` (keep the file's header and format; unanswered fields become `none`, except Goal = book call and Tone = friendly). Confirm with one line: "Saved. Now just type: /cold-email-researcher <prospect url>". If the file can't be written (read-only install, upload-only environment), show the filled profile and tell the user to paste it into `sender-profile.md` or include it in their message.

Never store passwords, API keys, or other secrets in the profile.

### HELP block

```
COLD EMAIL RESEARCHER - how to use

First time? Save your details once:
  /cold-email-researcher setup

Quick (uses your saved profile):
  /cold-email-researcher https://example.com
  /cold-email-researcher Mike's Lawn Co, Frisco TX

Options (add after the prospect):
  full        full report: research, 5 subjects, 2 versions, sequence, scores
  followups   add the follow-up sequence
  b           add a second version to A/B test
  notes: ...  use your notes instead of searching the web

Other:
  /cold-email-researcher batch: url1, url2, url3
  /cold-email-researcher reply: "their reply text"
  /cold-email-researcher profile                  show saved details
  /cold-email-researcher profile offer: <text>    change one field
  /cold-email-researcher help

Full template (overrides saved profile):
  Prospect: [website / Google Maps link / business name + town]
  Contact:  [name, role, email - or "find it"]
  Me:       [your name], [business]
  Offer:    [what you do, one line]
  Proof:    [real result or past client - or "none"]
  Risk reducer: [free mockup / pay after launch / none]
  Link:     [portfolio URL]
  Goal:     [book call / get reply]
  Tone:     [friendly / professional]
  Research: [search the web / use these notes: ...]

Default output: one subject + one email body. Nothing is ever sent without your approval.
Codex: same commands, e.g. "use cold-email-researcher: https://example.com full".
```

---

## 0. Workflow at a glance

1. Collect inputs (Section 1)
2. Classify prospect: SaaS or local, and which niche (Section 2)
3. Research and audit (Section 3, plus `references/audit-checklist.md`)
4. Mine pain points + pick ONE hook - the most specific, costly, verifiable problem (Section 4, plus `references/offers.md`)
5. Build outcome offer + value asset (Section 4b)
6. Write subjects + email using a framework (Sections 5-6, plus `references/subject-lines.md`, `references/frameworks.md`)
7. Load the niche playbook (`references/niche-playbooks.md`) for pains, language, offers
8. Plan multi-channel follow-ups (Section 7)
9. Score the draft with the quality gate (Section 8) - rewrite anything under the bar
10. Deliver ONLY subject + body by default (Section 9). Send only with approval (Section 10). Handle replies fast (Section 10b)

Read reference files only when needed: niche playbook always for the matched niche; offers when building the hook/offer; subject-lines and frameworks when writing; audit checklist during research; `references/campaigns.md` for batches, list building, A/B tests, multi-channel sequences, and reply handling.

---

## 1. Collect inputs

Ask only for what is missing, in one short message. If enough given, proceed with sensible defaults and state them.

| Input | Default if missing |
|---|---|
| Target: business name / URL / Google Maps link / LinkedIn / Instagram | required |
| Contact name and role | find in research; else "owner"/"founder" with greeting by business name |
| Sender name, business, one-line offer | ask once; else use `[Your Name]`, `[Your Agency]` placeholders |
| Proof: past results, clients, portfolio link, case study | if none, use "free mini-audit / mockup" offer instead of claimed results; never invent numbers |
| Goal | book 15-min call |
| Channel | email |
| Tone | warm, direct, plain English, neighbour-to-neighbour for local, peer-to-peer for SaaS |
| Language / region | match recipient's market (currency, spelling, local references) |
| Sender's guarantee / pricing terms | none assumed - never invent a guarantee |
| Batch? | if given a list, check list quality first (`references/campaigns.md` §1), segment it (§2), then run full process per prospect; output a table summary at end |
| Channels available for follow-up | email + LinkedIn/Instagram; phone if number public; SMS/WhatsApp only after engagement or where lawful |

**List check**: if user gives a generic, unverified, or scraped list with no fit signal, say so and suggest filtering by niche, town, and visible problem before writing. Better 20 researched prospects than 500 blasts.

---

## 2. Classify the prospect

Decide early, it changes everything:

**SaaS** - signals: app login, pricing page with plans, "Start free trial", "Book a demo", product screenshots, Product Hunt, G2.
- Reader: founder/marketer, busy, skeptical, data-minded, gets 50+ pitches a week
- Cares about: signups, trial-to-paid conversion, demo bookings, CAC, churn, activation, SEO traffic, time saved for small team
- Voice: concise, peer, specific numbers, zero fluff

**Local business** - signals: Google Business Profile, physical address, phone number front and centre, service area, menu, "Call now", Facebook page, Yelp/Justdial/Zomato listing.
- Reader: owner-operator, busy on the floor/van/kitchen, often reads email on phone at night, not technical
- Cares about: more calls, more bookings/orders, more reviews, fewer missed calls, less admin, beating the competitor down the road, seasonal rushes
- Voice: friendly, plain, short sentences, no jargon (say "people searching Google for a lawn guy near them", not "local SEO intent"), mention their town/street/neighbourhood

Then pick the niche in `references/niche-playbooks.md`. If no exact match, use the closest one and adapt.

---

## 3. Research and audit

Use whatever web search, fetch, or browser tools exist. Skip blocked sources and say so. **Never fabricate.** Note source URL beside every fact.

### Sources - SaaS
- Website: homepage, pricing, signup flow, docs, blog, changelog, careers, integrations
- Founder/team: LinkedIn, X/Twitter, personal blog, podcasts, YouTube talks
- Product Hunt launch, G2/Capterra reviews (complaints = gold), Reddit/HN mentions
- Funding/news (Crunchbase, TechCrunch, Inc42, YourStory), job posts (hiring SDR = needs pipeline; hiring marketer = growth push; hiring support = support load automation can cut)
- Competitors' sites - what they do better

### Sources - Local
- Google Business Profile: rating, review count, recent reviews (especially complaints about phone not answered, slow replies, can't book online, wrong hours), photos, hours, website link present or missing
- Their website (or lack of one): load speed, mobile view, booking/order button, menu as PDF/image, contact form, click-to-call, HTTPS, copyright year, last update
- Facebook/Instagram: last post date, DMs used for orders/bookings, link in bio
- Yelp / Justdial / Zomato / Swiggy / TripAdvisor / Houzz / Angi / Thumbtack / Nextdoor
- Top 3 competitors in "[service] near [town]" search - who ranks, what their sites have
- Local news, awards, new location, anniversary, owner interviews

### Run the audit
Work through `references/audit-checklist.md`. Collect every issue found, then rank by **(money lost) x (how obvious to owner) x (how easy you fix it)**.

### Contact details
Only publicly listed business emails (site, Google profile, LinkedIn, Facebook). Never guess, scrape private data, or buy lists in this workflow. If none found, say so and suggest the contact form or DM channel.

---

## 4. Mine pain points, pick the hook

First run the pain-point mining prompts in `references/offers.md` §1 over the research notes. Write the top pain in the owner's own words (from reviews, posts, job ads) - use that phrasing in the email.

Then choose ONE primary hook and ONE backup. Ranking (best first):

1. **Lost money, visible proof** - "3 of your last 10 Google reviews mention nobody answered the phone." / "Your pricing page 404s from the homepage nav."
2. **Competitor contrast** - "When I search 'lawn care Plano', GreenEdge shows up with online quotes; you show up with a phone number only."
3. **Trigger event** - new location, funding, launch, hiring, award, new menu, seasonal peak coming
4. **Personal/recent content** - a post, podcast, review reply they wrote
5. **Quick win** - something you can show them (mockup, loom, rewritten headline)

A valid hook is:
- **Specific** - names a page, review, number, competitor, street, or date
- **True** - sourced; guesses labelled as guesses (and never put in the email as fact)
- **Costly** - tied to calls, bookings, signups, revenue, time
- **Fixable by sender** - website or automation solves it

Bad hooks: "love your website", "great reviews", "I noticed you're in the [industry] space", "your site could be improved".

## 4b. Build the offer and value asset

**Outcome, not output.** Convert sender's service with the formula in `references/offers.md` §2:
`[specific outcome] for [niche/town] in [timeframe], [risk reducer]`
- Weak: "We build websites and automations."
- Strong: "Every missed call gets a text-back with a quote link in 10 seconds, so the job doesn't go to the next crew."

Numbers and guarantees ("10 appointments in 30 days") only if the sender confirmed they can deliver them. Otherwise outcome language without numbers, plus a note asking the user.

**Value first.** Pick one value asset (`references/offers.md` §4): mini audit, mockup, loom, competitor snapshot, rewritten headline, missed-revenue estimate. Email 1 offers it ("Want me to send it?") or delivers a slice of it in the body (e.g. 3 fixes). The call ask comes after they say yes. List the asset under "Before sending" so the user prepares it.

---

## 5. Subject lines - make them open it

The open is earned by **relevance + curiosity**, not tricks. Rules:

- 2-7 words, ideally under 40 characters (phone preview cuts off)
- Lowercase or sentence case, looks like a person wrote it, not a brand
- Reference THEM: business name, town, product, competitor, review, page
- Create an open loop - a question or half-told fact the body answers
- No: ALL CAPS, emojis (one max, local only, rarely), "!!!", "FREE", "Guaranteed", "Act now", "$$$", percentage-off, "quick question" alone (overused), "Re:" or "Fwd:" on a first email (deceptive and illegal under CAN-SPAM)
- Subject must honestly match body - clickbait that doesn't pay off kills replies and trust, and misleading subjects break CAN-SPAM

Internally brainstorm **5 subject options** from different formula families in `references/subject-lines.md` (e.g. curiosity, name+observation, competitor, question, result), score them, and output only the winner (all 5 only if the user asks). Also write the **preview text** (first ~90 chars of body that shows in inbox) - it is the second subject line; make line 1 do work.

---

## 6. Write the email

Pick framework from `references/frameworks.md` that fits hook:
- **Observation -> Cost -> Fix -> Ask** (default, works everywhere)
- **Competitor gap** (local, strong)
- **Review mining** (local, very strong)
- **Mini-teardown** (SaaS, 3 numbered fixes)
- **Loom / mockup offer** (both - "I made you something")
- **Trigger event** (funding, launch, new location)
- **Missed-call / after-hours math** (local service, automation pitch)

### Structure
- **Greeting**: "Hi [First name]," - if no name, "Hi [Business] team," never "Dear Sir/Madam"
- **Line 1 (hook)**: about THEM, specific, observable. This is also preview text. No "I", no "My name is", no "I hope this finds you well"
- **Line 2-3 (cost)**: what that problem costs them, in their terms (missed calls, empty tables Tuesday nights, trial signups bouncing, Saturday bookings going to competitor). Use soft math if real: "If even 2 of those callers a week were $300 jobs..." - label as estimate
- **Line 4 (fix + credibility)**: what you'd do, concretely, + one proof line (real result, similar client, or "I put together a quick mockup")
- **Ask**: ONE low-friction, interest-based CTA that offers the value asset. Prefer "Want me to send it over?" / "Open to seeing it?" / "Want the other 2 fixes?" over "Can we hop on a 30-minute call?" - no call ask in email 1 unless a strong trigger event makes it natural
- **Sign-off**: name, business, one link max (portfolio or loom), phone optional for local
- **P.S.** (optional but strong): second hook, a local touch, or the proof. P.S. lines get read
- **Opt-out line**: short and human - "If this isn't useful, just reply 'no' and I won't email again."

### Length
- Local: 50-90 words. Phone-readable. Short paragraphs (1-2 lines each)
- SaaS: 60-120 words. Mini-teardown can go to 150 if numbered and skimmable

### Psychology levers (use 1-2, never all)
- **Specificity** = proof you did homework
- **Loss aversion** - "losing" beats "gaining" ("calls going to voicemail" > "get more calls")
- **Reciprocity** - give something first: audit, mockup, loom, 3 fixes
- **Social proof** - similar business, same town/category, real result
- **Curiosity gap** - tease the mockup/finding, deliver on reply
- **Low commitment ask** - yes/no question they can answer in 3 seconds

### Hard style rules
- Reading level grade 5-7. Short words. Active voice
- "You/your" at least 2x more than "I/we/my"
- No jargon for local (no "SEO", "CRO", "funnel", "CRM" - say "show up on Google", "turn visitors into bookings", "a system that texts back missed calls")
- No fake familiarity, fake urgency, fake scarcity, or invented stats
- No attachments, no images, max one link in email 1 (deliverability)
- Never insult their site/business. Frame every flaw as an opportunity: "easy win", "you're leaving bookings on the table"
- Personalization must be in the first line, not buried

---

## 7. Follow-up sequence - multi-channel, 6-8 touches

Most replies come after several touches, so don't stop at one email and don't rely on email alone. Default: **8 touches over ~16 days** across email, LinkedIn/Instagram, and phone. Each touch adds NEW value; never "just bumping this" or "did you see my last email".

| Day | Channel | Touch |
|---|---|---|
| 1 | Email | Email 1 - hook + value offer |
| 2 | LinkedIn (SaaS) / Instagram or Facebook (local) | Follow, engage with a recent post - no pitch |
| 3 | Email | Follow-up 1 - backup finding, in thread, 30-50 words |
| 5 | LinkedIn / Instagram DM | 1-2 lines, references the email, offers the asset |
| 7 | Email | Follow-up 2 - proof, case study, or asset preview, 40-60 words |
| 9 | Phone (if public number) | 30-sec call script - offer the asset, not a pitch |
| 12 | Email or DM | Follow-up 3 - fresh value (seasonal tip, competitor change) |
| 16 | Email | Breakup - polite close, easy out, 25-40 words |

Use 6 touches for short-cycle local niches if the user prefers fewer. SMS/WhatsApp only after they engage, gave that number for this, or where local law allows (US TCPA, India TRAI DND, WhatsApp opt-in rules). Stop every channel the moment they reply or opt out.

Email follow-ups reply in thread unless the user wants new subjects. Templates in `references/frameworks.md`; channel scripts and cadence details in `references/campaigns.md` §4.

---

## 8. Quality gate - score before delivering

Score each draft 1-5 on each item. Any item below 4 -> rewrite before showing user.

1. **Specific** - first line could ONLY be about this business
2. **Relevant** - problem matters to their money or time
3. **True** - every claim sourced or clearly marked estimate
4. **Short** - within word limit, phone-skimmable
5. **Clear ask** - one yes/no CTA
6. **Human** - sounds like a person, not a template or AI (no "I hope this email finds you well", "I came across your", "leverage", "synergy", "elevate", "streamline", "unlock", "game-changer", "in today's digital age", em-dash overuse)
7. **Subject match** - subject honest, curiosity paid off in body
8. **Deliverable** - no spam words, one link max, no attachments
9. **Value-first** - gives or offers something useful before asking for time
10. **Outcome** - offer is framed as a result for them, not a service list

Scores stay internal; show them only if the user asks.

---

## 9. Deliver - output format

**Default output = ONE subject line + ONE email body. Nothing more, nothing less.**

All research, audit, offer building, subject brainstorming (5 options), A/B variants, and quality scoring happen internally. Pick the single best subject and the single best body, and print only this:

```
Subject: [best subject]

[email body, including sign-off, P.S. if used, opt-out line, and [Postal address] placeholder where required]
```

Hard rules for default output:
- No headings, intro, explanation, research summary, scores, notes, alternatives, follow-ups, or closing question
- No code fences around the email; plain text only
- Unknown facts the sender must fill stay as short `[brackets]` inside the body (e.g. `[Postal address]`) - never as separate notes
- If a critical fact is missing and can't be bracketed (e.g. no prospect given), ask one short question instead of writing

**Full report only on request.** If the user explicitly asks for research, alternatives, follow-ups, sequence, scores, or "full report", output the matching parts of this template:

```
## Prospect snapshot
- Business / type / niche / location
- Contact: name, role, email (source) - or "not found"
- Key findings (3-6 bullets, each with source URL)
- Biggest opportunity: [one line] | Estimated impact: [soft estimate, labelled]

## Recommended email (Version A)
Subject options: 1-5 (mark recommended)
Preview text: ...
[body]

## Version B - different angle / shorter
## Offer (outcome + value asset)
## A/B variants (opener B, CTA B)
## Multi-channel sequence (Day 2-16)
## Quality score
## Before sending (unverified items, asset to prepare, best send time: local Tue-Thu 2-4pm or 7-9pm their time; SaaS Tue-Thu 8-10am their time)
```

For batches / campaigns (`references/campaigns.md`):
- Group prospects into segments (niche x town x problem); one campaign per segment with its own subjects, offer, and case study
- Per prospect: Subject + body only (default rule above) - first line always custom, never templated
- Optional spintax version of the shared body (greetings, transitions, CTA phrasing only; never the hook or facts)
- Summary table: business, segment, hook, recommended subject, email found Y/N, fit score
- A/B plan: which variable to test first (offer -> opener -> CTA -> subject), ~100+ sends per variant before judging

---

## 10. Sending - draft by default, send only with approval

Default is **draft only**. Never send automatically.

If the user wants it sent and an email tool exists (Gmail, Outlook, etc.):
1. Show final recipient address, subject, and body for each email
2. Ask: "Send these N emails now? Reply yes to send, or edit first."
3. Send only after an explicit "yes" for that exact batch. Approval does not carry over to later batches or follow-ups
4. Prefer creating drafts in their mailbox when available - safest middle ground
5. Report what was sent, to whom, and when; remind them to schedule follow-ups

Never send to an address that was guessed, and never send more than the user approved.

## 10b. Speed to lead - replies

A positive reply goes cold fast. When the user pastes a reply, classify it right away (interested, price question, not now, already have someone, who are you, not interested, out of office, referral) and draft the response using `references/campaigns.md` §5:
- Interested: send the promised asset + 2 specific call times in the same reply. Target: respond within the hour
- Under 60 words, match their tone, one next step
- "Not interested" / opt-out: one polite line, mark do-not-contact on every channel
- Remind user to turn on reply notifications; suggest a reply-alert automation if they run volume

Sending the reply still follows Section 10 approval.

---

## 11. Compliance and deliverability

- Business information only; no private or sensitive personal details
- Honest subject line, sender identity, working opt-out, postal address where required: CAN-SPAM (US), GDPR/PECR legitimate interest + easy opt-out (UK/EU), CASL (Canada - stricter, implied consent needed), DPDP (India), Spam Act (Australia - consent needed)
- Volume: scale by adding segmented campaigns and warmed mailboxes, not by blasting one list. New mailbox warm-up; under ~30-50 cold emails per mailbox per day; separate sending domain; SPF, DKIM, DMARC set up; verified list with bounce rate under ~2%
- Bought lists: risky or unlawful for cold email in EU/UK, Canada, Australia; verify and check local law first
- Plain text beats HTML for cold email; no tracking pixels on first touch if deliverability is a concern

Practical guidance, not legal advice.
