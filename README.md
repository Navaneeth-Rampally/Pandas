🐼 Pandas Data Analysis – Complete Practical Guide

A structured repository documenting my hands-on learning and implementation of Pandas, the powerful Python library used for data manipulation and analysis.

This README covers:

**1. Data Reading**

**2. Data Inspection**

**3. Data Handling**

**4. Data Transformation & Analysis**

**5. Pivot Tables**

**6. Merging Tables**

**7. Exporting Datasets**

📌 **What is Pandas?**

Pandas is an open-source Python library built on top of NumPy, designed for fast, flexible, and expressive data analysis.

import pandas as pd

Core Data Structures:

Series → 1D labeled array

DataFrame → 2D labeled tabular data

1️. **Reading Data**- Reading data means loading datasets from external sources (CSV, Excel, JSON, SQL, etc.) into a Pandas DataFrame.

🔹 Syntax
**CSV file**
df = pd.read_csv("data.csv")

**Excel file**
df = pd.read_excel("data.xlsx")

**JSON file**
df = pd.read_json("data.json")

**SQL**
import sqlite3
conn = sqlite3.connect("database.db")
df = pd.read_sql("SELECT * FROM table_name", conn)


2️⃣ **Inspection of Data** - Data inspection helps understand the structure, size, types, and summary statistics of the dataset.

🔹 Syntax
df.head()        # First 5 rows
df.tail()        # Last 5 rows
df.info()        # Data types and null counts
df.describe()    # Statistical summary
df.shape         # (rows, columns)
df.columns       # Column names
df.dtypes        # Data types


3️⃣ **Handling Data**

**3.1 Data Selection**

**Definition**- Selecting specific rows and columns from a dataset.

🔹 **Syntax**

df["column_name"]                  # Select single column
df[["col1", "col2"]]               # Multiple columns
df.loc[0:5, ["col1", "col2"]]      # Label-based selection
df.iloc[0:5, 0:2]                  # Index-based selection

**Conditional filtering**


df[df["age"] > 25]


**3.2 Handling Missing Values**
🔹 **Definition**- Managing null/NaN values in the dataset.

🔹 **Syntax**

df.isnull()            # Detect missing values
df.isnull().sum()      # Count missing values

df.dropna()            # Remove rows with null values
df.fillna(0)           # Replace null values with 0

df["col"].fillna(df["col"].mean(), inplace=True)


**3.3 Datatype Conversion**\

🔹 **Definition** - Changing column data types for correct analysis.

🔹 **Syntax**

df["age"] = df["age"].astype(int)

df["date"] = pd.to_datetime(df["date"])

df["category_col"] = df["category_col"].astype("category")


**3.4 Removing Duplicates**
🔹 **Definition**- Eliminating duplicate rows to maintain data integrity.

🔹 **Syntax**

df.duplicated()             # Check duplicates
df.drop_duplicates()        # Remove duplicates

df.drop_duplicates(subset=["col1"])


4️⃣ **Data Transformation & Analysis**


**4.1 Sorting Data**
🔹 **Definition**- Arranging data in ascending or descending order.

🔹 **Syntax**

df.sort_values("age")                     # Ascending
df.sort_values("age", ascending=False)    # Descending

df.sort_values(["col1", "col2"])


**4.2 Value Counts**
🔹 **Definition**- Counting frequency of unique values.

🔹 **Syntax**

df["gender"].value_counts()
df["gender"].value_counts(normalize=True)  # Percentage


**4.3 Grouping Data (GroupBy)**
🔹 **Definition**- Grouping data based on categories to perform aggregation.

🔹 **Syntax**

df.groupby("department")["salary"].mean()

df.groupby("department").agg({
    "salary": "mean",
    "age": "max"
})


**4.4 Feature Engineering**


🔹 **Definition**- Creating new features (columns) from existing data to improve analysis.

🔹 **Syntax**

df["bonus"] = df["salary"] * 0.10

df["age_group"] = df["age"].apply(lambda x: "Adult" if x >= 18 else "Minor")


5️⃣ **Pivot Tables**
🔹 **Definition**- Summarizing data in a table format using aggregation.

🔹 **Syntax**

pd.pivot_table(
    df,
    values="sales",
    index="region",
    columns="product",
    aggfunc="sum"
)
6️⃣ **Merging Tables**
🔹 **Definition**- Combining multiple DataFrames based on a common column (like SQL joins).

🔹 **Syntax**

**Inner Join**
pd.merge(df1, df2, on="id", how="inner")

**Left Join**
pd.merge(df1, df2, on="id", how="left")

**Right Join**
pd.merge(df1, df2, on="id", how="right")

**Outer Join**
pd.merge(df1, df2, on="id", how="outer")


7️⃣ **Exporting Datasets**


🔹 **Definition**- Saving processed data to external files.

🔹 **Syntax**

df.to_csv("output.csv", index=False)

df.to_excel("output.xlsx", index=False)

df.to_json("output.json")


