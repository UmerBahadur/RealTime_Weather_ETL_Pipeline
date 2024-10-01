![WeatherETL (2)](https://github.com/user-attachments/assets/08d61b3f-3ebb-4a8b-a9a3-11a4d23da6e9)

# Weather Data ETL Pipeline

A comprehensive data pipeline using **OpenWeatherMap API**, **Apache Airflow**, **Amazon S3**, and **Snowflake**.

This project demonstrates an ETL (Extract, Transform, Load) solution that extracts real-time weather data from OpenWeatherMap, processes it, and loads it into Snowflake for further analytics and querying.

## Overview

The pipeline is designed to:

- **Extract** real-time weather data from OpenWeatherMap by calling the API.
- **Validate** the API's functionality using a dedicated DAG.
- **Store** the raw weather data in an S3 bucket.
- **Transform** the data using a transformation DAG.
- **Load** the transformed data into a Snowflake stage, which automatically gets ingested into a table for further querying.

## Tech Stack

- **OpenWeatherMap API**: Source of real-time weather data.
- **Apache Airflow**: Orchestrates the ETL process with three DAGs:
  - **DAG 1**: Checks if the API is functional.
  - **DAG 2**: Loads raw data from the API into S3.
  - **DAG 3**: Transforms the data and triggers the Snowpipe to load data into Snowflake.
- **Amazon S3**: Raw data storage.
- **Snowflake**: Data warehouse for storing and analyzing weather data.
- **Snowpipe**: Automates the data ingestion from S3 into Snowflake tables.

## Workflow

1. **Data Extraction**: A DAG fetches real-time weather data from OpenWeatherMap API in JSON format.
2. **API Health Check**: The first DAG checks whether the API is responsive before further tasks are executed.
3. **Data Transformation**: Another DAG processes the raw weather data into a format ready for analytics.
4. **Data Loading**: The transformed data is uploaded to an S3 bucket, and a Snowpipe is triggered to ingest the data into Snowflake for further analysis.
5. **Snowflake Queries**: Once in Snowflake, you can perform queries to analyze weather data as per your requirements.


