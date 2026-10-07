---
name: taste-check
description: Check a feature or fix against its definition of done by walking the real user path. Use after implementing a feature or fixing a bug, when reviewing an agent's work, or whenever something "works but...".
---

# Taste check

## Steps

1. Get the bar, the definition of "done" this feature shipped under. feature-kitchen writes one before building. For a fix, it's the expected behavior from sent-back's complaint. None anywhere? That is the first finding. Report it and stop, because a check with no bar can't pass.
2. Run the three checks below, in order. Each one ends with its finding names.
3. Judge the walk against the bar, not the code. Quote the evidence that a user can, or can't, do the one-sentence outcome.
4. Report a verdict in one of two shapes. Every check gets a line with evidence, and "looks fine" is not evidence.
   - `PASS`, with the walk you took.
   - `FIX`, a list of `finding: evidence, location`.

## Reach

First, because everything else depends on it. Find the path a real user takes and walk it in the running app. Reading code is not walking it. quality-control's station is how you run the project; if none exists, write one before walking.

Walk to the end. The path should land somewhere, like a confirmation, a return to where the user started, or a clear next action.

- **no path.** Nothing to walk, an app that won't run included. A correct feature behind a broken entry point is still broken.
- **breaks mid-walk.** The path exists but fails partway. Check saving, reloading, the step after the step.
- **no landing.** The walk finishes and leaves the user stranded, with no sign it worked and nowhere to go.

Then walk what was there before. Every ledger line whose path shares files, routes, or data with the change gets walked again, as written. The walk is done when each of those lines has passed or become a finding.

- **regressed.** A ledger line that passed before fails now. It's the change's bug, even when the failing feature isn't the one being checked.

## Half-baked

Cuts both ways.

- **half-baked.** Underdone. Does it actually do the thing, or does it fake parts of it? Stubs, TODOs, "works if you click twice".
- **speculative.** Overdone. Building for imagined futures is half-baking in the other direction, effort spread wide with nothing finished. The measure is feature-kitchen's vertical slice. A thin slice that works beats a wide foundation that doesn't.

## Easy, not simple

Hickey's distinction, applied to the code in front of you. Easy is what was at hand: the pattern copied from the neighboring file, the library one install away, the abstraction added "just in case". Simple is what doesn't intertwine. One concern per thing, nothing speculative, deleting it leaves no holes. Tangled code is harder to carve out and breaks more often.

- **tangled.** A change touches five places, or deleting it makes something else wobble.
- **unexplainable.** You can't say how it works in one breath.
