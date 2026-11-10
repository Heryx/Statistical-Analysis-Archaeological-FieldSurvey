# Suasa 2023 Survey — Statistical Analysis

Jupyter notebook for the statistical analysis of the 2023 field survey at Suasa. It examines how
surveyor, ground visibility and weather conditions relate to the recorded finds (`MAT` and
common ware, `CCom`), on the whole dataset and on a restricted area corresponding to a
hypothesised suburban villa.

## Contents

| File | Description |
|---|---|
| `Suasa_2023_survey_analysis.ipynb` | The analysis notebook (code, comments and methodological notes) |

## What the notebook does

1. Loads the survey points and the polygon of the restricted area (shapefiles) and selects the
   points falling within the polygon.
2. **Surveyor bias**: Shapiro-Wilk test and Kruskal-Wallis test on `MAT` by surveyor.
3. **Visibility and common ware**: Kruskal-Wallis test of `CCom` by visibility level, on the
   whole dataset and on the restricted area, with a Dunn post-hoc test (Bonferroni) for the latter.
4. **Weather and common ware**: Kruskal-Wallis test of `CCom` by weather condition.
5. **Multivariate models**: OLS regression of `dens_CCom` (restricted area) and `dens_MAT`
   (whole dataset) on visibility, weather and surveyor, all treated as categorical variables.
6. Prints a summary of the key statistics.

The notebook states the methodological choices made in this version (categorical coding of
surveyor and visibility, separate analyses for the two spatial subsets, weather as a possible
confounder) in its introduction.

## Requirements

The notebook was developed with Python 3.10 and needs:

- `geopandas` (with `pyogrio` as an alternative reading engine)
- `pandas`, `numpy`
- `matplotlib`, `seaborn`
- `scipy`
- `statsmodels`
- `scikit-posthocs`
- `jupyter`

**[TODO: add the exact package versions, e.g. from `pip freeze`, or a `requirements.txt`.]**

## Data

The notebook expects two shapefiles, whose paths are set in the configuration cell:

- survey points: `SHP/UT_lastunion/UT_union_noduplicate_centroide.shp`
- restricted area polygon: `SHP/UT_lastunion/area_restrizione_indagine_pol.shp`

**[TODO: state where the data are available (repository folder, Zenodo record or DOI) and under
which licence.]**

Field names are those stored in the shapefiles; the notebook includes a table describing them.

## How to run

1. Clone the repository and install the requirements.
2. Place the shapefiles at the paths above, or edit `PATH_POINTS` and `PATH_RESTRICTED_AREA` in
   the configuration cell.
3. Open the notebook and run all cells in order. The last cell of Section 8 collects the key
   results; Section 9 contains two supplementary analyses.

If `fiona` raises `AttributeError: module 'fiona' has no attribute 'path'`, use
`engine="pyogrio"` in `gpd.read_file(...)`, as indicated in the notebook.

## Citation

**[TODO: add the citation once the Zenodo DOI is issued, or add a `CITATION.cff` file.]**

## Licence

**[TODO: state the licence of the code.]**

## Contact

**[TODO: author name, affiliation and ORCID.]**
