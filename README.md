# Applied Geodata Science: Project Portfolio

**Author:** Nora Bisang

**Course:** Applied Geodata Science (AGDS)

**Acknowledgments:** Code derived from Benjamin Stocker and Fabian Bernhard. 
ChatGPT was used for error explanation and debugging as well as ReadMe structure provision. 

## Project overview
This repository contains two geospatial workflows developed for the AGDS course:

### 1. Phenology Modelling and Spatial Upscaling

* Implementation of a **Growing Degree Day (GDD)** phenology model.
* Calibration using **PhenoCam** data and spatial upscaling via **DAYMET** temperature data.
* Cross-evaluation against the **MODIS MCD12Q2** phenology product.

### 2. Digital Soil Mapping 

* Prediction of waterlogged soils at **100 cm depth**.
* Utilizes **Random Forest** trained on environmental covariates.
* Includes hyperparameter tuning to optimize model generalization.

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
The raw data is not modified and obtained from external sources.

* **Remote Sensing:** PhenoCam (via `phenocamr`), DAYMET temperature data, and MODIS MCD12Q2.
* **Note:** MODIS data requires an [Earthdata login](https://urs.earthdata.nasa.gov/).
* **Soil Data:** `berne_soil_sampling_locations.csv`
* **Covariates:** Raster stack located in `geodata/covariates/`


### Processed data (`data/`)
* **Trained Models:** RF model objects saved as `.rds` files.
* **Spatial Predictions:** `raster_pred_bor.tif` (GeoTIFF format).

---

## Reproducibility

To reproduce the analysis:

1. Clone the repository.
2. Open the R Project file (`.Rproj`) in RStudio.
3. Install required packages (see list below).
4. Knit the R Markdown files in the `analysis/` directory.

The analysis was created with recent versions of the listed R packages.


### Required R packages

- dplyr
- ggplot2
- terra
- sf
- leaflet
- ranger
- caret
- phenocamr
- appeears
- MODISTools
- tidyterra
- lubridate
- signal
- pROC
- here


---

## Key Outputs

- **Spatial Prediction Maps:** Binary map of soil waterlogging at 100 cm depth.
- **Model Performance Metrics:** Evaluation of Random Forest classification models (accuracy, sensitivity, specificity, balanced accuracy, ROC/AUC).
- **Phenology Model Results:** Calibrated GDD based leaf-out prediction and spatially scaled phenology maps.
- **Figures and Visuals:** Statistical comparisons, ROC curves, and spatial maps.



Rendered HTML versions of the reports are included in the `analysis/` directory.






