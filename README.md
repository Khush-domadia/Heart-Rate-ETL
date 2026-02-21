# Heart Rate ETL Pipeline 🚀

Production-grade, modern data pipeline processing **synthetic heart rate streams** from generation to analytics-ready Snowflake warehouse. Built with Airbyte, dbt, Dagster for scalable, observable ETL.

[![Dagster](https://dagster.io/badges/prod.svg)](https://dagster.io) [![Airbyte](https://img.shields.io/badge/Airbyte-Active-brightgreen)](https://airbyte.com) [![dbt](https://img.shields.io/badge/dbt-Core-blue)](https://getdbt.com)

## Architecture

Faker Producers → Kafka (Confluent) → Airbyte (S3→Snowflake) → dbt (staging→serving) → Dagster (orchestration) → Tableau

- **Data Generation**: Realistic heart rate signals (BPM, HRV, anomalies) via Faker/Python producers.
- **Streaming**: Kafka topics for real-time user/activity/heart-rate events.
- **Ingestion**: Airbyte connectors sync S3-parsed streams to Snowflake.
- **Transformation**: dbt models (staging → mart layers with session aggregates, anomaly detection).
- **Orchestration**: Dagster assets/pipelines for dependency-aware scheduling.

## Quick Start 🛫

### Prerequisites

- Python 3.10+, Docker
- Accounts: Confluent Cloud (Kafka), AWS S3, Snowflake, Dagster Cloud (optional)

### Clone & Setup

```bash
git clone https://github.com/Khush-domadia/Heart-Rate-ETL.git
cd Heart-Rate-ETL
pip install -r requirements.txt
```

Run Pipeline
# 1. Generate data to Kafka
python src/producer.py

# 2. Airbyte sync (Docker)
docker run --config airbyte/config.yaml airbyte/source-kafka

# 3. dbt transform
cd dbt && dbt run --models +staging+mart

# 4. Dagster orchestrate (full pipeline)
dagster dev -m heart_rate_etl

Project Structure
# 1. Generate data to Kafka
python src/producer.py

# 2. Airbyte sync (Docker)
docker run --config airbyte/config.yaml airbyte/source-kafka

# 3. dbt transform
cd dbt && dbt run --models +staging+mart

# 4. Dagster orchestrate (full pipeline)
dagster dev -m heart_rate_etl

Key Features
Observable: Dagster asset lineage, dbt docs.

Scalable: Kafka streaming, Snowflake serving layer.

Tested: 100% pytest coverage for extract/transform/load.

CI/CD: GitHub Actions auto-test/deploy.

Teck Stack
| Layer       | Tools            |
| ----------- | ---------------- |
| Generate    | Python, Faker    |
| Stream      | Kafka, Confluent |
| Ingest      | Airbyte          |
| Transform   | dbt              |
| Orchestrate | Dagster          |
| Warehouse   | Snowflake, S3    |
| Viz         | Tableau          |

Development
# Tests
pytest tests/

# Dagster UI (localhost:3000)
dagster dev

# dbt docs
cd dbt && dbt docs generate && dbt docs serve
ß
