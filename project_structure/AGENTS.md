# AGENTS

## Core rules

 - Always use first-principles thinking, grounding your decisions on what actually makes sense.
 - Unit test all logic with **mentally derived** expectations. Do not compute expectations or get them from failing test reports. Unit tests only work when they are based on the INTENDED behavior, not the observed. We care about correct logic, not green tests.
 - When tests fail, analyze whether it's due to a code bug or stale/wrong tests. Always prioritize finding bugs, as the point of testing is to catch wrong code.
- Consider the public contracts before substantial changes. Ask when the two clash.
- Make a short plan before multi-file or unclear work.
- Keep diffs focused on the task.
- Use type hints in new and modified Python code.
- Don't use jargon. Keep communication clear, humanly understandable, and completely honest. If I'm wrong, you should stop and tell me why you think so.
- Add plenty of comments and docstrings in the code. These are for me, collaborators and external users reviewing the code, so keep it humanly understandable - no dev jargon to sound smart or to be too concise.

## Structure

- `README`: User-facing explanation/guide. This is ONLY for communicating with users.
- `src/<project>/`: application code
- `tests/`: automated tests
- `docs/`: specs, plans, research, resources, prompt examples, testing guidance, and review guidance

## Commands

Always run the linter after code changes to ensure working code. 

- Tests: `uv run pytest`
- Lint: `uv run ruff check .`
- Format: `uv run ruff format .`
- Types: `uv run ty check`

## Done

- The requested change is implemented.
- Relevant checks pass, or failures are explained clearly.
- Important follow-up risks are called out.

## References

- `docs/specs/README.md`
- `docs/plans/README.md`
- `docs/research/README.md`
- `docs/resources/README.md`
- `docs/TESTING.md`
- `docs/CODE_REVIEW.md`
- `docs/PROMPT_EXAMPLES.md`
