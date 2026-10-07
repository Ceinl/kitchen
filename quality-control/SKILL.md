---
name: quality-control
description: Per-project station and ledger for proving features work in the running app. Use from taste-check's Reach check, whenever you need to know how this project runs and what counts as proof, or before trusting any "it works" claim.
---

# Quality control

Every project cooks differently. Each one keeps its own station: how to run it for real, how to reset it, what breaks first. taste-check's Reach check depends on it. Without a station, "walk the real path" is a guess.

Both files live in the project repo, under `.agents/quality-control/`, so they travel with the code:

- `station.md` holds how the project runs. One per project.
- `ledger.md` holds one proof line per feature, added as each one ships.

## Steps

1. The station exists? Read it fresh and follow it. Don't wander.
2. None yet? Write it from evidence, then follow it. The step is done when every heading holds a line you ran, a line marked `[unverified]`, or a line with its source. The app won't start at all? That's taste-check's **no path** finding. Write down what you ran and report it.
3. The feature being checked has a proof line? Walk it as written. No line? Walk the path taste-check finds, and add the line once the walk passes. Inside feature-kitchen or sent-back, their Report step writes the line.

## Station

`.agents/quality-control/station.md`. Five questions as headings, one or two lines each.

- **Run.** The command from clean clone to running app.
- **Access.** The surfaces and how to reach each: web UI, CLI commands, API, queues. URL, port, login, test account where they apply.
- **Clean state.** How to reset between checks: seed, migration, fixture.
- **Hazards.** What breaks first: cold caches, build watches, flaky tests, rate limits, cookies.
- **Dirty truth.** What the app does that nobody fixed but everyone lives with, so you don't mistake it for a bug.

Run, Access, and Clean state come from running them. Run each step once before writing it. A station written from memory is fiction, so anything you didn't run yourself gets marked `[unverified]`. Hazards and Dirty truth come from experience. Write each with its source: a walk you took, or something the user said.

The station fits on one screen. A longer one means the dev setup is the bug. Report that to the user as a finding, and keep the station to what works.

## Ledger

`.agents/quality-control/ledger.md`. One proof line per feature or entry point, written once its walk passes:

```
<slug>: <how to walk it>, <what proves it>
```

Examples:

```
export-csv: run `notes export --format csv`, count lines > 0, diff against db dump
login: sign in with the test account, check the redirect lands on /home
```

A proof line fits one line. A longer one means the walk isn't thin, and feature-kitchen's slice probably isn't either.

## Keep it true

- **Current.** A failed station step or proof line gets fixed before it gets followed. A stale ledger is worse than none, it teaches the agent to distrust the project.
- **User, not proxy.** "Tests pass" is not proof. The proof is what the user sees when they do the thing.
