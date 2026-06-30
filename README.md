# Crime Incidents Data Cleaning Project

## Project Overview

This project demonstrates a complete data cleaning workflow using Python and Pandas on a messy crime incidents dataset.

Real-world datasets often contain missing values, duplicate records, inconsistent formatting, incorrect data types, and invalid entries. The goal of this project is to transform raw, unreliable data into a clean, structured dataset suitable for analysis.

___

## Objectives

* Identify and handle missing values
* Remove duplicate records
* Standardize text formatting
* Correct inconsistent categorical values
* Convert columns to appropriate data types
* Detect and handle outliers
* Validate and clean date fields
* Create a clean and analysis-ready dataset

___

## 📂 Project Structure

```
│   README.md
│   
├───01_Original_Dataset              #Raw dataset
│       crime_incidents_messy.csv    
│       
├───02_Data_Cleaning                 #Notebook
│       data_cleaning.ipynb
│       
└───03_Cleaned_Dataset               #Cleaned dataset
        crime_incidents_cleaned.csv
```

___

## Tools & Technologies

* Jupyter Notebook
* Python
* Pandas
* NumPy
* RE (Regular Expression Library)

___

## Data Cleaning Steps Performed

### 1. Import Required Libraries

The project starts by importing the necessary Python libraries:

* Pandas for data manipulation
* NumPy for numerical operations
* RE for Text pattern matching, string cleaning, and data standardization

```python
import pandas as pd
import numpy as np
import re
```
___

### 2. Load the Dataset

Loaded the raw crime incidents dataset into a Pandas DataFrame for inspection and preprocessing.

```python
df = pd.read_csv("crime_incidents_messy.csv")
```
___

### 3. Initial Data Inspection

Before making any changes, explored the dataset to understand its structure and quality.

Tasks performed:

* Viewed sample records
* Checked dataset dimensions
* Inspected column names
* Reviewed data types
* Generated summary statistics
* Identified missing values

Methods used:

```python
df.head()
df.info()
df.shape
df.describe()
df.isnull().sum()
```
___

### 4. Remove Duplicate Records

Duplicate rows were identified and removed to ensure each crime incident was represented only once.

```python
df.drop_duplicates(inplace=True)
```

Benefits:

* Prevents double-counting incidents
* Improves data reliability
___

### 5. Standardize Column Names

Column names were cleaned and standardized for consistency.

Tasks performed:

* Converted names to lowercase
* Replaced spaces with underscores
* Removed unnecessary special characters

Example:

```text
Crime Type → crime_type
Incident Date → incident_date
```
___

### 6. Handle Missing Values

Missing values were treated according to each column's data type.

#### Numerical Columns

Missing numerical values were replaced using the median value.

```python
for col in num_cols:
    df[col]=df[col].fillna(df[col].median())
```

#### Datetime Columns

Missing date values were filled using the most frequent date (mode).

```python
for col in datetime_cols:
    df[col]=df[col].fillna(df[col].mode()[0])
```

#### Categorical Columns

Missing text values were replaced with the most common category.

```python
for col in obj_cols:
    df[col]=df[col].fillna(df[col].mode()[0])
```
___

### 7. Correct Data Types

Columns were converted to their appropriate data types.

Examples:

* Dates → Datetime format
* Counts and IDs → Integer format
* Measurements → Numeric format

```python
pd.to_datetime()
pd.to_numeric()
```

Benefits:

* Enables accurate calculations
* Improves analytical efficiency
___

### 8. Clean Text Data

Text-based columns were standardized to remove inconsistencies.

Tasks performed:

* Removed the spaces before and after the text
* Fixed capitalization issues
* Standardized category names

Example:

```text
" theft "
"THEFT"
"Theft"

→ Theft
```
___

### 9. Validate Data Quality

After cleaning, the dataset was rechecked to confirm:

* No unexpected missing values remained
* Data types were correct
* Duplicate records were removed
* Column values were consistent

Methods used:

```python
df.info()
df.isnull().sum()
df.describe()
```

---

### 10. Export the Cleaned Dataset

Finally, the cleaned dataset was saved for future analysis and visualization.

```python
df.to_csv("crime_incidents_cleaned.csv",index=False)
```
___


## Key Outcomes

* Improved overall data quality
* Eliminated inconsistencies and errors
* Created a reliable dataset for further analysis
* Established a reusable data-cleaning workflow

___

## How to Run the Project

### Clone the Repository

```bash
git clone https://github.com/yourusername/crime-incidents-data-cleaning.git
```

### Install Dependencies

```bash
pip install pandas numpy jupyter
```

### Launch Jupyter Notebook

```bash
jupyter notebook
```

Open:

```bash
data_cleaning.ipynb
```

and run all cells.
___

## Future Improvements

* Automate data validation checks
* Build a reusable cleaning pipeline
* Create visualizations for cleaned data insights
___

## Learning Outcomes

Through this project, I gained hands-on experience in:

* Data preprocessing
* Data quality assessment
* Missing value treatment
* Data transformation
* Feature standardization
* Preparing datasets for analytics and machine learning
___

## Author
Chirantan Sarkar
___
