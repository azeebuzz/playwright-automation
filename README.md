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

The configured project uses Chromium by default. The examples are organized into two groups:

- `01_Basics` checks page titles and demonstrates Playwright annotations such as `skip`, `only`, `fail`, `slow`, and conditional skipping.
- `02_first_tests` introduces browser contexts and pages, test-fixture isolation, multiple users and tabs, and context settings such as locale, geolocation, and mobile emulation.

These are learning examples rather than a clean, all-green suite. The annotation example contains `test.only`, which focuses local runs and is rejected in CI. Also, `212_Browser_Context_Pages.spec.ts`, `213_Multiple_Context.spec.ts`, and `214_Multiple_Pages.spec.ts` start browser scripts at module load; because they use the `.spec.ts` extension, Playwright can execute those scripts while discovering tests. Move them out of test discovery or convert them to Playwright tests before relying on a complete local or CI run.

## Project structure

```text
tests/
├── 01_Basics/
    ├── Lab209.spec.ts
    ├── Lab210_Test_Annoations.spec.ts
    └── Util.ts
└── 02_first_tests/
    ├── 211_First_Test.spec.ts
    ├── 212_Browser_Context_Pages.spec.ts
    ├── 213_Multiple_Context.spec.ts
    ├── 214_Multiple_Pages.spec.ts
    ├── 215_Test_PW.spec.ts
    ├── 216_Manual_Context.spec.ts
    ├── 217_Manual_Context_Options.spec.ts
    └── 218_Context_Reuse.spec.ts
playwright.config.ts
```

## Continuous integration

GitHub Actions runs the tests on pushes and pull requests targeting `main` or `master`. It installs dependencies and Playwright browsers, runs the suite, and uploads the HTML report as an artifact.