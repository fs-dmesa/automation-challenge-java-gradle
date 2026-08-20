# Automation Challenge — Java / Gradle

Scaffold for the FastSpring SDET technical interview. This repo sets up the
environment only — the actual challenge is given during your interview session.

## Prerequisites

- JDK 17+ (no local Gradle install needed — the wrapper is included)

## Setup

```
./gradlew test
```

This installs Chromium the first time, then runs the smoke test. It should
pass before your interview starts — if it doesn't, let us know ahead of time
rather than during the session.

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
result, with each test's Playwright trace attached inline — pass or fail.
Stop it with Ctrl+C.

## Layout

- `src/main/java/challenge/pages` — page objects
- `src/main/java/challenge/support` — shared constants
- `src/test/java/challenge` — test classes
