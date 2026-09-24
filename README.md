# Playwright Automation

Basic end-to-end tests written with [Playwright Test](https://playwright.dev/docs/test-intro) and TypeScript.

## Prerequisites

- Node.js 18 or newer
- npm

## Setup

Install the project dependencies and the Chromium browser:

```bash
npm install
npx playwright install chromium
```

## Run the tests

Run the configured test suite:

```bash
npx playwright test
```

Useful commands:

```bash
# List tests without running them
npx playwright test --list

# Run tests with a visible browser
npx playwright test --headed

# Open the HTML report after a run
npx playwright show-report
```

The tests use the Chromium project by default. The suite currently covers a VWO title check, a Playwright website title check, and examples of Playwright annotations such as `skip`, `only`, `fail`, `slow`, and conditional skipping.

The annotation example contains `test.only` for demonstration purposes. Remove or disable that focused test before running the complete suite in CI, because the Playwright configuration rejects focused tests when `CI` is set.

## Project structure

```text
tests/
└── 01_Basics/
    ├── Lab209.spec.ts
    ├── Lab210_Test_Annoations.spec.ts
    └── Util.ts
playwright.config.ts
```

## Continuous integration

GitHub Actions runs the tests on pushes and pull requests targeting `main` or `master`. It installs dependencies and Playwright browsers, runs the suite, and uploads the HTML report as an artifact.