# enterprise-claims-modernization-platform
End-to-end fraud detection system using Azure Lakehouse, MLflow, Dataiku, FastAPI, and RAG-based explainable AI.
# Enterprise Claims Modernization Platform

### Azure Lakehouse + Dataiku + MLflow + GenAI + MLOps

## Overview

Healthcare insurance companies often rely on legacy ETL pipelines, manual claim reviews, and fragmented analytics systems. These limitations slow fraud detection, reduce transparency, and make it difficult for analysts to explain decisions.

This project modernizes the claims processing pipeline using a **cloud-native Lakehouse architecture** combined with **machine learning, RAG-based explainability, and production-grade deployment**.

The platform ingests healthcare claims data, processes it using the **Medallion Architecture**, trains a fraud detection model, exposes predictions through an API, and provides explainable insights through a **Retrieval Augmented Generation (RAG)** system.

---

# Business Problem

Insurance companies face several operational challenges:

* Legacy ETL pipelines that are difficult to scale
* Slow or manual fraud detection
* Lack of centralized analytics
* Unstructured medical documentation
* Limited explainability for model predictions

This platform addresses these challenges by building a modern **AI-enabled fraud detection system**.

---

# Key Capabilities

* Modern **Azure Lakehouse architecture**
* Automated **fraud risk scoring**
* **RAG-powered explanations** using LLMs
* **ML lifecycle management with MLflow**
* **Dataiku orchestration for feature engineering and ML governance**
* Containerized **FastAPI prediction service**
* **Power BI dashboard** for business insights

---

# Architecture

The system follows a layered architecture:

```
Data Sources
   ↓
Azure Data Factory
   ↓
Azure Data Lake (Bronze)
   ↓
Databricks + Delta Lake (Silver)
   ↓
Dataiku (Feature Engineering + ML + RAG orchestration)
   ↓
MLflow Model Registry
   ↓
Fraud Probability Output (Gold Layer)
   ↓
FastAPI (Dockerized API)
   ↓
Power BI Dashboard
   ↓
RAG System for Explanations
```

---

# Data Sources

The project uses healthcare datasets representing real insurance workflows.

### Structured Data

* Inpatient claims
* Outpatient claims
* Beneficiary information
* Provider fraud labels

### Unstructured Data

* Medical transcription notes used for RAG-based explanation.

---

# Medallion Data Architecture

### Bronze Layer

Raw data ingestion stored in Azure Data Lake.

Examples:

* inpatient claims
* outpatient claims
* beneficiary data
* provider fraud labels
* doctor notes

### Silver Layer

Cleaned and joined datasets.

Operations include:

* Schema normalization
* Missing value handling
* Feature preparation
* Data enrichment

Output dataset:

```
claims_enriched
```

### Gold Layer

Business-level datasets used by analytics and applications.

Examples:

* fraud risk scores
* provider risk metrics
* claim volume trends

---

# Machine Learning Pipeline

Fraud detection is implemented using supervised machine learning.

### Features

Examples of engineered features:

* Claim frequency per beneficiary
* Average claim amount per provider
* Chronic condition indicators
* Historical fraud risk signals

### Models Evaluated

* Random Forest
* XGBoost

### Model Lifecycle

Experiments and models are tracked using **MLflow**.

Steps:

1. Model training
2. Performance evaluation
3. Experiment comparison
4. Model registration

Output:

```
Fraud Probability Score (0–1)
```

---

# RAG-Based Explainability

Fraud predictions alone are not enough. Analysts must understand **why** a claim was flagged.

This platform implements **Retrieval Augmented Generation (RAG)**.

### Workflow

1. Doctor notes are chunked
2. Embeddings are generated
3. Vectors stored in a search index
4. Relevant documents retrieved
5. LLM generates contextual explanation

Example user query:

```
Why was this claim marked high risk?
```

The system retrieves related medical context and produces a natural-language explanation.

---

# API Layer

A containerized **FastAPI service** exposes fraud predictions and explanations.

Endpoints:

```
POST /predict
POST /explain
```

### Example Response

```
{
  "claim_id": "C10231",
  "fraud_probability": 0.87,
  "risk_level": "High"
}
```

---

# Dashboard

A Power BI dashboard provides executive-level visibility.

Key insights include:

* Fraud rate trends
* High-risk providers
* Monthly claim volumes
* Risk distribution

---

# Technology Stack

### Cloud & Infrastructure

* Azure Data Factory
* Azure Data Lake Storage Gen2
* Azure Databricks
* Delta Lake

### Data Science & ML

* Dataiku
* MLflow
* Python
* PySpark

### Generative AI

* Azure OpenAI
* Vector Search

### Deployment

* FastAPI
* Docker

### Visualization

* Power BI

---

# Repository Structure

```
enterprise-claims-modernization-platform/

architecture/
databricks/
dataiku/
ml/
rag/
api/
deployment/
dashboard/
README.md
```

---

# Future Enhancements

Possible improvements include:

* Real-time claim scoring using streaming pipelines
* Model drift monitoring
* Automated retraining workflows
* Fraud network graph analysis
* Interactive AI investigation assistant

---

# Author

Project developed as part of an enterprise-scale data and AI architecture study combining **data engineering, machine learning, and generative AI**.
