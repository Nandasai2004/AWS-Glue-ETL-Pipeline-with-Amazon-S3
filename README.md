# AWS Glue ETL Pipeline with Amazon S3

## 📌 Project Overview

This project demonstrates how to build an ETL (Extract, Transform, Load) pipeline using **Amazon S3 and AWS Glue**. Employee data is stored in Amazon S3, discovered using an AWS Glue Crawler, transformed using an AWS Glue ETL job, and stored in a curated S3 folder in Parquet format for efficient analysis.

## 🎯 Aim

To design and implement an AWS Glue ETL pipeline with Amazon S3 to extract, clean, transform, and load employee data for further analysis.

## 🎯 Objectives

- Store raw employee data in Amazon S3.
- Use AWS Glue Crawler to identify the data schema.
- Create metadata in the AWS Glue Data Catalog.
- Clean and transform employee data using PySpark.
- Filter records based on salary and remove missing values.
- Store transformed data in Parquet format in Amazon S3.
- Prepare data for analysis using Amazon Athena.

## 🛠️ Technologies Used

- **Amazon S3** – Storage for raw and processed data.
- **AWS Glue** – ETL processing service.
- **AWS Glue Crawler** – Automatic schema discovery.
- **AWS Glue Data Catalog** – Metadata management.
- **PySpark** – Data cleaning and transformation.
- **AWS IAM** – Access control and permissions.
- **Amazon Athena** – SQL-based data analysis (optional).

## 🏗️ Architecture

```text
Employee CSV File
       |
       v
Amazon S3 (raw/)
       |
       v
AWS Glue Crawler
       |
       v
AWS Glue Data Catalog
       |
       v
AWS Glue ETL Job
   (PySpark)
       |
       v
Data Cleaning and Transformation
       |
       v
Amazon S3 (curated/)
   (Parquet Format)
       |
       v
Amazon Athena
   (Optional Analysis)
```

## 📂 S3 Bucket Structure

```text
your-s3-bucket/
├── raw/
│   └── employees.csv
└── curated/
    ├── part-00000-....snappy.parquet
    └── _SUCCESS
```

## 📊 Dataset Description

The project uses an employee dataset containing the following columns:

| Column | Description |
|---|---|
| employee_id | Unique employee identifier |
| name | Employee name |
| department | Employee department |
| salary | Employee salary |
| city | Employee city |

## ⚙️ Implementation Steps

### Step 1: Upload Raw Data

Create an Amazon S3 bucket and upload `employees.csv` into the `raw/` folder.

### Step 2: Configure IAM Permissions

Create or select an IAM role for AWS Glue with the required permissions to read from the source S3 folder, write to the destination folder, access the Data Catalog, and publish logs.

### Step 3: Create an AWS Glue Crawler

Configure the crawler to scan the `raw/` folder and create a table in the Glue Data Catalog database.

### Step 4: Create the ETL Job

Create an AWS Glue Spark job using Python and PySpark. Read employee data from the Glue Data Catalog.

### Step 5: Transform the Data

Perform the following operations:

- Remove records with missing required fields.
- Trim unnecessary spaces from text columns.
- Standardize department names to uppercase.
- Convert salary values into numeric format.
- Filter employees whose salary is greater than ₹50,000.

### Step 6: Store Processed Data

Write the transformed data in Parquet format to the `curated/` folder in Amazon S3.

### Step 7: Verify the Output

Run the Glue job and verify that it succeeds. Check the output files in S3. Optionally, use Amazon Athena to query the processed dataset.

## 🔄 ETL Process

- **Extract:** Read employee data from Amazon S3 through the Glue Data Catalog.
- **Transform:** Clean, format, and filter the employee records using PySpark.
- **Load:** Store the transformed data in Parquet format in Amazon S3.

## ✅ Expected Outcome

The pipeline produces a cleaned and transformed employee dataset in Parquet format. This data is stored in Amazon S3 and is ready for further querying and analysis.

## 🔐 Security Considerations

- Follow the principle of least privilege for IAM permissions.
- Restrict access to the required S3 bucket and folders.
- Avoid storing AWS access keys or credentials in source code.
- Review Glue job logs to troubleshoot errors.

## 🚀 Future Enhancements

- Automate the pipeline using Amazon EventBridge and AWS Glue triggers.
- Add data quality checks and error handling.
- Use Amazon Athena for advanced analytical queries.
- Integrate Amazon QuickSight for dashboards and reporting.
- Implement notifications for job success or failure.

## 📚 Conclusion

This project demonstrates how Amazon S3 and AWS Glue can be used to build a scalable cloud-based ETL pipeline. It provides practical experience in data ingestion, schema discovery, data transformation, and preparing structured data for analytics.

## 👨‍💻 Author

**Nanda Sai**

GitHub: [Nandasai2004](https://github.com/Nandasai2004)
