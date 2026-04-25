# Airflow Energy Forecasting Pipeline 🔋

**End-to-end ML pipeline: Airflow orchestration + LSTM/Transformer/SSL for building energy forecasting**  
1,000+ buildings · MSc Data Science research · Fully containerized with Docker

---

## Overview

A production-style data engineering and deep learning research pipeline that automates the full journey from raw CSV ingestion to trained forecasting models — built as part of MSc Data Science research on self-supervised learning for energy systems.

**Research questions addressed:**
- Does self-supervised pretraining improve model robustness under sensor failure and sparse data?
- How do LSTM, Transformer, and SSL models compare on building energy consumption forecasting?

---

## Results

| Model | Dataset | Key Finding |
|---|---|---|
| LSTM | ASHRAE (1,000+ buildings) | Baseline temporal model |
| Transformer | ASHRAE (1,000+ buildings) | Better on complex patterns |
| SSL pretrained | ASHRAE (1,000+ buildings) | Most robust under sensor failure simulation |

SSL pretraining improved robustness in sparse data and simulated sensor-failure scenarios — validating the research hypothesis.

---

## Architecture

```
Raw CSV Data (ASHRAE dataset)
   ↓
[Airflow DAG] — scheduled ingestion & transformation
   ↓
[PostgreSQL] — structured storage (building + weather tables)
   ↓
[Deep Learning Models]
   ├── LSTM          — temporal baseline
   ├── Transformer   — long-range dependency capture  
   └── SSL           — self-supervised pretraining → fine-tune
   ↓
Model outputs: MAE, loss curves, prediction vs actual plots
```

---

## Pipeline stages

### 1. Extract
- Reads ASHRAE building metadata and weather CSV files
- Handles multiple building types across 1,000+ sites

### 2. Transform
- Standardizes column names and timestamps
- Handles missing values and sensor anomalies
- Prepares feature matrices for time-series models

### 3. Load
- Stores structured data into PostgreSQL (`building`, `weather` tables)
- Enables reproducible dataset generation across experiments

### 4. Model training
- Airflow DAG triggers model training after data load
- Each model variant (LSTM/Transformer/SSL) runs independently
- Results exported to `/figures/` for research report

---

## Tech stack

| Component | Technology |
|---|---|
| Orchestration | Apache Airflow (Astro Runtime) |
| Containerization | Docker + Docker Compose |
| Storage | PostgreSQL |
| Data processing | Python · Pandas · NumPy |
| Deep learning | TensorFlow · Keras |
| DB inspection | pgAdmin |

---

## Project structure

```
airflow-energy-pipeline/
├── dags/
│   └── load_excel_to_postgres.py    # Main Airflow DAG
├── src/
│   └── models/                      # LSTM, Transformer, SSL implementations
├── include/data/
│   ├── building_metadata.csv        # ASHRAE building metadata
│   └── weather.csv                  # Weather feature data
├── figures/                         # Model output charts (loss curves, predictions)
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
└── config.yaml
```

---

## How to run

```bash
# Start Airflow (requires Astro CLI)
astro dev start

# Or with Docker Compose directly
docker-compose up -d

# Trigger DAG manually
airflow dags trigger load_excel_to_postgres
```

---

## Model outputs

The pipeline generates:
- Training/validation loss curves per model
- Prediction vs actual energy consumption plots
- Error distribution analysis across clean, sparse, and sensor-failure scenarios
- Performance comparison: LSTM vs Transformer vs SSL

All figures used in the MSc research report were generated from data prepared by this pipeline.

---

## Related projects

- [Support Mail Agent](https://github.com/suhasvenkat/Support_Mail_Agent) — RAG pipeline with LangGraph + FAISS · [Live Demo](https://supportmailagent-fkhguftdphxuvvhkkj7fmh.streamlit.app)
- [Bone Fracture Detection](https://github.com/suhasvenkat/bone-fracture-detection) — ResNet-50, 88% accuracy · [Live Demo](https://bone-fracture-detection-ayxoamgewsy78kfc5ajtxp.streamlit.app/)

---

**Built by [Suhas Venkat](https://suhasvenkat.github.io)** · [LinkedIn](https://linkedin.com/in/suhas-venkat)
