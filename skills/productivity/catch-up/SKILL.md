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
4. **Render the catch-up** with `html_render` as one dashboard I can read at a glance, top to bottom:
   - **Why we started**: the original goal, my opening words quoted, and the reason behind it. If the goal shifted along the way, show the original and the current one side by side with when and why it changed.
   - **Working on**: a progress strip of the pieces of work, each marked done, in flight, or not started.
   - **Blocker**: the one thing stopping progress and who can clear it (me, you, someone else), or "none". It's the most prominent card on the page.
   - **Next step**: one concrete action, and whether you can take it or it needs me. If it's a decision, show the options side by side with your recommendation marked.
   - **To close the loop**: a verdict on the goal (met, partly met, not met), backed by step 3's evidence. Then a checklist to settle the thread, each item marked done or open with who does it:
     - Goal met: what makes closing safe (work merged and deployed, no uncommitted changes, no running jobs or child tasks, worktree removable, nothing a sibling thread still waits on).
     - Goal not met: each piece of the original goal still undone, as a concrete task.

     End with the one line that says when this thread can be closed.
   - **While you were away**: a timeline of what changed between the thread's last message and now, merged across sibling threads, GitHub and deployments, each event tagged with its source. Or "nothing moved".

   Every status and date on the page comes from step 3. Done when `html_preview` at 728 and 390 shows every card unclipped.
5. **Reply in text** with only what the page can't carry: a clickable link to each file, commit, PR and sibling thread it mentions. If `html_render` is unavailable, write the same six sections as text instead.

Then wait for my go before taking the next step.
