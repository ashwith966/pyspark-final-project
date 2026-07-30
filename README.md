# PySpark Final Project - Milestone 2

## Student Information

- **Name:** Ashwith
- **Course:** Data Engineering with Apache Spark
- **Project:** Milestone 2 – Data Engineering using PySpark on Databricks

---

# Project Overview

This project demonstrates an end-to-end data engineering workflow using Apache Spark (PySpark) on Databricks. The Netflix Movies and TV Shows dataset was loaded, explored, validated, transformed, cleaned, and finally stored in Parquet format.

---

# Dataset

### Dataset Name
Netflix Movies and TV Shows

### Dataset Description
The dataset contains information about movies and TV shows available on Netflix. It includes details such as title, director, cast, country, release year, rating, duration, genres, and descriptions.

### Dataset Source
https://www.kaggle.com/datasets/shivamb/netflix-shows

---

# Technologies Used

- Python
- Apache Spark (PySpark)
- Databricks
- GitHub

---

# Project Workflow

## 1. Dataset Acquisition

Downloaded the Netflix Movies and TV Shows dataset from Kaggle.

---

## 2. Upload Dataset

Uploaded the dataset into a Databricks Unity Catalog Volume.

---

## 3. Read Dataset

The dataset was read using the following options:

- Header = True
- Infer Schema = True
- Read Mode = PERMISSIVE

PERMISSIVE mode was selected so that malformed records would not stop the job execution.

---

## 4. Data Exploration

Performed the following exploratory tasks:

- Printed all column names
- Counted total rows
- Displayed DataFrame schema
- Counted the total number of columns

---

## 5. Corrupted Record Detection

Checked for the `_corrupt_record` column to identify malformed records.

No corrupted records were found in the dataset.

---

## 6. Custom Schema Creation

Created a custom schema using `StructType` and `StructField` to explicitly define the data types for each column and reloaded the dataset using this schema.

---

## 7. Data Transformations

The following transformations were performed:

- Renamed the `listed_in` column to `genre`
- Filtered only Movie records
- Used aliases for selected columns
- Added a constant column named `Source` with value `Kaggle`
- Added a calculated column named `Category` based on release year
- Cast `release_year` to Integer type
- Removed the unnecessary `description` column

---

## 8. Null Value Handling

Handled missing values using `fillna()`.

Missing values were replaced with meaningful defaults:

- Director → Unknown
- Country → Not Available
- Rating → Not Rated

---

## 9. Duplicate Removal

Duplicate records were removed using `dropDuplicates()`.

---

## 10. Write Processed Data

The cleaned dataset was written in **Parquet** format using **Overwrite** mode.

---

# Justification of Decisions

## Why PERMISSIVE Mode?

PERMISSIVE mode allows Spark to read malformed records without failing the entire job, making it suitable for real-world datasets.

## Why Custom Schema?

A custom schema ensures that each column has the correct data type, improves performance, and avoids incorrect type inference.

## Why These Transformations?

The transformations improved readability, cleaned the data, simplified analysis, and added useful information for downstream processing.

## Why Fill Null Values?

Replacing missing values preserved records while making the dataset more complete for analysis.

## Why Parquet?

Parquet is a columnar storage format that provides:

- Faster query performance
- Better compression
- Reduced storage space
- Efficient analytics

---

# Screenshots

Include screenshots of the following outputs inside the `screenshots` folder:

- Dataset Upload
- DataFrame Preview
- Schema (`printSchema()`)
- Column Names
- Row Count
- Corrupted Record Check
- Custom Schema
- Data Transformations
- Null Value Handling
- Duplicate Removal
- Final Parquet Output

---

# Repository Structure

```
pyspark-final-project/
│
├── README.md
├── notebook/
│   └── MILESTONE 2.ipynb
│
├── screenshots/
│
├── data/
│   └── netflix_titles_sample.csv (Optional)
│
└── docs/
```

---

# Challenges Faced

- Understanding Spark transformations
- Creating a custom schema
- Handling null values correctly
- Working with Databricks file paths
- Writing the final dataset in Parquet format

### Resolution

The challenges were resolved by using PySpark DataFrame APIs, validating the schema, applying appropriate transformation functions, and testing the output after each processing step.

---

# Conclusion

This project successfully demonstrates a complete ETL workflow using PySpark in Databricks. The dataset was loaded, explored, validated, cleaned, transformed, and stored in Parquet format, following standard data engineering practices.
