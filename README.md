# **Student Performance Analysis: Descriptive Analytics**
📊 *Analyzing student performance patterns using data visualization and descriptive analytics.*

## Table of Contents
[Project Overview](#project-overview)
[Dataset Description](#dataset-description)
[Analysis Steps](#analysis-steps)
[Pyhton Code](#python-code)
[Key Findings](#key-findings)

---

## Project Overview
This project focuses on analyzing student performance patterns using data visualization and descriptive analytics. The dataset used contains information on students' socioeconomic scores, study hours, sleep hours, attendance percentages, and grades. The goal is to uncover insights into how these factors influence student performance.

---

## Dataset Description
The dataset consists of multiple students with five key attributes:

| Feature | Description |
|---------|------------|
| **Socioeconomic Score** | A numerical value indicating socioeconomic background |
| **Study Hours** | The number of hours the student spends studying per day |
| **Sleep Hours** | The number of hours the student sleeps per night |
| **Attendance (%)** | The percentage of classes attended by the student |
| **Grades** | The final grades obtained by the student |

Data was analyzed using **Python (Pandas, NumPy, Seaborn, Matplotlib)**.

---

## Analysis Steps
Data was analyzed using **Python (Pandas, NumPy, Seaborn, Matplotlib)**.

✅ **Step 1: Data Collection**  
➡ Load the dataset and perform an initial inspection to understand its structure and identify any missing values or anomalies.

✅ **Step 2: Descriptive Statistics**  
➡ Calculate basic descriptive statistics to summarize the data.

✅ **Step 3: Data Visualization**  
➡ Create visualizations to explore relationships between variables and identify patterns.  

✅ **Step 4: Correlation Analysis**  
➡ Analyze the correlation between different variables to understand their relationships.

---

## Python Code
### Data Collection
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
```

### Descriptive Statistics
```python
# Descriptive statistics for numerical columns
print(df.describe())
```

### Data Visualization
```python
# Set the aesthetic style of the plots
sns.set(style="whitegrid")

# Distribution of Grades
plt.figure(figsize=(8, 6))
sns.histplot(df['Grades'], kde=True, bins=30)
plt.title('Distribution of Grades')
plt.xlabel('Grades')
plt.ylabel('Frequency')
plt.show()

# Scatter plot of Study Hours vs Grades
plt.figure(figsize=(8, 6))
sns.scatterplot(x='Study Hours', y='Grades', data=df)
plt.title('Study Hours vs Grades')
plt.xlabel('Study Hours')
plt.ylabel('Grades')
plt.show()

# Scatter plot of Sleep Hours vs Grades
plt.figure(figsize=(8, 6))
sns.scatterplot(x='Sleep Hours', y='Grades', data=df)
plt.title('Sleep Hours vs Grades')
plt.xlabel('Sleep Hours')
plt.ylabel('Grades')
plt.show()

# Scatter plot of Attendance (%) vs Grades
plt.figure(figsize=(8, 6))
sns.scatterplot(x='Attendance (%)', y='Grades', data=df)
plt.title('Attendance (%) vs Grades')
plt.xlabel('Attendance (%)')
plt.ylabel('Grades')
plt.show()

# Pairplot to visualize relationships between all numerical variables
sns.pairplot(df)
plt.show()
```

### Correlation Analysis
```python
# Correlation matrix
corr_matrix = df.corr()

# Heatmap of the correlation matrix
plt.figure(figsize=(10, 8))
sns.heatmap(corr_matrix, annot=True, cmap='coolwarm')
plt.title('Correlation Matrix')
plt.show()
```

---

## Key Findings & Insights
### 🔹 **Main Observations**
- There is a positive correlation between Study Hours and Grades, indicating that students who study more tend to perform better.
- Sleep Hours also show a positive correlation with Grades, suggesting that adequate sleep is important for academic performance.
- Attendance (%) has a moderate positive correlation with Grades, highlighting the importance of regular class attendance.
- Socioeconomic Score has a weaker correlation with Grades compared to other factors, but it still plays a role in student performance.
