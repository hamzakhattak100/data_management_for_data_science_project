# data_management_for_data_science_project
# MSA Event Attendance Prediction

## Overview
This final project predicts the attendance number for Rutgers MSA (Muslim Student Association) events using historical event data, social media engagement, and event details. The goal is to determine what features impact attendance and use them to estimate the attendance for future events.

The final model uses engagement (likes, comments, shares) and if there is food as the main predictors.

---

## Dataset
The dataset contains MSA events from the last three school years:
- 2023–2024 
- 2024–2025 
- 2025–2026 

The original event CSV files contain:
- event name
- event type
- date
- attendance

More data was later added through enrichment and SQL integration:
- engagement 
- food (yes/no) 
- location 
- weather 

After preprocessing, the dataset has around 50–60 events.

---

## Data Collection and SQL Integration
The attendance data came from historical Rutgers MSA attendance records. Social media engagement data was manually collected from Rutgers MSA Instagram event posts using likes, comments, and shares.

Historical weather data was added using the event dates from https://www.ncei.noaa.gov/cdo-web/. SQLite was used to add all the original event records with the additional event details before machine learning.

The project used separate CSV files for:
- original event records
- event engagement/location/food data
- final combined dataset

---

## Data Preprocessing
The following steps were performed:
- Added three CSV files into a single dataset 
- Added weather data using event dates from website
- Combined event details using SQL 
- Removed any rows with no engagement values 
- Standardized the names of location for consistency 
- Converted categorical variables using one-hot encoding 
- Chose the most relevant features for modeling 

Final features used:
- engagement 
- food_yes 

---

## Model
The following models were tested:
- Linear Regression 
- Decision Tree Regressor 
- Random Forest Regressor 

The final model chosen was Decision Tree Regressor after comparing the results with the other models.

Train/test split:
- 85% training 
- 15% testing 

---

## Results
Final model performance:
- MAE: ~64.7 
- RMSE: ~91.2 
- R²: ~-0.15 

Example:
- Input: food = yes, engagement = 479 
- Predicted attendance: ~ 309
- Actual attendance: 309 

---

## How to Run (Reproducibility)

1. Install dependencies:

```bash
pip install pandas numpy scikit-learn matplotlib seaborn ipywidgets requests
```

2. Open the notebook:

```text
project.ipynb
```

3. Run all cells from top to bottom 

4. Use the prediction function:

```python
predict_attendance("yes", 479)
```

---

## Project Structure

```text
project/
│── data/
│   ├── msa_events_2023_2024_final.csv
│   ├── msa_events_2024_2025_final.csv
│   ├── msa_events_2025_2026_final.csv
│
│   ├── msa_events_2023_2024_event_food_engagement_location.csv
│   ├── msa_events_2024_2025_event_food_engagement_location.csv
│   ├── msa_events_2025_2026_event_food_engagement_location.csv
│
│   ├── data.csv
│
│── project.ipynb
│── README.md
```

---

## Key Insights
Engagement impacts attendance the most. If there is food, it also improves attendance predictions. Models with fewer features performed better than models with too many features.

---

## Limitations
Small dataset size reduced the accuracy of the model. Missing engagement values reduced the number of usable events. Some factors such as speaker popularity, event marketing, and timing were not included.

---

## Future Work
Collect more data  
Include additional features  
Improve model accuracy  
Test more machine learning models
