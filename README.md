# Master Resume Test Suite

This folder contains a comprehensive QA test suite for the **Master Resume** feature.

## Test Target Links

- Website under test: [https://cv-ai.work/](https://cv-ai.work/)
- Feature documentation: [https://cv-ai.work/docs](https://cv-ai.work/docs)

## Contents

- `test_suite.md` — Main test document with all test sections and test cases

## Test Case Format

Each test case in `test_suite.md` uses a **detailed markdown block format**:

| Column | Description |
|---|---|
| `Title` | Test case heading (example: `### TC-A-001: Upload an existing resume file (PDF)`) |
| `Field / Detail table` | Includes `Test ID`, `Priority`, and `Type` |
| `Preconditions` | Setup requirements before execution (if applicable) |
| `Steps` | Numbered actions to execute |
| `Expected Results` | Bullet list of required outcomes |

## How To Use

1. Open `test_suite.md`.
2. Execute tests section by section (A to L), or prioritize by `Priority` value in each test case.
3. For each test case, run all listed steps and compare actual outcomes against all expected results.
4. Record execution outcomes in your tracker of choice (for example: spreadsheet, test management tool, or issue tracker).

## Recommended Execution Order

- **Smoke / Critical path first:** run all `P0` test cases
- **High-risk validation next:** run `P1` validation and negative scenarios
- **Full regression:** run remaining `P2` and `P3` cases

## Pass/Fail Guidance

- A test case should be marked **Pass** only when all expected results are satisfied and no blocking errors occur.
- A test case should be marked **Fail** if there is any mismatch, data loss, crash, or unexpected behavior.

## Execution Notes Best Practices

When logging results externally, include:

- Bug reference ID (example: `BUG-123`)
- Environment details (browser, viewport, network mode)
- Actual result summary
- Any workaround discovered during testing

