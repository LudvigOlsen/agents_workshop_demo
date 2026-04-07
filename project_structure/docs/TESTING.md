# Testing Notes

Most important rule: The objective is correct code logic, not green tests. If the code is wrong, tests MUST fail.

Use `pytest` as the default test runner for small Python projects unless there is a good reason not to.

## Basic commands

- Run all tests: `uv run pytest`
- Run one file: `uv run pytest tests/test_smoke.py`
- Run one test: `uv run pytest tests/test_smoke.py -k hello`

## Testing habits

- All test expectations should be mentally derived (not computed) based on the intended behavior.
- Prefer small tests that verify behavior clearly.
- Add a regression test when fixing a bug.
- Run the smallest useful test set first, then broader checks if needed.
- If you skip a test, explain why.

## Verification context

Useful verification context includes:

- the exact test command
- the expected output
- any manual check needed for UI or CLI behavior

### Structure & naming

Use Arrange–Act–Assert (AAA) layout inside each test.

Name tests as Given_When_Then or Should_X_When_Y.
Example: splits_fields_when_quotes_present.

One behavioral concept per test. Multiple assertions are fine if they express the same idea.

Use descriptive comments to show your derivations and intentions with each block in pedagogical terms.
