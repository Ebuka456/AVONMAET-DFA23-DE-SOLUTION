# ETL Pipeline Documentation: AVONMAET DFA23 SOLUTION

<p align="center" > <img  src="https://github.com/Ebuka456/DE_ETL_DATAFEST2023/blob/main/DE_ETL_DATAFEST2023/ETL.png" alt="Alt text" style= "width: 700px; height: 350px"/></p>

## Overview
This document outlines the detailed steps undertaken during the ETL (Extract, Transform, Load) process for Agricultural Monitoring Systems. The primary objective of this data engineering project is to efficiently extract raw sensor data, perform necessary data transformations, and load the curated data into structured fact and dimension tables within our Snowflake data warehouse.

## ETL Steps

### Step 1: Data Extraction
Raw data is sourced from various heterogeneous systems, including SensorDataRaw, WeatherDataRaw, SoilDataRaw, CropDataRaw, PestDataRaw, IrrigationDataRaw, and LocationDataRaw. These diverse data streams are ingested into designated staging tables (STG_CROPDATARAW, STG_IRRIGATIONDATARAW, STG_LOCATIONDATARAW, STG_PESTDATARAW, STG_SENSORDATARAW, STG_SOILDATARAW, STG_WEATHERDATARAW) within the AVONMAET Data Warehouse Schema.

### Step 2: Data Preprocessing and Cleaning
The data in the staging tables undergo comprehensive preprocessing and data quality improvement processes. Key data anomalies and cleaning actions are outlined as follows:

#### STG_CROPDATARAW
- Crop Type:
  - Standardized crop type values (e.g., "Cron" corrected to "Corn").
  - Null value handling.
  - Ensured consistent data types.
- Growth Stage:
  - Standardized growth stage values (e.g., "Flowerring" corrected to "Flowering").
  - Handled "NA" and null values.
  - Ensured consistent data types.
- Pest Type:
  - Standardized pest type values (e.g., "Aphiods" corrected to "Aphids").
  - Handled "NA" and null values.
  - Ensured consistent data types.
- Crop Yield:
  - Handled "NA" and null values.
  - Converted units to International System (Kg/m²).
  - Ensured consistent data types.
- Timestamp:
  - Ensured data type consistency.

#### STG_PESTDATARAW
- Pest Type:
  - Standardized pest type values (e.g., "Aphiods" corrected to "Aphids").
  - Ensured consistent data types.
- Pest Description:
  - Corrected misspelled words.
  - Ensured consistent data types.
- Pest Severity:
  - Standardized severity values (e.g., "Hihg" corrected to "High").
  - Replaced "NA" with null values.
  - Ensured consistent data types.
- Timestamp:
  - Ensured data type consistency.

#### STG_WEATHERDATARAW
- Weather Condition:
  - Corrected misspelled words.
  - Handled "NA" values.
  - Ensured consistent data types.
- Wind Speed:
  - Handled "NA" and null values.
  - Converted units.
  - Ensured consistent data types.
- Precipitation:
  - Handled "NA" and null values.
  - Converted units.
  - Ensured consistent data types.
- Timestamp:
  - Ensured data type consistency.

#### STG_IRRIGATIONDATARAW
- Sensor ID:
  - Extracted sensor IDs from complex strings.
  - Ensured consistent data types.
- Irrigation Method:
  - Corrected spelling errors.
  - Ensured consistent data types.
- Water Source:
  - Corrected spelling errors.
  - Handled null values.
  - Ensured consistent data types.
- Irrigation Duration:
  - Handled "NA" values.
  - Converted units to seconds.
  - Ensured consistent data types.
- Timestamp:
  - Ensured data type consistency.

#### STG_SOILDATARAW
- Handled null and "NA" values.
- Ensured consistent data types.

#### STG_SENSORDATARAW
- Addressed anomalies in the Timestamp and Sensor ID columns.
- Handled null and "NA" values.
- Ensured consistent data types.

#### STG_LOCATIONDATARAW
- Addressed invalid characters in the Sensor ID column.
- Ensured consistent data types.

## Creation of Dimensions and Fact Tables
Following data transformation and cleaning, dimensions and fact tables were designed and constructed to facilitate data analysis and reporting. Here's an outline of these tables:

### Dimension Tables
1. Dim_Crop_Type
2. Dim_Growth_Stage
3. Dim_Pest_Type
4. Dim_Irrigation_Method
5. Dim_Water_Source
6. Dim_Date
7. Dim_Weather_Condition
8. Dim_Sensor
9. Dim_Location

### Fact Tables
1. Fact_Crop
2. Fact_Irrigation
3. Fact_Pest
4. Fact_Sensor
5. Fact_Soil
6. Fact_Weather

These tables establish a structured foundation for efficient data warehousing, enabling data analysts and scientists to perform advanced analytics and gain insights from the data.

## Query Optimization, Final Quality Check, and Documentation
To enhance query performance, clustering keys were employed to determine the physical storage order of data, reducing data movement during query execution. Additionally, comprehensive quality checks were conducted to ensure the data's cleanliness and integrity.

For more details, including SQL scripts and additional information, please refer to the accompanying documentation.
