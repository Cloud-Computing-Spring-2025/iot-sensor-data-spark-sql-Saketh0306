IoT Sensor Data Analysis using Spark SQL
This project processes IoT sensor data using Apache Spark. The goal is to perform exploratory analysis, filtering, aggregation, ranking, and pivoting on sensor readings, and save the output of each task to CSV files.

Dataset
The dataset sensor_data.csv contains simulated IoT sensor readings, with fields:

sensor_id (integer)

timestamp (string — date & time)

temperature (float)

humidity (float)

location (string)

sensor_type (string)

Tasks Overview
✅ Task 1: Load & Basic Exploration
Loaded the dataset using Spark with inferred schema.

Created a temporary view (sensor_readings) for SQL queries.

Displayed the first 5 rows.

Counted total records.

Retrieved distinct locations.

💾 Output: task1_output.csv

✅ Task 2: Filtering & Simple Aggregations
Filtered sensor data to include only temperature readings between 18°C and 30°C.

Counted in-range and out-of-range records.

Computed average temperature and humidity grouped by location.

Sorted locations by avg_temperature descending.

💾 Output: task2_output.csv

✅ Task 3: Time-Based Analysis
Converted the timestamp column from string to Spark TimestampType.

Extracted the hour of the day from the timestamp.

Grouped data by hour_of_day to compute avg_temp.

Identified the hour with the highest average temperature.

💾 Output: task3_output.csv

✅ Task 4: Window Function Analysis
Computed average temperature for each sensor_id.

Used RANK() window function to rank sensors by avg_temp in descending order.

Displayed the top 5 highest-ranked sensors.

💾 Output: task4_output.csv

✅ Task 5: Pivot & Interpretation
Created a pivot table: location as rows, hour_of_day as columns.

Calculated average temperature for each (location, hour) combination.

Identified the hottest (location, hour) based on the pivoted data.

💾 Output: task5_output.csv

How to Run
Ensure Apache Spark is installed and configured.

Place sensor_data.csv in the same directory.

Run the Python script:

spark-submit tasks.py
The results will be saved as:

task1_output.csv

task2_output.csv

task3_output.csv

task4_output.csv

task5_output.csv