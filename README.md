# README: Python Process for Loading and Joining CSV Files

## Overview

This process is designed to load multiple CSV files from two categories, perform a join operation to match records between these two categories using **pandasql**, and write the final joined dataset to a CSV file. The process is implemented in a Python Notebook to ensure easy execution and interaction.

## Requirements

Before running the Notebook, ensure you have the following dependencies installed:

### Python Version
- Python 3.9.13

### Required Libraries
The following Python libraries are required:
- **pandas**: For data manipulation and file reading.
- **pandasql**: For performing SQL-like queries on pandas DataFrames.
- **os**: To navigate directories and load files.

You can install these libraries via pip:
```bash
pip install pandas pandasql
```

## Process Workflow

1. **Load CSV Files from Two Categories**:  
   The Notebook will load all CSV files from two distinct directories representing two categories of data.
   
2. **Join Operation**:  
   A SQL-like join will be performed between the records of the two categories using **pandasql** to match the desired columns.
   
3. **Output the Final Joined Data**:  
   The final dataset from the join operation will be written to a new CSV file.

### Input and Output

- **Input**: Multiple CSV files categorized into two folders (e.g., `category_1/` and `category_2/`).
- **Output**: A single CSV file containing the joined records.

## Folder Structure

Ensure the input data is structured as follows:
```
/data
│
├── /category_1
│   ├── file1.csv
│   ├── file2.csv
│   └── ...
|   │
|   └── /category_2
|       ├── file1.csv
|       ├── file2.csv
|       └── ...
├── /main
|   └── process.py
└── /output

```

## Notebook Instructions

### 1. Import Libraries
At the beginning of the Notebook, the required libraries will be imported:
```python
import os
import glob
import pandas as pd
import pandasql as psql
```

### 2. Load CSV Files from Both Categories
The process will load all CSV files from the two categories using `glob` and `pandas`:
```python
category_1_path = 'data/category_1/*.csv'
category_2_path = 'data/category_2/*.csv'

# Load category 1 files
category_1_files = glob.glob(category_1_path)
df_category_1 = pd.concat([pd.read_csv(file) for file in category_1_files], ignore_index=True)

# Load category 2 files
category_2_files = glob.glob(category_2_path)
df_category_2 = pd.concat([pd.read_csv(file) for file in category_2_files], ignore_index=True)
```

### 3. Perform Join Operation
Using **pandasql**, the Notebook will execute a SQL query to join the dataframes on matching columns:
```python
# Example SQL query to join the datasets on a common column, 'id'
query = '''
SELECT a.*, b.*
FROM df_category_1 a
JOIN df_category_2 b
ON a.id = b.id
'''

df_joined = psql.sqldf(query, locals())
```
Adjust the `ON` clause based on the specific columns used to join.

### 4. Write the Final Dataset to a CSV File
The final joined dataset will be saved as a CSV file:
```python
output_file = 'data/joined_output.csv'
df_joined.to_csv(output_file, index=False)
```

## Usage

1. Place the CSV files into their respective category folders as described in the **Folder Structure** section.
2. Open and run the Jupyter Notebook.
3. The final joined dataset will be saved as `joined_output.csv` in the `data/` folder.

## Customization

- **File Structure**: You can change the folder paths by modifying the `category_1_path` and `category_2_path` variables.
- **Join Conditions**: Modify the SQL query in the `query` string to adjust the join condition based on your dataset.

## Notes

- Ensure all CSV files have consistent formatting for smooth operation.
- If the column names differ across files, adjust the column references in the SQL query.

---

This process should provide an efficient way to automate the joining of multiple CSV files from two categories and output the result in a single CSV file.
