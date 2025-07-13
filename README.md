# Abhit-s_AWS_ETL_Pipeline
This project demonstrates a serverless ETL pipeline using AWS Lambda, S3, Glue, and Athena. It converts semi-structured JSON order data into Parquet format, catalogs it, and enables SQL querying via Athena.

### Architecture Overview
S3 (orders_json_inc) ──▶ Lambda ──▶ S3 (orders_parquet) ──▶ Glue Crawler ──▶ Glue Catalog ──▶ Athena
                                  
                                  

## S3 Folder Structure

    s3://abhit-etl-project/orders_json_inc/
    Contains incoming JSON files with order data.

    s3://abhit-etl-project/orders_parquet/
    Stores Parquet-formatted files output by Lambda.

# AWS Lambda (my_etl_pipeline)

    Trigger: Automatically invoked when new files are added to orders_json_inc/.

    Purpose: Reads and flattens nested JSON, converts it to Parquet, and uploads to orders_parquet/.

    Permissions: IAM Role allows read/write access to the S3 bucket.

# AWS Glue Setup

    Database: abhit_db_glue

    Crawler: abhit_crawler1

        Scans orders_parquet/

        Creates/updates schema in Glue Catalog

        Outputs metadata table under abhit_db_glue

# AWS Athena

    Connected to Glue Catalog.

    Enables SQL queries on the Parquet table created by the crawler.

    Reflects new data automatically as JSON files are added to orders_json_inc/.











    
