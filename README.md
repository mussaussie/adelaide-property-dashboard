# Adelaide Property Market Explorer

Interactive Streamlit dashboard exploring **414 Adelaide suburbs** with 7 years of property data (Q1 2019 - Q4 2025).

## Features

- **Market Overview** - Top growth suburbs, highest risk alerts, price tiers
- **Year-to-Year Growth** - Annual price trends with CAGR, best/worst year analysis
- **Demographics** - Population, median age, household income, mortgage data (ABS Census 2021)
- **Crime & Safety** - Total crime counts, property vs person crimes, crime rate per 1,000 residents, top offense types
- **Rental & Yield** - Fair vs actual rent, house/unit yields, affordability categories, greediness gap
- **Predictions & Risk** - ML-predicted prices (Ridge Regression), 2026 forecasts, risk scores, investment strategies
- **Cultural Communities** - Indian, Chinese, Vietnamese, Italian, Greek populations with diversity index
- **PDF & DOCX Reports** - Downloadable suburb-level reports

## Data Sources

| Source | Period | Description |
|--------|--------|-------------|
| SA Property Sales | Q1 2019 - Q4 2025 | 28 quarters, 414 suburbs, median prices |
| ABS Census 2021 | 2021 | Demographics, income, rent, household data |
| SA Government Crime | FY 2019-20 to Q1 2025-26 | Crime counts by type and suburb |
| ML Predictions | 2025-2026 | Ridge Regression model (3 scenarios) |

## Tech Stack

- **Frontend**: Streamlit with custom CSS (animated gradients, responsive design)
- **Charts**: Plotly.js (client-side rendering)
- **Maps**: Folium with GeoJSON suburb boundaries
- **Reports**: fpdf2 (PDF), python-docx (DOCX)
- **Data**: pandas, numpy

## Run Locally

```bash
pip install -r requirements.txt
streamlit run app.py
```

## Deployment

Deployed on [Streamlit Community Cloud](https://streamlit.io/cloud).

## Project Structure

```
adelaide-property-dashboard/
├── app.py                          # Main Streamlit application
├── requirements.txt                # Python dependencies
├── adelaide_suburbs.geojson        # Suburb boundary polygons
├── suburb_coordinates.json         # Suburb lat/lng centroids
└── data/
    ├── clean/
    │   ├── master_dataset_by_suburb.csv      # 414 suburbs, 1093 features
    │   └── property_timeseries_2019_2025.csv # Quarterly price history
    ├── predictions/
    │   └── price_predictions_2025_2026.csv   # ML model predictions
    ├── risk_analysis/
    │   └── complete_risk_analysis.csv        # Investment risk scores
    ├── rental/
    │   └── complete_rental_analysis.csv      # Rental yield analysis
    ├── demographics/
    │   └── cultural_demographics.csv         # Cultural community data
    └── suburb_crime_offense_analysis.csv     # Top crime types per suburb
```

## Disclaimer

Demographics and rental data are from **ABS Census 2021** (most recent available). Crime data covers SA Government records through **Q1 2025-26**. Property prices span **Q1 2019 - Q4 2025**. Rental figures are inflation-adjusted estimates. This dashboard is for informational purposes only and does not constitute financial advice.

## Author

**Abdul Mussavir** | February 2026
