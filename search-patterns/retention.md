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
