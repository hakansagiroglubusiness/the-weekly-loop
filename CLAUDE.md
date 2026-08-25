# Working rules for this repo

This is Hakan's Growth OS — a public working repository for AI-native growth work.

## Language

- `00-strategy/` → **Turkish.** These are personal working notes.
- Everything else (`README.md`, `10-playbooks/`, `20-skills/`, `50-portfolio/`) → **English.**
  This repo is read by an international audience. Never write English content in Turkish
  and translate later; write it in English the first time.

## Non-negotiables

**Client confidentiality.** No brand names, no absolute revenue figures, no account IDs,
no screenshots containing identifiable account data. Percentages, ratios, and indexed
values only. When in doubt, index to 100.

**No invented numbers.** Every figure in `50-portfolio/` traces to real data. If a number
can't be sourced, it doesn't go in. Placeholder values must be visibly marked `[TBD]` —
never a plausible-looking fake.

**Show the failure mode.** A skill without a documented failure mode is not finished.
A case study without a "what went wrong" section is marketing, not evidence.

## Skill conventions

Skills in `20-skills/` follow the standard `SKILL.md` format. Each one must document:

1. **Trigger** — when this fires
2. **Inputs** — what data it needs and where it comes from
3. **Guardrails** — what it must never do; what requires human approval
4. **Failure modes** — where it's been observed to be wrong
5. **Eval cases** — inputs with known-correct outputs, used to check regressions

A skill that writes to a live ad account must **never** activate, pause, or change budget
without explicit typed confirmation from the user. Read and analyze freely; write only on
confirmation.

## Style

Write plainly. No em-dash-heavy hype, no "unlock", no "game-changer", no emoji in
committed files. Short sentences. Tables over prose when comparing things. If a
paragraph doesn't change the reader's decision, cut it.
