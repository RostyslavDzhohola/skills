# Changelog

Versions follow `.claude-plugin/plugin.json`; each release is tagged `vX.Y.Z`.

## 0.2.0 (2026-11-03)

- `/catch-up` now leads with a brief: one paragraph (goal, where it stands, blocker, next step, when it can close) you can act on alone. The dashboard below it holds the detail in cards of three lines or fewer and leaves out empty sections. "To close the loop" shows only open items, "While you were away" keeps the five events that matter, and the closing reply is one line of links.

## 0.1.0 (2026-10-22)

- Add `/catch-up`: reads the thread and its sibling threads, checks git, GitHub and deployments for what moved, and renders a dashboard: why we started, working on, blocker, next step, how to close the loop, and what changed while you were away.
