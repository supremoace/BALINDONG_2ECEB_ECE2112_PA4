# BALINDONG_2ECEB_ECE2112_PA4
## Programming Assignment 4  

This repository contains my solutions for **Experiment 4: Data Wrangling and Data Visualization**.

**Table of Contents**
PA4:

1:

2:

## PA4 - ECE BOARD EXAM PROBLEM

### Data Frame Creation
**Task 1:** Create new DataFrames from the ECE Board Exam dataset based on specific conditions.
1. Load the dataset into Pandas
```python
import pandas as pd  

df = pd.read_excel("board2.xlsx")  
df.head()
```
2. Create DataFrame 'Instru'
    - Condition: Track = Instrumentation, Hometown = Luzon, Electronics > 70
```python
Instru = df.loc[(df['Track']=='Instrumentation') & 
                (df['Hometown']=='Luzon') & 
                (df['Electronics']>70), 
                ['Name', 'GEAS', 'Electronics']]  
Instru
```
3. Create DataFrame 'Mindy'
    - Condition: Female students, Hometown = Mindanao, Average ≥ 55
```python
# Compute average
df['Ave'] = df[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)

Mindy = df.loc[
    (df['Hometown'] == 'Mindanao') & 
    (df['Gender'] == 'Female') & 
    (df['Ave'] >= 55), 
    ['Name', 'Track', 'Electronics', 'Ave']
]  
Mindy
```

### Data Frame Creation
**Task:** Create visualizations to analyze how different features affect the average score.
1. Compare average grades based on track, gender, and hometown.
2. Use the visualization Library (matplotlib) to create bar charts or box plots.
```python
import matplotlib.pyplot as plt  

df.groupby('Track')['Ave'].mean().plot(kind='bar')  
plt.title("Average Grade per Track")  
plt.ylabel("Average Score")  
plt.show()
```
