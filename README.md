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
│   │   ├── national_boundary/                               # Spatial shapefiles (.shp) for Kenya administrative boundaries
│   │   └── county_boundary/                                 # Spatial shapefiles for Narok County and specific sub-regions
│   │   └── chirpsKenya_monthlySums_1981_2021_AgZnExtent2.nc # NetCDF file containing calculated long-term 40-year monthly precipitation means
│   │   └── nino34raw_2.csv                                  # Nino 3.4 time series indices
│   │   └── IODtimeseries_.csv                               # Indian Ocean Dipole Mode (IOD) time series indices
│   │
│   └── Processed/
│   |   ├── Climatology/
│   |   │   └── KenyaAgroEcoZones_..._chirpsCellsize*.tif    # Sptail layers matching the spatial resolution and extent of CHIRPS rainfall data. These define various agro-climatic zones (E.g., arid, humid) 
│   |
|   |
|   └── Figures/                                             # Output figures are saved here (.png, .tiff)

```

## Notebook Breakdown & Analysis Steps1. 

1. **Monthly Rainfall Compositing and Climatology:**

   File: `Scripts/monthly_rainfallCompositing_plot-Gem.ipynb`
   Purpose: Ingests multi-temporal gridded spatial rasters covering the 1981–2021 temporal domain. Aggregates values into long-term monthly arrays, masks values using administrative vector files.

2. **Wavelet Analytics and Teleconnection Index Coherence:**
   File: `Scripts/waveletData_indiceCorr_Kenya_Narok_20May2026-tempPattern_git.ipynb`
   Purpose: Transforms monthly rainfall arrays into spectral space using Morlet wavelets to extract power spectrums, cross-wavelet power, and phase relationships against macro-climate drivers (such as ENSO and the Indian Ocean Dipole).Key Features: Applies automated zero-padding corrections, visualizes the Cone of Influence (COI), and maps lead-lag vector arrows showing phase angles for statistically significant ($p \le 0.05$) coherence pools.

## Data Source & Citation
### Associated Zenodo Dataset
The data required to run this repository are hosted open-access on Zenodo.

Dataset Title: Data for: Observations of enhanced rainfall variability in Kenya, East Africa

DOI: 

Note: Please ensure the unpacked asset structures map precisely onto the directory layouts documented above to avoid working-directory pathway breaks.

## Manuscript Citation

If you use these scripts or data configurations in your academic work, please cite the primary publication:

Kotikot, S. M., Smithwick, E. A. H., & Greatrex, H. (2024). Observations of enhanced rainfall variability in Kenya, East Africa. Scientific Reports, 14, 12915. DOI: 10.1038/s41598-024-63786-2




