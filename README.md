# Master Resume Test Suite

This folder contains a comprehensive QA test suite for the **Master Resume** feature.

## Contents

- `test_suite.md` — Main test document with all test sections and test cases

## Test Case Format

Each test case is documented in a table row with the following columns:

| Column | Description |
|---|---|
| `Test Case ID` | Unique identifier (example: `TC-A-001`) |
| `Test Case Description` | What the test verifies |
| `Type` | Test classification (Functional, Validation, UI, Edge, Integration, etc.) |
| `Priority` | Execution priority (for example: P0 Critical, P1 High, P2 Medium, P3 Low) |
| `Steps` | Actions to execute the test |
| `Expected Result` | Required outcome for pass criteria |
| `Pass` | Mark when actual behavior matches expected result |
| `Fail` | Mark when actual behavior differs from expected result |
| `Notes` | Extra context such as preconditions, defects, or observations |

## How To Use

1. Open `test_suite.md`.
2. Execute tests section by section (A to L, or based on priority).
3. For each test case, mark exactly one outcome:
   - `Pass` if expected result is fully met
   - `Fail` if any expected result is not met
4. Add relevant details in `Notes` (bug ID, screenshots, environment, repro notes).

## Recommended Execution Order

- **Smoke / Critical path first:** run all `P0` test cases
- **High-risk validation next:** run `P1` validation and negative scenarios
- **Full regression:** run remaining `P2` and `P3` cases

## Pass/Fail Guidance

- A test case should be marked **Pass** only when all expected results are satisfied and no blocking errors occur.
- A test case should be marked **Fail** if there is any mismatch, data loss, crash, or unexpected behavior.

## Notes Best Practices

Use the `Notes` column for:

- Bug reference ID (example: `BUG-123`)
- Environment details (browser, viewport, network mode)
- Actual result summary
- Any workaround discovered during testing

