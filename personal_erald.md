# personal_erald.md

This file is for Erald. Not a summarizer. A search guide.

The goal: **pinpoint specific case studies, frameworks, and real tactics from the 269 Lenny's Podcast transcripts** — with the exact quote and the episode it came from.

---

## What I'm Looking For

### Content types (in priority order)
1. **Real company case studies** — What a specific company (Airbnb, Notion, Stripe, Uber, etc.) actually *did* at a specific moment. Not advice. Facts.
2. **Named frameworks & mental models** — A guest gives a concept a name, a structure, or a formula.
3. **Specific tactics & decisions** — How they priced it, who they called first, what they cut, the exact thing they tested.

### My focus domains
- **Early-stage / 0→1 building** — Finding PMF, getting first users, early decisions, what to ignore, what to obsess over.
- **Growth & distribution** — Acquisition, retention, word of mouth, virality, go-to-market, pricing pivots.

---

## What Makes a Good Find vs. a Bad Find

A good case study has **3 parts**. All 3 must be present. A quote missing any of them is a platitude, not a case study — do not surface it.

| Part | What to look for | Red flag |
|---|---|---|
| **1. Setup** | The bad situation, ideally with a number. *"By 2018 we had 40% churn"* | Vague: *"we had a retention problem"* |
| **2. Action** | The specific thing they actually did. *"Sorted churn reasons by ARR, took top 10, made it the roadmap"* | Generic: *"we focused on retention"* |
| **3. Result** | What changed, ideally with a number. *"Retention went from 60% to 90%"* | Missing or vague: *"it really helped us grow"* |

**Bonus (prize these):** The speaker also acknowledges *where the solution stops working* or what they'd do differently. This signals a complete, honest narrative — not a victory lap.

**The test:** Could this quote have been said by anyone, at any company, at any time? If yes, reject it. A good find is anchored to a specific company, a specific moment, and specific numbers.

> **Example of a BAD find (Duolingo/Gina Gotthilf):**
> *"If you don't force yourself to pay attention to retention and finding the users to whom this is most useful really early on, you risk convincing yourself of metrics..."*
> → No setup. No action. No result. Pure philosophy. Reject.

> **Example of a GOOD find (Mixpanel/Vijay Iyengar):**
> Setup: *"By 2018 we had 40% revenue churn... we were just not up to the market in terms of features."*
> Action: *"Sorted churn reasons by ARR, took top 10 things and made that our roadmap."*
> Result: *"Retention went from about 60% to 90%, NPS went from 16 to 50."*
> Limitation bonus: *"It is an approach that outlives its usefulness pretty fast."*
> → All 3 parts present. Surface it.

---

## Output Format (Claude: always use this)

When you find a match, return:

```
**[Guest Name] — [Episode Title]**
Episode: [youtube_url from frontmatter]

Setup:   > "[exact quote describing the bad situation]"
Action:  > "[exact quote describing what they did]"
Result:  > "[exact quote describing the outcome]"
Limit:   > "[exact quote on where it stops working]"  ← only if present
```

If the query is broad (e.g. "what do people say about cold outreach"), surface **3–5 different guests** each with one key quote + episode link.

If the query is specific (e.g. "how did Airbnb get their first users"), find **the single sharpest moment** — exact quote, exact episode.

**Read the intent.** Specific question = one precise find. Broad topic = multiple perspectives.

---

## How to Search (Claude: follow this)

### Step 1 — Check the topic index first
Use `index/` to identify which episodes are relevant before reading full transcripts.
```
Read index/{topic}.md   →  get list of episode folders
```
Relevant index files for Erald's domains:
- `index/product-market-fit.md`
- `index/startup-growth.md`
- `index/growth-strategy.md`
- `index/entrepreneurship.md`
- `index/product-led-growth.md`
- `index/bootstrapping.md`
- `index/network-effects.md`
- `index/word-of-mouth.md`
- `index/experimentation.md`
- Company-specific: `index/airbnb.md`, `index/stripe.md`, `index/uber.md`, `index/facebook.md`, `index/google.md`, `index/slack.md`

### Step 2 — Load search patterns, then grep
Before grepping, check if a pattern file exists for the topic:
```
search-patterns/retention.md    ← retention, churn
```
If it exists, use the **Narrative Signals** from that file as your grep patterns — do not generate patterns from scratch.

If no pattern file exists for the topic, generate patterns on the fly and consider adding them to a new file afterward.

Transcripts are large (25,000+ tokens). Always grep before reading full files.
```
Grep pattern="[narrative signal]" path="episodes/" output_mode="content" -C=6
```
Examples:
```
Grep pattern="retention went from" path="episodes/" output_mode="content" -C=6
Grep pattern="churn (dropped|fell).{0,30}%" path="episodes/" output_mode="content" -C=6
Grep pattern="we found.*users who" path="episodes/" output_mode="content" -C=6
```

### Step 3 — Read frontmatter to confirm the episode
```
Read file_path="episodes/{guest}/transcript.md" limit=20
```
This gives you guest name, title, youtube_url, publish_date.

### Step 4 — Read in chunks to find the exact passage
```
Read file_path="episodes/{guest}/transcript.md" offset=X limit=300
```

### Step 5 — For wide research across many transcripts
Use `Agent subagent_type="Explore"` with a specific prompt.

---

## Query Patterns That Work Well

These are the kinds of questions that surface great case studies:

```
"Find me a case study on [topic] — who said it, exact quote, episode link"
"Which guests talked about [tactic]? Give me the 3 sharpest takes"
"What did [Company] do when [situation]? Find the exact episode"
"Find examples of founders who [did X] — real examples only, not advice"
"Who mentioned [framework name]? What exactly did they say?"
```

---

## My Notes — Running Finds

Finds live in **[erald_finds.md](erald_finds.md)**, organized by topic.

When you find a good case study, add it there — not here.
