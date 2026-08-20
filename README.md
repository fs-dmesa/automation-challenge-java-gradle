# Automation Challenge — Java / Gradle

Environment scaffold for a FastSpring SDET technical interview. This repo
contains no challenge content — that's given during the session.

## Prerequisites

- JDK 17+ (no local Gradle install needed — the wrapper is included)

## Setup

```
./gradlew test
```

This installs Chromium the first time, then runs the smoke test — it
verifies the environment is wired up correctly.

## Headed vs headless

Tests run headless by default. To watch the browser instead:

```
./gradlew test -Dheadless=false
```

## Report

```
./gradlew allureView
```

Opens at the `http://localhost:<port>/` URL it prints. Shows the full test
result, with each test's Playwright trace attached — pass or fail. Download
it from the report and open it at
[https://trace.playwright.dev/](https://trace.playwright.dev/) for the full
trace viewer. Stop the server with Ctrl+C.

## Layout

- `src/main/java/challenge/pages` — page objects (`@Step`-annotated actions show up in the report)
- `src/main/java/challenge/support` — shared constants
- `src/test/java/challenge` — test classes
- `src/test/java/challenge/support/ChallengeAssertions` — assertion helpers that also log an Allure step, so a passed assertion still shows up in the report
