---
name: recipe
description: Plan a feature and validate the plan against the codebase before writing code. Use between choosing an approach and building (feature-kitchen's recipe step), when the user asks for a plan, or when a plan or spec is handed over to check.
---

# Recipe

A plan that meets the codebase for the first time during Build turns into rework. This step checks it against the code first.

## Steps

1. **Write.** A plan was handed over? That's your draft, go to Validate. Otherwise write one for the thinnest vertical slice:
   - The done sentence it serves.
   - The user path, step by step.
   - Each layer the path crosses, with the files to change or create and the existing code to reuse.
   - The order, heart of the feature first.
   - Open questions.

   A plan fits on one screen. A longer one means the slice isn't thin.
2. **Validate.** Check every line against the codebase, not memory. Each check below either passes or goes into the plan as a fix. The step is done when every file and function the plan names has been opened or marked new, and every check passes.
3. **Hand off.** Inside feature-kitchen, go to Build. A load-bearing choice or open question goes to the user first. A plan that was handed over goes back fixed, with each change and its reason.

## Checks

- **ghost.** The plan names a file, function, table, or route that doesn't exist and isn't marked new. Open each one.
- **duplicate.** The plan builds something the codebase already has. Search for each new piece by what it does.
- **gap.** The path skips a layer it needs, like UI without the endpoint, or an endpoint without the data. A plan with a gap is not a slice.
- **misses done.** Walking the planned path end to end doesn't deliver the done sentence.
- **new tool.** The plan needs something the stack doesn't have. That goes through equipment before Build.
