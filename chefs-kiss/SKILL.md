---
name: chefs-kiss
description: Finishing touches, the small details that make a feature feel finished on any surface, UI, CLI, API, or library. Answers to every action, empty and error states, confirmations, fast paths for experienced hands. Use when a feature works but feels flat, when the user asks to polish or improve UX or DX, or as the last pass before calling a feature done.
---

# Chef's kiss

A feature that works and a feature that feels finished are different things. The difference is a hundred small moments where the product either answers or goes silent. This skill finds the silences and fills them.

Every section below applies to every surface. The examples name the common ones: a screen, a terminal, an API, a library call.

## Steps

1. Walk the real user path, taste-check's walk a second time, running the app the way quality-control's station says. Note every moment the product goes silent: the click with no response, the command that exits without a word, the error that says only "failed", the empty result with no hint of what goes there.
2. Fill each silence using the sections below. Use what the codebase already has, like its spinner, toast, logger, or error format, before adding a library.
3. Walk the path once more. A touch that breaks the path comes back out.
4. Report what was added and why. A touch with no reason is decoration.

## Silence

Every action gets an answer. The most common unfinished feeling is not a bug. It's an unanswered gesture.

- **Screen.** A pressed button presses back, so hover, active, focus, and disabled states all exist. A save says it saved. Status changes reach screen readers through `aria-live`.
- **Terminal.** A command that changed something says what it changed. The exit code tells scripts the truth.
- **API.** The status code means what it says, and a create returns what it created.

A wait shows it's waiting, with a spinner, skeleton, or progress line, and nothing sits silent longer than a beat.

## Nothing teleports

Things that appear from nowhere or vanish without a trace make the user re-orient, free work the product should have done.

- **Screen.** Dialogs that snap, rows that vanish. Motion is the answer, and it's cheap. 150 to 250ms, one easing, done. Under `prefers-reduced-motion`, swap movement for a short fade.
- **Terminal.** Progress redraws in place instead of flooding the scrollback. Output fits the terminal, and color drops out when piped.

Motion that draws attention to itself is overdone, see Restraint.

## States beyond happy

Every surface has at least four appearances: empty, loading, error, and full. The blank state is not a state. It's a bug wearing one.

- **Empty** teaches: "nothing here yet, here's what goes here", or "no notes yet, add one with `notes add`".
- **Error** explains what broke and what to try, in words the user can act on. On a terminal it goes to stderr. From an API it carries a message and the field at fault. From a library it names the bad argument.
- **Loading** commits to the layout instead of shifting it.

## Ask, then tell

Destructive actions ask before acting, or better, act and offer undo. On a terminal, that's a prompt with `--yes` to skip it, or `--dry-run` to preview. Successful actions say so with a toast, a checkmark, a highlighted row, or a one-line summary. The user should never finish an action and wonder whether it happened.

## Fast hands

Experienced users move fast, and the product keeps up.

- **Screen.** The path a mouse can walk, keys can walk. Enter submits, Esc closes, focus lands somewhere sensible, and tab order matches reading order.
- **Terminal.** `--help` answers with an example. Flags match the neighboring commands. A scriptable mode, like `--json` or no prompts, exists wherever output gets piped.
- **API and library.** Defaults cover the common case, so the first call is the short one.

## Restraint

Two kinds of touch. Answers are required, and every silence above gets one. A flourish is optional, and one per path is plenty, placed on the moment that matters most. Animation that delays, confirmation on actions that can't hurt, chatter on every command. That's effort spread wide with nothing finished, half-baking in taste-check's words. If a touch makes the user notice the touch, cut it. The best polish is felt, not seen.
