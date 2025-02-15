

## Overview

This project showcases an end-to-end **data pipeline** using **dbt, Google Cloud (BigQuery), and Power BI**. The goal is to transform raw data into actionable insights.

- Create a Google Cloud Platform (GCP) project.
- Access sample data in a public dataset.
- Connect dbt Cloud to BigQuery.
- Take a sample query and turn it into a model in your dbt project. A model in dbt is a select statement.
- Add tests to your models.
- Document your models.
- Schedule a job to run.

## Tech Stack
- **dbt** (Data Build Tool) for transformations
- **Google Cloud BigQuery** as the data warehouse
- **Power BI** for visualization and reporting
- **Google Cloud Storage** for raw data ingestion (optional)

## Architecture Setup
- GCP setup : use sample dataset and 14 free trial account, create service account on google cloud ** pic
- dbt setup : create trial dbt cloud account, use GCP service account credentials and connect to dbt instance using BigQueryCredentials ** pic
- create intial branch in dbt for git versioning

  
 ## dbt Setup
 1. **Build Model**: Add new data Load sample data **select * from `dbt-tutorial.jaffle_shop.customers** execute **dbt run ** 
 2. **Model Persist to warehouse**: dbt allows you to change view to table models: editing the **yml file directly** pic
 3. **Build other models**:Separate logic, transform data to add new models for further analysis ** pic
 4. **DCG Diagram** - lineage **: Allows to view existing lineage and dependency
 5. **Add Test to the Models** - lineage **: Validate models are working, test for Referential integrity/ nulls ** dbt test ** ** pic
 6. **Document your Models** Add documentation to your models, share information with team and stakeholders ** pic yml file**
 7. **Deploy your Models** Create and trigger Production jobs. As business picks up there is need to rebuild source tables and keep data up to date.
    
