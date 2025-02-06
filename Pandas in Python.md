# Pandas in Python

## Table of Contents

1. **Introduction to Pandas**
    - What is Pandas?
    - Installation and Setup
    - Importing Pandas
2. **Pandas Data Structures**
    - Series
    - DataFrame
3. **Basic Operations**
    - Creating Series and DataFrames
    - Indexing and Selection
    - Data Inspection
    - Data Cleaning
    - Handling Missing Data
    - Data Filtering
    - Sorting
4. **Data Manipulation**
    - Adding and Removing Columns
    - Applying Functions
    - GroupBy Operations
    - Merging, Joining, and Concatenating
    - Pivoting and Melting
5. **Advanced Operations**
    - MultiIndexing
    - Time Series Analysis
    - Handling Categorical Data
    - Working with Text Data
    - Performance Optimization
6. **Input and Output**
    - Reading and Writing CSV, Excel, SQL, and more
7. **Visualization with Pandas**
    - Basic Plotting
8. **Practical Examples and Use Cases**

---

## 1. Introduction to Pandas

### What is Pandas?

Pandas is an open-source data manipulation and analysis library for Python. It provides data structures and functions needed to manipulate structured data, including functions for reading and writing data, handling missing data, filtering, sorting, and more.

### Installation and Setup

You can install Pandas using pip:

bash

Copy

```
pip install pandas
```

### Importing Pandas

To use Pandas, you need to import it:

python

Copy

```
import pandas as pd
```

---

## 2. Pandas Data Structures

### Series

A Series is a one-dimensional array-like object that can hold any data type. It is similar to a column in a spreadsheet.

python

Copy

```
import pandas as pd

# Creating a Series
s = pd.Series([1, 2, 3, 4, 5])
print(s)
```

### DataFrame

A DataFrame is a two-dimensional, size-mutable, and potentially heterogeneous tabular data structure with labeled axes (rows and columns).

python

Copy

```
# Creating a DataFrame
data = {
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Age': [25, 30, 35],
    'City': ['New York', 'Los Angeles', 'Chicago']
}

df = pd.DataFrame(data)
print(df)
```

---

## 3. Basic Operations

### Creating Series and DataFrames

You can create Series and DataFrames from lists, dictionaries, and other data structures.

python

Copy

```
# From a list
s = pd.Series([1, 2, 3, 4, 5])

# From a dictionary
data = {'Name': ['Alice', 'Bob'], 'Age': [25, 30]}
df = pd.DataFrame(data)
```

### Indexing and Selection

You can select data using labels or positions.

python

Copy

```
# Selecting a column
ages = df['Age']

# Selecting a row
row = df.loc[0]

# Selecting by position
row = df.iloc[0]
```

### Data Inspection

Inspect the first few rows, last few rows, and summary statistics.

python

Copy

```
df.head()  # First 5 rows
df.tail()  # Last 5 rows
df.info()  # Summary of the DataFrame
df.describe()  # Statistical summary
```

### Data Cleaning

Handle missing data, duplicates, and incorrect data types.

python

Copy

```
# Drop rows with missing values
df.dropna()

# Fill missing values
df.fillna(0)

# Remove duplicates
df.drop_duplicates()
```

### Handling Missing Data

Pandas provides methods to handle missing data.

python

Copy

```
# Check for missing values
df.isnull()

# Drop missing values
df.dropna()

# Fill missing values
df.fillna(0)
```

### Data Filtering

Filter data based on conditions.

python

Copy

```
# Filter rows where Age is greater than 30
df[df['Age'] > 30]
```

### Sorting

Sort data by one or more columns.

python

Copy

```
# Sort by Age
df.sort_values(by='Age')

# Sort by multiple columns
df.sort_values(by=['Age', 'Name'])
```

---

## 4. Data Manipulation

### Adding and Removing Columns

Add or remove columns from a DataFrame.

python

Copy

```
# Add a new column
df['Salary'] = [50000, 60000, 70000]

# Remove a column
df.drop('Salary', axis=1, inplace=True)
```

### Applying Functions

Apply functions to data.

python

Copy

