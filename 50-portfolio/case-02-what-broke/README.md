# Case 02 — What the Agent Got Wrong

> **Status:** Skeleton. Written Week 9, sourced from incidents logged in Week 8.
> **Thesis:** Everyone publishes the win. Almost nobody publishes the failure
> modes. This is the piece that demonstrates judgment — and judgment is the
> actual job.

---

## Why this piece exists

An agent system that has never been observed failing is a system nobody has run
long enough. This is a catalogue of real breakages from running an unsupervised
weekly reporting and optimization agent in production, and what each one taught
me about where the human boundary belongs.

## The incidents

*Sourced from `40-automations/incidents.md`. For each:*

```
### Incident N — one-line title

**What happened:** 
**Why it happened:** 
**What it would have cost if unnoticed:** 
**The fix:** guardrail / eval case / human gate / accepted risk
```

**Expected categories — fill from real incidents, don't pre-write:**
- [ ] Confident output from incomplete data (the most dangerous class)
- [ ] Silent API / connector failure
- [ ] Metric definition mismatch across platforms
- [ ] Attribution window confusion
- [ ] Recommendation that was technically right and commercially wrong

## What this changed about how I build

*The general lesson. Where does an agent get autonomy, where does it get a gate,
and what's the test for deciding?*

## What I still don't trust it with

*A concrete list. This is the most credible section in the whole portfolio.*

---

**Anonymization checklist:** same as case-01.
