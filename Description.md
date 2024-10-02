### Project Description: CSV Data Joiner with Python and PandasQL

This project implements a Python-based solution for loading, processing, and integrating multiple CSV files from two distinct categories. The main goal is to automate the process of combining datasets by performing a SQL-like join operation using **pandasql**. The final output is a unified CSV file that consolidates data from both categories based on specified matching criteria.

#### Key Features:
- **Multi-File Loader**: Automatically loads multiple CSV files from two predefined directories.
- **SQL-Like Join with pandasql**: Uses SQL queries to join records from both categories based on common keys.
- **Data Output**: Writes the final joined dataset into a single, clean CSV file.
- **Scalable & Flexible**: Capable of handling large datasets and can be customized to fit various join conditions and file structures.

#### Use Case:
This project is ideal for data engineers, analysts, or anyone dealing with distributed datasets who need to automate the process of merging data from different sources, such as merging sales reports with customer information, or combining logs from different systems.

#### Technology Stack:
- **Python**
- **pandas** for data manipulation
- **pandasql** for SQL queries on DataFrames
- **Jupyter Notebook** for interactive execution

The project aims to provide a scalable, customizable solution to streamline data integration tasks in a notebook format, allowing for quick deployment and adaptation to different datasets.