```
# Apply a function to a column
df['Age'] = df['Age'].apply(lambda x: x + 1)
```

### GroupBy Operations

Group data and perform aggregate operations.

python

Copy

```
# Group by City and calculate mean Age
df.groupby('City')['Age'].mean()
```

### Merging, Joining, and Concatenating

Combine DataFrames.

python

Copy

```
# Concatenate DataFrames
df1 = pd.DataFrame({'A': ['A0', 'A1'], 'B': ['B0', 'B1']})
df2 = pd.DataFrame({'A': ['A2', 'A3'], 'B': ['B2', 'B3']})
result = pd.concat([df1, df2])

# Merge DataFrames
df1 = pd.DataFrame({'key': ['A', 'B'], 'value': [1, 2]})
df2 = pd.DataFrame({'key': ['A', 'B'], 'value': [3, 4]})
result = pd.merge(df1, df2, on='key')
```

### Pivoting and Melting

Reshape data.

python

Copy

```
# Pivot
df.pivot(index='Date', columns='City', values='Temperature')

# Melt
pd.melt(df, id_vars=['Name'], value_vars=['Age', 'Salary'])
```

---

## 5. Advanced Operations

### MultiIndexing

Work with hierarchical indexing.

python

Copy

```
# Create a MultiIndex DataFrame
arrays = [['A', 'A', 'B', 'B'], [1, 2, 1, 2]]
index = pd.MultiIndex.from_arrays(arrays, names=('Group', 'Number'))
df = pd.DataFrame({'Value': [10, 20, 30, 40]}, index=index)
```

### Time Series Analysis

Handle time series data.

python

Copy

```
# Create a time series
dates = pd.date_range('20230101', periods=6)
df = pd.DataFrame({'Value': [1, 2, 3, 4, 5, 6]}, index=dates)

# Resample time series data
df.resample('M').mean()
```

### Handling Categorical Data

Work with categorical data.

python

Copy

```
# Convert to categorical
df['City'] = df['City'].astype('category')
```

### Working with Text Data

Manipulate text data.

python

Copy

```
# Convert to lowercase
df['Name'] = df['Name'].str.lower()

# Split strings
df['Name'].str.split(' ')
```

### Performance Optimization

Optimize performance using techniques like vectorization.

python

Copy

```
# Vectorized operations
df['Age'] = df['Age'] + 1
```

---

## 6. Input and Output

### Reading and Writing CSV, Excel, SQL, and more

Read and write data from/to various formats.

python

Copy

```
# Read CSV
df = pd.read_csv('data.csv')

# Write CSV
df.to_csv('output.csv', index=False)

# Read Excel
df = pd.read_excel('data.xlsx')

# Write Excel
df.to_excel('output.xlsx', index=False)

# Read SQL
import sqlite3
conn = sqlite3.connect('database.db')
df = pd.read_sql_query('SELECT * FROM table_name', conn)
```

---

## 7. Visualization with Pandas

### Basic Plotting

Create basic plots directly from DataFrames.

python

Copy

```
# Line plot
df.plot()

# Bar plot
df.plot(kind='bar')

# Histogram
df['Age'].plot(kind='hist')
```

---

## 8. Practical Examples and Use Cases

### Example 1: Data Cleaning

Clean a dataset by handling missing values, removing duplicates, and correcting data types.

python

Copy

```
# Load data
df = pd.read_csv('data.csv')

# Handle missing values
df.fillna(0, inplace=True)

# Remove duplicates
df.drop_duplicates(inplace=True)

# Correct data types
df['Age'] = df['Age'].astype(int)
```

### Example 2: Data Analysis

Perform a basic data analysis by grouping data and calculating summary statistics.

python

Copy

```
# Group by City and calculate mean Age
df.groupby('City')['Age'].mean()

# Calculate correlation
df.corr()
```

### Example 3: Time Series Analysis

Analyze time series data by resampling and plotting.

python

Copy

```
# Resample time series data
df.resample('M').mean().plot()
```

---

This tutorial covers the basics to advanced concepts in Pandas. By following this guide, you should be able to manipulate and analyze data effectively using Pandas. Happy coding!