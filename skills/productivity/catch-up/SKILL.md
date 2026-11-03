---
name: catch-up
description: Get back up to speed on a thread you've been away from: what you're working on, the blocker, the next step.
argument-hint: "Another thread, or a window like 'since yesterday'; nothing for this whole thread"
disable-model-invocation: true
---

I've been away from this work. Get me back in without me rereading the thread.

1. **Read the thread.** By default, this whole conversation. If I name another thread or a window, read that with `t3_thread_read` (find the thread with `t3_thread_search`). Done when you can state the **original goal** and why I started (quoted from my opening message, plus any later point where I changed it), the last decision, and the last thing tried, drawn from the whole window rather than its tail.
2. **Read the sibling threads.** The work rarely lives in one thread. Find every thread that shares this work: its delegated child tasks, threads on the same branch, worktree or PR (`t3_thread_list`, `t3_worktree_list`, `list_thread_pull_requests`), threads the main one links or names, and bot replies about it. Read each one from the point the main thread last touched it. Done when you can name every sibling and what it contributed, or confirm there are none.
3. **Check it against the world.** Every thread is a **stale** snapshot: work moved while I was gone. Fetch first (`git fetch`), then look at every artifact the threads touched as it stands now:
   - **Local**: branch, uncommitted changes, how far behind its base and origin it sits, background jobs, delegated tasks, ticket files.
   - **GitHub** (`gh`): commits others pushed to the branch and its base, PR state, checks, reviews and comments, linked issues.
   - **Deployments**: the latest deploy for each environment the work ships to (`gh api repos/{owner}/{repo}/deployments`, or the host's CLI), and whether it includes the work.

   Done when every claim about state comes from a command you ran in this turn. Where a thread and the world disagree, the world wins, and you say what changed. A source you can't reach is listed as unchecked on the page, never assumed.
4. **Write the brief** as your first message, before rendering anything: one paragraph of at most five sentences, in this order: the goal (my opening words, quoted and trimmed), where it stands, the blocker or "no blocker", the next step and who takes it, and when the thread can close. Done when I could act on it without reading further.
5. **Render the detail** with `html_render`, below the brief. The page carries the evidence behind each sentence of the brief, in cards of at most three lines each. A section with nothing to show is left out. Every status and date comes from step 3.
   - **Blocker**: the most prominent card, with who clears it (me, you, someone else).
   - **Working on**: a progress strip, each piece marked done, in flight, or not started.
   - **Next step**: the action and who takes it. If it's a decision, the options side by side with your pick marked.
   - **To close the loop**: the verdict (met, partly met, not met), then only the open items, each with its owner; done items collapse into a count ("4 of 6 done"). Goal met: the open items are what still stands in the way of a safe close (unmerged or undeployed work, uncommitted changes, running jobs or child tasks, a worktree to remove, a sibling thread still waiting). Goal not met: each undone piece of the original goal, as a concrete task.
   - **Goal shift**: the original goal beside the current one, with when and why it changed.
   - **While you were away**: up to five events that change what I do next, each tagged with its source (sibling thread, GitHub, deployment).
   - **Unchecked**: one line naming each source you couldn't reach.

   Done when `html_preview` at 728 and 390 shows every card unclipped.
6. **End with links**: one line linking each file, commit, PR and sibling thread the page names. If `html_render` is unavailable, follow the brief with the same sections as short bullets.

Then wait for my go before taking the next step.
