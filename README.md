🦠 COVID-19 Data Analysis with Python

This project performs an Exploratory Data Analysis (EDA) on the COVID-19 pandemic using Python.
It explores how the virus spread across countries and examines possible correlations between infection rates and global happiness factors (GDP, health, and social support).

📘 Overview

The notebook walks through the process of:

Loading and cleaning real-world COVID-19 confirmed case data.

Aggregating cases by country and identifying infection rate patterns.

Merging with World Happiness Report (2019) data.

Analyzing the relationships between infection rates and socioeconomic indicators.

Visualizing trends and insights using Matplotlib and Seaborn.

📂 Files
File	Description
covid19 data analysis notebook.ipynb	Main Jupyter Notebook containing the full workflow, analysis, and plots.
covid19_Confirmed_dataset.csv	COVID-19 global confirmed cases dataset (source: Johns Hopkins University).
2019.csv	World Happiness Report 2019 dataset (source: Kaggle / World Happiness Report).
🧰 Libraries Used

pandas → data loading, cleaning, and manipulation

numpy → numerical computations

matplotlib.pyplot → data visualization

seaborn → statistical visualizations and regression plots

Install them (if not already):

pip install pandas numpy matplotlib seaborn

🧩 Project Workflow
Task 1: Module Import

Basic Python data libraries are imported for analysis and visualization.

import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

Task 2: COVID-19 Data Preparation
🗂️ 2.1 Import Dataset

Read covid19_Confirmed_dataset.csv, containing country-wise cumulative cases from January to April 2020.

🧹 2.2 Data Cleaning

Dropped irrelevant columns like Lat and Long.

📊 2.3 Aggregation

Grouped data by Country/Region to get total confirmed cases per country.

📈 2.4 Visualization

Plotted confirmed cases over time for major countries like China, Italy, and India.

plt.figure(figsize=(10,6))
corona_dataset_aggregated.T["China"].plot(label='China')
corona_dataset_aggregated.T["Italy"].plot(label='Italy')
corona_dataset_aggregated.T["India"].plot(label='India')

Task 3: Infection Rate Analysis
⚙️ 3.1 Derivative Calculation

Computed daily change (first derivative) of confirmed cases per country.

🚨 3.2 Maximum Infection Rate

Calculated each country’s maximum daily increase in cases — the max_infection_rate.

📋 3.3 Data Preparation

Created a new DataFrame with only the max_infection_rate for each country.

Task 4: Integrating Happiness Report
🌍 4.1 Load World Happiness Report (2019)

Read the dataset 2019.csv and dropped unused columns like Overall rank, Score, Generosity, etc.

🧾 4.2 Data Cleaning

Set “Country or region” as index for easier merging.

🔗 4.3 Join Datasets

Merged COVID data with happiness metrics (GDP per capita, Social support, Healthy life expectancy, Freedom to make life choices).

🔢 4.4 Correlation Analysis

Generated a correlation matrix to study relationships:

Variable	Correlation with Max Infection Rate
GDP per capita	0.25
Social support	0.19
Healthy life expectancy	0.29
Freedom to make life choices	0.07
Task 5: Visualization of Results
💰 GDP per capita vs Infection Rate

Examined whether richer countries faced higher infection spikes.

🤝 Social Support vs Infection Rate

Used regression plots to show trend strength and direction.

🩺 Life Expectancy vs Infection Rate

Analyzed how healthcare quality affected infection rates.

🕊️ Freedom to Make Life Choices vs Infection Rate

Observed weaker correlation trends for this factor.

Example plot:

x = data["Healthy life expectancy"]
y = data["max_infection_rate"]
sns.regplot(x=x, y=np.log(y))
plt.title("Healthy Life Expectancy vs Max Infection Rate")

📊 Key Insights

Countries with higher GDP per capita showed slightly higher infection peaks, possibly due to better reporting and testing.

Healthy life expectancy correlated positively with infection rate, indicating developed healthcare systems detected more cases.

Social support and freedom metrics had weaker relationships with infection spread.

India, Italy, and China displayed distinct infection curves, reflecting different pandemic response timelines.

📈 Results Summary
Metric	Insight
Highest infection rate	Spain & Italy (April 2020)
Lowest infection rate	African and island nations
Strongest correlation	GDP per capita ↔ Life expectancy
Weakest correlation	Freedom of choice ↔ Infection rate
🧠 Learnings

Hands-on experience with real-world time-series data cleaning and aggregation.

Use of pandas for group-by and diff() analysis.

Visual storytelling with Matplotlib and Seaborn regression plots.

Understanding of how data correlations don’t always imply causation.

📚 References

Johns Hopkins University COVID-19 Data Repository

World Happiness Report 2019 – Kaggle

Our World in Data – Coronavirus Source Data
