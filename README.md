#  Global Fitness & Health Analysis

## Project Overview
End-to-end data analysis of 973 gym members' exercise and health data to uncover 
what drives calorie burn and how training habits differ across experience levels, 
workout types and gender. Data was loaded, inspected, cleaned and analysed in 
Python before being visualised in an interactive Tableau dashboard.

**Tools Used:** Python (pandas, matplotlib) · Tableau Public · GitHub

---

## 📊 Interactive Dashboard
https://public.tableau.com/views/GlobalFitnessHealthAnalysis/Dashboard1?:language=en-GB&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link

---

## Python Process — Step by Step

### 1. Environment Setup
- Installed Python 3.14 and configured Jupyter Notebook inside VS Code
- Installed required libraries via pip: `pandas`, `matplotlib`, `openpyxl`

### 2. Data Loading & First Inspection
```python
df = pd.read_csv('gym_members_exercise_tracking.csv')
print(df.shape)       # 973 rows, 15 columns
print(df.columns)     # inspected all column names
print(df.head())      # viewed first 5 rows
print(df.info())      # checked data types and null values
```
**Findings:**
- 973 rows, 15 columns
- Zero null values across all columns — no rows needed to be dropped
- Numeric columns correctly typed as float64/int64
- Text columns (Gender, Workout_Type) correctly typed as string
- No duplicate or erroneous data types found

### 3. Data Cleaning & Transformation
- Confirmed no missing values using `df.info()` — dataset was clean on import
- Added a new derived column `Experience_Label` to make numeric experience 
  levels human-readable for Tableau:
```python
df['Experience_Label'] = df['Experience_Level'].map(
    {1: 'Beginner', 2: 'Intermediate', 3: 'Expert'})
```
- Exported the cleaned and enriched dataset as `fitness_data_clean.csv` 
  for use in Tableau

### 4. Analysis & Aggregations
Used pandas `groupby()` and `agg()` to calculate:
- Average, min and max calories burned by workout type
- Average calories burned by experience level
- Overall descriptive statistics across age, BMI, session duration and fat percentage

### 5. Data Visualisation (matplotlib)
Created and saved 3 charts as PNG files:
- **Bar chart** — Average calories burned by workout type
- **Scatter plot** — Session duration vs calories burned (coloured by workout type)
- **Bar chart** — Average calories burned by experience level

---

## Key Findings

-  **Session duration is the #1 driver of calories burned** — a strong linear 
  relationship exists regardless of workout type
-  **Experts burn 74% more calories than beginners** — 1,265 vs 726 average calories
-  **Yoga burns nearly as many calories as HIIT** — only 22 calorie difference 
  on average (903 vs 926)
-  **All four workout types perform similarly** when session duration is equal — 
  how long you train matters more than what you do
-  **Females show higher body fat % at similar BMI levels** compared to males — 
  visible in the BMI vs Fat Percentage scatter plot

---

## Files in this Repository

| File | Description |
|---|---|
| `fitness_analysis.ipynb` | Main Python notebook — full analysis end to end |
| `gym_members_exercise_tracking.csv` | Raw dataset (source: Kaggle) |
| `fitness_data_clean.csv` | Cleaned and enriched dataset exported for Tableau |
| `chart1_calories_by_workout.png` | Bar chart — avg calories by workout type |
| `chart2_duration_vs_calories.png` | Scatter plot — session duration vs calories |
| `chart3_calories_by_experience.png` | Bar chart — calories by experience level |

---

## Python Skills Demonstrated

- Setting up a data analysis environment (Python, Jupyter, VS Code)
- Loading CSV data with **pandas**
- Data inspection using `df.shape`, `df.info()`, `df.head()`, `df.describe()`
- Identifying and confirming data quality (nulls, dtypes, duplicates)
- Creating derived columns using `.map()`
- GroupBy aggregations using `.groupby()` and `.agg()`
- Descriptive statistics using `.describe()`
- Data visualisation with **matplotlib** (bar charts, scatter plots)
- Saving chart outputs as PNG files
- Exporting clean data as CSV for BI tools

---

## Dataset
Source: [Gym Members Exercise Dataset — Kaggle](https://www.kaggle.com/datasets/valakhorasani/gym-members-exercise-dataset)  
973 records · 15 columns · No missing values
