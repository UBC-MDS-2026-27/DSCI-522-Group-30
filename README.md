# California Housing Price Analysis

## Authors

Lise Gong, Delaney Woods, Twinkle Francis (DSCI 522 Group 30)

## Summary

This project investigates California housing prices using housing-related variables from the California Housing dataset. The analysis explores the relationship between median income, bedrooms per household, and ocean proximity, to better understand which factors are associated with housing prices and to predict median house value.

Our selected Ridge regression model achieved a test RMSE of approximately \$72,900, about 36% lower than a mean baseline. Median income and ocean proximity were the most informative predictors, while the dataset's cap on house values at about \$500,000 limits predictions for the most expensive districts.

## Data Sources

The California Housing dataset was originally obtained from Kaggle, uploaded by Cam Nugent under the title California Housing Prices.

The dataset contains information from the 1990 California census and was originally featured in Aurélien Géron's book Hands-On Machine Learning with Scikit-Learn and TensorFlow.

For reproducibility, the dataset is downloaded programmatically from Géron's Hands-On Machine Learning GitHub repository. The download code saves the CSV file to data/raw/housing.csv when the Quarto analysis is rendered. The raw dataset does not need to be downloaded manually, and a copy is included in `data/raw/` for convenience.

## How to Run the Analysis

### Prerequisites

1. Install Docker Desktop and make sure it is running. An internet connection is required to download the Docker image and dataset.

2. If you do not already have an SSH key, create one before starting Docker:

   ```bash
   ssh-keygen -t ed25519
   ```

Press Enter at every prompt. Without a valid SSH key, Docker may create a folder named `~/.ssh/id_ed25519.pub`, and connecting to the container may fail. If this happens, delete the folder and run the command again.

### Run the analysis

1. Clone the repository and enter the project folder:

   ```bash
   git clone https://github.com/UBC-MDS-2026-27/DSCI-522-Group-30-California-Housing-Prediction.git
   cd DSCI-522-Group-30-California-Housing-Prediction
   ```

2. Download the project image:

   ```bash
   docker compose pull
   ```

3. Render the report from your terminal in the project directory:

   ```bash
   docker compose run --rm analysis-env uv run quarto render analysis/california-housing-prediction.qmd
   ```

The `--rm` option automatically removes the temporary container after rendering finishes.

Rendering runs the analysis inside the Docker container. It downloads the raw data from Géron's GitHub repository, so an internet connection is required, and writes the raw and processed datasets to `data/raw/` and `data/processed/`. The rendered HTML report is created at `analysis/california-housing-prediction.html`; the published copy is stored at `docs/index.html`.

## Report

The rendered report is available on [GitHub Pages](https://ubc-mds-2026-27.github.io/DSCI-522-Group-30-California-Housing-Prediction/).

## Contributing

If you want to change the analysis or contribute to the project, see [CONTRIBUTING.md](CONTRIBUTING.md).

## Dependencies

Project dependencies are installed inside the Docker image using `pyproject.toml` and `uv.lock`. Users do not need to create a local `.venv` or install the Python packages manually.

The Docker image is available on [Docker Hub](https://hub.docker.com/r/lisegong/dsci-522-group-30-california-housing-prediction).

## AI Use Statement

Our team used generative AI tools (ChatGPT and Claude) to help format documentation, debug Git and environment setup issues, and draft parts of the analysis code and report text. All AI-assisted contributions were reviewed, tested and edited by team members, who take full responsibility for the content of this repository. AI use is also disclosed in the relevant pull requests.

Example prompts we used:

- "Why does `uv sync` fail with 'Expected a Python module'?"
- "How do I review a pull request and check that the analysis is reproducible?"
- "How do I add a figure caption in Quarto?"
- "Why is Quarto using the host machine's `.venv` instead of the Python environment inside the Docker container, and how can I force it to use `/opt/venv/bin/python`?"
- "SSH public-key authentication fails when connecting to a Docker container from Windows, even though the key matches `authorized_keys`. Could Docker-mounted file permissions and `sshd`'s `StrictModes` setting cause the problem? What diagnostic test could confirm the cause, and what would be a secure permanent fix?"

## License
The project report is licensed under the Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International ([CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/)) license.

The software code is licensed under the MIT License.

See [LICENSE.md](https://github.com/UBC-MDS-2026-27/DSCI-522-Group-30-California-Housing-Prediction/blob/main/LICENSE.md) for the full license information.
