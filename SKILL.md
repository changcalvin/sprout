---
name: sprout
description: The user's persistent personal tax and investing profile (US). Use for any question about their taxes, investments, brokerage or retirement accounts, IRA/401(k) contributions, trading strategy, or tax-year planning, so answers are specific to their situation instead of generic. Also use for /sprout setup, show, update, and review.
---

# sprout — personal tax & investing profile

The user's data lives next to this file and is never committed (see `.gitignore`):

- `profile.md` — current snapshot (income, accounts, tax-year facts, contribution tracker, strategy, traps)
- `log.md` — dated log of decisions, notable trades, contributions, and profile changes

`profile.template.md` is the blank structure a new profile is built from.

## First run

If `profile.md` does not exist, do not answer from generic knowledge. Say the profile hasn't been set up and run **Setup** below (after which, answer the original question).

## Before answering

1. Read `profile.md` in full.
2. Read the recent entries in `log.md` (newest are at the top).

## How to answer

- Answer for their numbers, accounts, and tax situation. Skip generic background unless they ask for it.
- If the answer depends on a `TODO` in the profile, say which one and ask for it rather than guessing.
- Tax limits, brackets, and rules change every year. Before relying on any current-year figure (contribution limits, income phase-outs, brackets, standard deduction, kiddie-tax thresholds), verify it with a web search, preferring irs.gov. If it differs from the profile, update `profile.md`. Every figure in the profile carries an "as of" date; refresh the date when you re-verify.
- Flag tax traps proactively when they apply to what they are about to do. Check the "Rules / traps to watch" section of the profile against the action they describe (e.g. selling at a loss in a taxable account while an IRA holds the same ticker).
- End answers about taxes with one line reminding them to confirm with a CPA when the stakes are real. No other disclaimers or padding.

## Keeping the profile current

When something they say changes their situation (new job, income, contribution, account, holding, strategy):

1. Propose the exact edit to `profile.md` and show it as a before/after.
2. Apply it only after they confirm.
3. Add a one-line dated entry at the top of the entries in `log.md`: `YYYY-MM-DD — what changed`.

## Never store

Social Security numbers, account numbers, passwords, or login details. If they paste any, do not write them to `profile.md`, `log.md`, or anywhere else, and tell them they were not saved.

## Commands

- `/sprout` or `/sprout show` — summarize the current profile in a short overview: who they are for tax purposes, accounts, this year's contribution status, strategy, open TODOs.
- `/sprout setup` — run **Setup** below.
- `/sprout update` — walk through what has changed since the last `log.md` entry, section by section, a few questions at a time. Propose edits, apply on confirmation, log them.
- `/sprout review` — audit the profile:
  - stale figures (old "as of" dates, or a new tax year has started), re-verified by web search
  - upcoming deadlines (April filing deadline, prior-year IRA contribution deadline, estimated tax dates if they have 1099 income)
  - things to act on, e.g. unused contribution room before a deadline, remaining TODOs, holdings approaching the one-year long-term mark, strategy checkpoints

## Setup

Builds `profile.md` and `log.md` for this user. If `profile.md` already exists, never overwrite it: only ask about its remaining `TODO`s and anything they say has changed.

1. **Interview**, a few questions at a time (use a multiple-choice question tool if one is available; always allow free text). Let each answer decide what to ask next and skip what doesn't apply. Cover:
   - Work and income for the current tax year: employed, self-employed, student, or not working; rough amount; W-2 or 1099; any other income (gifts, scholarships, side income)
   - Age, student status, and whether anyone claims them as a dependent
   - Filing status; state of residence, and any other state they worked in
   - Accounts they have or plan to open: taxable brokerage, Roth/traditional IRA, 401(k)/403(b) and employer match, HSA, 529, and the broker for each
   - What they've contributed to each tax-advantaged account this tax year
   - Holdings, at whatever detail they want tracked (tickers, purchase dates, cost basis)
   - What each account is for, their strategy, time horizon, and ideas they're researching
   Anything they don't know stays `TODO`. Do not ask for identifiers listed under "Never store".
2. **Look up the current tax year's figures** that apply to them (contribution limits for the accounts they have, phase-outs for their filing status, deadlines) with a web search, preferring irs.gov. Record each with an "as of" date.
3. **Write `profile.md`** from `profile.template.md`: fill every section, state what the limits mean for them specifically (e.g. their actual IRA cap), and tailor "Rules / traps to watch" by removing traps that cannot apply to them and adding ones their situation creates (multi-state filing, self-employment tax, backdoor Roth pro-rata, and so on).
4. **Create `log.md`** : a `# Log` heading, the line "Newest first. One line per entry: `YYYY-MM-DD — what happened`.", and one dated entry noting the profile was created.
5. **Show the final `profile.md`**, list the remaining `TODO`s, and tell them the commands above.
