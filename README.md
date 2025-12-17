# Spotify Data Engineering Pipeline

## Overview

This project shows an end to end data engineering pipeline built on AWS for processing Spotify data. It covers ingestion, transformation, storage, querying, and visualization. The goal is to take raw CSV files and turn them into analytics ready data that can be explored with SQL and visualized in Power BI.

## Architecture

The pipeline uses the following AWS services:

- Amazon S3 for raw and processed data storage  
- AWS Glue for ETL processing  
- AWS Glue Crawler for schema discovery and metadata management  
- Amazon Athena for SQL based querying  
- Power BI for data visualization  

## Data Sources

The project uses three CSV files containing Spotify metadata:

- `artists.csv`  
- `albums.csv`  
- `tracks.csv`  

These files are manually uploaded to an Amazon S3 bucket.

## Data Flow

1. Upload CSV files to Amazon S3  
2. AWS Glue reads the raw data from S3  
3. A Glue ETL job performs inner joins across artists, albums, and tracks  
4. Transformed data is written back to S3 in Parquet format  
5. A Glue Crawler scans the Parquet data and creates tables in the Glue Data Catalog  
6. Amazon Athena queries the processed data using SQL  
7. Power BI connects to Athena to build dashboards and reports  

## Setup Instructions

### Step 1: Upload Raw Data

Upload `artists.csv`, `albums.csv`, and `tracks.csv` to the raw S3 bucket.

### Step 2: Create AWS Glue ETL Job

- Configure a Glue job to read CSV files from S3  
- Perform inner joins on artist, album, and track data  
- Write the output to an S3 location in Parquet format  
- Assign an IAM role with the required permissions  

### Step 3: Run Glue Crawler

- Create a Glue Crawler pointing to the Parquet output location  
- Run the crawler to generate metadata tables in the Glue Data Catalog  

### Step 4: Query Data with Athena

- Configure Athena to use the Glue Data Catalog  
- Run SQL queries on the processed Parquet tables  

### Step 5: Visualize Data

- Connect Power BI to Amazon Athena  
- Build dashboards and reports on top of the queried data  

## Output

- Cleaned and joined Spotify data stored in Parquet format  
- Queryable tables available in Amazon Athena  
- Interactive dashboards and reports built in Power BI  
