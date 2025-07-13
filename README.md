# Abhit-s_AWS_ETL_Pipeline
This project demonstrates a serverless ETL pipeline using AWS Lambda, S3, Glue, and Athena. It converts semi-structured JSON order data into Parquet format, catalogs it, and enables SQL querying via Athena.

# Architecture Overview
S3 (orders_json_inc) ──▶ Lambda ──▶ S3 (orders_parquet)
                                  │
                                  └─▶ Glue Crawler ──▶ Glue Catalog ──▶ Athena

# S3 Folder Structure

    s3://abhit-etl-project/orders_json_inc/
    Contains incoming JSON files with order data.

    s3://abhit-etl-project/orders_parquet/
    Stores Parquet-formatted files output by Lambda.
