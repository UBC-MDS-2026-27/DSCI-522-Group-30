# California Housing Price Analysis

## Authors

Lise Gong, Delaney Woods, Twinkle Francis (DSCI 522 Group 30)

## Summary

This project investigates California housing prices using housing-related variables from the California Housing dataset. The analysis explores the relationship between median income, bedrooms per household, and ocean proximity, to better understand which factors are associated with housing prices and to predict median house value.

Our selected Ridge regression model achieved a test RMSE of approximately \$72,900, about 36% lower than a mean baseline. Median income and ocean proximity were the most informative predictors, while the dataset's cap on house values at about \$500,000 limits predictions for the most expensive districts.

## Data Sources

The California Housing dataset was originally obtained from Kaggle, uploaded by Cam Nugent under the title California Housing Prices.

The dataset contains information from the 1990 California census and was originally featured in Aurélien Géron's book Hands-On Machine Learning with Scikit-Learn and TensorFlow.

For reproducibility, the dataset is downloaded programmatically from Géron's Hands-On Machine Learning GitHub repository. The download code saves the CSV file to data/raw/housing.csv when the Quarto analysis is rendered. The raw dataset does not need to be manually downloaded or committed to the repository.

### Setup

1. Clone this repository:

```bash
git clone https://github.com/UBC-MDS-2026-27/DSCI-522-Group-30.git
```

2. Navigate into the project directory:

```bash
cd DSCI-522-Group-30
```

3. Install the project dependencies:

```bash
uv sync
```

4. Ensure Quarto is installed and render the analysis:

```bash
uv run quarto render analysis/california-housing-prediction.qmd
```

Rendering runs the full analysis from scratch: it downloads the raw data from Géron's GitHub repository (so you need an internet connection) and overwrites the files in `data/processed/`. The rendered report is written to `analysis/california-housing-prediction.html`.

## Dependencies

Project dependencies are managed through pyproject.toml and uv.lock.

## Required software:

- Python (version 3.14 or higher)
- uv (version: 0.12.7)
- Quarto (version: 1.10.18)

Python package dependencies are listed in pyproject.toml, with exact versions recorded in uv.lock.

## AI Use Statement

Our team used generative AI tools (ChatGPT and Claude) to help format documentation, debug Git and environment setup issues, and draft parts of the analysis code and report text. All AI-assisted contributions were reviewed, tested and edited by team members, who take full responsibility for the content of this repository. AI use is also disclosed in the relevant pull requests.

## Report
The rendered project report can be found here:

[HTML]() or [PDF]() 

## License
The project report is licensed under the Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International ([CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/)) license.

The software code is licensed under the MIT License.

See [LICENSE.md](https://github.com/UBC-MDS-2026-27/DSCI-522-Group-30/blob/main/LICENSE.md) for the full license information.