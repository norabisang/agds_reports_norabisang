# Applied Geodata Science: Project Portfolio

**Author:** Nora Bisang

**Course:** Applied Geodata Science (AGDS)

**Acknowledgments:** Code derived from Benjamin Stocker and Fabian Bernhard.

## Project overview
This repository contains two geospatial workflows developed for the AGDS course:

### 1. Phenology Modelling and Spatial Upscaling

* Implementation of a **Growing Degree Day (GDD)** phenology model.
* Calibration using **PhenoCam** data and spatial upscaling via **DAYMET** temperature data.
* Cross-evaluation against the **MODIS MCD12Q2** phenology product.

### 2. Digital Soil Mapping 

* Prediction of waterlogged soils at **100 cm depth**.
* Utilizes **Random Forest** trained on environmental covariates.
* Includes hyperparameter tuning (via `caret`/`ranger`) to optimize model generalization.

---

## Project structure

```text
agds_reports_norabisang/
├── analysis/       # RMarkdown analysis reports
├── data-raw/       # Raw data (immutable) and download scripts
├── data/           # Processed datasets, trained .rds models, and raster outputs
├── R/              # Model and helper functions
├── fig/            # Phenology map
├── vignettes/      # Rendered HTML reports
├── renv.lock       # Dependency management file
└── LICENSE         # Project license
```

---

## Data

### Raw data (`data-raw/`)
Raw data are obtained from external sources and are not modified:

* **Remote Sensing:** PhenoCam (via `phenocamr`), DAYMET temperature data, and MODIS MCD12Q2.
* **Note:** MODIS data requires an [Earthdata login](https://urs.earthdata.nasa.gov/).
* **Soil Data:** `berne_soil_sampling_locations.csv`
* **Covariates:** Raster stack located in `geodata/covariates/`


### Processed data (`data/`)
* **Trained Models:** RF model objects saved as `.rds` files.
* **Spatial Predictions:** `raster_pred_bor.tif` (GeoTIFF format).

---

## Reproducibility

This project uses `{renv}` to ensure a consistent R environment.

1. **Clone the repository** to your local machine.
2. **Open the R Project** (`.Rproj` file).
3. **Restore dependencies** by running the following in the R console:

```r
renv::restore()

```
---

## Key Outputs

* **Maps:** Predictions of waterlogging.
* **Model Stats:** Evaluation of GDD phenology and RF classification accuracy.
* **Visuals:** Statistical comparisons and spatial maps stored in `fig/`.

Rendered HTML reports can be found in the analysis/ directory after knitting.



