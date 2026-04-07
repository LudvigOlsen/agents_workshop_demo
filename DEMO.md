# Workshop demo

April 10, 2026, by Ludvig Renbo Olsen, Mathilde Hartvig Diekema, and Codex.

---

Let's build some ambitious projects!!

This document describes the following steps:

 - Installing requirements
 - Create GitHub repository
 - Initialize the python project with `uv init`
 - Copy in the project structure
 - Describe the project in `specs`
 - Perform deep research on science, tools, alternatives in `research`
 - Update specs based on the research
 - Plan how to implement in `plans`
 - Start building!
 - Testing, testing, testing
 - Demoing

## Requirements

You will need the following things installed as a minimum. A few more things will be installed later in the project.

 - Install `git`: https://git-scm.com/downloads
 - Verify `git`: `git --version`
 - Install `gh`: https://cli.github.com/
 - Verify `gh`: `gh --version`
 - Install `uv`: https://docs.astral.sh/uv/getting-started/installation/
 - Verify `uv`: `uv --version`

VS Code and Codex extension:

 - Install `VS Code`: https://code.visualstudio.com/download
 - Install the `Codex` VS Code extension. Find it in **Extensions** in the left toolbar or at https://marketplace.visualstudio.com/items?itemName=OpenAI.chatgpt
 - Sign in to the `Codex` extension with your `ChatGPT` account

A similar extension is available for Claude Code.

## GitHub repository

You will be placing your code in a `GitHub` repository and using `git` to push code changes to it. This requires having/making a GitHub account. Then go to https://github.com/new and give your project a name and small description. In "Choose visibility", you may prefer "Private" (optional though).

```bash
 gh auth login --web --git-protocol https
 gh repo clone OWNER/REPO
```

Now open the project folder in a new `VS Code` window. You should only have this project in the folder:

```text
File >> New Window >> Open Folder
```

## Initialize project

Now that we have the project open, we will initialize it to work with the `uv` package manager and install some development dependencies:

```bash
uv init
uv add --dev pytest ruff ty
```

 - `pytest` is for testing the code. 
 - `ruff` is for formatting the code.
 - `ty` is for type checking the code.


## Project structure

Now we can copy in the project structure from `project_structure/` in the workshop repository.

 - Copy the **contents** of `project_structure/` into the new repository.
 - Rename `src/your_project/` to the real package name.
 - Update `tests/test_smoke.py` to import the renamed package.

Now that the core structure is ready, let's *add*, *commit* and *push* the changes to the github repository with git:

```bash
# Check the git status
git status
# Add all files to the next commit
git add .
# Commit the changes with a small and clear message
git commit -m "Adds project structure"
# Push to GitHub (after the first push, you just use `git push`)
git push -u origin main
# Check the git status again
git status
```

**Tip**: Go to GitHub and see how your code is now backed up. If you make changes you don't like, you can always revert the code base to a previous commit. And if you want to do very experimental changes without destroying your main code, you can create new branches via `git switch -c new-branch-name` but this is beyond this tutorial.

`git status` is quite nice for checking which files have changed since the previous commit.You can also use `git diff` to see the actual code changes.

If you prefer not to do git in the command line, there are desktop applications for it as well. You can actually do it right here in VS Code (ask Codex or Google). Ludvig uses the `GitKraken` application.

---

**Intermezzo**: Where the previous steps were quite manual in nature, you can now start getting the agent to do most of the work.

---

## Project specifications

It's now time to describe the product you want implemented. If you just have a vague idea, you can chat with codex in the sidebar about how to make it more specific. The most important thing for working with agents is to provide **CONTEXT**. It should be as clear as possible what you want it to do. And, again, it's completely reasonable to have it generate potential specifications based on vague ideas and then iterate on them, until you have a concrete specification.

Specifications are markdown (`.md`) files that goes in `docs/specs/`. In complex projects, you may want a specification per larger feature/command, but it's often fine to start with a single spec.

You can either choose to manually write the initial specification or to have codex generate it based on your conversation and then edit it (correct misunderstandings, add extra context and rules, etc.). This is worth spending some time on, as codex can sometimes write things in vague terms, which later makes it (or later instances of codex!) misunderstand what you actually wanted.

