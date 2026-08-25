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

## [TBD] — an agent-produced error reached a client

> **Write this in Week 1.** This incident predates the repo. It already happened,
> the details are fading, and it is the most valuable single artifact available
> for `50-portfolio/case-02-what-broke`. Nothing else in the portfolio
> demonstrates judgment the way a real, owned failure does.

- **Automation:** *(which skill / workflow produced it)*
- **Symptom:** *(what the output said; what was wrong about it)*
- **Root cause:** *(missing data? wrong metric definition? attribution window?
  the model filling a gap with a plausible number?)*
- **How it was caught:** *(who noticed, and after how long)*
- **Cost:** *(what decision was made or nearly made on the strength of it)*
- **Fix:** *(what changed afterwards, if anything)*
- **What should have caught it:** *(the guardrail or eval that did not exist)*

Anonymize as you write: no brand name, no absolute figures.
