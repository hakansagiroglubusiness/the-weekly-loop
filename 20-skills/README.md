# Skills

Production Claude Code skills — the actual automation layer.

Every skill here must document five things. A skill missing any of them is not
finished, regardless of whether it works:

1. **Trigger** — when this fires
2. **Inputs** — what data it needs and where it comes from
3. **Guardrails** — what it must never do; what requires human approval
4. **Failure modes** — where it has been observed to be wrong
5. **Eval cases** — inputs with known-correct outputs, to catch regressions

## The write rule

A skill that touches a live ad account **never** activates, pauses, or changes a
budget without explicit typed confirmation. Read and analyze freely; write only on
confirmation. This is not a preference — an agent with unsupervised write access to
a spending account is a liability, not a feature.

## Planned — `growth-os` plugin v1

| Skill | Purpose | Week |
|---|---|---|
| `weekly-report` | Cross-platform WoW performance report | 2 |
| `paid-audit` | Account/campaign audit, structural problems and profit leaks | 2-3 |
| `search-term-triage` | Search term classification, negative list proposal | 3 |
| `creative-fatigue` | Fatigue detection, rotation recommendation | 3 |
