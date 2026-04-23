# extinctFD
Detecting functional diversity loss under directional, stabilizing, and disruptive models of nonrandom anthropogenic extinction of species. 

## Overview
This repository contains data and code to detect nonrandom extinction patterns by tracking changes in trait means and variances under directional, stabilizing, and disruptive extinction models.

The framework is applied to the Caribbean lizard genus *Leiocephalus* to evaluate past and predicted-future functional diversity loss.

## Abstract  
Humans alter extinction pressures in ways that favor some species over others, causing nonrandom loss of functional diversity. The three classic models of natural selection within species—directional, stabilizing, and disruptive—are widely used to explain trait evolution, but it remains unclear whether they can also capture human-caused nonrandom functional diversity loss among species. Here we develop a framework to test for nonrandom extinction by tracking how trait means and variances change as species with different functional traits are sequentially lost. Applying this approach to the Caribbean lizard genus Leiocephalus, which has already lost 8 of its 32 species and has 10 more threatened with future extinction, we found that past extinctions were directional with respect to ecomorphological traits, as large-bodied species were disproportionately eliminated, likely due to hunting and introduced predators. In contrast, predicted-future extinctions are best explained by stabilizing processes, with species exhibiting extreme appendage morphologies most at risk and species with intermediate appendage lengths least likely to go extinct in the future. Such generalized lizard ecomorphology may be better adapted to the deforested habitats that dominate Caribbean islands today. Such a shift from directional to stabilizing nonrandom extinction is expected when natural extinction pressures are replaced by anthropogenic pressures that directionally shift trait distributions to new adaptive optima. By linking trait-based extinction sequences to classic evolutionary models, our approach provides a generalizable framework for detecting and comparing nonrandom extinction across traits, clades, and ecosystems.

## Key Features
- Simulation of extinction sequences under multiple models:
  - random
  - directional (large and small)
  - stabilizing
  - disruptive
- Trait-based tracking of:
  - mean shifts
  - variance changes
- Model fitting using RMSE and simulation-based comparison
- Application to empirical ecomorphological data

## Data
The dataset includes:
- Species-level trait data (body size and morphology)
- Extinction timing estimates (past and predicted-future)
- PCA-derived trait axes

Body size (SVL) is available for all species, while additional traits are available for a subset of extant species and one extinct species.

## Methods Summary
Extinction sequences are analyzed by comparing observed changes in trait mean and variance to expectations under simulated extinction models.

Model fit is evaluated using:
- Root-mean-square error (RMSE)
- Euclidean distance between observed and simulated trajectories
- Simulation-based goodness-of-fit comparisons

The framework compares observed extinction trajectories to simulated expectations under five extinction models:

- random
- directional (loss of large values)
- directional (loss of small values)
- stabilizing
- disruptive

For each model, extinction is simulated stepwise and changes in trait mean and variance are tracked through time. Model fit is evaluated using:

- root-mean-square error (RMSE) between observed and expected trajectories
- Euclidean distance between observed and simulated goodness-of-fit summaries
- simulation-based comparison of observed fit relative to the distribution of simulated fits
  
## Repository contents

The repository is organized into three main components:

- `R/`  
  Core functions used to simulate extinction sequences and quantify changes in trait distributions.
  - `rnre.R` — simulate random and nonrandom extinction trajectories
  - `sample_extinction.R`
  - `stepwise_extinction.R`

- `data/`  
  Processed `.rda` objects used in the analyses, including:
  - morphology and body-size data
  - IUCN threat-status data
  - PCA data objects
  - simulated extinction outputs
  - empirical extinction replicate objects

- `vignettes/`  
  Reproducible analysis workflows for data processing and case-study analyses:
  - `vig_00_morphology_clean.Rmd` — morphology cleaning and preparation
  - `vig_011_extinction.Rmd` — body-size extinction analyses
  - `vig_020_mPCA.Rmd` — PCA construction
  - `vig_021_extinction_pca.Rmd` — PCA-based extinction analyses

## Analysis workflow

A typical workflow is:

1. Clean and prepare morphology data  
   `vignettes/vig_00_morphology_clean.Rmd`

2. Construct PCA trait space  
   `vignettes/vig_020_mPCA.Rmd`

3. Analyze body-size extinction patterns  
   `vignettes/vig_011_extinction.Rmd`

4. Analyze multivariate morphological extinction patterns  
   `vignettes/vig_021_extinction_pca.Rmd`

## Data objects

Key data objects in `data/` include:

- `morph.rda` — specimen-level morphology data
- `morph_means.rda` — species-level morphology summaries
- `maxsvl.rda` — species-level maximum SVL data
- `iucn.rda` — IUCN categories and extinction-order information
- `dat_pca_tidy*.rda` — PCA-ready trait datasets under alternative scaling options
- `sim_extinction*.rda` — simulated extinction outputs
- `rep_emp*.rda` and `empirical_extinct_reps*.rda` — empirical extinction replicate objects
- `trait_key.rda` — trait metadata/key


## Reproducibility

The analyses are documented in the vignette files in the order listed above. Each vignette reads processed `.rda` files from the `data/` directory and reproduces the corresponding analysis steps.

Because this repository is organized around vignette workflows rather than a single driver script, users should run the `.Rmd` files directly.

## Citation

If you use these code or data, please cite:

Huron, N. A., Hedges, S. B., and Helmus, M. R. In press. Detecting functional diversity loss under directional, stabilizing, and disruptive models of nonrandom anthropogenic extinction of species. *Oikos*.

Preprint version:

Huron, NA, Hedges, SB, Helmus, MR. 2022. Detecting stabilizing, directional, and disruptive patterns of anthropogenic species loss with general models of nonrandom extinction. bioRxiv. [doi:10.1101/2022.09.11.507476](https://doi.org/10.1101/2022.09.11.507476).

## Keywords
adaptive landscape, anthropogenic impact, statistical methods, Caribbean, herpetology, island biogeography, lizard, Anthropocene, hunting, deforestation, land development, introduced predators, natural selection, nonrandom extinction, functional diversity, Leiocephalus, body size
