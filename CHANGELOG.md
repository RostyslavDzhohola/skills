# Changelog

Versions follow `.claude-plugin/plugin.json`; each release is tagged `vX.Y.Z`.

## 0.3.0 (2026-11-03)

- `/catch-up` now says whether the thread is safe to settle: the brief ends on yes or no, and a "Safe to settle" card (which replaces "To close the loop") lists what still stands in the way.
- It ends with numbered questions only you can answer, each with options and a recommended pick, so you can reply in one line. When the thread is safe to settle, the last question offers to settle it.

## 0.2.0 (2026-11-03)

- `/catch-up` now leads with a brief: one paragraph (goal, where it stands, blocker, next step, when it can close) you can act on alone. The dashboard below it holds the detail in cards of three lines or fewer and leaves out empty sections. "To close the loop" shows only open items, "While you were away" keeps the five events that matter, and the closing reply is one line of links.

## 0.1.0 (2026-10-22)

- Add `/catch-up`: reads the thread and its sibling threads, checks git, GitHub and deployments for what moved, and renders a dashboard: why we started, working on, blocker, next step, how to close the loop, and what changed while you were away.
