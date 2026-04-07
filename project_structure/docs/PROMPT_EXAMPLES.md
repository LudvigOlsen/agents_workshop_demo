# Prompt Examples

Starter prompts for common coding-agent workflows in VS Code.

## Explore

```md
Read the project structure and explain how this codebase is organized.
Focus on the main entry points, tests, and any important conventions.
Do not make changes yet.
```

## Plan

```md
I want to add [feature].

Start by reading the relevant files and any relevant spec in `docs/specs/`, then propose a short implementation plan.
Call out which files you expect to change, how you will verify the result, and any risks.
Do not edit code yet.
```

## Implement

```md
Implement the approved plan for [feature].

Constraints:
- Keep the diff small and readable.
- Follow existing patterns in the repo.

Verification:
- Run the smallest relevant test set.
- Report what you changed and how to verify it manually.
```

## Review

```md
Review the current diff like a code reviewer.
Prioritize bugs, regressions, missing tests, and unclear behavior.
List findings first, then any open questions.
```
