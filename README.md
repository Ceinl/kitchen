# Skills kitchen

Agent skills for shipping features and fixing bugs that work in the running app, not only in the diff. Every skill ends on the same test: a real user walks the real path, and it works.

## Entry points

Two skills start the work. The agent picks one from the request.

- **feature-kitchen** for new behavior: "add export to CSV", "build a login page".
- **sent-back** for broken behavior: "export crashes on empty notes", "login stopped working".

The other skills are steps inside those two, and each one can also be used on its own.

```
feature-kitchen                         sent-back
 0 equipment (if needed)                 1 complaint
   bug? ─────────────────────────────►   2 reproduce
 1 done                                  3 pin
 2 shape                                 4 cause
 3 recipe                                5 fix
 4 build                                 6 taste-check
 5 taste-check ⇄ build                   7 report → ledger
   → chefs-kiss
 6 report → ledger

 quality-control: how the project runs and what counts as proof,
 used by taste-check, chefs-kiss, and sent-back
```

## Skills

| Skill | Does | Use it on its own when |
| --- | --- | --- |
| feature-kitchen | Ships a feature: done, shape, plan, thin slice, check, polish, report | You ask for any new feature, even a small one |
| sent-back | Fixes a bug: reproduce, pin, cause, fix, check | You report a bug or something that used to work |
| equipment | Picks tools before code: a new project's stack, or one new dependency or service | The repo is empty, or the task needs a database, queue, auth, or similar |
| recipe | Plans a slice and checks the plan against the codebase | You want a plan, or have a spec to check |
| taste-check | Walks the real user path and judges it against done, including a regression walk | You want an agent's work reviewed |
| chefs-kiss | Adds the small details that make a feature feel finished, on any surface: UI, CLI, API, library | A feature works but feels flat |
| quality-control | Keeps the project's station (how it runs) and ledger (how each feature is proven) | You need to know how to run the project, or whether "it works" is true |

## Files in your project

quality-control writes two files into the project it works on, so they travel with the code:

- `.agents/quality-control/station.md`: run, access, clean state, hazards, dirty truth.
- `.agents/quality-control/ledger.md`: one proof line per feature, like `login: sign in with the test account, check the redirect lands on /home`.

Commit them. The ledger is what the regression walk replays.

## Install

Copy the skill folders into your agent's skills directory. For Claude Code that's `~/.claude/skills/` for every project, or `.claude/skills/` inside one project. Install them together, since the skills call each other by name.
