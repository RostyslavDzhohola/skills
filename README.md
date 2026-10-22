# Skills

Agent skills I use every day, versioned here. Built in the style of [mattpocock/skills](https://github.com/mattpocock/skills).

| Skill | What it does |
|---|---|
| [`/catch-up`](skills/productivity/catch-up/SKILL.md) | Get back into a thread you've been away from: why you started, what's done, the blocker, the next step, and what it takes to close the thread. Checks git, GitHub and deployments, so a stale thread can't mislead you. |

`/catch-up` is written for [T3 Code](https://github.com/pingdotgg/t3code): it reads sibling threads through T3's thread tools and renders its dashboard with `html_render`. In other harnesses it reads the current conversation and answers in text.

## Install

**Claude Code plugin** (updates itself):

```bash
claude plugin marketplace add RostyslavDzhohola/skills
claude plugin install rostyslav-skills@rostyslav
```

**[skills.sh](https://skills.sh)** (copies editable files):

```bash
npx skills add RostyslavDzhohola/skills
```

**By hand:** copy a folder from `skills/` into `~/.claude/skills/`.

## Layout

`skills/<category>/<name>/SKILL.md`, one folder per skill. Every skill is listed in `.claude-plugin/plugin.json`. Changes are recorded in [CHANGELOG.md](CHANGELOG.md), and each release is tagged.

## License

[MIT](LICENSE)
