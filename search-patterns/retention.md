# search-patterns/retention.md

Seed keywords: **retention**, **churn**

Use this file before running any retention-related search. Start with Narrative Signals — they catch stories. Fall back to Vocabulary only if signals return too few results.

---

## Narrative Signals
*Patterns that indicate a before/after story is being told. These are the primary grep layer.*

### "We had a problem" signals (Setup)
```
retention (was|is|had been|were).{0,60}(bad|low|poor|terrible|broken|awful|horrible|rough)
churn (was|is|had been|were).{0,60}(bad|high|terrible|horrible|rough|a problem|an issue)
we (had|were seeing|were experiencing|were at).{0,60}(churn|retention)
(our|the) churn (was|is|had been|hit|reached|got to)
(our|the) retention (was|is|had been|hit|dropped to|fell to)
(users|customers|people) (were|started) (leaving|churning|dropping off|falling off)
we were losing.{0,40}(users|customers|people)
people (weren't|didn't) (come back|return|stick around|stay)
```

### "We discovered" signals (finding the retaining segment)
```
we (found|noticed|discovered|realized|learned) that (users|customers|people|those) who
users who.{0,60}(more likely to|retained|stayed|came back|stuck around)
(the users|customers).{0,20}that (retained|stayed|stuck|came back)
(if|when) (users|customers|people).{0,40}(they|were more likely to|retained|stayed)
we saw that.{0,60}(retain|churn|stay|come back)
the (segment|cohort|group|users|people) who.{0,60}(retain|stay|stick|come back)
activation.{0,80}retention
(aha moment|magic moment).{0,80}retain
```

### "We fixed it / result" signals (Action + Result)
```
retention went from
retention (improved|increased|jumped|went up|climbed|grew) from
retention (improved|increased|jumped|went up|climbed|grew).{0,30}%
churn (dropped|fell|went down|decreased|went from|came down)
churn (dropped|fell|went down|decreased).{0,30}%
went from.{0,30}% (churn|retention).{0,30}to.{0,30}%
(improved|fixed|solved|turned around).{0,40}(retention|churn)
reduce(d)? (our )?(churn|churn rate)
(we|it).{0,30}(increased|improved|lifted).{0,40}retention
```

---

## Vocabulary
*Synonyms and adjacent concepts. Use when narrative signals return too few results, or to broaden a search.*

### Direct synonyms
```
churning
churned (users|customers)
churn rate
re-engage
reactivation
win-back
came back
returned to
drop-off
dropped off
falling off
people (left|leaving)
users (left|leaving)
```

### Retention metrics & proxies
```
day.?30
week.?4
D30
W4
monthly retention
annual retention
cohort retention
DAU.?MAU
DAU\/MAU
stickiness
sticky
lifetime value
LTV
```

### Behavioral signals (often used as retention proxies)
```
habit
streak
notification.{0,40}(retain|bring back|re-engage)
came back.{0,40}(day|week|time)
daily active
weekly active
power user
core user
```

---

## Anti-patterns (skip results that match only these — too generic)
```
"retention matters"
"retention is important"
"focus on retention"
"care about retention"
"retention is key"
"improve retention"        ← without a number or specific action attached
"churn is bad"
```

---

## Usage notes

**Run narrative signals first, with context:**
```
Grep pattern="retention went from" path="episodes/" output_mode="content" -C=6
Grep pattern="churn (dropped|fell|went down).{0,30}%" path="episodes/" output_mode="content" -C=6
```

**If a result line is omitted (too long), read that chunk directly:**
```
Read file_path="episodes/{guest}/transcript.md" offset=X limit=100
```

**Add new patterns here when you find a phrase in a real transcript that surfaced a good story.**

---

## Checked episodes

*Episodes manually reviewed for retention/churn case studies (Setup + Action + Result). Checked sequentially from the episodes/ folder.*

| Folder | Guest | Result |
|---|---|---|
| ada-chen-rekhi | Ada Chen Rekhi | ❌ No retention content (career advice clip, 3:50 duration) |
| adam-fishman | Adam Fishman (Patreon, Lyft) | ⚠️ Partial — Patreon onboarding: 25% creator LTV lift from human-touch onboarding → productized as "opinionated defaults". Strong Action + Result, weak Setup (no specific bad number). |
| adam-grenier | Adam Grenier (Uber, MasterClass) | ❌ No retention story (episode about acquisition channels & Growth CMO role) |
| adriel-frederick | Adriel Frederick (Reddit, Lyft, Facebook) | ❌ No retention story (diversity, Lyft pricing, Facebook marginal user framework — all acquisition/conversion, not retention) |
| aishwarya-naresh-reganti-kiriti-badam | Aishwarya Naresh Reganti + Kiriti Badam | ❌ No retention content (AI product development episode) |
| albert-cheng | Albert Cheng (Duolingo, Grammarly, Chess.com) | ⚠️ Partial — Chess.com game review: flipped post-loss framing from blunders→brilliant moves. 25% more game reviews, 20% more subs, retention up "a lot" (unquantified). Also: losing first game = 10% worse retention (no fix described). |
| alex-hardimen | Alex Hardiman (NYT CPO) | ❌ No retention story (NYT product org, COVID response, Wordle acquisition) |
| alex-komoroske | Alex Komoroske (Google, Stripe) | ❌ No retention content (strategy/philosophy episode) |
| alexander-embiricos | Alexander Embiricos (OpenAI Codex) | ❌ No retention content (AI coding agent episode) |
| alisa-cohn | Alisa Cohn (executive coach) | ❌ No retention content (difficult conversations / leadership) |
| ami-vora | Ami Vora (Faire, ex-WhatsApp/FB/IG) | ❌ No retention content (leadership/authenticity episode) |
| amjad-masad | Amjad Masad (Replit CEO) | ❌ No retention content (Replit product/AI coding) |
| andrew-wilkinson | Andrew Wilkinson (Tiny) | ❌ No retention story (holding company philosophy, network effects — retention/churn keywords from ad reads only) |
| andy-johns | Andy Johns (ex-FB, Twitter, Quora) | ❌ No retention content (personal journey/burnout episode) |
| andy-raskin (+ andy-raskin_) | Andy Raskin | ❌ No retention content (strategic narrative/pitching; andy-raskin_ is duplicate) |
| anneka-gupta | Anneka Gupta (Rubrik CPO) | ❌ No retention content (strategy/leadership episode) |
| annie-duke | Annie Duke (poker/decision-making) | ❌ No retention content (decision frameworks; "churn" is passing VC signal mention) |
| annie-pearl | Annie Pearl (Calendly CPO) | ❌ No retention story (team structure/PLG; retention mentioned only as funnel stage label) |
| anton-osika | Anton Osika (Lovable CEO) | ❌ No retention content (AI startup growth story) |
| anuj-rathi | Anuj Rathi (Swiggy, Jupiter Money, Flipkart) | ❌ No retention content (full-stack PM / growth episode) |
| aparna-chennapragada | Aparna Chennapragada (Microsoft CPO) | ❌ No retention content (AI product strategy) |
| april-dunford | April Dunford (Sales Pitch) | ❌ No retention content (sales pitch/positioning; keyword tag only) |
| april-dunford-20 | April Dunford 2.0 (Obviously Awesome) | ❌ No retention content (product positioning; keyword tag only) |
