# Best Practices for Using AI Coding Tools in VS Code

By Codex GPT-5.4.

_Based on current OpenAI Codex and Anthropic Claude Code documentation, reviewed on April 7, 2026._

This guide is for newcomers who want to use tools like Codex and Claude Code well in VS Code without getting lost in hype, prompting tricks, or unnecessary complexity.

The short version is simple:

- Give the agent a clear goal.
- Give it enough context to succeed.
- Tell it how to verify the result.
- Use planning for bigger tasks.
- Keep instructions short and reusable.

Both OpenAI and Anthropic now recommend very similar working habits. The exact buttons and commands differ, but the workflow is largely the same.

## The Main Idea

AI coding tools work best when they are treated less like search engines and more like junior collaborators with fast hands.

They can read files, propose plans, edit code, run commands, and review diffs. But they still need direction. If the task is vague, they often produce code that looks reasonable without actually solving the real problem.

That is why the best modern advice is not "learn magic prompts." It is:

1. Be clear about the outcome.
2. Point to the right context.
3. Define what "done" means.
4. Check the result.

## The Workflow That Works Best

For ambitious or unclear work, the most reliable pattern is:

1. Explore
   Ask the tool to read the relevant files and explain what it found.
2. Plan
   Ask for a short implementation plan before editing.
3. Implement
   Let it make the change.
4. Verify
   Run tests, replay the bug, compare screenshots, or check expected output.
5. Review
   Look at the diff and ask for a self-check or second-pass review.

This is especially useful for newcomers because it gives you a repeatable loop instead of a vague "just ask the AI."

For very small changes, planning can be skipped. If the task is basically one clear edit, it is usually faster to go straight to implementation.

## What Good Prompts Usually Include

A good prompt usually has five parts:

- Goal: what you want built or fixed
- Context: where in the codebase it lives
- Constraints: what should not change
- Verification: how to test whether it worked
- Deliverable: what you want back

Example:

```md
Goal:
Add a simple CSV import command for demo data.

Context:
Look at main.py and follow the existing command style.

Constraints:
- Keep the code simple and readable.
- Do not add heavy dependencies.

Verification:
- Add or update a small test if practical.
- Show the exact command to run the import.

Deliverable:
- The code change
- A short explanation
- Any follow-up suggestions
```

This style works well in both Codex and Claude Code because it reduces ambiguity without becoming overly technical.

## The Highest-Leverage Habit: Verification

The strongest shared recommendation across the docs is that agents do much better when they can verify their own work.

That means giving them one of these:

- a test command
- a failing bug reproduction
- an expected output
- a screenshot or design reference
- a linter or typecheck command

Without verification, the human becomes the only feedback loop. That is slow, tiring, and easy to get wrong.

In practice, this means every project should have at least one working way to check progress, even if it is only a tiny smoke test.

## What Helps an Agent-Friendly Project

Recommended pieces:

- `README.md`
  Explain what the project is, how to set it up, how to run it, and how to verify work.
- `AGENTS.md` (Codex) or `CLAUDE.md` (Claude)
  Put shared instructions here so participants do not need to repeat them in every prompt.
  The two files can link to each other to avoid repeating the info.
- A small spec template
  Help you describe the project idea before you start building.
- At least one test or smoke check
  Give the agent and the participant a way to confirm progress.
- Clear commands
  Include the exact run, test, lint, and format commands.
- Example prompts
  It helps to have a few strong starting prompts ready to use.

OpenAI uses `AGENTS.md` as the main shared-instructions file for Codex. Anthropic uses `CLAUDE.md` for Claude Code. The idea is the same in both tools: keep durable project guidance in a short file the tool can read every session.

## Keep Shared Instructions Short

This is one of the easiest mistakes to make.

A long instruction file feels helpful, but often becomes noisy and easy for the model to ignore. The best shared instruction files contain only things the tool cannot reliably infer on its own.

Good things to include:

- run, test, lint, and format commands
- important repo conventions
- project-specific do-not rules
- what "done" means
- common gotchas

Things to avoid:

- long tutorials
- full architecture essays
- obvious coding advice
- details that change often

If the file becomes bloated, it stops being a guide and starts becoming background noise.

OpenAI's current recommendation is not to turn `AGENTS.md` into one giant handbook. A better pattern is to keep `AGENTS.md` short and use it as the top-level guide for the repository, then point to more specific markdown files when needed.

For example, `AGENTS.md` might hold the core rules and link to deeper files for:

- testing
- planning
- code review
- architecture notes

This gives the tool a clear starting point without overloading every session with details that only matter for some tasks.

## Best Practices in VS Code

For newcomers using VS Code, these habits are especially useful:

- Reference files directly instead of describing them loosely.
- Use selections and line ranges when asking about specific code.
- Review plans before accepting edits on bigger tasks.
- Review diffs instead of trusting the final message.
- Keep separate sessions or tabs for separate tasks.
- Start a fresh session when the conversation gets messy or unrelated.

This matters because context fills up quickly. Long conversations often drift, and quality usually drops when too much unrelated history is carried along.

## A Good Working Pattern

If you are building an ambitious demo, a practical loop is:

1. Write a one-page mini spec.
2. Ask the tool to explore the repo and suggest a plan.
3. Edit the plan if needed.
4. Ask the tool to implement one slice only.
5. Run checks.
6. Repeat.

This is better than asking for the whole app in one go.

Large requests often produce impressive-looking but fragile output. Smaller verified slices are slower at first, but much more reliable by the end of the session.

## Common Mistakes

These are the patterns most worth warning newcomers about:

- Asking for a full product with no spec
- Giving no verification method
- Letting one chat thread hold every task
- Treating the model's confidence as evidence
- Accepting changes without reading the diff
- Writing giant instruction files nobody will maintain
- Skipping planning for multi-file or unclear work

None of these are fatal, but they are common reasons people conclude the tools are worse than they really are.

## A Good Repo Shape

If a repository is meant to work well with coding agents, this is a strong starting shape:

- `README.md` with setup, run, test, lint, and example prompts
- `AGENTS.md` with short repo rules for Codex
- `CLAUDE.md` if you want the repo to work equally well with Claude Code
- `docs/specs/SPEC_TEMPLATE.md` for planning a project before coding
- `docs/PROMPT_EXAMPLES.md` with explore, plan, implement, and review prompts
- `tests/` with at least one simple check

That structure helps both you and the tool work in a more reliable way.

## A Simple Rule of Thumb

When in doubt, ask:

"If the AI did exactly what I asked, how would I know it succeeded?"

If that answer is unclear, the task is not ready yet.

## Sources

These recommendations are based mainly on current official documentation:

- OpenAI Codex best practices  
  https://developers.openai.com/codex/learn/best-practices
- OpenAI Codex workflows  
  https://developers.openai.com/codex/workflows
- OpenAI guide to `AGENTS.md`  
  https://developers.openai.com/codex/guides/agents-md
- OpenAI Codex prompting guide  
  https://developers.openai.com/cookbook/examples/gpt-5/codex_prompting_guide
- OpenAI Codex MCP guide  
  https://developers.openai.com/codex/mcp
- OpenAI guide on AI-native engineering teams  
  https://developers.openai.com/codex/guides/build-ai-native-engineering-team
- Anthropic Claude Code best practices  
  https://code.claude.com/docs/en/best-practices
- Anthropic Claude Code in VS Code  
  https://code.claude.com/docs/en/vs-code
- Anthropic Claude Code common workflows  
  https://code.claude.com/docs/en/tutorials
- Anthropic Claude Code memory and instruction files  
  https://code.claude.com/docs/en/memory
