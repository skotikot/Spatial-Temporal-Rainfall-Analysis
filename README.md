# Spatial-Temporal-Rainfall-Analysis
Replication code for for the national and county-level climate trend analysis featured in **Kotikot et al. (2024), Scientific Reports**. 

The codebase processes multi-decadal blended satellite-gauge precipitation products (1981–2021) across Kenya to isolate sub-seasonal anomalies, compute localized monthly climatologies, and map time-frequency patterns of ocean-atmospheric driver teleconnections using Continuous Wavelet Transforms (CWT) and Wavelet Coherence (WCT).

---

## Directory Structure

To ensure the scripts execute correctly, organize your local project root folder (`/`) as follows. The underlying raster grids and time-series arrays must be retrieved from the accompanying **Zenodo Dataset** and unpacked directly into the `/Data` directory.

```tree
.
├── Scripts/
│   ├── monthly_rainfallCompositing_plot-Gem.ipynb  # National grid aggregation, masking, and seasonal compositing pipeline
│   └── waveletData_indiceCorr_Kenya_Narok_20May2026-tempPattern_git.ipynb # Wavelet transform, cross-wavelet power, and climate index coherence engine
│
├── Data/
│   ├── Raw/
│   │   ├── national_boundary/                       # Spatial shapefiles (.shp) for Kenya administrative boundaries
│   │   └── county_boundary/                         # Spatial shapefiles for Narok County and specific sub-regions
│   │
│   └── Processed/
│       ├── Climatology/
│       │   └── monthly_averages_1981_2021.nc        # NetCDF file containing calculated long-term 40-year monthly precipitation means
│       │
│       └── TimeSeries/
│           ├── national_monthly_precip_anom.csv     # Extracted area-weighted national rainfall anomaly records
│           └── narok_seasonal_indices.csv           # Cleaned temporal index arrays matching ENSO, IOD, and local rain timelines
│
└── Outputs/
    └── Figures/                                     # High-resolution publication-quality visual panels (.png, .tiff)
