# New project

The repo is empty, so every choice is open. Ask a few questions in one batch, each with your recommended answer so the user can just say yes:

- What is it, and who uses it? A CLI, an API, a web app, a mobile app.
- Where does it run? Locally, on a server, serverless, on a specific host.
- What does the user know or prefer? Languages and frameworks to use or avoid.
- What must it connect to? Existing databases, APIs, auth providers.

A user who doesn't care has accepted your recommendations. Go with them.

Propose the stack as a short list: language, framework, data store, package manager, test runner, deploy target. Give one line of reason per choice. The user's familiarity beats novelty.

Once the user confirms, scaffold so the app runs on day one. Test runner and lint wired up, a README with the run command, a first commit. Write quality-control's station while the run command is fresh, so taste-check can walk the app from it.
