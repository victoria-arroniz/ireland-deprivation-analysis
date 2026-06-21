# Ireland Deprivation Index — Multivariate Analysis

Multivariate statistical analysis of socioeconomic inequality across Irish electoral districts, using dimensionality reduction and clustering to uncover spatial deprivation patterns from the 2022 Census.

## Context

MSc in Statistics & Data Science, University College Dublin — Multivariate Analysis module. The analysis uses the [Pobal HP Deprivation Index 2022](https://www.pobal.ie/research-analysis/open-data/), a publicly available dataset derived from the Irish Census of Population, covering 1,229 electoral districts and 13 socioeconomic variables.

## What it does

1. **Data preparation** — random sample of 1,000 districts (reproducible via `set.seed`); identification and treatment of missing values and empty strings; outlier assessment.
2. **Exploratory analysis** — distribution plots and correlation structure of socioeconomic covariates (education, unemployment, housing tenure, household composition, overcrowding).
3. **Dimensionality reduction** — Principal Component Analysis (PCA) to identify the main axes of socioeconomic variation and reduce multicollinearity before clustering.
4. **Clustering** — hierarchical and k-means methods applied to the PCA-transformed data; cluster profiles interpreted against the deprivation index labels (Extremely Disadvantaged → Affluent).
5. **Discrimination** — SVM and PLS-DA used to assess how well socioeconomic variables discriminate between deprivation categories.

## Tech stack

| Layer | Tools |
|---|---|
| Language | R (Quarto document) |
| Analysis | `tidyverse`, `MASS`, `cluster`, `pls`, `e1071` |
| Visualisation | `corrplot`, `dendextend` |
| Reproducibility | Quarto PDF report |

## Key results

- The first two principal components capture the dominant gradient between affluent and deprived districts, primarily driven by education level (`EDHIGH`, `EDLOW`), employment category (`HLPROF`, `LCLASS`) and unemployment rates.
- Clustering recovers deprivation groups broadly consistent with the Pobal index labels, validating the unsupervised structure of the data.
- Strong negative correlation between third-level education and unemployment; local authority renting (`LARENT`) is the variable most associated with extreme deprivation.

## Data

Data available publicly from [Pobal](https://www.pobal.ie/research-analysis/open-data/). Download `pobal_di_2022.csv` and place it in `data/` before rendering the Quarto document.
