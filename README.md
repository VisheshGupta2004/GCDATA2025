# GCDATA2025 — E-commerce Marketing Analytics

Competition project exploring sales and marketing performance for an electronics retailer. The work combines data preparation, exploratory analysis, marketing mix modeling (MMM), budget optimization, and a React dashboard for reviewing business KPIs and model outputs.

> **Competition entry:** This repository contains the analysis and dashboard developed for GCDATA2025. The original competition datasets are not included; see [Data requirements](#data-requirements) before running the notebooks.

## Project highlights

- Cleans customer orders and product data and creates a daily sales dataset.
- Prepares weather data, fills missing values, and calculates temperature degree-day features.
- Builds a monthly dataset by combining sales, media investment, sale calendar, NPS, stock, and weather information.
- Explores sales and marketing drivers and derives KPIs, including GMV, units, marketing ROI (MROI), DPI, SDPI, MSG, SPT, NPS, order delay, and CPA.
- Fits a marketing mix model and produces channel response and budget optimization outputs.
- Includes a React dashboard backed by exported JSON files for viewing summary metrics, channel performance, category revenue, response curves, and budget recommendations.

## Repository layout

```text
.
├── cleaning.ipynb                 # Raw customer, order, and SKU preparation
├── create_monthly_data.ipynb       # Daily-to-monthly dataset assembly
├── weather.ipynb                   # Weather cleaning and feature creation
├── eda.ipynb                       # Exploratory analysis, KPIs, dashboard exports
├── Model.ipynb                     # Marketing mix model and budget optimization
├── requirements.txt                # Python dependencies
└── electromart-dashboard copy/
    └── electromart-dashboard copy/ # React dashboard application and exported JSON
```

## Requirements

- Python 3.9 or later, with Jupyter Notebook or JupyterLab
- Node.js and npm

Install the Python packages from the repository root:

```bash
python -m pip install -r requirements.txt
```

## Run the dashboard

The dashboard project is nested under a directory whose name contains spaces. Run:

```bash
cd "electromart-dashboard copy/electromart-dashboard copy"
npm install
npm start
```

The development server will print its local URL (Create React App defaults to `http://localhost:3000`). The app reads its dashboard data from JSON files under `src/components/src/data/`; those exports are included in the repository, so the dashboard can be explored without running the notebooks.

## Run the analysis notebooks

Run the notebooks from the repository root so their relative paths resolve. Prepare the input files described below, then execute the notebooks in this order:

1. `cleaning.ipynb` — writes `Data/daily_data.csv`.
2. `weather.ipynb` — writes `Data/weather_combined.csv`.
3. `create_monthly_data.ipynb` — combines the daily and weather data with media inputs and writes `Data/monthly_dataset.csv`.
4. `eda.ipynb` — performs EDA and exports KPI/dashboard data.
5. `Model.ipynb` — fits the MMM, optimizes allocations, and exports model results.

`create_monthly_data.ipynb` requires the daily and weather outputs, so run both preparation notebooks before it. The notebooks may write generated files to `Data/`; create that directory if it does not exist.

## Data requirements

The notebooks expect competition source files in a `Raw_Data/` directory at the repository root:

| Expected file                                     | Used by                       |
| ------------------------------------------------- | ----------------------------- |
| `Customers_Orders_Data.csv`                     | `cleaning.ipynb`            |
| `SKU_details.csv`                               | `cleaning.ipynb`            |
| `Canada Holiday List.xlsx`                      | `cleaning.ipynb`            |
| `Weather Data ONTARIO-2023.csv`                 | `weather.ipynb`             |
| `Weather Data ONTARIO-2024.csv`                 | `weather.ipynb`             |
| `Media data-Sale Calendar-NPS Scores_Data.xlsx` | `create_monthly_data.ipynb` |

These source datasets are not present in the repository. Obtain them through the competition materials and place them in `Raw_Data/` before running the full pipeline. The notebooks also produce intermediate files in `Data/`.

## Technology

- **Analysis:** Python, pandas, NumPy, SciPy, scikit-learn, Matplotlib, Seaborn, Plotly
- **Dashboard:** React, Recharts, Tailwind CSS, Lucide React

## License

This project is available under the [MIT License](LICENSE).
