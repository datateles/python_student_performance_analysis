# **Student Performance Analysis: Descriptive Analytics**
📊 *Analyzing student performance patterns using data visualization and descriptive analytics.*

## **Table of Contents**
1. [Project Overview](#project-overview)
2. [Dataset Description](#dataset-description)
3. [Project Workflow](#project-workflow)
4. [Data Cleaning & Preparation](#data-cleaning--preparation)
5. [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
6. [Study Trends & Performance Analysis](#study-trends--performance-analysis)
7. [Key Findings & Insights](#key-findings--insights)

---

## **1. Project Overview**
This project analyzes student performance using **synthetic data**, applying **descriptive analytics and data visualization** techniques.  
Key variables include:
- **Study hours**
- **Sleep hours**
- **Socioeconomic background**
- **Class attendance**
- **Final grades (target variable)**

The objective is to identify **patterns and insights** that impact student success through visualization techniques.

---

## **2. Dataset Description**
The dataset consists of multiple students with five key attributes:

| Feature | Description |
|---------|------------|
| **Socioeconomic Score** | Normalized score (0-1) indicating socioeconomic background |
| **Study Hours** | Average daily study hours |
| **Sleep Hours** | Average daily sleep hours |
| **Attendance (%)** | Percentage of classes attended |
| **Grades** | Final student performance score (target variable) |

Data was analyzed using **Python (Pandas, NumPy, Seaborn, Matplotlib)**.

### **Load and Preview the Dataset**
```python
import pandas as pd

# Load dataset
df = pd.read_csv("student_performance.csv")

# Display basic info
print(df.info())

# Show first few rows
df.head()
```

---

## **3. Project Workflow**
This project follows a structured **descriptive analytics** workflow:

✅ **Step 1: Data Collection**  
➡ Dataset was loaded from a CSV file.

✅ **Step 2: Data Cleaning & Preparation**  
✔ Checked for missing values.  
✔ Identified **outliers** using boxplots and removed extreme values.  
✔ Standardized numerical features using **z-score normalization**.

✅ **Step 3: Exploratory Data Analysis (EDA)**  
✔ Generated **histograms, scatter plots, and correlation heatmaps**.  
✔ Identified key relationships between study habits, attendance, and grades.  

✅ **Step 4: Trend Analysis & Performance Patterns**  
✔ Investigated **study habits and performance** using box plots and regression analysis.  
✔ Categorized students into **study levels** to analyze trends in academic performance.

---

## **4. Data Cleaning & Preparation**
### **Handling Outliers & Standardization**
```python
import numpy as np
from sklearn.preprocessing import StandardScaler

# Remove outliers using IQR method
def remove_outliers(df, column):
    Q1 = df[column].quantile(0.25)
    Q3 = df[column].quantile(0.75)
    IQR = Q3 - Q1
    lower_bound = Q1 - 1.5 * IQR
    upper_bound = Q3 + 1.5 * IQR
    return df[(df[column] >= lower_bound) & (df[column] <= upper_bound)]

df_cleaned = remove_outliers(df, "Study Hours")
df_cleaned = remove_outliers(df, "Sleep Hours")

# Normalize numerical columns
scaler = StandardScaler()
df_cleaned[["Socioeconomic Score", "Study Hours", "Sleep Hours", "Attendance (%)"]] = scaler.fit_transform(
    df_cleaned[["Socioeconomic Score", "Study Hours", "Sleep Hours", "Attendance (%)"]])

df_cleaned.head()
```

---

## **5. Exploratory Data Analysis (EDA)**
### **Key Visualizations**
- **Grade Distribution Histogram**: Shows how grades are spread across students.
- **Scatter Plots**: Highlight correlations between study hours, attendance, and grades.
- **Box Plots**: Compare performance across different student groups.
- **Violin Plots**: Show distributions of grades based on attendance and study patterns.

```python
import matplotlib.pyplot as plt
import seaborn as sns

# Histogram - Grade Distribution
plt.figure(figsize=(8, 5))
sns.histplot(df_cleaned["Grades"], bins=30, kde=True)
plt.title("Grade Distribution")
plt.show()

# Scatter Plot - Study Hours vs Grades
plt.figure(figsize=(8, 5))
sns.scatterplot(x=df_cleaned["Study Hours"], y=df_cleaned["Grades"])
plt.title("Study Hours vs Grades")
plt.show()

# Scatter Plot - Attendance vs Grades
plt.figure(figsize=(8, 5))
sns.scatterplot(x=df_cleaned["Attendance (%)"], y=df_cleaned["Grades"])
plt.title("Attendance vs Grades")
plt.show()
```

---

## **6. Study Trends & Performance Analysis**
### **Study Habits & Student Performance Trends**
To better analyze the impact of study habits, we categorized students into four **study levels**:

| Study Category | Definition |
|---------------|------------|
| **Low** | Bottom 25% of students by study hours |
| **Medium** | 25-50% study hour range |
| **High** | 50-75% study hour range |
| **Very High** | Top 25% of students by study hours |

#### **Box Plot - Study Category vs Grades**
```python
# Creating a study category
df_cleaned["Study Category"] = pd.qcut(df_cleaned["Study Hours"], q=4, labels=["Low", "Medium", "High", "Very High"])

# Visualizing study category vs grades
plt.figure(figsize=(8, 5))
sns.boxplot(x=df_cleaned["Study Category"], y=df_cleaned["Grades"])
plt.title("Study Category vs Grades")
plt.show()
```

#### **Regression Analysis: Study Hours vs Grades**
```python
# Trend line analysis
plt.figure(figsize=(8, 5))
sns.regplot(x=df_cleaned["Study Hours"], y=df_cleaned["Grades"], scatter_kws={"alpha":0.3})
plt.title("Study Hours vs Grades (Trend Line)")
plt.show()
```

---

## **7. Key Findings & Insights**
### 🔹 **Main Observations**
- Students in the **"Very High"** study category achieve higher grades.
- **Low study hour students** show more variation in grades.
- **A linear correlation exists** between study hours and grades, but extreme study hours don’t always lead to the highest performance.
- **The optimal study range** is between **medium to high study time**.
