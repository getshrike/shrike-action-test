# Shrike Action integration test

This repository exercises the Shrike GitHub Action against a real pull request.

- `main` has a live call to `add` in `src/index.ts`.
- A test pull request removes that call, leaving `add` newly dead.
- The `shrike` workflow installs `getshrike`, runs the Action in delta mode
  against `origin/main`, and uploads `.shrike/action-delta.json`.

Expected on the test PR: one newly dead symbol (`add`), with `fail-on: never`
so the run reports the finding without failing the build.
