# NYC_taxi 🚖

A full end-to-end ML pipeline project using the NYC Yellow Taxi trip data (2023–2024).  
This pipeline ingests, processes, models, and visualizes taxi fare and trip predictions using **LightGBM models** and a real-time dashboard powered by **Streamlit**.

---

## 📦 Project Overview

This project builds a **local machine learning pipeline** for predicting taxi demand and trip fares across NYC.  

The project includes:
- Raw data ingestion from the NYC Taxi dataset (2023 & 2024)  
- Feature engineering and preprocessing pipelines  
- Predictive modeling using **LightGBM**  
- Batch and inference pipelines for model training and testing  
- A **Streamlit dashboard** for visualization and monitoring  

---

## 🛠️ Tech Stack

- **Python** – Data preprocessing, modeling, and pipelines  
- **Pandas / NumPy** – Data manipulation  
- **Scikit-learn / LightGBM** – Machine learning models  
- **Streamlit** – Interactive dashboard & visualization  
- **GitHub Actions** – CI/CD workflows for pipelines  
- **Jupyter Notebooks** – Exploratory data analysis and experiments  

---

## 🔁 Pipeline Architecture

```plaintext
NYC Taxi Data 
   └──▶ Feature Pipeline (feature_pipeline.yaml)
   └──▶ Model Training Pipeline (model_training_pipeline.yaml)
   └──▶ Inference Pipeline (inference_pipeline.yaml)
                 └──▶ Predictions + Metrics
                               └──▶ Streamlit Dashboard
