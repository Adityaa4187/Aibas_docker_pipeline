# AI-Based Employee Attrition Risk Prediction Pipeline

This project delivers a complete **machine learning pipeline** for predicting employee attrition risk.  
It includes preprocessing, multiple model predictions, rule-based early risk scoring, and deployment-ready inference — all fully containerized using Docker.

The system is designed for **easy execution**, **portability**, and **reproducible ML deployment**.

---

## Project Overview

The system consists of two containerized stages:

| Stage | Purpose |
|------|---------|
| **Training Environment** | Generates evaluation reports and visualizations (models already pre-trained) |
| **Activation (Inference) Pipeline** | Uses trained models to predict attrition risk on new employee data |

You do **not** need to train models yourself — trained models and preprocessing artifacts are already packaged inside the deployment image.

---

## Machine Learning Models Included

- Ordinary Least Squares (OLS)  
- Logistic Regression  
- Random Forest  
- Artificial Neural Network (ANN)  
- Rule-based Early Attrition Risk Score  

---

## Prerequisites

Before running this project, ensure you have:

### 1️⃣ Docker Installed  
Install Docker Desktop (Windows/Mac) or Docker Engine (Linux).

### 2️⃣ Docker Hub Access  
A Docker Hub account is recommended so you can log in and pull the images.

---

# Step-by-Step Instructions

## Step 1 — Login to Docker Hub

```bash
docker login
```
Enter your Docker Hub username and password (or access token).


### Step 2 — Pull the Required Images
```bash
docker pull adityaa0403/aibas_knowledgebase:latest
docker pull adityaa0403/aibas_activation:latest
```
### Verify images are available locally:
```bash
docker images
```

## Step 3 — Clone This Repository
```bash
git clone https://github.com/Adityaa4187/Aibas_docker_pipeline.git
cd Aibas_docker_pipeline
```

This repository contains the Docker Compose files used to run the containers.


## Step 4 — Run the Training Container
This step generates model evaluation reports and plots.

```bash
docker compose up
```

After successful execution, results will be available in the following folders:

1. data/ (Scrapped data which)
2. reports/ (Preprocessing and model evaluation plots)
3. saved_models/ (Saved trained models)
4. out/ (Intermediate and processed datasets)
These folders are created/updated automatically.

## Step 5 — Run the Activation (Inference) Pipeline
This runs attrition risk prediction using the packaged trained models

```bash
docker compose -f docker-compose_activation.yml up
```
After successful execution, results will be available in the following folders:
1. reports/ (activation_risk_report.csv)


### Architecture
1. Training Container
2. Generates evaluation plots and reports
3. Used mainly for analysis and visualization

### Activation Container
1. Contains trained models and preprocessing pipeline
2. Performs inference on new employee data
3. Saves prediction results to reports/

This reflects real-world ML deployment practices where training and inference environments are separated.


