# Unemployment Analysis in India

## The Problem

Unemployment is not just a number. When people lose jobs — or cannot find one — it affects everything around them. Families struggle, spending goes down, local businesses close, and the economy slows down. If too many people are unemployed at the same time, it creates a chain reaction that is very hard to stop once it starts.

The real danger is not just the current unemployment. The real danger is when a crisis hits — like a pandemic, a recession, or a natural disaster — and we are not prepared for it. We do not know which areas will be hit the hardest, which months are already vulnerable, or how long it will take to recover.

That is the problem this project tries to address.

---

## Why I Built This

My thinking was simple: if a similar crisis happens in the future, we need to know what to expect. But to predict the future, we first have to understand the past.

India went through one of the worst employment crises in recent history during 2020. Millions of people lost their jobs almost overnight. But was 2020 truly an exception, or were there already weak points in the employment situation before that? Are certain months always more vulnerable? Are Rural areas hit differently than Urban areas?

If we can answer these questions by looking at past data, we can be in a much better position the next time something like this happens. We can identify which regions need the most support, when unemployment tends to rise, and what the warning signs look like before things get bad.

That is the story behind this project — not just analysis for the sake of analysis, but analysis that can actually help us prepare.

---

## What This Project Does

This project takes monthly unemployment data from across different states and regions of India and walks through the full data analysis process:

- Understanding what the data looks like and what problems exist in it
- Cleaning and fixing those problems so the analysis is accurate
- Handling extreme values that could distort the results
- Visualizing yearly and monthly trends to find patterns

The goal is to build a clear picture of how unemployment has behaved over time in India — so that in the future, if a crisis hits, we already know the historical baseline and can act faster.

---

## Dataset

**File:** `Unemployment in India.csv`

| Column | Description |
|---|---|
| Date | Month and year of the record |
| Region | State or region in India |
| Area | Rural or Urban |
| Unemployment Rate (%) | Percentage of people without jobs |
| Estimated Employed | Number of employed people |
| Labour Participation Rate (%) | Percentage of people actively in the workforce |

- 768 rows of monthly data across multiple states
- Covers both Rural and Urban breakdowns

---

## Libraries Used

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import plotly.express as px
from scipy import stats
import statsmodels.api as sm
```

---

## Project Workflow

### Step 1 — Import Libraries
Load all the Python libraries needed for data manipulation, analysis, and visualization.

### Step 2 — Load the Dataset
Read the CSV file into a pandas DataFrame using `pd.read_csv()`.

### Step 3 — Explore the Data
Before making any changes, I explored the raw data to understand what I was working with. The dataset had 768 rows and 7 columns. I noticed that column names had leading spaces, and the Date column was stored as plain text instead of a proper datetime format. Both of these needed to be fixed.

### Step 4 — Clean the Data
Raw data almost never comes in a ready-to-use state. I found and fixed five issues:

1. Removed 28 completely empty rows using `dropna(how='all')`
2. Renamed columns to remove the leading spaces that were making them hard to work with
3. Converted the Date column from plain text to proper datetime format using `pd.to_datetime()`
4. Dropped the Frequency column — it said "Monthly" for every single row, so it added no information
5. Converted the Area column to a category type since it only holds two values: Rural and Urban

### Step 5 — Handle Outliers
Some rows had an unemployment rate as high as 76.74%, while the average was around 11.8%. Values like these can heavily distort charts and make trends invisible.

To fix this, I used IQR clipping — a method where values that fall too far above or below the middle range get pulled back to a reasonable boundary, without deleting any rows. After clipping, the maximum unemployment rate came down to 32.73%, which is much more representative for visualization purposes.

### Step 6 — Final Check
One last look at the cleaned dataset to confirm everything was in order before moving to visualizations.

### Step 7 — Yearly Trends
Plotted bar charts to see how unemployment and employment changed year by year. This step makes the COVID-19 impact clearly visible and shows how the job market looked before and after 2020.

### Step 8 — Monthly Trends
Went deeper to check if unemployment follows any seasonal pattern across the 12 months. Some months may consistently have higher unemployment due to agricultural cycles or other seasonal factors. This step helps identify those patterns.

---

## How to Run This Project

1. Clone or download this repository
2. Install the required libraries:
   ```bash
   pip install pandas numpy matplotlib seaborn plotly scipy statsmodels
   ```
3. Place `Unemployment in India.csv` in the same folder as the notebook
4. Open the notebook:
   ```bash
   jupyter notebook Unemployment_Analysis_with_Python.ipynb
   ```
5. Run all cells from top to bottom

---

## Files in This Repository

```
unemployment-analysis-india/
    Unemployment_Analysis_with_Python.ipynb
    Unemployment in India.csv
    README.md
```

---

## What We Can Learn From This

Looking at past unemployment data is not just a history lesson. It is a preparation tool. When we know which regions are historically vulnerable, which months tend to see a rise in unemployment, and how fast recovery happened after past downturns, we can make better decisions in the future.

If a similar crisis hits again — another pandemic, an economic slowdown, or a major disruption in any sector — this kind of historical analysis gives policymakers, researchers, and even businesses a foundation to respond faster and more effectively.

The idea is simple: understand the past, handle the future better.
