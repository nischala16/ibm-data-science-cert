# SpaceX Falcon 9 First Stage Landing Prediction

A comprehensive data science capstone project analyzing SpaceX Falcon 9 launch data to predict first stage landing success using machine learning.

---

## Project Overview

SpaceX advertises Falcon 9 rocket launches at a cost of $62 million, significantly lower than other providers whose costs can exceed $165 million. Much of this cost savings comes from SpaceX's ability to reuse the first stage of its rockets. This project aims to predict whether the Falcon 9 first stage will successfully land, which directly impacts launch cost estimation.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Methodology](#methodology)
- [Data Sources](#data-sources)
- [Key Findings](#key-findings)
- [Technologies Used](#technologies-used)
- [Project Notebooks](#project-notebooks)
- [Results](#results)
- [Conclusions](#conclusions)

---

## Methodology

### 1. Data Collection
Data was gathered from two primary sources:
- **SpaceX REST API** — Open source API providing launch, rocket, core, capsule, launchpad, and landing pad data
- **Wikipedia Web Scraping** — Historical Falcon 9 launch records extracted using BeautifulSoup

### 2. Data Wrangling
Preprocessing performed using pandas and NumPy:
- One-hot encoding of categorical variables
- Column filtering and selection
- Data normalization and standardization
- Handling missing values

### 3. Exploratory Data Analysis (EDA)
- Visualization using Seaborn and Matplotlib
- SQL queries for data exploration
- Feature correlation analysis
- Feature engineering (converting categorical features to dummy values)

### 4. Interactive Visual Analytics
- **Folium** — Geospatial visualization with interactive maps showing launch sites, proximities, and coordinates
- **Plotly Dash** — Interactive dashboard with dropdown filters, pie charts, payload sliders, and scatter plots

### 5. Predictive Modeling
- Train/test split (80/20)
- Hyperparameter tuning using Grid Search
- Model evaluation using Confusion Matrix, F1 Score, and Jaccard Score

**Classification algorithms evaluated:**
- Logistic Regression (LR)
- Support Vector Machine (SVM)
- Decision Tree (DT)
- K-Nearest Neighbors (KNN)

---

## Data Sources

| Source | Description |
|--------|-------------|
| [SpaceX API](https://api.spacexdata.com/v4/launches/past) | REST API for launch, rocket, and landing data |
| [Wikipedia - Falcon 9 Launches](https://en.wikipedia.org/wiki/List_of_Falcon_9_and_Falcon_Heavy_launches) | Historical launch records |

---

## Key Findings

### Launch Site Analysis

| Launch Site | Total Trials | Successful | Failed | Success Rate |
|-------------|--------------|------------|--------|--------------|
| CCAFS SLC-40 | 55 | 33 | 22 | 60% |
| VAFB SLC-4E | 13 | 10 | 3 | 77% |
| KSC LC-39A | 22 | 17 | 5 | 77% |

- **Best performing site:** KSC LC-39A with 76.9% mission success rate
- All launch sites are coastal (Florida or California) for safety and logistics

### Orbit Analysis

- **Best orbits for first stage return:** ES-L1, GEO, HEO, SSO
- **Challenging orbit:** GTO (Geostationary Transfer Orbit) shows lower success rates due to payload demands
- Heavy payloads negatively influence GTO orbit success

### Payload Insights

- Missions with payloads under 4,000 kg tend to have higher success rates
- Total payload transported to space by NASA via SpaceX: **45,596 kg**
- Average payload mass for F9 v1.1 booster: **2,928 kg**

### Historical Trends

- Success rate increased steadily from 2013 to 2020
- First successful ground pad landing: **December 22, 2015**
- Overall mission success: 99 successful vs 1 failed mission

---

## Technologies Used

| Category | Tools |
|----------|-------|
| **Languages** | Python, SQL |
| **Data Processing** | pandas, NumPy |
| **Visualization** | Matplotlib, Seaborn, Plotly |
| **Interactive Maps** | Folium |
| **Dashboards** | Plotly Dash |
| **Web Scraping** | BeautifulSoup, Requests |
| **Machine Learning** | Scikit-learn |
| **API Requests** | Requests library |

---

## Project Notebooks

| Notebook | Description |
|----------|-------------|
| [SpaceX API Data Collection](#) | Data extraction from SpaceX REST API |
| [Web Scraping](#) | Wikipedia data extraction using BeautifulSoup |
| [EDA with Visualization](#) | Exploratory analysis with Seaborn and Matplotlib |
| [EDA with SQL](#) | Data exploration using SQL queries |
| [Interactive Map with Folium](#) | Geospatial visualization of launch sites |
| [Interactive Dashboard with Plotly Dash](#) | Dashboard with filters and visualizations |
| [Machine Learning Prediction](#) | Classification model training and evaluation |

*Note: Replace the `#` links above with your actual GitHub notebook URLs*

---

## Results

### Model Performance Comparison

| Model | Jaccard Score | Performance |
|-------|---------------|-------------|
| Logistic Regression | 0.80 | Best |
| Support Vector Machine | 0.80 | Best |
| K-Nearest Neighbors | 0.80 | Best |
| Decision Tree | < 0.80 | Weakest |

### Best Model Confusion Matrix (LR, SVM, KNN)

|  | Predicted Positive | Predicted Negative |
|--|--------------------|--------------------|
| **Actual Positive** | 12 (TP) | 3 (FN) |
| **Actual Negative** | 0 (FP) | 3 (TN) |

---

## Conclusions

1. **Mission characteristics influence first stage success** — Success varies with orbit type, payload mass, and booster version. Lighter to moderate payloads and orbits such as ES-L1, GEO, HEO, and SSO show higher return success, while GTO missions have notably lower performance.

2. **Launch site selection supports safety and operational efficiency** — All active SpaceX launch sites are coastal, close to transport infrastructure and water for safe ascent and recovery, reducing logistical costs and mitigating risks.

3. **SpaceX performance improved significantly over time** — From 2013 through 2020, first stage return success rate rose steadily, reflecting gains in engineering reliability, mission design, and vehicle reusability.

4. **Predictive modeling confirms success is not random** — Machine learning models achieved competitive performance with a Jaccard score of 0.80, confirming that mission outcomes can be predicted from operational data.

---

## SQL Queries Performed

Key exploratory queries included:
- Unique launch site names
- Records where launch sites begin with 'CCA'
- Total payload mass carried by NASA (CRS) boosters
- First successful ground pad landing date
- Boosters with drone ship success and payload between 4,000–6,000 kg
- Total successful and failed mission outcomes
- Booster versions carrying maximum payload mass
- Failed drone ship landings in 2015
- Landing outcome rankings between 2010-06-04 and 2017-03-20

---

## Author

Built by Nischala Nagisetty

---

## License

This project is for educational purposes as part of a data science capstone.

---

## Acknowledgments

- SpaceX for providing open API access
- Wikipedia contributors for maintaining launch records
- IBM Data Science Professional Certificate program
