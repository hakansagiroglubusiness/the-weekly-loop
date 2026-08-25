# Incident Log

Every time an automation produces a wrong, missing, or misleading output, it goes
here. Same day — details evaporate fast.

This file is the raw material for `50-portfolio/case-02-what-broke`.

**Format:**
```
## YYYY-MM-DD — one-line title
- **Automation:** which one
- **Symptom:** what the output looked like
- **Root cause:** why
- **Cost if unnoticed:** what a human acting on this would have done wrong
- **Fix:** guardrail / eval case / human gate / accepted risk
```

---

## [date TBD] — every metric for one campaign was wrong, and nobody knew until the call

**Status:** unresolved. Nothing was changed after this. It can happen again tomorrow.

- **Automation:** weekly cross-platform performance report
- **Symptom:** every metric for one campaign was wrong. Not one figure off — the
  whole row.
- **How it was caught:** live, during the client presentation. Not in review, not
  by a check, not before sending. In the room, mid-sentence.
- **Cost:** none, by luck. No decision was made on the numbers before the error
  surfaced. The cost was credibility, not money.
- **Suspected root cause:** a campaign naming mismatch. Not confirmed — this was
  never formally diagnosed, which is itself part of the incident.

### Why a naming mismatch is worse than it sounds

Campaign names are the join key. The report matches platform rows to campaigns by
name, and every downstream number is computed from whichever rows that match
returns. When a name drifts — a renamed campaign, a changed convention, a stray
character — the match silently returns the wrong set of rows, or none.

Nothing errors. The arithmetic still works perfectly. It just runs on the wrong
rows and produces a clean, confident, entirely fictional number.

### The part that matters: it gave no warning

The report did not flag uncertainty. It did not say a campaign was missing, that
row counts had changed since last week, or that a total no longer reconciled with
the platform. It presented wrong numbers with exactly the same confidence as
right ones.

This is the most dangerous failure class in an agent system. A crash is safe —
you know something is wrong. Silent, confident wrongness is what reaches a client
presentation, because there is nothing to notice until someone who knows the real
number happens to be in the room.

### What should have caught it, and did not exist

- **Reconciliation:** report total vs. platform total. Any gap above a threshold
  stops the report instead of rendering it.
- **Completeness check:** did every campaign expected this week actually appear?
  A campaign silently vanishing from a report is the exact signature of a broken
  join.
- **Row-count delta:** flag when the number of matched rows changes sharply
  week over week without a corresponding spend change.
- **Refusal over inference:** when a source does not resolve, the report says so
  and stops. It never fills the gap with something plausible.

None of these existed. None of them are hard. That is the point.

### What actually changed afterwards

Nothing.

The resolution was "I'll be more careful next time" — which is not a control,
it is an intention. Being careful does not survive a busy week, and it does not
scale to a system that runs while you sleep. The same report, with the same
missing checks, is still the one being produced.

This is the honest state of it, and it is the reason the rest of this repo
exists.

---

*Seeds `50-portfolio/case-02-what-broke`. Fix tracked in the week 7 eval and
guardrail work.*

---

