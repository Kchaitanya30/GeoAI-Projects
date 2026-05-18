# Vehicle Crime Hotspot Risk Map — Baltimore City

An interactive GIS-based machine learning project that predicts auto theft and carjacking hotspot areas across Baltimore City using Random Forest classification.

**[View Live Map](https://YOUR-USERNAME.github.io/baltimore-crime-hotspot-map/)**

---

## What This Project Does

This project builds a spatial risk model for vehicle crime in Baltimore City. Instead of just mapping where crime happened, it predicts which 500m × 500m areas are likely to become future hotspots — similar to how engineers model flood susceptibility.

- **53,264** vehicle crime records (2015–2024)
- **1,022** grid cells covering Baltimore City
- **12** spatial features per grid cell
- **87.5%** model accuracy · **0.952** ROC-AUC

---

## Live Interactive Map

The interactive map lets you:
- Click any grid cell to see its full risk profile
- View hotspot probability, past crime count, and all spatial features
- Toggle between probability map, predicted hotspots, and actual hotspots
- Compare model predictions against ground truth

---

## Files in This Repository

| File | Description |
|------|-------------|
| `index.html` | Interactive Folium map (open in any browser) |
| `baltimore_hotspot_prediction.py` | Full Python analysis script (Google Colab) |
| `grid_predictions.csv` | Grid cells with predictions and all features |
| `cleaned_vehicle_crimes.csv` | Cleaned crime incident data |
| `model_comparison_table.csv` | Model performance metrics |
| `decision_tree_rules.txt` | Printed decision tree IF/THEN rules |
| `plots/` | All matplotlib charts and maps |
| `presentation/` | Final project presentation (.pptx) |

---

## How to Run the Analysis

1. Open [Google Colab](https://colab.research.google.com)
2. Upload `baltimore_hotspot_prediction.py`
3. Run Section 0 (installs packages) then restart the runtime
4. Run all sections in order
5. Download outputs from `/content/outputs/`

---

## Data Sources

| Source | Data | Access |
|--------|------|--------|
| Open Baltimore (ArcGIS API) | BPD Part 1 Crime Data 2015–2024 | Public |
| OpenStreetMap (osmnx) | Road network, intersections, POIs | Open license |
| US Census ACS 2020 | Population density (block groups) | Public |
| Baltimore DHCD (ArcGIS API) | Vacant property locations | Public |

---

## Machine Learning Models

Three models were trained and compared:

| Model | Accuracy | F1 | ROC-AUC |
|-------|----------|-----|---------|
| Logistic Regression | 0.879 | 0.792 | 0.948 |
| Decision Tree | 0.848 | 0.748 | 0.945 |
| **Random Forest** | **0.875** | **0.778** | **0.952** |

**Random Forest** was selected as the final model for highest ROC-AUC and Precision, with hyperparameters tuned using GridSearchCV (5-fold cross-validation).

**Top 3 features by importance:**
1. `past_vehicle_crime_count` — 40.0%
2. `road_density` — 14.6%
3. `intersection_count` — 13.8%

---

## Ethics and Limitations

- This model predicts **area-level risk only** — not where any individual will commit a crime
- Based on reported crimes — areas with lower reporting rates may appear safer than they are
- Features show **association, not causation**
- Intended use: city planning, infrastructure investment, traffic safety decisions
- Must not be used to target or profile individuals or communities

---

## References

- Tobler, W. (1970). A Computer Movie Simulating Urban Growth in the Detroit Region. *Economic Geography*, 46(sup1), 234–240.
- Maryland State Police Vehicle Theft Prevention Council Annual Report (2024)
- Baltimore Police Department Part 1 Crime Data via Open Baltimore

---

*GIS Final Project · Baltimore City, Maryland*
