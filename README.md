# Automobile Data Cleaning Project

## Overview

This project demonstrates how to clean and process automobile data using SQL queries in a database environment. The goal was to clean a dataset of historical sales data for a used car dealership to identify the most popular cars for inventory planning.

By performing various cleaning tasks such as checking for missing values, correcting data inconsistencies, and ensuring data integrity, the project prepares the dataset for reliable analysis.

## Dataset

The dataset used in this project is based on a `.csv` file containing historical automobile sales data. The data includes various features such as car make, fuel type, body style, and price, which were analyzed and cleaned to meet the necessary requirements for further analysis.

## Technologies Used
- **SQL** for querying and cleaning data.
- **BigQuery** (Google Cloud) for creating datasets and tables, and performing SQL queries.
- **CSV** format for data storage.

## Steps Performed

### 1. Dataset Creation
- Downloaded the `automobile_data.csv` file and uploaded it into Google Cloud BigQuery.
- Created a new dataset named `cars` and a table called `car_info` to store the data.

### 2. Data Inspection and Cleaning

#### Fuel Type
- Inspected the `fuel_type` column to ensure that it only contained valid values: `diesel` and `gas`.
- Ran a query to check for distinct values in the `fuel_type` column:
  ```sql
  SELECT DISTINCT fuel_type
  FROM `bold-artifact-458415-p5.cars.car_info`
  LIMIT 1000;
  ```

#### Length Column
- Verified that the values in the `length` column fell within the expected range (141.1 to 208.1).
- Ran a query to check the minimum and maximum values of the `length` column:
  ```sql
  SELECT MIN(length) AS min_length, MAX(length) AS max_length
  FROM `bold-artifact-458415-p5.cars.car_info`;
  ```

#### Missing Data (Null Values)
- Inspected the `num_of_doors` column for missing (null) values.
- Updated the `num_of_doors` column for rows with missing values based on business rules:
  ```sql
  UPDATE `bold-artifact-458415-p5.cars.car_info`
  SET num_of_doors = 'four'
  WHERE make = 'dodge' AND fuel_type = 'gas' AND body_style = 'sedan';
  ```

#### Data Inconsistencies
- Identified and corrected inconsistencies in the `num_of_cylinders` column, where some values were misspelled (e.g., "tow" instead of "two").
- Ran the following query to find distinct values in `num_of_cylinders`:
  ```sql
  SELECT DISTINCT num_of_cylinders
  FROM `bold-artifact-458415-p5.cars.car_info`;
  ```
- Corrected the misspelled values using an `UPDATE` statement:
  ```sql
  UPDATE `bold-artifact-458415-p5.cars.car_info`
  SET num_of_cylinders = 'two'
  WHERE num_of_cylinders = 'tow';
  ```

#### Compression Ratio
- Checked the `compression_ratio` column for errors, as some values were outside the expected range (7 to 23).
- Identified a value of 70, which was likely a data entry error. The value was corrected by deleting the erroneous row:
  ```sql
  DELETE FROM `bold-artifact-458415-p5.cars.car_info`
  WHERE compression_ratio = 70;
  ```

#### Consistency Check (Drive Wheels)
- Detected extra spaces in the `drive_wheels` column values (e.g., `4wd` appearing twice with different string lengths).
- Used the `TRIM` function to remove extra spaces:
  ```sql
  UPDATE `bold-artifact-458415-p5.cars.car_info`
  SET drive_wheels = TRIM(drive_wheels)
  WHERE TRUE;
  ```

### 3. Data Validation
After cleaning the dataset, I validated that:
- The data no longer contained missing or erroneous values.
- Columns like `fuel_type`, `length`, and `num_of_doors` now adhered to the expected data types and formats.
- The `drive_wheels` column was consistent without extra spaces.

## Conclusion

This project highlights the importance of data cleaning in ensuring the accuracy and reliability of the dataset before performing any analysis. By addressing missing values, correcting inconsistencies, and ensuring data integrity, the dataset is now ready for further exploration and analysis, such as identifying the most popular cars for the dealership’s inventory.

## Files

- **automobile_data.csv**: Original dataset used for cleaning.
- **queries.sql**: SQL queries used for data cleaning and validation.
