---
name: weekly-report
description: Cross-platform paid performance report comparing two periods. Pulls spend and revenue from each ad platform and sessions from analytics, reconciles them, and renders a presentable HTML deck. Refuses to render when the numbers do not reconcile.
---

# weekly-report

Produces the recurring paid performance report: current period against a
comparison period, broken down by platform, campaign, and optionally product.

The report is presented live in client meetings. That single fact drives every
design decision here. A report that is merely usually right is not good enough,
because the moment an error surfaces is the worst possible moment — in the room,
mid-sentence, in front of the person paying for the work.

## Trigger

- "weekly report", "haftalık rapor", "WoW report", "performance report"
- A named period: "report for Nov 3-9", "last week's numbers"
- Explicit comparison: "vs last year", "YoY"

## Inputs

### Client profile (required)

Platform coverage varies by client. Never assume a fixed set.

```yaml
client:            # internal label only, never rendered into public output
currency:
platforms:         # any subset of: google_ads, meta, tiktok
analytics:         ga4
comparison:        previous_period | previous_year
breakdowns:        [platform, campaign]   # add `product` when requested
```

### Data pulled

| Source | Fields | Grain |
|---|---|---|
| Each ad platform | spend, impressions, clicks, conversions, revenue | campaign |
| GA4 | sessions, revenue, transactions | source / medium, campaign |

Both periods are pulled in full. The comparison period is never inferred from a
single-period pull.

### Metrics rendered

| Metric | Definition |
|---|---|
| Spend | Sum of platform spend, in the client's currency |
| Cost per session | Paid spend ÷ paid sessions |
| Revenue | Attributed revenue |
| ROAS | Revenue ÷ spend |

**Cost per session spans two systems.** Spend comes from the ad platforms;
sessions come from analytics. The two are joined on campaign identity, and that
join is the single most fragile thing in this skill. See Failure modes.

Every metric is shown as: current value, comparison value, and the change
between them. A number without its comparison is not reportable.

## Guardrails

### 1. Reconciliation gate

Before rendering, per platform, compare the report's total spend against the
platform's own reported total for the same period.

- Gap ≤ 1%: proceed
- Gap > 1%: **stop.** Report the discrepancy. Do not render the deck.

A report that does not reconcile is not a report with a small problem. It is a
report computing on the wrong rows, and every downstream figure inherits that.

### 2. Completeness gate

Compare the set of campaigns present this period against last period.

- A campaign that appears in the comparison period but is absent now, with no
  corresponding spend change, is a **failed join until proven otherwise** — not a
  paused campaign. Stop and surface it.
- A platform in the client profile that returned no rows at all is an error, not
  a zero.

### 3. Never fabricate

If a source does not resolve, the report says so in place of the number. It never
substitutes an estimate, a prior value, a zero, or an interpolation. Missing data
is rendered as missing, visibly, in the output that reaches the client.

An empty cell that says "not available" costs a sentence of explanation. A
plausible wrong number costs the client relationship.

### 4. Read only

This skill reads. It never activates, pauses, or changes budget on any account,
under any phrasing of the request. Optimization is a different skill with a
different confirmation flow.

### 5. No client identity in shared artifacts

Client names, account IDs, and absolute revenue figures never leave the client's
own deck. Anything published or committed uses indexed or percentage values.

## Failure modes

Observed, not hypothetical.

### Campaign naming mismatch — confirmed, unresolved

**Campaign name is the join key** between platform rows and analytics rows. When a
name drifts — a rename, a changed convention, a stray character — the join
silently returns the wrong row set, or none.

Nothing errors. The arithmetic runs correctly on the wrong rows and produces a
clean, confident, entirely fictional number.

This reached a live client presentation: every metric for one campaign was
wrong, with no warning of any kind. Full write-up in
[`40-automations/incidents.md`](../../40-automations/incidents.md).

The reconciliation and completeness gates above exist specifically because of it.

### Attribution window mismatch

Platforms attribute on their own windows and models; analytics attributes on
last-click by default. Revenue will not agree, and it is not supposed to. Report
each source labelled, and never sum revenue across platforms and analytics into
a single figure.

### Currency and timezone boundaries

Accounts may report in different currencies and different timezones. A period
boundary that differs by one timezone shifts a day of spend between periods,
which is invisible at the total level and obvious in a daily chart. Normalize
both explicitly; never rely on platform defaults agreeing.

### Analytics thresholding

GA4 withholds low-volume rows. A campaign with real spend can show zero sessions,
producing an infinite cost per session. Detect and label it, do not render `∞`
or silently drop the row.

### Comparison period length

A "previous period" of unequal length invalidates every comparison in the deck.
Assert equal length before computing any change.

## Eval cases

Run before shipping a change. Each has a known correct behavior.

| # | Input | Expected |
|---|---|---|
| 1 | Two clean periods, all platforms return data | Renders; all metrics have comparisons |
| 2 | One campaign renamed between periods | **Stops** at the completeness gate, names the campaign |
| 3 | One platform returns zero rows | **Stops**, reports the platform as failed, not as zero |
| 4 | Report total 3% below platform total | **Stops** at the reconciliation gate |
| 5 | Campaign with spend, zero sessions from analytics | Renders, cost per session labelled unavailable, not `∞` |
| 6 | Comparison period one day shorter | **Stops**, reports unequal period lengths |
| 7 | Two accounts in different currencies | Normalizes, states the rate and its date |
| 8 | Product breakdown requested, no product data | Renders other breakdowns, states product data unavailable |

Cases 2, 3, 4 and 6 are the ones that matter. They are all variations of the same
question: *does this skill fail loudly, or does it fail quietly?*

## Output

- **HTML deck** — self-contained, presented live in meetings. No external assets.
- **Table** — same numbers, for pasting into email or chat.

Both are rendered from the same reconciled dataset. They never diverge.
