# Adelaide Property Decision Dashboard

**[Data Analysis Repo](https://github.com/mussaussie/adelaide-property-market-analysis)**

Presentation-focused Streamlit dashboard exploring **414 Adelaide suburbs** with property data from **Q1 2019 to Q1 2026**. The deployment entry point is `app_presentation.py`.

Dashboard link: https://sapropertyinsights.com/

## Features

- **Overview** - Quick-search suburb rankings, executive snapshot, risk-return landscape
- **Explore Suburb** - Price history, sales count, next-year forecast, risk, rent, crime, and community details
- **Compare Suburbs** - Side-by-side suburb comparison across key investment metrics
- **Opportunity Finder** - Filtered shortlist for growth, yield, risk, and affordability signals
- **Map Lab** - Interactive suburb map with switchable metrics
- **Year-to-Year Growth** - Annual price trends with best/worst year analysis
- **Demographics** - Population, median age, household income, mortgage data (ABS Census 2021)
- **Crime & Safety** - Total crime counts, property vs person crimes, crime rate per 1,000 residents, top offense types
- **Rental & Yield** - Fair vs actual rent, house/unit yields, affordability categories, greediness gap
- **Predictions & Risk** - ML-predicted latest prices (Ridge Regression), next-year forecast values, risk scores, investment strategies
- **Cultural Communities** - Indian, Chinese, Vietnamese, Italian, Greek populations with diversity index
- **PDF & DOCX Reports** - Downloadable suburb-level reports
- **Methodology & Glossary** - Plain-English notes for non-technical users

## Data Sources

| Source | Period | Description |
|--------|--------|-------------|
| SA Property Sales | Q1 2019 - Q1 2026 | 29 quarters, 414 suburbs, median prices and sales counts |
| ABS Census 2021 | 2021 | Demographics, income, rent, household data |
| SA Government Crime | FY 2019-20 to Q2 2025-26 | Crime counts by type and suburb |
| ML Predictions | Latest property snapshot plus next-year forecast | Ridge Regression model (3 scenarios) |

## Latest Data Refresh

Latest copied outputs were refreshed on **23 April 2026** from the analysis project.

- Latest property quarter included: **Q1 2026**
- Latest crime data included: **Q2 2025-26**, covering records through **31 December 2025**
- Main dashboard dataset: `data/clean/master_dataset_by_suburb.csv`
- Property time series: `data/clean/property_timeseries_2019_2025.csv`
- Prediction output: `data/predictions/price_predictions_2025_2026.csv`
- Sales activity fields: `Current_Sales_Count`, `Avg_Sales_Count`, `Total_Sales_Count`, `Market_Liquidity_Category`

Some filenames still contain `2025` or `2025_2026` because the Streamlit app expects those paths. The file contents are the refreshed latest outputs.

Sales count is displayed as dashboard context only. It was tested as a prediction feature in the analysis project, but it slightly reduced model validation performance, so the final Ridge model keeps the stronger no-sales feature set while the dashboard still shows sales volume and liquidity.

## Tech Stack

- **Frontend**: Streamlit with custom CSS and responsive layout
- **Charts**: Plotly.js (client-side rendering)
- **Maps**: Folium with GeoJSON suburb boundaries
- **Reports**: fpdf2 (PDF), python-docx (DOCX)
- **Data**: pandas, numpy

## Run Locally

```bash
pip install -r requirements.txt
streamlit run app_presentation.py
```

For local phone testing on the same Wi-Fi network:

```bash
streamlit run app_presentation.py --server.address 0.0.0.0 --server.port 8502
```

## Railway Deployment

This project is intended to run on Railway as a Python Streamlit service.

Use this Railway start command:

```bash
streamlit run app_presentation.py --server.address 0.0.0.0 --server.port $PORT
```

Recommended Railway scale setting for this dashboard:

- 1 region
- 1 replica
- choose the region closest to the target users

## Project Structure

```
adelaide-property-dashboard/
├── app_presentation.py             # Presentation-focused Streamlit application for deployment
├── app.py                          # Original Streamlit application
├── requirements.txt                # Python dependencies
├── adelaide_suburbs.geojson        # Suburb boundary polygons
├── suburb_coordinates.json         # Suburb lat/lng centroids
└── data/
    ├── clean/
    │   ├── master_dataset_by_suburb.csv      # 414 suburbs, 1102 features incl. sales count
    │   └── property_timeseries_2019_2025.csv # Quarterly price and sales history through Q1 2026
    ├── predictions/
    │   └── price_predictions_2025_2026.csv   # Refreshed ML predictions, forecast, and sales context
    ├── risk_analysis/
    │   └── complete_risk_analysis.csv        # Investment risk scores
    ├── rental/
    │   └── complete_rental_analysis.csv      # Rental yield analysis
    ├── demographics/
    │   └── cultural_demographics.csv         # Cultural community data
    └── suburb_crime_offense_analysis.csv     # Top crime types per suburb through Q2 2025-26
```

## Disclaimer

Demographics and rental data are from **ABS Census 2021** (most recent available). Crime data covers SA Government records through **Q2 2025-26**. Property prices span **Q1 2019 - Q1 2026**. Rental figures are inflation-adjusted estimates. This dashboard is for informational purposes only and does not constitute financial advice.

## Author

**Abdul Mussavir** | February 2026
