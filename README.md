# India Census 2011 — Insight Lab


## Project overview

India Census 2011 — Insight Lab is an end-to-end **Data Analytics + Machine Learning** project built as a single Jupyter Notebook.

The notebook contains the complete implementation in one file:

- Python data loading and cleaning
- Derived demographic and household metrics
- Exploratory data analysis
- Five visualizations
- Five observations
- Five insights
- Three hypotheses
- Three recommendations
- Random Forest regression
- Model evaluation
- Feature-importance analysis
- Flask backend
- REST API endpoints
- HTML/CSS/JavaScript frontend
- Interactive charts
- State filter
- District explorer
- Interactive district literacy-rate estimation

## Dataset

### Primary dataset source

**Kaggle — India Census 2011**

https://www.kaggle.com/danofer/india-census

The notebook specifically references:

https://www.kaggle.com/datasets/danofer/india-census?select=india-districts-census-2011.csv

The project uses the district-level file:

`india-districts-census-2011.csv`

### Runtime download

The notebook uses a public CSV mirror so the application can retrieve the dataset without requiring Kaggle API credentials:

https://raw.githubusercontent.com/nishusharma1608/India-Census-2011-Analysis/master/india-districts-census-2011.csv

The Kaggle page is the stated dataset source; the GitHub URL is used only as a convenient runtime mirror.

## Why this dataset

The final project applies the analytics techniques taught during the internship to a dataset different from the e-commerce dataset used in the Masterclasses.

The Census file contains district-level population, demographic, literacy, employment and household-amenity information, which supports both descriptive analytics and a regression-based prediction exercise.

## Main analytical questions

The notebook explores:

1. How population is distributed across state aggregates.
2. How aggregate literacy rates differ across states.
3. How sex ratio varies across state aggregates.
4. How household electricity coverage varies.
5. How household internet coverage varies.
6. Whether selected demographic and household indicators can provide a useful model-based estimate of district literacy rate.

## Derived metrics

The notebook calculates:

- `literacy_rate = Literate / Population × 100`
- `female_share`
- `workers_share`
- `urban_share`
- `electricity_pct`
- `internet_pct`
- `computer_pct`
- `lpg_pct`
- `television_pct`
- `telephone_pct`
- `car_pct`
- `motorcycle_pct`
- `sex_ratio = Female / Male × 1000`

## Machine-learning model

The notebook uses a **Random Forest Regressor** to estimate district literacy rate.

### Target

`literacy_rate`

### Model inputs

- `female_share`
- `workers_share`
- `urban_share`
- `electricity_pct`
- `internet_pct`
- `computer_pct`
- `lpg_pct`
- `television_pct`
- `telephone_pct`
- `car_pct`
- `motorcycle_pct`

The target-derived fields `Literate` and `literacy_rate` are not used as model inputs.

### Evaluation

The notebook calculates:

- R²
- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)

It also visualizes Random Forest feature importance.

The model metrics are calculated when the notebook runs against the available dataset; they are intentionally not hard-coded into this README.

## Web application

The same notebook contains a Flask web application.

### Backend API

The Flask backend provides:

- `/api/summary` — overview KPI data
- `/api/states` — state-level summary data
- `/api/districts` — district-level data with state filtering
- `/api/insights` — five analytical insight cards
- `/api/model` — model metrics and feature importance
- `/api/predict` — literacy-rate prediction endpoint
- `/` — frontend dashboard

### Frontend

The frontend is embedded directly inside the notebook's Flask application using `render_template_string()`.

It uses:

- HTML
- CSS
- JavaScript
- Chart.js via CDN

The UI includes:

- KPI cards
- Population chart
- Literacy chart
- Electricity chart
- Internet chart
- Five insight cards
- State selector
- District table
- Prediction form
- Model-quality panel
- Feature-importance chart
- Responsible-use section

## Single-file architecture

```text
India_Census_2011_Insight_Lab_FULL(1).ipynb
│
├── Data loading / cleaning
├── Feature engineering
├── Exploratory analysis
├── Random Forest model
├── Model evaluation
│
└── Flask application
    ├── REST API
    └── HTML/CSS/JavaScript frontend
```

There is no need for separate backend and frontend source files when using the submitted notebook.

## How to run

### Option A — Jupyter Notebook

Install dependencies:

```bash
pip install -r requirements.txt
```

Open the notebook:

```bash
jupyter notebook
```

Then run the cells from top to bottom.

### Option B — Google Colab

1. Upload the `.ipynb` notebook.
2. Run the dependency cell if the environment is missing packages.
3. Run the notebook from top to bottom.
4. The final application cell starts Flask on port `5000`.
5. In a local Jupyter environment, open:

```text
http://127.0.0.1:5000
```

6. In Google Colab, the notebook includes a `google.colab.output` helper to expose the running port when available.

## Output and reproducibility

The notebook downloads the dataset when it is not already present under:

```text
data/india-districts-census-2011.csv
```

The notebook then calculates the descriptive statistics, charts and model metrics from the loaded dataset.

## Masterclass alignment

### Masterclass 2 — AI Discovers the Story

Applied concepts:

- visualization
- observation
- insight
- hypothesis
- recommendation

Implementation:

- five visualizations
- five observations
- five insights
- three hypotheses
- three recommendations

### Masterclass 3 — AI Predicts What Happens Next

Applied concepts:

- predictive modeling
- model evaluation
- prediction output
- feature importance
- analytical action

Implementation:

- Random Forest regression
- R², MAE and RMSE
- literacy-rate estimate
- feature-importance chart
- interactive prediction interface

## Limitations

- Census 2011 is historical data and does not represent current 2026 conditions.
- The data is aggregate district/state information rather than individual-level observations.
- `literacy_rate` is a project-derived metric calculated from Census count fields.
- Model performance depends on the supplied data and the notebook's train/test split.
- Feature importance indicates model behavior; it does not prove causal relationships.
- The prediction panel is an educational analytical feature and should not be used as a stand-alone system for consequential decisions.

## Project deliverables

- `India_Census_2011_Insight_Lab_FULL(1).ipynb` — complete code, backend and frontend
- `requirements.txt` — Python dependencies
- `India_Census_2011_ProjectReport.docx` — project report
- `README.md` — project documentation

## Author

**Name:** Sunnam Mehta

**Program:** B.Tech Computer Science and Engineering (AI/ML)

**Institution:** VIT Bhopal University
