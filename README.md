# Tropical Cyclone Analysis

An exploratory analysis of tropical cyclones worldwide from 2010 to 2025. We use historical storm tracks to study where and when cyclones occur, compare their intensity across ocean basins, examine relationships between wind speed, pressure, and observed track duration, and group storms with similar characteristics. The final notebook brings these results together in visualizations and a real case study.

## Datasets

- **Storm tracks:** NOAA's [International Best Track Archive for Climate Stewardship (IBTrACS), version 4r01](https://www.ncei.noaa.gov/products/international-best-track-archive).  The processing notebook selects observations dated 2010–2025 and produces `datasets/processed/cyclones_2010_2025.csv`: **100,949 timestamped observations from 1,667 cyclones**. Each cyclone can have many rows along its track.
- **Satellite imagery:** NOAA's [HURSAT-B1 v06 dataset](https://www.ncei.noaa.gov/products/hurricane-satellite-data) supplies the NetCDF observations used for the Hurricane Patricia infrared animation in the final notebook.

The original IBTrACS CSV is not committed to this repository. To rerun the processing notebook, download it from the link above and save it as `datasets/raw/cyclones-since-1980.csv`. The processed CSV is included, so the later notebooks can use it directly.

## Notebooks

| Notebook | What it contains |
| --- | --- |
| [01 — Data processing](01_data_processing.ipynb) | Imports IBTrACS, selects the 2010–2025 observations and analysis variables, checks missing values, and exports the processed CSV. |
| [02 — Data exploration](02_data_exploration.ipynb) | Explores data quality, geographic and seasonal patterns, intensity, movement, and differences between observations and distinct cyclones. |
| [03 — Data analysis](03_data_analysis.ipynb) | Compares intensity across basins and years, and examines how peak wind, minimum pressure, and observed track duration relate. |
| [04 — Data clustering](04_data_clustering.ipynb) | Uses standardized storm characteristics, PCA, K-means, and Mean-Shift to explore possible cyclone profiles. |
| [05 — Data visualization](05_data_visualization.ipynb) | Presents global track and coastal proximity visuals, then follows Hurricane Patricia's track, rapid intensification, and satellite imagery. |

## Project structure

```text
.
├── 01_data_processing.ipynb … 05_data_visualization.ipynb
├── datasets/
│   ├── raw/                    # Original IBTrACS CSV (download separately)
│   ├── processed/              # Analysis-ready 2010–2025 CSV
│   └── HURSAT_PATRICIA/        # Patricia satellite observations (NetCDF)
├── assets/physical_earth/      # Basemap image for visualizations
├── outputs/                    # Patricia infrared animation
├── requirements.txt            # Python dependencies
└── tropical_cyclones.pptx      # Project presentation
```

## Dependencies and use

The Python packages in [`requirements.txt`](requirements.txt) are **NumPy, pandas, SciPy, scikit-learn, Matplotlib, Seaborn, Plotly, GeoPandas, Cartopy, PyArrow, ipykernel, and netCDF4**. They cover data preparation, statistical analysis, clustering, mapping, interactive plots, notebook execution, and satellite file reading.

Install them with `python -m pip install -r requirements.txt`, then open the notebooks in a Jupyter-compatible environment from the repository root. Run them in numbered order if you want to recreate the processed data and all figures.

## Presentation

The project findings are summarized in the [PowerPoint presentation](tropical_cyclones.pptx). The [Patricia infrared animation](outputs/patricia_hursat_ir_2015.gif) is also available separately.

Project done by Fernando Henrique Gavezzotti and Enxhi Lamce.
