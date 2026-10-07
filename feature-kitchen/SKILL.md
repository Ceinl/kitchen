---
name: feature-kitchen
description: Process to ship a feature, meaning new behavior. Use whenever the user asks to implement, build, or add a feature, even a small one, or when a request for new behavior arrives without a definition of "done". Broken existing behavior goes to sent-back.
---

# Feature kitchen

Kitchen, not factory. You're not stamping copies, you're deciding how this one gets made. The steps below are rails for that judgment.

## Steps

0. **Mise en place.** Empty repo, or the task needs something the stack doesn't have? Run equipment first. Something that used to work is broken? That's a bug, not a feature. Run sent-back instead.
1. **Done.** Get a definition of "done". None given? Ask first.
2. **Shape.** Pick the approach that fits the occasion. The step is finished when you can name the occasion and the chosen shape in one line.
3. **Recipe.** Run recipe to plan the slice and validate the plan against the codebase.
4. **Build.** The thinnest vertical slice, carried through every layer, end to end, following the recipe. Unspecified parts still get built with taste.
5. **Verify.** Run taste-check on the slice. A fix list sends you back to Build. A clean pass goes to chefs-kiss. The same finding surviving two rounds goes to the user.
6. **Report.** What shipped, how to walk it, and every call you made on the user's behalf. Add the proof line for this feature to quality-control's ledger, one line, `slug: walk, evidence`. This is the one place in a feature's run where it gets written.

## Done

You can't build anything if you don't know what result is expected. "Implement X" is not a definition. The definition is what "done" looks like, meaning how the user will know the feature shipped. If they haven't said, ask before anything else. This is the one place work waits. The gate is met when you can state in one sentence what a user will be able to do once this ships.

If the user can't define done either, extract the smallest concrete user outcome you can agree on. A task with no writable "done" is a conversation, not a task. No user to ask at all? Write the smallest done you'd defend, label it an assumption in the report, and proceed.

## Shape

Every feature is a request, but it can be built many ways: hard-coded or parameterized, new endpoint or extended neighbor, quick proof or long-lived feature. The occasion picks the shape, and the occasion comes from the user's context. A hotfix before a demo is built differently than a feature meant to outlive the quarter. When two approaches are plausible and the choice is expensive to undo, the decision is load-bearing. Show the options, don't guess. Small forks like names, defaults and knobs are yours to decide.

### Trust

The user handed over the whole feature, not a checklist of questions, and silence about details is not permission for the blank version. When steps or details are missing, the work is still yours. Implement them anyway, and make them good, because what the user is trusting is your taste. A gap is where taste shows. Fill it with what a careful user would have asked for had they thought of it: the real validation instead of a stubbed one, the real error state instead of a TODO, the edge handled instead of ignored.

The boundary holds. Scope, deliverable, and what "done" means go back to the user.

## Vertical slice

The minimum this ships is the thinnest real user path, carried through every layer, working end to end. "Backend done, frontend next" is not a slice. "Pipeline built, wiring pending" is not a slice. The slice is the unit of done. A real user does the real thing, thin as it may be, or the feature isn't finished. A wide foundation where nothing finishes is prep, not progress.

Find the heart of the feature, the one part the user path can't skip, and build that first, completely. The rest waits.

## Architecture

Build in this codebase, not an imaginary one. The utilities, patterns, and conventions of neighboring files come first. Reach for them before installing anything new. Something you "would have used if it existed" is either already there or a question for equipment's new tool path, not a private dependency.
