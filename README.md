

![banner](https://github.com/user-attachments/assets/b93be2b4-0e2f-4bc4-8776-318850d2eb12)


## Overview

This project showcases an end-to-end **data pipeline** using **dbt, Google Cloud (BigQuery), and Power BI**.
The goal is to transform raw data into actionable insights

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
- GCP setup : use sample dataset and 14 free trial account, create service account on google cloud 

![gcp](https://github.com/user-attachments/assets/830752f4-032e-45f7-855b-aebfa0d183fd)


- dbt setup : create trial dbt cloud account, use GCP service account credentials and connect to dbt instance using BigQueryCredentials
  

  ![dbt](https://github.com/user-attachments/assets/304ec669-8485-4c94-8640-bce17f09f2f3)

  

 ## dbt Setup
 1. **Build Model**: Add new data Load sample data **select * from `dbt-tutorial.jaffle_shop.customers** 


![customermodel](https://github.com/user-attachments/assets/194b814e-6edd-4c12-aec3-4e4035815a79)

    
 3. **Model Persist to warehouse**: dbt allows you to change view to table models: editing the **yml file directly** 


![persisttable](https://github.com/user-attachments/assets/22cc3166-6ebd-461d-bdea-5459b4c895dd)

**By editing the yaml file directly**

[version: 2

models:
  - name: customers
    description: One record per customer
    columns:
      - name: customer_id
        description: Primary key
        tests:
          - unique
          - not_null
      - name: first_order_date
        description: NULL when a customer has not yet placed an order.

  - name: stg_customers
    description: This model cleans up customer data
    columns:
      - name: customer_id
        description: Primary key
        tests:
          - unique
          - not_null

  - name: stg_orders
    description: This model cleans up order data
    columns:
      - name: order_id
        description: Primary key
        tests:
          - unique
          - not_null
      - name: status
        tests:
          - accepted_values:
              values: ['placed', 'shipped', 'completed', 'return_pending', 'returned']
      - name: customer_id
        tests:
          - not_null
          - relationships:
              to: ref('stg_customers')
              field: customer_idUploading schema.yml…]()


 4. **Build other models**:Separate logic, transform data to add new models for further analysis 
 5. **DCG Diagram** - lineage **: Allows to view existing lineage and dependency
  
![dag](https://github.com/user-attachments/assets/8d8392aa-3cd0-4e16-ab86-d9796619a5c4)


 7. **Add Test to the Models** - lineage **: Validate models are working, test for Referential integrity/ nulls 


![dbttest](https://github.com/user-attachments/assets/4d1ae81b-3d4c-404d-bc3f-b9fbd35980f5)

    
 9. **Document your Models** Add documentation to your models, share information with team and stakeholders

  ![documentation](https://github.com/user-attachments/assets/d05935b8-ea4b-4d32-be37-1f49ff1eb579)

 11. **Deploy your Models** Create and trigger Production jobs. As business picks up there is need to rebuild source tables and keep data up to date.
 12. 
![deploy](https://github.com/user-attachments/assets/61601082-2193-4174-b514-16ee932fd4e4)

     
    
