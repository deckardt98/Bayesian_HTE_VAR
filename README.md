# Bayesian_HTE_VAR

R code and data for the Kerala Diabetes Prevention Program (K-DPP) application in **[Hierarchical Bayesian modeling of heterogeneous outcome variance in cluster randomized trials](https://doi.org/10.1177/17407745231222018)** by Guangyu Tong, Jiaqi Tong, Yi Jiang, Denise Esserman, Michael O. Harhay, and Joshua L. Warren (*Clinical Trials*, 2024).

The analysis compares four Bayesian models for continuous outcomes in cluster randomized trials. These models estimate the intervention effect and characterize heterogeneity in outcome variances and intraclass correlations across treatment arms and clusters, including associations with cluster-level covariates.

## Repository contents

| File | Description |
| --- | --- |
| [`analysis.R`](analysis.R) | Main script: prepares the data, fits the four models, and saves the results. |
| [`function.R`](function.R) | Functions for data preparation, JAGS model fitting, posterior summaries, and WAIC calculation. |
| [`kdpp_cleaned.csv`](kdpp_cleaned.csv) | Cleaned K-DPP data used in the application. |

## Requirements

Install R and [JAGS](https://mcmc-jags.sourceforge.io/), then install the R packages:

```r
install.packages(c("rjags", "coda"))
```

## Run the analysis

Download or clone this repository and set the R working directory to the repository folder. Run:

```r
source("analysis.R")
```

Alternatively, run the script from a terminal in the repository folder:

```sh
Rscript analysis.R
```

The default settings in `analysis.R` use three MCMC chains per model, 30,000 burn-in iterations, 300,000 retained draws per chain, and no thinning (`thin = 1`).

## Output

The script writes `table4.csv` to the repository folder, with one row for each of Models 1–4. It contains posterior means, medians, and 95% highest posterior density (HPD) intervals for the intervention effect and variance regression coefficients, together with the widely applicable information criterion (WAIC). Variance regression summaries are reported for Models 3–4; the corresponding entries for Models 1–2 are `NA`.

When run in an R session, the `posterior` object retains the samples from each chain for further analysis and convergence assessment.

## Citation

Tong G, Tong J, Jiang Y, Esserman D, Harhay MO, Warren JL. Hierarchical Bayesian modeling of heterogeneous outcome variance in cluster randomized trials. *Clinical Trials*. 2024;21(4):451–460. [doi:10.1177/17407745231222018](https://doi.org/10.1177/17407745231222018).
