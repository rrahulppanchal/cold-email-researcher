# cold-email-researcher

Agent skill for Claude and Codex. Researches a prospect (website, Google Business Profile, reviews, socials, competitors, news, hiring posts), audits their website and automation gaps, then writes a personalized cold email - one subject line and one body by default, with a full report, A/B versions, and a multi-channel follow-up sequence on request.

Built for anyone selling **websites and automation** to:
- **SaaS companies** - landing pages, comparison/SEO pages, onboarding and lead-routing automation
- **Local businesses** - cafes, restaurants, lawn care, landscaping, home services, cleaners, salons, gyms, clinics, auto shops, real estate agents

## Install

Copy this folder into your agent's skills directory:

- **Claude Code**: `~/.claude/skills/cold-email-researcher/` (or `.claude/skills/` inside a project)
- **Claude app**: zip the folder and upload it under Settings > Capabilities > Skills
- **Codex**: `~/.codex/skills/cold-email-researcher/` or `.agents/skills/cold-email-researcher/` in a repo (check current Codex docs for the exact path)

Start a new session after installing so the agent picks up the skill.

## First run: save your details

```
/cold-email-researcher setup
```

The agent asks 8 quick questions (name, business, offer, proof, risk reducer, link, goal, tone) and saves the answers to `sender-profile.md` in the skill folder. You can also edit that file by hand. If you skip setup, the skill asks automatically the first time you use it.

Change one field later:
```
/cold-email-researcher profile offer: booking websites for dental clinics
```

In Codex (no slash commands), say the same thing in words: "use cold-email-researcher setup", "use cold-email-researcher: https://example.com full".

## Use

```
/cold-email-researcher https://example.com
/cold-email-researcher Mike's Lawn Co, Frisco TX
/cold-email-researcher https://example.com full
/cold-email-researcher https://example.com followups
/cold-email-researcher https://example.com b
/cold-email-researcher https://example.com notes: <your research notes>
/cold-email-researcher batch: url1, url2, url3
/cold-email-researcher reply: "sure, send the mockup"
/cold-email-researcher profile
/cold-email-researcher help
```

| Option | Output |
|---|---|
| (none) | one subject + one email body |
| `full` | research summary, 5 subjects, 2 versions, offer, A/B variants, sequence, scores, pre-send checklist |
| `followups` | email + 8-touch multi-channel sequence |
| `b` | Version A + Version B for A/B testing |
| `notes:` | uses your notes instead of web search |

## Files
- `SKILL.md` - commands, setup, workflow, hook selection, writing rules, quality gate, output format, approval-gated sending
- `sender-profile.md` - your saved sender details (blank until you run setup)
- `references/niche-playbooks.md` - pains, offers, language, and hook examples per niche
- `references/offers.md` - pain-point mining prompts, outcome offers, value-first assets
- `references/subject-lines.md` - subject formulas and scoring
- `references/frameworks.md` - email frameworks, follow-ups, worked examples
- `references/audit-checklist.md` - website/automation audit and soft-estimate formulas
- `references/campaigns.md` - list quality, segmentation, A/B tests and spintax, multi-channel sequence, reply handling

## Safety
Drafts only by default. It sends only if an email tool is connected AND you explicitly approve the exact batch. It uses only publicly listed business emails and never guesses addresses. Follow the cold-email laws for your recipients' country (CAN-SPAM, GDPR/PECR, CASL, DPDP, Spam Act) - the skill adds opt-out lines and flags where a postal address is needed. Practical guidance, not legal advice.
