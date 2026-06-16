# Task 1: Data Cleaning and Preprocessing using Python

## Project Overview

This project focuses on performing data cleaning and preprocessing on the **Netflix Movies and TV Shows Dataset** obtained from Kaggle. The objective is to prepare the raw dataset for further analysis by identifying and handling missing values, removing duplicate records, standardizing data formats, validating data types, and ensuring overall data quality.

Data preprocessing is a critical step in the data analytics workflow because clean and consistent data leads to more accurate analysis, visualization, and machine learning outcomes.

---

## Dataset Information

**Dataset Name:** Netflix Movies and TV Shows Dataset

**Source:** Kaggle

**File Used:** `netflix_titles.csv`

### Dataset Features

| Column Name  | Description                            |
| ------------ | -------------------------------------- |
| show_id      | Unique identifier for each title       |
| type         | Content type (Movie or TV Show)        |
| title        | Name of the movie or TV show           |
| director     | Director(s) of the content             |
| cast         | Cast members featured in the content   |
| country      | Country of production                  |
| date_added   | Date the content was added to Netflix  |
| release_year | Original release year                  |
| rating       | Content maturity rating                |
| duration     | Duration of movie or number of seasons |
| listed_in    | Genre/category                         |
| description  | Brief summary of the content           |

---

## Objectives

The main objectives of this project were:

* Load and inspect the dataset.
* Identify and handle missing values.
* Check and remove duplicate records.
* Standardize column names.
* Standardize text values.
* Convert date formats into a consistent format.
* Verify and validate data types.
* Export a cleaned dataset for future analysis.

---

## Technologies Used

* Python 3.x
* Pandas
* NumPy
* Jupyter Notebook / VS Code

---

## Data Cleaning Process

### 1. Import Required Libraries

The Pandas and NumPy libraries were imported to perform data manipulation and preprocessing tasks.

```python
import pandas as pd
import numpy as np
```

### 2. Load Dataset

The dataset was loaded into a Pandas DataFrame using:

```python
df = pd.read_csv("netflix_titles.csv")
```

### 3. Initial Data Inspection

The dataset structure was examined using:

```python
df.head()
df.info()
df.shape
```

This helped understand the number of rows, columns, and data types.

### 4. Missing Value Analysis

Missing values were checked using:

```python
df.isnull().sum()
```

Result:

| Column     | Missing Values |
| ---------- | -------------- |
| director   | 2634           |
| country    | 831            |
| cast       | 825            |
| date_added | 10             |
| rating     | 4              |
| duration   | 3              |

### 5. Handling Missing Values

Missing values were handled using the following methods:

* Filled missing values in **director**, **cast**, and **country** with `"Unknown"`.
* Removed records with missing **date_added** values.
* Filled missing values in **rating** with `"Not Rated"`.
* Filled missing values in **duration** with `"Unknown"`.

Example:

```python
df['director'] = df['director'].fillna('Unknown')
df['cast'] = df['cast'].fillna('Unknown')
df['country'] = df['country'].fillna('Unknown')

df.dropna(subset=['date_added'], inplace=True)

df['rating'] = df['rating'].fillna('Not Rated')
df['duration'] = df['duration'].fillna('Unknown')
```

### 6. Duplicate Record Detection

Duplicate rows were checked using:

```python
df.duplicated().sum()
```

Duplicates, if found, were removed using:

```python
df.drop_duplicates(inplace=True)
```

### 7. Column Name Standardization

Column names were standardized to improve readability and maintain consistency.

Example:

```text
show_id → show_id
release_year → release_year
date_added → date_added
```

Code used:

```python
df.columns = (
    df.columns
      .str.lower()
      .str.strip()
      .str.replace(' ', '_')
)
```

### 8. Text Value Standardization

Text values were cleaned by removing extra spaces and converting them into a consistent format.

```python
text_columns = ['type', 'country', 'rating']

for col in text_columns:
    df[col] = df[col].str.strip().str.title()
```

Example:

```text
movie → Movie
united states → United States
```

### 9. Date Format Conversion

The `date_added` column was converted from string format to datetime format.

```python
df['date_added'] = pd.to_datetime(df['date_added'])
```

Then converted into a standardized format:

```python
df['date_added'] = df['date_added'].dt.strftime('%d-%m-%Y')
```

Example:

```text
September 25, 2021 → 25-09-2021
```

### 10. Data Type Validation

Data types were verified using:

```python
df.dtypes
```

Result:

* Release year stored as integer.
* Date values standardized.
* Text columns stored as object/string data type.

### 11. Export Cleaned Dataset

The cleaned dataset was exported using:

```python
df.to_csv("netflix_cleaned.csv", index=False)
```

---

## Results

The dataset was successfully cleaned and prepared for analysis.

### Key Findings

* Missing values were identified and handled.
* Duplicate records were removed.
* Text values were standardized.
* Date formats were converted into a consistent format.
* Column names were standardized.
* Data types were verified and validated.
* Dataset was prepared for exploratory data analysis and machine learning tasks.

---

## Output Files

```text
netflix_titles.csv
netflix_cleaned.csv
```

---

## Project Structure

```text
Task1-Data-Cleaning/
│
├── netflix_titles.csv
├── netflix_cleaned.csv
├── task1.ipynb
├── task1.py
└── README.md
```

---

## Conclusion

This project successfully demonstrated the complete data cleaning and preprocessing workflow using Python and Pandas on the Netflix Movies and TV Shows Dataset. Missing values were handled, duplicate records were removed, text and date formats were standardized, and data quality was validated. The cleaned dataset is now ready for exploratory data analysis, visualization, and machine learning applications.
