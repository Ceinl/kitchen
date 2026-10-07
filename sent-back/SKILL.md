---
name: sent-back
description: Fix a bug by reproducing it before touching code. Use when the user reports a bug, something that used to work broke, or a walk fails on code that already shipped.
disable-model-invocation: true
---

# Sent back

The dish came back. Before cooking it again, find out what was wrong with it. A fix written before the bug is seen failing is a guess, and a guess that happens to pass teaches nothing.

## Steps

1. **Complaint.** Get three things: what the user did, what they expected, what happened instead. The expected behavior is the bar, taste-check's definition of done for this fix. Missing one? Ask. No user to ask? Write the expected behavior you'd defend, label it an assumption, and proceed.
2. **Reproduce.** Run the app the way quality-control's station says and walk the complaint until it fails the way the user described. The step is done when you can make it fail on demand.
3. **Pin.** Capture the reproduction so it can go red and green: a failing test where the codebase has tests for this layer, otherwise a written walk with the exact inputs. It's red now.
4. **Cause.** Trace from where the bug shows to where it starts. The step is done when you can explain the bug in one breath, and the explanation predicts the reproduction.
5. **Fix.** Change the code at the cause, as little as it takes. Other places sharing the same cause get the same fix.
6. **Verify.** The pin goes green. Then run taste-check on the fix, including its regression walk.
7. **Report.** The cause, the fix, and the pin. Add a proof line for the path to quality-control's ledger if it had none, because a path that broke unnoticed was a path nobody walked.

## Reproduce first

A bug you can't make fail is a bug you can't prove fixed. When the walk won't fail, the difference is somewhere between your run and the user's: data, environment, version, account, order of steps. Narrow it down one difference at a time. Still no failure? Report what you tried and what you need, and go back to the user. That's the one place this work waits.

When the failure turns out to be something the station lists under Dirty truth, stop and ask whether it's being fixed now or stays lived with.

## Cause, not symptom

The bug shows in one place and starts in another. A null check where the crash happens hides the bug. The fix goes where the bad value was made. A fix you can't explain in one breath is a symptom patch, taste-check's **unexplainable** finding before it's written.

## Scope

A sent-back dish gets fixed, not redesigned. The fix is the smallest change at the cause. Nearby mess you notice along the way goes into the report, not into the diff. A fix that needs a new shape, like a schema change, a new dependency, or a rework of the feature, is a load-bearing decision, so it goes to the user first, the same way feature-kitchen's Shape handles one.
