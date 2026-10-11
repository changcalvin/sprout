# sprout

A Claude skill that keeps a persistent tax and investing profile for you, so finance questions get answered for your situation instead of with generic info. US tax rules.

It interviews you once, writes a `profile.md` (income, accounts, this year's limits, contribution tracker, strategy, tax traps) and a `log.md`, then reads both before answering any finance question. It re-verifies yearly figures by web search, proposes profile edits when your situation changes, and warns you about traps like cross-account wash sales before you act.

## Install

```sh
git clone https://github.com/YOUR_USERNAME/sprout ~/.claude/skills/sprout
```

Start a new Claude Code session and run:

```
/sprout setup
```

## Commands

| Command | What it does |
|---|---|
| `/sprout setup` | Interview you and create your profile |
| `/sprout` or `/sprout show` | Short overview of your profile |
| `/sprout update` | Walk through what's changed since the last update |
| `/sprout review` | Check for stale figures, upcoming deadlines, and things to act on |

Or just ask a question about your taxes, IRA, brokerage accounts, or strategy.

## Your data

`profile.md` and `log.md` stay on your machine in the skill folder and are gitignored. The skill is instructed never to store SSNs, account numbers, passwords, or logins. Update with `git pull`; your profile is untouched.

## Disclaimer

Not tax, legal, or investment advice. Confirm with a CPA when the stakes are real.

## License

MIT
