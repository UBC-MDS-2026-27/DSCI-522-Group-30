# Contributing to DSCI-522-Group-30

Thank you for your interest in contributing to our project! This document explains how to report problems, suggest changes and submit your own work. Please read it before opening an issue or a pull request.

All contributors are expected to follow our [Code of Conduct](CODE_OF_CONDUCT.md)


## Ways to contribute

- Report a bug or an error in the analysis
- Suggest an improvement to the code, the report or the documentation
- Fix a typo, a broken link or unclear wording
- Submit a change to the code or the report through a pull request

### Reporting a bug

If something does not work (for example, the environment does not install, the analysis does not render, or a figure looks wrong), please open an issue and include:

- a short, descriptive title
- the steps you followed, starting from cloning the repository
- what you expected to happen, and what happened instead
- any error messages, copied in full
- your operating system (e.g. macOS, Windows)

Before opening a new issue, please check the existing issues to see if the problem has already been reported.

## Submitting your work

We use the GitHub flow workflow. No one pushes directly to `main`.

1.  **Open or claim an issue.** Every change should be linked to an issue. Assign the issue to yourself so others know you are working on it.

2.  **Set up the environment.** Follow the instructions in the [README](README.md) to install the project dependencies.

3.  **Create a branch from the latest `main`.** Use a short, descriptive name, such as `add-eda-plot` (not `branch1` or your name):

    ``` bash
    git switch main
    git pull
    git switch -c add-eda-plot
    ```

    Team members create branches directly in this repository. External contributors should fork the repository first.

4.  **Make your changes and commit often.** Keep each branch focused on one piece of work. Commit only the files you changed (`git add <file>`), not rendered HTML or unrelated files. Write commit messages that describe what changed, for example:

    - Good: `Add histogram of median house value to EDA`
    - Not helpful: `update`, `fix stuff`

5.  **Render the report before pushing.** Run `uv run quarto render analysis/california-housing-prediction.qmd` and commit any data files it regenerates, so that committed outputs always match what the code produces.

6.  **Push your branch and open a pull request.**

    ``` bash
    git push -u origin add-eda-plot
    ```

    In the pull request description, briefly explain what you changed, why, and how to test it. Include `Closes #<issue number>` so the issue closes automatically when the pull request is merged. This only works in the description, not in a comment.

7.  **Request a review.** At least one other team member must review and approve every pull request before it is merged. Within the team, we follow a review rotation, which we update each milestone.

8.  **Respond to feedback.** If the reviewer requests changes, commit the fixes to the same branch. The pull request will update automatically.

9.  **Merge.** Once the pull request is approved, **the author merges it** into `main` and deletes the branch. If `main` has changed since you branched, merge `main` into your branch and re-render before merging. Everyone then runs `git pull` on `main` before starting new work.

Issues are closed when their work is merged into `main`, not when the code is written.

## Reviewing a pull request

When reviewing, please:

- check that the change does what the linked issue describes
- check out the branch, run `uv sync`, delete the processed data files and render the report. Then run `git status`: committed data files should be unchanged, which confirms the change is reproducible
- leave specific, constructive comments (e.g. "This link is broken, could you update it?")
- use **Review changes** to approve only when you are satisfied, or request changes if something needs fixing

## Suggesting a change

To suggest a change, open an issue that describes what you would like to change and why. For larger changes, please wait for a team member to respond before starting work, so that effort is not duplicated.

## AI policy

We allow the use of generative AI tools (such as ChatGPT, Claude and GitHub Copilot) when contributing to this project, under the following rules:

- **You are responsible for your contribution.** You must understand, test and be able to explain any code or text you submit, whether or not an AI tool helped write it.
- **Disclose AI use.** If an AI tool generated or substantially edited part of your contribution, say so in your pull request description, and briefly describe how it was used (e.g. "Used Claude to draft the first version of this section, then edited it").
- **People, not AI agents, run the workflow.** Issues and pull requests must be opened, reviewed and merged by a human contributor. AI agents may not open, approve or merge pull requests on anyone's behalf.
- **Check facts and references.** AI tools can produce incorrect code, wrong numbers and references that do not exist. Verify every citation before adding it to the report.
- **Do not share private information.** Do not paste personal information or private team discussions into AI tools.

Contributions that break these rules may be asked to be revised or may not be merged.

## Questions

If you have a question that is not covered here, please open an issue and a team member will respond.