# California Housing Price Analysis

## Authors

Lise Gong, Delaney Woods, Twinkle Francis (DSCI 522 Group 30)

## Summary

This project investigates California housing prices using housing-related variables from the California Housing dataset. The analysis explores the relationship between median income, number of bedrooms, and ocean proximity, to better understand which factors are associated with housing prices.

## Data Sources

The California Housing dataset was originally obtained from Kaggle, uploaded by Cam Nugent under the title California Housing Prices.

The dataset contains information from the 1990 California census and was originally featured in Aurélien Géron's book Hands-On Machine Learning with Scikit-Learn and TensorFlow.

For reproducibility, the dataset is downloaded programmatically from Géron's Hands-On Machine Learning GitHub repository. The download code saves the CSV file to data/raw/housing.csv when the Quarto analysis is rendered. The raw dataset does not need to be manually downloaded or committed to the repository.

## How to Run the Analysis

### Setup
1. Clone this repository and navigate into the project directory:
bash
git clone https://github.com/UBC-MDS-2026-27/DSCI-522-Group-30.git
cd DSCI-522-Group-30

2. Navigate into the project directory:
bash
cd DSCI-522-Group-30

3. Install the project dependencies:
bash
uv sync

4. Ensure Quarto is installed and render the analysis:
bash
quarto render analysis/california-housing-prediction.qmd

The dataset will automatically download into data/raw/ during rendering.

## Dependencies

Project dependencies are managed through pyproject.toml and uv.lock.

## Required software:

- Python (version 3.14 or higher)
- uv (version: 0.12.7)
- Quarto (version: 1.10.18)

Python package dependencies are listed in pyproject.toml, with exact versions recorded in uv.lock.

## AI Use Statement
In alignment with our [CONTRIBUTING.md](https://github.com/UBC-MDS-2026-27/DSCI-522-Group-30/blob/main/CONTRIBUTING.md) AI contribution guidelines, generative AI usage is permitted under the following rules:

You are responsible for your contribution. You must understand, test and be able to explain any code or text you submit, whether or not an AI tool helped write it. Disclose AI use. If an AI tool generated or substantially edited part of your contribution, say so in your pull request description, and briefly describe how it was used (e.g. "Used Claude to draft the first version of this section, then edited it"). People, not AI agents, run the workflow. Issues and pull requests must be opened, reviewed and merged by a human contributor. AI agents may not open, approve or merge pull requests on anyone's behalf. Check facts and references. AI tools can produce incorrect code, wrong numbers and references that do not exist. Verify every citation before adding it to the report. Do not share private information. Do not paste personal information or private team discussions into AI tools.

## Report
The rendered project report can be found here:

HTML: TO EDIT
PDF: TO EDIT 

## License
The project report is licensed under the Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International ([CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)) license.

The software code is licensed under the MIT License.

See [LICENSE.md](https://github.com/UBC-MDS-2026-27/DSCI-522-Group-30/blob/main/LICENSE.md) for the full license information.