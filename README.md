# Asian Elephant Habitat Dashboard: Sri Lanka

**Projected Habitat Change and Protected-Area Gaps for the Asian Elephant (*Elephas maximus*) in Sri Lanka: Ensemble Habitat Suitability Modelling under CMIP6 Climate and Land-Use Scenarios**

An interactive web dashboard for a Spatial Modelling course project at Symbiosis Institute of Geoinformatics. It shows where elephant habitat is in Sri Lanka today, how it may change under future climate and land use, and how much of it lies outside protected areas.

**Live dashboard:** https://elephant-habitat-dashboard.vercel.app

---

## What the dashboard shows

| Section | Contents |
|---|---|
| **Overview** | Key numbers: 42,080 km² suitable habitat (64.4 % of land), final model AUC 0.904 / TSS 0.734, 60 % of suitable habitat outside protected areas |
| **Study Area** | Interactive map of 25 districts shaded by % suitable, GBIF presence boxes, precise records, 568 protected areas and 2,624 national survey squares |
| **Methodology** | Step-by-step workflow from data collection to gap analysis |
| **Habitat Model** | Weighted ensemble of MaxEnt, Random Forest and GLM, plus each model alone and the suitable/unsuitable map |
| **Future Change** | Habitat change under SSP2-4.5 and SSP5-8.5 for 2041–2060 and 2061–2080, agreement among five CMIP6 GCMs, and range-wide climatic suitability |
| **Gap Analysis** | Suitable habitat inside and outside protected areas, today and under SSP5-8.5 (2061–2080), with a district chart |
| **Conclusion** | Main findings and a link to the full report (PDF) |

## Key results

- **Current habitat:** 42,080 km² suitable (64.4 % of land area), mainly in the dry zone of the north, east and north-central regions.
- **Model accuracy:** final ensemble AUC = 0.904, TSS = 0.734, tested on the independent 5 × 5 km national elephant survey.
- **Future change:** a net loss of about 10.6–17.8 % of suitable habitat by 2041–2080, mostly driven by hotter summers.
- **Protection gap:** about 60 % of suitable habitat lies outside protected areas.

## Methods in brief

1. **Occurrences:** GBIF records were cleaned and turned into 75 presence boxes of 0.2°. A separate set of 54 precise records was kept back for checking.
2. **Bias correction:** a recording-effort surface was built from iNaturalist records of other mammals.
3. **Predictors:** 17 layers at 1 km covering climate, terrain, vegetation, water, land use and human pressure (VIF ≤ 5.05).
4. **Models:** MaxEnt, GLM and Random Forest were combined in a weighted ensemble, with nested spatial cross-validation.
5. **Range-wide climate niche:** a climate model was fitted across all 13 elephant range countries.
6. **Future scenarios:** SSP2-4.5 and SSP5-8.5 using five CMIP6 GCMs, with SSP land-use and population change.
7. **Gap analysis:** overlay with 568 WDPA protected areas.

## Data sources

GBIF · WorldClim 2.1 and CMIP6 · SRTM · Sentinel-2 · Esri Land Cover · WorldPop · VIIRS night lights · OpenStreetMap · JRC Global Surface Water · WDPA (Protected Planet) · Fernando et al. (2019) national elephant survey · GADM boundaries.
Basemaps: Esri (World Dark Gray, Light Gray, Topographic, Imagery, Streets, National Geographic).

## Built with

- Static HTML, CSS and JavaScript, so there is no build step
- [Leaflet 1.9.4](https://leafletjs.com/) for the interactive maps
- [Chart.js 4.4.1](https://www.chartjs.org/) for the charts
- Map layers made in Python (rasterio, geopandas), reprojected to Web Mercator and exported as PNG overlays and GeoJSON

## Project structure

```
├── index.html          # the whole dashboard (single page, hash routing)
├── report.pdf          # full project report
├── vercel.json         # Vercel settings
├── data/               # GeoJSON / JSON layers (districts, protected areas, records, survey)
└── img/                # map overlays (PNG) and predictor layouts (JPG)
    └── layouts/
```

## Run locally

```bash
git clone <this-repo-url>
cd elephant-habitat-dashboard
python -m http.server 8000
# open http://localhost:8000
```

Use a local server rather than opening the file directly, because the page loads data files with `fetch`.

## Deploy

The site is fully static. On [Vercel](https://vercel.com), import this repository with the **Framework Preset set to "Other"** and no build command. Each push to `main` deploys again automatically.

## Team

- S. Karthika (25070241045)
- Sohini Chakraborty (25070241061)
- Swapnanil Saha (25070241071)

**Guide:** Prof. (Dr.) Sandipan Das, Symbiosis Institute of Geoinformatics, Pune

---

*Academic course project, Spatial Modelling, Semester III.*
