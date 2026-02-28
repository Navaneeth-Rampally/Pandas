Markdown
# 🐼 Pandas Data Analysis Toolkit

Welcome to my Pandas Data Analysis repository! This project serves as a comprehensive guide and reference for essential data manipulation techniques using the Python `pandas` library.

Below is a summary of the core concepts covered in this repository, including definitions and syntax references.

## 📋 Table of Contents
1. [Reading & Inspecting Data](#1-reading--inspecting-data)
2. [Handling Data](#2-handling-data)
3. [Data Transformation & Analysis](#3-data-transformation--analysis)
4. [Advanced Operations](#4-advanced-operations)
5. [Exporting Data](#5-exporting-data)

---

## 1. Reading & Inspecting Data

### Reading Data
Loading data from external sources into a Pandas DataFrame.
```python
import pandas as pd

# Reading a CSV file
df = pd.read_csv('filename.csv')

# Reading an Excel file
df = pd.read_excel('filename.xlsx')
Inspection of Data
Quickly viewing the structure, summary, and integrity of the dataset.

Python
# View top 5 rows
df.head()

# View summary of columns, non-null counts, and data types
df.info()

# Statistical summary of numerical columns
df.describe()

# Check shape (rows, columns)
df.shape
2. Handling Data
Data Selection
Extracting specific rows and columns.

.loc: Label-based selection.

.iloc: Integer index-based selection.

Python
# Select specific column
df['Column_Name']

# Select rows by index (integer position)
df.iloc[0:5] 

# Select rows by label/condition
df.loc[df['Age'] > 25]
Handling Missing Values
Identifying and managing NaN (Not a Number) or null values.

Python
# Check for missing values
df.isnull().sum()

# Drop rows with missing values
df.dropna()

# Fill missing values with a specific value (e.g., 0 or mean)
df.fillna(0)
df['Column'].fillna(df['Column'].mean())
Datatype Conversion
Changing the data type of a series (column) to optimize memory or enable specific operations.

Python
# Convert a column to integer
df['Price'] = df['Price'].astype(int)

# Convert to datetime
df['Date'] = pd.to_datetime(df['Date'])
Removing Duplicates
Identifying and removing duplicate rows to ensure data uniqueness.

Python
# Drop duplicate rows
df.drop_duplicates(inplace=True)

# Check for duplicates
df.duplicated().sum()
3. Data Transformation & Analysis
Sorting Data
Ordering data based on the values of one or more columns.

Python
# Sort by a column in ascending order
df.sort_values(by='Price', ascending=True)

# Sort by multiple columns
df.sort_values(by=['Date', 'Price'], ascending=[True, False])
Value Counts
Counting the frequency of unique values in a column. Great for categorical data.

Python
# Count occurrences of unique values
df['Category'].value_counts()
Grouping Data
Grouping data points based on categories and applying aggregation functions (sum, mean, count).

Python
# Group by 'Category' and calculate mean of 'Price'
df.groupby('Category')['Price'].mean()

# Multiple aggregations
df.groupby('Region').agg({'Sales': 'sum', 'Profit': 'mean'})
Feature Engineering
Creating new columns or modifying existing ones to extract more insight.

Python
# Creating a new column from existing data
df['Total_Cost'] = df['Quantity'] * df['Unit_Price']

# Applying a function to a column
df['Discounted_Price'] = df['Price'].apply(lambda x: x * 0.9)
4. Advanced Operations
Pivot Tables
Reshaping data to summarize it, similar to Excel Pivot Tables.

Python
pivot = pd.pivot_table(
    df, 
    values='Sales', 
    index='Region', 
    columns='Year', 
    aggfunc='sum'
)
Merging Tables
Combining two DataFrames based on a common key (similar to SQL JOINs).

Python
# Inner Join
merged_df = pd.merge(df1, df2, on='User_ID', how='inner')

# Concatenating (Stacking data vertically)
combined_df = pd.concat([df1, df2], axis=0)
5. Exporting Data
Saving the cleaned and transformed DataFrame back to a file.

Python
# Save to CSV (without index numbers)
df.to_csv('cleaned_data.csv', index=False)

# Save to Excel
df.to_excel('report.xlsx', index=False)