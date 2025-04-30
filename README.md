# SQL Data Cleaning: Automobile Dataset

This project contains SQL queries used to clean and analyze historical car sales data using Google BigQuery. Each `.sql` file represents a specific cleaning step or check.

## Files
- _inspect_fuel_type.sql`: Checks unique fuel types.
- _check_length_column.sql`: Confirms length column values are in the expected range.
- _null_num_of_doors.sql`: Identifies and updates null values in `num_of_doors`.
- _fix_num_of_cylinders.sql`: Fixes spelling errors in cylinder count.
- _check_compression_ratio.sql`: Identifies and deletes outlier values.
- _trim_drive_wheels.sql`: Removes trailing spaces in drive wheel entries.
