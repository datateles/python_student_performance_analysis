# **Student Performance Analysis: Descriptive Analytics**
📊 *Analyzing student performance patterns using data visualization and descriptive analytics.*

## Overview
This project focuses on analyzing student performance patterns using data visualization and descriptive analytics. The dataset used contains information on students' socioeconomic scores, study hours, sleep hours, attendance percentages, and grades. The goal is to uncover insights into how these factors influence student performance.

## Dataset
The dataset, `student_performance.csv`, includes the following columns:
- **Socioeconomic Score**: A numerical value representing the socioeconomic status of the student.
- **Study Hours**: The number of hours the student spends studying per day.
- **Sleep Hours**: The number of hours the student sleeps per night.
- **Attendance (%)**: The percentage of classes attended by the student.
- **Grades**: The final grades obtained by the student.

## Analysis Steps
1. **Data Loading and Initial Inspection**: Load the dataset and perform an initial inspection to understand its structure and identify any missing values or anomalies.
2. **Descriptive Statistics**: Calculate basic descriptive statistics to summarize the data.
3. **Data Visualization**: Create visualizations to explore relationships between variables and identify patterns.
4. **Correlation Analysis**: Analyze the correlation between different variables to understand their relationships.
5. **Insights and Conclusions**: Summarize the findings and draw conclusions based on the analysis.

## Python Code

### 1. Data Loading and Initial Inspection

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load the dataset
df = pd.read_csv('student_performance.csv')

# Display the first few rows of the dataset
print(df.head())

# Check for missing values
print(df.isnull().sum())

# Basic information about the dataset
print(df.info())
