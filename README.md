# Automation Challenge — Java / Gradle

Scaffold for the FastSpring SDET technical interview. This repo sets up the
environment only — the actual challenge is given during your interview session.

## Prerequisites

- JDK 17+ (no local Gradle install needed — the wrapper is included)

## Setup

```
./gradlew playwrightCli   # installs Chromium, once per machine
./gradlew test            # runs the smoke test
```

The smoke test opens the target storefront (Test Mode — no login or account
required) and checks that a product title renders. It should pass before your
interview starts; if it doesn't, that's an environment problem worth chasing
down ahead of time rather than during the session.

## Test report

Gradle writes an HTML report automatically, no extra command needed:

```
open build/reports/tests/test/index.html
```

## Traces

Every test writes a Playwright trace to `traces/<testName>.zip`, pass or
fail. View one by uploading the file at
[https://trace.playwright.dev/](https://trace.playwright.dev/) — no install
needed. If you have Node, `npx playwright show-trace traces/<name>.zip`
works too.

## Layout

- `src/main/java/challenge/pages` — page objects
- `src/main/java/challenge/support` — shared constants
- `src/test/java/challenge` — test classes
