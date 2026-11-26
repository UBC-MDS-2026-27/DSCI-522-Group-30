# Contributing to DSCI-522-Group-30

Thank you for your interest in contributing to our project! This document explains how to report problems, suggest changes and submit your own work. Please read it before opening an issue or a pull request.

All contributors are expected to follow our [Code of Conduct](CODE_OF_CONDUCT.md)


## Ways to contribute

- Report a bug or an error in the analysis
- Suggest an improvement to the code, the report or the documentation
- Fix a typo, a broken link or unclear wording
- Submit a change to the code or the report through a pull request

### Reporting a bug

If something does not work (for example, the Docker container does not start, the analysis does not render, or a figure looks wrong), please open an issue and include:

- a short, descriptive title
- the steps you followed, starting from cloning the repository
- what you expected to happen, and what happened instead
- any error messages, copied in full
- your operating system (e.g. macOS, Windows)

Before opening a new issue, please check the existing issues to see if the problem has already been reported.

## Submitting your work

We use the GitHub flow workflow. No one pushes directly to `main`.

1.  **Open or claim an issue.** Every change should be linked to an issue. Assign the issue to yourself so others know you are working on it.

2.  **Set up the environment.** Follow the instructions in the [README](README.md) for the initial SSH-key and Docker setup. Do not install the project dependencies in a local `.venv`.

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

5.  **Render the report inside the Docker container before pushing.** 

    ```bash
    docker compose run --rm analysis-env uv run quarto render analysis/california-housing-prediction.qmd
    ```

Check that the report renders successfully. Commit only the files required for your change and do not add unnecessary generated files.

6. **Open a pull request and wait for it to be reviewed and merged.**

In the pull request description, briefly explain what you changed, why, and how to test it. Include `Closes #<issue number>` so the issue closes automatically when the pull request is merged. This only works in the description, not in a comment.

7.  **Request a review.** At least one other team member must review and approve every pull request before it is merged. Within the team, we follow a review rotation, which we update each milestone.

8.  **Respond to feedback.** If the reviewer requests changes, commit the fixes to the same branch. The pull request will update automatically.

9.  **Merge.** Once the pull request is approved, **the author merges it** into `main` and deletes the branch. If `main` has changed since you branched, merge `main` into your branch and re-render before merging.

10. **After the pull request is merged, update your local copy:**

    ```bash
    git switch main
    git pull
    docker compose pull
    ```
    
Issues are closed when their work is merged into `main`, not when the code is written.
   
## Working in the container with Positron

1. **Install [Positron](https://positron.posit.co/download.html) and check Git configuration before starting.**

Positron includes the Remote SSH feature, so no additional extension is required.
Follow the setup instructions in the [README](README.md), then start the container:

Check that Git knows your identity on your computer:

  ```bash
  git config --global user.name
  git config --global user.email
  ```

The email should match the email associated with your GitHub account. If either value is missing, set them with:

  ```bash
  git config --global user.name "Your Name"
  git config --global user.email "you@example.com"
  ```
    
Each time you work on the project:

2. **In a terminal, from the project directory, start the container:**

    ```bash
    docker compose up -d
    ```
    
3. **Check that the container is running:**

    ```bash
    docker compose ps
    ```
    
The service should be listed as `analysis-env`.
    
4. **In Positron:** 

- Open the Command Palette.

Mac: `Cmd+Shift+P`
Windows: `Ctrl+Shift+P`

- Select `Remote SSH: Show Remote Menu`.

- Select `Connect to Host`.

- Enter `root@localhost:2222`.

- Choose `Linux` if Positron asks for the remote platform. If Positron asks whether you trust the host fingerprint, select `Yes` or `continue`.

- Open the `/workspace` folder.

Select `/opt/venv/bin/python` as the Python interpreter. Do not select the local `.venv` interpreter because it belongs to the host computer and may not contain the container’s packages.

- To verify the interpreter, run this in the Python console:

    ```python
    import sys
    print(sys.executable)
    ```
    
It should print: `/opt/venv/bin/python`
The terminal, Python console, and Quarto Render button now run inside the container.
    
5. **When you finish working, close Positron and stop the container from your computer’s terminal:**

    ```bash
    docker compose down
    ```
    
## Troubleshooting Positron connections

1. **If you see REMOTE HOST IDENTIFICATION HAS CHANGED, run this on your computer’s terminal:**

    ```bash
    ssh-keygen -R "[localhost]:2222"
    ```
    
If Positron asks for an SSH password, confirm that an SSH key exists as described in the [README](README.md), then restart the container and try connecting again.
If port 2222 is already in use, contact the project maintainers before changing the port in `docker-compose.yml`, because the Positron connection command must use the same port.
  
2. **Then restart the container and reconnect.**

    ```bash
    docker compose down
    docker compose up -d
    ```
      
## Adding or updating a package

1. **Create a branch before changing the project environment:**

    ```bash
    git switch main
    git pull
    git switch -c add-package-name
    ```
    
2. **Inside the container, add the package with an exact version:**

    ```bash
    uv add package-name==version
    ```

3. **Commit the updated environment files and push the branch:**

    ```bash
    git add pyproject.toml uv.lock
    git commit -m "Add package-name dependency"
    git push -u origin add-package-name
    ```
    
4. **Wait for the new image, then update your branch.**

Pushing the branch makes GitHub Actions build and publish a new Docker image and commit its tag to `docker-compose.yml` on your branch. Once the run in the Actions tab shows a green check, run this on your computer:

  ```bash
  git pull
  docker compose pull
  ```
    
Do not edit the SHA tag in `docker-compose.yml` manually.

5. **Open a pull request and wait for it to be reviewed and merged.**

Open a pull request using the workflow described in the “Submitting your work” section. Wait for review and merge before updating your local `main` branch.
After the pull request is merged, GitHub Actions will again build and publish a new Docker image and update the image tag in `docker-compose.yml`. Do not edit the SHA tag manually.

6. **Update your local copy:**

    ```bash
    git switch main
    git pull
    docker compose pull
    ```
    
## Publishing the report

1. **Before rendering, confirm that the Quarto YAML header includes:**

    ```yaml
    embed-resources: true
    ```

2. **Render the report inside the container using the command in step 5 of the “Submitting your work” section.**

3. **After rendering the report inside the container, copy it to the GitHub Pages directory:**

    ```bash
    cp analysis/california-housing-prediction.html docs/index.html
    touch docs/.nojekyll
    ```

4. **Commit and push the published report through a pull request:**

    ```bash
    git add docs/index.html docs/.nojekyll
    git commit -m "Update published report"
    git push
    ```
    
Open a pull request and wait for it to be reviewed and merged.   
After the pull request is merged, the report is published from the `main` branch using the `/docs` folder.

The published report is available at the [GitHub Pages](https://ubc-mds-2026-27.github.io/DSCI-522-Group-30-California-Housing-Prediction/).

## Reviewing a pull request

When reviewing, please:

- check that the change does what the linked issue describes
- check out the branch, follow the [README](README.md) for the Docker setup, and render the report inside the container. Confirm that the report renders successfully and that no conflict markers, broken links, unnecessary generated files, or secrets were added
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