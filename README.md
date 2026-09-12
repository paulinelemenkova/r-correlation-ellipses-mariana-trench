# R Correlation Ellipses — Correlogram of Morphometric Factors

An R script that computes a pairwise correlation matrix of morphometric,
bathymetric and geological factors and visualises it as a correlogram of
correlation ellipses. In this encoding each off-diagonal cell is drawn as an
ellipse whose eccentricity and orientation represent the strength and sign of
the corresponding correlation coefficient: a narrow, tilted ellipse marks a
strong positive or negative correlation, while a near-circular shape marks a
weak one. The script is applied to a factor table describing the Mariana Trench.

## Related publication

This script (correlation_ellipses_plotcorr.R) produced figures in:

Lemenkova, P. R Scripting Libraries for Comparative Analysis of the Correlation
Methods to Identify Factors Affecting Mariana Trench Formation. Journal of
Marine Technology and Environment 2018, 2, 35-42.

- DOI (figshare): https://doi.org/10.6084/m9.figshare.7434167
- arXiv:          https://arxiv.org/abs/1812.01099 (physics.geo-ph)
- HAL:            https://hal.archives-ouvertes.fr/hal-01992349
- Zenodo:         https://zenodo.org/record/2145302
- SSRN:           https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3296836
- Journal:        https://jmte.eu/ (ISSN 1844-6116)

## Script

### correlation_ellipses_plotcorr.R
- Reads a factor table (Morphology.csv) and removes incomplete records
  (na.omit, with a per-row missing-value check).
- Computes the pairwise Pearson product-moment correlation matrix with cor().
- Seriates the matrix by ordering variables on the first row (order()), so that
  correlated factors are grouped and block structure becomes visible.
- Builds a diverging colour ramp of 100 shades from the ColorBrewer Spectral
  palette (brewer.pal + colorRampPalette) and maps correlation values onto it.
- Renders the ordered matrix twice with ellipse::plotcorr: once as correlation
  ellipses (outline) and once as a numeric correlogram (numbers = TRUE).

## Methods and algorithms

- Pearson product-moment correlation matrix estimation (cor).
- Correlation-ellipse encoding of a correlation matrix (ellipse package,
  plotcorr): ellipse eccentricity and tilt map to coefficient magnitude and sign.
- Matrix seriation / variable ordering to reveal correlation block structure.
- Diverging colour mapping with a ColorBrewer Spectral ramp.
- Missing-data handling (listwise deletion via na.omit).

## Data

- Morphology.csv: morphometric, bathymetric and geological factors sampled along
  the Mariana Trench (variables in columns, observations in rows).

## Requirements

- R (>= 3.5)
- Packages: ellipse, RColorBrewer (the wider environment is loaded by
  load_packages.R)

Install with:

    install.packages(c("ellipse", "RColorBrewer"))

## Usage

Place Morphology.csv in the working directory and run:

    Rscript correlation_ellipses_plotcorr.R

The script draws the two correlograms to the active graphics device.

## Author and citation

Polina Lemenkova
ORCID: https://orcid.org/0000-0002-5759-1089

If you use this script, please cite:

Lemenkova, P. R Scripting Libraries for Comparative Analysis of the Correlation
Methods to Identify Factors Affecting Mariana Trench Formation. Journal of
Marine Technology and Environment 2018, 2, 35-42.
https://doi.org/10.6084/m9.figshare.7434167

## License

See the LICENSE file in this repository.
