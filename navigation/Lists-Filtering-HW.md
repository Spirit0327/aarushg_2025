---
layout: page
title: Lists and Filtering HW Aarush Gowda Code Snippets
description: Homework submission for Lists and Filtering using Python lists and Pandas.
permalink: /lists/
---

# Lists and Filtering Homework Submission

**Student:** Aarush Gowda  
**Email:** gowda.aarush@gmail.com

---

## Multiple Choice Questions

1. **What is the primary difference between a Python list and a Pandas Series?**  
   **Answer:** B – *Pandas Series have labeled indices, while lists use integer positions.*

2. **Which of the following creates a DataFrame in Pandas?**  
   **Answer:** C – *`df = pd.DataFrame({'Name': ['Alice'], 'Score': [95]})`*

3. **What will `df.shape[0]` return when `df` is a DataFrame?**  
   **Answer:** B – *It returns the number of rows.*

4. **Which operation would you use to remove the value 3 from a Pandas Series?**  
   **Answer:** B – *`series = series[series != 3]` filters out values equal to 3.*

---

## Popcorn Hacks

### Popcorn Hack 1: Find Students with Scores in a Range

The function below filters a DataFrame to return only those rows where the student's "Score" is within a specified range (inclusive).

```python
def find_students_in_range(df, min_score, max_score):
    """
    Returns rows from df where the 'Score' column is between min_score and max_score (inclusive).
    Assumes df has a column named 'Score'.
    """
    return df[(df['Score'] >= min_score) & (df['Score'] <= max_score)]

# Example usage:
import pandas as pd
student_data = pd.DataFrame({
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Emma'],
    'Score': [95, 88, 76, 92, 84],
    'Grade': ['A', 'B', 'C', 'A', 'B']
})
print("Students with scores between 80 and 90:")
print(find_students_in_range(student_data, 80, 90))
```
### Popcorn Hack 2:
```python
def add_letter_grades(df):
    """
    Adds a 'Letter' column to the DataFrame based on the 'Score' values.
    Grading scale: A: 90-100, B: 80-89, C: 70-79, D: 60-69, F: below 60.
    Returns the modified DataFrame.
    """
    def assign_grade(score):
        if score >= 90:
            return 'A'
        elif score >= 80:
            return 'B'
        elif score >= 70:
            return 'C'
        elif score >= 60:
            return 'D'
        else:
            return 'F'
    
    df['Letter'] = df['Score'].apply(assign_grade)
    return df

# Example usage:
student_data = add_letter_grades(student_data)
print("Student Data with Letter Grades:")
print(student_data)
```
### Popcorn Hack 3:
```python
def find_mode(series):
    """
    Returns the most frequent value (mode) from a Pandas Series.
    If there are multiple modes, returns the first one.
    If the Series is empty, returns None.
    """
    mode_values = series.mode()
    if mode_values.empty:
        return None
    else:
        return mode_values[0]

# Example usage:
s = pd.Series([1, 2, 2, 3, 4, 2, 5])
print("The mode of the series is:", find_mode(s))
```
### HOMEWORK:
```python
import pandas as pd

# Load the dataset (replace 'data_title.csv' with your actual CSV filename)
fire_data = pd.read_csv('data_title.csv')

# ---- Task 1: Find Fire Incidents with Highest and Lowest Overall Temperature ----
# We assume the dataset has a 'Temperature' column.

highest_temp_incident = fire_data.loc[fire_data['Temperature'].idxmax()]
lowest_temp_incident = fire_data.loc[fire_data['Temperature'].idxmin()]

print("Highest Temperature Incident:")
print(highest_temp_incident)
print("\nLowest Temperature Incident:")
print(lowest_temp_incident)

# ---- Task 2: Calculate Temperature Difference for Each Incident ----
# Assumes columns 'Max_Temperature' and 'Min_Temperature' exist.
fire_data['Temp_Difference'] = fire_data['Max_Temperature'] - fire_data['Min_Temperature']
print("\nTemperature Difference for each fire incident (Incident_ID and Temp_Difference):")
# Assuming there is an 'Incident_ID' column for identification.
print(fire_data[['Incident_ID', 'Temp_Difference']])

# ---- Task 3: Identify Incidents where Temperature Exceeded Overall Average ----
overall_avg_temp = fire_data['Temperature'].mean()
high_temp_incidents = fire_data[fire_data['Temperature'] > overall_avg_temp]
print("\nFire incidents with temperature above overall average (Temperature > {:.2f}):".format(overall_avg_temp))
print(high_temp_incidents)

# ---- Task 4: Group by Vegetation Type and Weather Condition ----
# Calculate average Temperature and Wind Speed for each group.
grouped_stats = fire_data.groupby(['Vegetation_Type', 'Weather_Condition'])[['Temperature', 'Wind_Speed']].mean().reset_index()
print("\nGrouped statistics (Average Temperature and Wind Speed):")
print(grouped_stats)

# ---- Homework Analytical Questions ----

# (a) Correlation between vegetation type and fire intensity.
# (If vegetation type is encoded numerically, for example as 'Vegetation_Type_Code', uncomment the following lines)
# if 'Vegetation_Type_Code' in fire_data.columns:
#     correlation_value = fire_data['Vegetation_Type_Code'].corr(fire_data['Fire_Intensity'])
#     print("\nCorrelation between vegetation type and fire intensity:", correlation_value)

# (b) Which weather condition is associated with the highest average fire intensity?
avg_intensity_by_weather = fire_data.groupby('Weather_Condition')['Fire_Intensity'].mean()
highest_intensity_weather = avg_intensity_by_weather.idxmax()
print("\nWeather condition with highest average fire intensity:", highest_intensity_weather)

# (c) What percentage of fire incidents recorded temperatures above 100°F?
num_high_temp = len(fire_data[fire_data['Temperature'] > 100])
total_incidents = len(fire_data)
percentage_high_temp = (num_high_temp / total_incidents) * 100
print("\nPercentage of fire incidents with temperature above 100°F: {:.2f}%".format(percentage_high_temp))
```