Specs should define the overall goal(s) and sub goals, scope, non-goals, constraints, and acceptance checks. See the `docs/specs/SPEC_TEMPLATE.md` for this.

Once you have a good specification, remember to *commit* it, so you can detect if the agent goes rogue and changes it... In general, it's good to *commit* after each big step and then use `git diff` to see exactly what changes the agents have made.

```bash
# Check what changes has been made since last commit
git diff
# Add all files to the next commit
# NOTE: You can also add just a subset of the files for a commit
git add .
# Commit the changes with a small and clear message
git commit -m "Adds initial specification"
# Push to GitHub
git push
```

## Deep research

Now that you have a specification of the project, ask codex to research the main topics via web search and distill the most important knowledge into markdown reports in `docs/research/`. Specifically ask it to cite all its findings in the report, to reduce hallucinations and make it a more useful read for you. You don't technically need to read it though, it's more to give the agent more context.

You can spend a few prompts on this, so it covers more ground.

After the research steps, talk to codex about how the specifications might be improved based on what it found. Spend some time optimizing the specifications. Then *commit* and move on.

```text
Example prompt
--------------

Based on the specs, please do deep research via web search on all topics and open questions relevant for implementing and optimizng the specs. Please distill the findings into markdown documents in docs/research/ with sources for each statement. Go deep on this, so we have enough context to make optimal choices.
```

## Plans

We're sooo close to the building step! We just need to make a plan first.

Now that we know what the product should be, let's make a plan for the first build phases. Codex is quite good at this, so ask it to turn the specification into a plan+checklist in `docs/plans/`.

```text
Example prompt
--------------

We need a detailed plan for building the product. Please convert the specs to a plan + checklist with goals and sub goals in docs/plans/. Save it as a markdown document so we can track the progress. The steps should be so clear that you can do it without my intervention or constant review. So be very specific up-front, so I can catch any misunderstandings before you start.
```

Once this is done, *commit* the plan. This makes it easy to `git diff` which sub goals it crosses off in the build phase.

## Start building!

Finally! It's time for you to lean back and for the agent to implement! :-)

The VS Code codex extension allows queing prompts, so you can actually just set up a few "keep going" prompts while you play foosball or knit a hat or something.

```text
Example prompt
--------------

Please implement the plan one slice at a time. Everything must be based on the intention in the specs and plans. Don't drift into other ideas. The code should go in src/<project>/. Every piece of logic must be unit tested with mentally derived expectations. Tests go in tests/test_*.py. Keep the plan up-to-date: check off the checklist and add notes about what and how you solved the tasks, so future agents know exactly where we are and what to do next. Keep going for a long time to get as far as possible with the plan.
```

Then you can queue up this prompt 5 times and take a break while it builds. This "loop prompts until finished" is called Ralph loops after Ralph Wiggum. When you come back, ask it to update the plan and give you a progress report. Then check the `git diff` to see what it changed.

### Run tests

If you want to run the unit tests, you can do so with `uv run pytest`. If they fail, talk to codex about whether it's because there are bugs or unimplemented things in the code or because the tests are wrong. The point of tests is to find bad code. So it's not necessarily a good sign if no tests fail, as that sometimes means codex just wrote the tests to fit the implementation instead of your intentions (big difference!).

**Tip**: In some projects, it might be beneficial to tell codex *never to run the tests* but only rely on mental derivation. Then **you** run the tests manually and tell it to find bugs and test flaws *mentally* based on just the failing test's name. If you give it the actual outcome, it often cheaps out and just replaces the expectations in the test instead of finding the code bugs.

## Demo

You should occasionally check whether your product is on the right track.

If you are building an app or website, have codex guide you on how to build and run it.

If you are building a command line tool, check whether it runs, etc.

## Feedback loop for continued building

You made it through the initial spec+plan+build phase. Nice! But perhaps your product isn't quite done yet? Or you've become more ambitious? This is a good time to go back to the specs+planning phase. Add the new parts you want and make a good plan for the next build phase. Then build and test. Or have it do some more research to get more ideas based on external work. 

## Final tips

After a day of building, the codex model can become quite confused and start making maaany errors. While you can definitely yell at it, it's often better to start a new instance. But before you do so, have the old instance update the plans etc. and perhaps write a "hand-over document". This way, the new instance starts with a better and more up-to-date context.

Good work today!