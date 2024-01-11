<p align="center">
  <img src="https://earth-chris.github.io/elapid/img/elapid-logo.png" alt="elapid logo"/>
</p>

<p align="center">
  <em>QGIS plugin utilizing Maxent for predictive modelling.</em>
</p>

![GitHub](https://img.shields.io/github/license/earth-chris/elapid)
![PyPI version](https://img.shields.io/pypi/v/elapid)
![Anaconda version](https://anaconda.org/conda-forge/elapid/badges/version.svg)
![PyPI downloads](https://img.shields.io/pypi/dm/elapid)
![GitHub last commit](https://img.shields.io/github/last-commit/earth-chris/elapid)
[![DOI](https://joss.theoj.org/papers/10.21105/joss.04930/status.svg)](https://doi.org/10.21105/joss.04930)

---

**Documentation**: [earth-chris.github.io/elapid](https://earth-chris.github.io/elapid)

**Source code**: [earth-chris/elapid](https://github.com/earth-chris/elapid)

---

## Introduction

This documentation is not designed to be an introduction to QGIS; it gives workflows specific to this plugin.  If you need common operations there is a QGIS resource section or Google.

---

## :seedling: Installation

`pip install elapid` or `conda install -c conda-forge elapid`

Installing `glmnet` is optional, but recommended. This can be done with `pip install elapid[glmnet]` or `conda install -c conda-forge elapid glmnet`. For more support, and for information on why this package is recommended, see [this page](https://elapid.org/install#installing-glmnet).

The `conda` install is recommended for Windows users. While there is a `pip` distribution, you may experience some challenges. The easiest way to overcome them is to use [Windows Subsystem for Linux (WSL)](https://docs.microsoft.com/en-us/windows/wsl/about). Otherwise, see [this page](https://elapid.org/install) for support.

---

## :deciduous_tree: Why use elapid?

The amount and quality of bioegeographic data has increased dramatically over the past decade, as have cloud-based tools for working with it. `elapid` was designed to provide a set of modern, python-based tools for working with species occurrence records and environmental covariates to map different dimensions of a species' niche.

`elapid` supports working with modern geospatial data formats and uses contemporary approaches to training statistical models. It uses `sklearn` conventions to fit and apply models, `rasterio` to handle raster operations, `geopandas` for vector operations, and processes data under the hood with `numpy`.

This makes it easier to do things like fit/apply models to multi-temporal and multi-scale data, fit geographically-weighted models, create ensembles, precisely define background point distributions, and summarize model predictions.

It does the following things reasonably well:

:globe_with_meridians: **Point sampling**

Select random geographic point samples (aka background or pseudoabsence points) within polygons or rasters, handling `nodata` locations, as well as sampling from bias maps (using `elapid.sample_raster()`, `elapid.sample_vector()`, or `elapid.sample_bias_file()`).

:chart_with_upwards_trend: **Vector annotation**

Extract and annotate point data from rasters, creating `GeoDataFrames` with sample locations and their matching covariate values (using `elapid.annotate()`). On-the-fly reprojection, dropping nodata, multi-band inputs and multi-file inputs are all supported.

:bar_chart: **Zonal statistics**

Calculate zonal statistics from multi-band, multi-raster data into a single `GeoDataFrame` from one command (using `elapid.zonal_stats()`).

:bug: **Feature transformations**

Transform covariate data into derivative `features` to expand data dimensionality and improve prediction accuracy (like `elapid.ProductTransformer()`, `elapid.HingeTransformer()`, or the all-in-one `elapid.MaxentFeatureTransformer()`).

:bird: **Species distribution modeling**

Train and apply species distribution models based on annotated point data, configured with sensible defaults (like `elapid.MaxentModel()` and `elapid.NicheEnvelopeModel()`).

:satellite: **Training spatially-aware models**

Compute spatially-explicit sample weights, checkerboard train/test splits, or geographically-clustered cross-validation splits to reduce spatial autocorellation effects (with `elapid.distance_weights()`, `elapid.checkerboard_split()` and `elapid.GeographicKFold()`).

:earth_asia: **Applying models to rasters**

Apply any pixel-based model with a `.predict()` method to raster data to easily create prediction probability maps (like training a `RandomForestClassifier()` and applying with `elapid.apply_model_to_rasters()`).

:cloud: **Cloud-native geo support**

Work with cloud- or web-hosted raster/vector data (on `https://`, `gs://`, `s3://`, etc.) to keep your disk free of temporary files.

Check out some example code snippets and workflows on the [Working with Geospatial Data](https://elapid.org/examples/WorkingWithGeospatialData/) page.

---

:snake: `elapid` requires some effort on the user's part to draw samples and extract covariate data. This is by design.

Selecting background samples, computing sample weights, splitting train/test data, and specifying training parameters are all critical modeling choices that have profound effects on inference and interpretation.

The extra flexibility provided by `elapid` enables more control over the seemingly black-box approach of Maxent, enabling users to better tune and evaluate their models.

---

## Citation

```

Or click "Cite this repository" on [GitHub](https://github.com/Scotsman1973/archaeo_modelling).

---

## Plugin created by

[Andrew Prentice](https://digitalarchaeology.com.au)
