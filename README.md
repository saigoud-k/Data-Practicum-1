# Data-Practicum-1

# Data-Driven Traffic Safety: Identifying High-Crash-Concentration Locations and Conditions in Colorado

## Project Overview

This project analyzes Colorado crash data from the Colorado Department of Transportation (CDOT) to identify geographic concentrations of reported crashes, examine temporal and environmental patterns, and evaluate machine learning models for distinguishing crashes involving injuries or fatalities.

The goal is to provide transportation-safety stakeholders with evidence-based starting points for prioritizing further safety investigations.

## Research Question

Where are reported crashes concentrated in Colorado, what patterns appear across time and observed crash conditions, and how effectively can machine learning models distinguish crashes involving an injury or fatality?

## Objectives

- Identify geographic areas with high concentrations of reported crashes.
- Examine crash counts by county, hour of day, weather, road surface, and lighting conditions.
- Develop a binary outcome indicating whether a crash involved at least one injury or fatality.
- Compare Logistic Regression and Random Forest using held-out test data.
- Communicate findings, limitations, and recommendations for transportation-safety investigations.

## Data Source

The project uses crash records from the Colorado Department of Transportation (CDOT).

The original dataset contained **95,696 records and 110 columns**. After filtering for valid geographic coordinates, **95,460 records** remained for geographic analysis.

The working dataset includes derived variables used for exploratory analysis and modeling.

**Data source:** [Colorado Department of Transportation](https://www.codot.gov/)

Consult the official source for dataset access, documentation, and applicable data-use conditions. The original dataset is not included in this repository; obtain it from the appropriate official source before reproducing the analysis.

## Methodology

### 1. Data Preparation

The analysis includes examining the available variables, preparing crash records, checking geographic coordinates, and creating derived fields for analysis.

The binary target variable, `Any Injury or Fatality`, is defined as:

- **True:** At least one person was reported injured or killed.
- **False:** No injuries or fatalities were reported.

The target contained 25,455 positive records (26.6%) and 70,241 negative records (73.4%).

### 2. Exploratory Data Analysis

The analysis examines:

- Geographic concentrations using latitude and longitude.
- Reported crash counts by county.
- Hourly and day-of-week patterns.
- Weather conditions, road surface conditions, and lighting.
- Patterns associated with injury and fatality outcomes.

Geographic bins represent aggregated areas rather than exact intersections.

### 3. Machine Learning

Two classification models were evaluated:

- **Logistic Regression:** A baseline classification model.
- **Random Forest:** An ensemble model combining multiple decision trees.

The models were evaluated using held-out test data and metrics including the Area Under the ROC Curve (AUC), precision, recall, F1-score, and accuracy.

## Key Findings

### Geographic Concentration

The geographic analysis identified concentrated clusters of reported crashes, particularly around the Denver area. The highest-count geographic bin contained 299 reported crashes.

### County Patterns

Denver County recorded 15,933 reported crashes, followed by Adams County with 10,211 and El Paso County with 9,940.

These figures are raw counts and are not adjusted for traffic volume, vehicle miles traveled, or population.

### Temporal Patterns

The highest hourly count occurred at 5 PM, with 7,855 reported crashes. This indicates a concentration of reported crashes during the late afternoon, but does not establish that this hour has the highest crash risk.

### Observed Conditions

Most records involved clear weather, dry road surfaces, and daylight. These conditions were common in the dataset; their high counts do not establish that they are more dangerous than other conditions.

### Model Comparison

| Metric | Logistic Regression | Random Forest |
|---|---:|---:|
| AUC | 0.671 | 0.737 |
| Precision | 0.550 | 0.512 |
| Recall | 0.082 | 0.447 |
| F1-score | 0.142 | 0.477 |
| Accuracy | 0.738 | 0.739 |

Random Forest achieved a higher AUC and recall than Logistic Regression on the held-out test data. The results indicate better discrimination between the two outcome classes, although performance remains imperfect.

## Limitations

- Traffic-exposure data, such as vehicle miles traveled or traffic volume, was not available. Therefore, the analysis cannot establish which locations have the highest crash risk.
- Geographic bins indicate approximate areas, not specific intersections or road segments.
- Observed patterns do not establish causation.
- Some predictors, including driver actions and human contributing factors, may only be known during or after a crash investigation.
- The models should not be interpreted as validated real-time crash prediction or prevention systems.
- Model performance depends on the available data, feature definitions, and evaluation design.

## Recommendations

Transportation-safety agencies should use locations with concentrated reported crashes to prioritize further safety investigations.

Before selecting specific safety interventions, future work should:

1. Incorporate traffic volume or vehicle miles traveled.
2. Add roadway design and infrastructure information.
3. Validate geographic hotspots at the road-segment or intersection level.
4. Separate pre-crash predictors from variables recorded during or after a crash.
5. Evaluate model performance using additional validation and appropriate risk-adjusted measures.

## Repository Structure

```text
Data-Practicum-1/
├── README.md
├── requirements.txt
├── crash.ipynb
├── outputs/
│   ├── README.md
│   ├── FINAL_county_summary.csv
│   ├── FINAL_geographic_hotspots.csv
│   ├── FINAL_model_results.csv
│   ├── FINAL_project_numbers.csv
│   ├── FINAL_QA_evidence.csv
│   └── FINAL_random_forest_feature_importance.csv
└── figures/
    ├── README.md
    ├── presentation_chart_1_geographic_concentration.png
    ├── presentation_chart_2_model_comparison.png
    └── presentation_chart_3_hourly_pattern.png
```

The filenames above describe the intended organization. Files should be included only if they exist in the repository and contain the corresponding final results.

## How to Run the Project

### Prerequisites

- Python 3.10 or a compatible Python version.
- Jupyter Notebook.
- The CDOT crash dataset used in the analysis.

### Installation

Clone the repository:

```bash
git clone https://github.com/saigoud-k/Data-Practicum-1.git
cd Data-Practicum-1
```

Create and activate a virtual environment if desired:

```bash
python -m venv .venv
```

On macOS or Linux:

```bash
source .venv/bin/activate
```

Install the required packages:

```bash
python -m pip install -r requirements.txt
```

Download the dataset from the appropriate official source and follow the file path or loading instructions documented in the notebook. Then launch Jupyter:

```bash
jupyter notebook
```

Open `crash.ipynb` and run the notebook cells in order. Exact data paths and package versions should be confirmed against the notebook before reproducing the analysis.

## Conclusion

This project demonstrates how exploratory data analysis and machine learning can help identify patterns in reported traffic crashes. The results support using geographic concentrations to prioritize further investigation, while emphasizing that traffic exposure, roadway context, and careful validation are necessary before making conclusions about crash risk or selecting interventions.

## Author

**Sai Goud Koyyala**

MSDS Data Practicum

Project: Data-Driven Traffic Safety in Colorado
