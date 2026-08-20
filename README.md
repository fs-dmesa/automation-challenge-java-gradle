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
works too. Every trace is also attached to the Allure report below, so you
usually don't need this file directly.

## Allure report

```
./gradlew test allureView
```

This runs the tests, generates an Allure report, and serves it at the URL it
prints (`http://localhost:<port>/`). Allure's report loads its data via XHR,
which browsers block outright under `file://` — opening `index.html`
directly just shows a blank page — so `allureView` runs a small embedded
HTTP server instead of requiring `allure serve` or a separate Allure install.
Each test's Playwright trace appears inline as an attachment. Stop the
server with Ctrl+C.

## Layout

- `src/main/java/challenge/pages` — page objects
- `src/main/java/challenge/support` — shared constants
- `src/test/java/challenge` — test classes
