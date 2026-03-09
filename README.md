<h1>⚡ Energy Forecasting Research Pipeline — Airflow + Deep Learning</h1>

<p>
  <img src="https://img.shields.io/badge/Airflow-Orchestration-017CEE?style=for-the-badge&logo=apacheairflow&logoColor=white"/>
  <img src="https://img.shields.io/badge/Models-LSTM%20%7C%20Transformer%20%7C%20SSL-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white"/>
  <img src="https://img.shields.io/badge/Storage-PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white"/>
  <img src="https://img.shields.io/badge/Container-Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white"/>
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge"/>
</p>

End-to-end data engineering and deep learning pipeline for building energy consumption forecasting.
Compares **LSTM**, **Transformer**, and **Self-Supervised Learning (SSL)** architectures on real building + weather data.

---

## 📌 What it does

Automates the full ML research workflow:

1. 📥 Ingests raw CSV datasets (building metadata + weather data)
2. 🔄 Cleans, transforms, and validates the data via Airflow DAG
3. 🗄️ Loads structured data into PostgreSQL
4. 🤖 Feeds prepared datasets into deep learning models
5. 📊 Produces reproducible experiment results across model architectures

---

## 🧠 Models

| Model | Purpose | Notes |
|-------|---------|-------|
| **LSTM** | Baseline time-series forecasting | Captures temporal dependencies |
| **Transformer** | Long-range pattern detection | Outperforms LSTM on complex sequences |
| **Self-Supervised (SSL)** | Robustness under sparse/noisy data | Pretrained then fine-tuned on labeled data |

SSL model evaluated under 3 conditions: ✅ clean data · ⚠️ sparse data · ❌ simulated sensor failures

---

## 🛠️ Stack

![Apache Airflow](https://img.shields.io/badge/Apache%20Airflow-017CEE?style=for-the-badge&logo=apacheairflow&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)
![Keras](https://img.shields.io/badge/Keras-D00000?style=for-the-badge&logo=keras&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)

---

## 📁 Project structure
```
airflow-energy-pipeline/
├── dags/
│   └── load_excel_to_postgres.py   # Airflow DAG
├── include/data/
│   ├── building_metadata.csv
│   └── weather.csv
├── src/                            # Model training scripts
├── figures/                        # Training curves & evaluation plots
├── tables/                         # Result tables
├── tests/dags/                     # DAG unit tests
├── Dockerfile
├── requirements.txt
└── README.md
```

---

## ▶️ How to run
```bash
# Start Airflow locally
astro dev start

# Trigger the DAG via Airflow UI at localhost:8080
# Or schedule it to run automatically
```

---

## 🔬 Research questions

- What impact does self-supervised pretraining have on forecasting robustness under sparse or noisy conditions?
- Does integrating physical constraints into deep learning models improve forecast accuracy vs purely data-driven approaches?

---

## 📊 Evaluation

Metrics used: **MAE**, training/validation loss curves, error distribution analysis, robustness comparison across clean/sparse/failure scenarios.

---

## 🔮 What I'd add next

- [ ] MLflow experiment tracking
- [ ] Automated model retraining on new data
- [ ] FastAPI endpoint for live energy forecasts
- [ ] Grafana dashboard for real-time monitoring
