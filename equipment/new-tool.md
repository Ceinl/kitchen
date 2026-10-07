# New tool

The stack exists and the task needs something it doesn't have.

## Look

The capability may already be here under another name. Check three places:

- **Dependencies.** The manifest and lockfile. A library may already do it, pulled in for another feature.
- **Code.** Search by what the capability does, not by a library name. A helper, a wrapper, a half-built version.
- **Services.** Docker compose, env vars, infra config, CI. A database or queue may already be running.

Looking is done when all three are checked. Found it? Use it, and skip the rest.

Small enough to write in a few lines of plain code, with no service behind it? Write it. This path is for dependencies and services.

## Propose

Offer two or three options that fit what's installed, your recommendation first. Compare them on what actually separates them:

- **Fit.** Works with the current language, framework, and patterns.
- **Health.** Maintained recently, used widely enough that answers exist.
- **License.** Compatible with the project.
- **Weight.** Install size and transitive dependencies.
- **Cost.** A library, or a service to run, pay for, or sign up for.

## Install

After the user picks, install with the package manager the lockfile names, and put the integration where the codebase keeps its others. The new tool should look like it was always there.
