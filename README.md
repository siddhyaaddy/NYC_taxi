# urban-traffic-forecast

A full end-to-end ML pipeline project using the NYC Yellow Taxi trip data (2023–2024) built with AWS services. This pipeline ingests, processes, models, and visualizes taxi demand predictions using LightGBM models and a real-time dashboard powered by Streamlit.

---

## 📦 Project Overview

This project builds a **cloud-based machine learning pipeline** for forecasting hourly taxi demand across NYC using AWS Lambda, Glue, Athena, RDS, and Streamlit. The project includes:

- Raw data ingestion from the NYC Taxi data repo (2023 & 2024)
- ETL using AWS Glue
- Predictive modeling using LightGBM
- Prediction storage and querying via S3, Athena, and RDS
- A live Streamlit dashboard deployed on AWS Elastic Beanstalk

---

## 🛠️ Tech Stack

AWS Lambda – Automate data ingestion
AWS S3 – Data lake for raw, filtered, transformed, and prediction data
AWS Glue – Data transformation jobs & crawling
AWS Athena – SQL queries on transformed and prediction data
AWS RDS (PostgreSQL) – Central database for dashboard-ready predictions
LightGBM – ML models with lag-based and feature-based training
Streamlit + AWS Elastic Beanstalk – Visualize and interact with metrics in real time

---


## 🔁 Pipeline Architecture

```plaintext
S3 (raw) ──▶ Lambda (triggered) 
           └──▶ Glue Job (filter + transform)
                         └──▶ S3 (filtered, transformed)
                                       └──▶ Glue Crawler + Athena Table
                                                       └──▶ LightGBM Modeling
                                                                   └──▶ Predictions to S3 + RDS
                                                                                   └──▶ Streamlit Dashboard



```

---
## 📁 taxi-pipeline-forecast/
```
├── lambda/
│   ├── download_data.py
│   └── trigger_glue.py
├── glue/
│   ├── filter_transform_job.py
│   └── create_crawler.py
├── modeling/
│   ├── model_1_lag_features.py
│   ├── model_2_feature_selection.py
│   └── batch_inference.py
├── rds/
│   ├── postgres_uploader.py
│   └── schema.sql
├── streamlit_app/
│   ├── app.py
│   └── dashboard_utils.py
├── utils/
│   └── athena_queries.py
├── README.md


```

---

## 🧠 ML Models

Model 1: LightGBM with Lag Features
Uses 28-day lag values

Trained separately for:

Location ID 43

2 other selected locations

Model 2: LightGBM with Feature Selection
Max 10 features:

Mandatory: lag 1, 24, 48, 72, 96

Avg. across past 4 weeks

5 from feature importance

---

## 📊 Streamlit Dashboard
Hosted on AWS Elastic Beanstalk.
Main Features:

Tabs: Athena View | RDS View

Dropdown: Select 3 NYC locations

Metrics: MAE & MAPE for both models

Cache: Auto-invalidates at the top of every hour

---

📁 S3 Folder Structure
```
s3://<bucket_name>/taxi/
│
├── raw/year=<YYYY>/month=<MM>/
├── filtered/year=<YYYY>/month=<MM>/
├── transformed/year=<YYYY>/month=<MM>/
└── predictions/model=<model_id>/location_id=<ID>/year=<YYYY>/month=<MM>/day=<DD>/hour=<HH>/

```
---

## 🌐 Live Demo

🔗 Streamlit Dashboard – https://github.com/siddhyaaddy/NYC_taxi/blob/main/streamlit-frontend_v2-2025-03-06-08-03-78.mp4

---
