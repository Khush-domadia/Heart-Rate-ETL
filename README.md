# Heart Rate ETL Pipeline

Modern, production-grade data pipeline processing synthetic heart rate streams from generation to analytics-ready warehouse. Built incrementally with best-in-class open-source tools.

## Recent Progress
- **Commit 1 (Setup)**: Project structure, `.github/workflows` for CI/CD (auto-README), `.gitignore`, `mock-data/` folder, `requirements.txt`.
- **Commit 2 (Core Ingestion & Transform)**: Added `airbyte/` (connectors for S3 → Snowflake ingestion from Kafka streams) and `dbt/` (staging models for data cleaning/feature engineering on heart rate signals).

## Tech Stack
- **Data Generation**: Python + Faker (user/activity/heart rate simulators)
- **Streaming**: Kafka + Confluent Cloud (real-time heart rate events)
- **Storage**: AWS S3 (data lake)
- **Ingestion**: Airbyte (S3 → Snowflake)
- **Transformation**: dbt (raw → staging → serving layers)
- **Orchestration**: Dagster (asset pipelines)
- **Visualization**: Tableau (semantic layer/dashboards)

## Local Setup
1. Clone: `git clone https://github.com/Khush-domadia/Heart-Rate-ETL.git`
2. Install deps: `pip install -r requirements.txt`
3. Config: Update `airbyte/` YAMLs and `dbt/profiles.yml` with your creds (Confluent, S3, Snowflake).
4. Test ingestion: Run Airbyte connectors locally.

## Run ETL (Current)
- Airbyte: `airbyte/` syncs Kafka-parsed heart rate data to Snowflake.
- dbt: `cd dbt && dbt run --models staging+` (transforms BPM anomalies, aggregates sessions).

## Next Up (Commit 3 Preview)
- Dagster assets for end-to-end orchestration.
- Data generation producers (`producer.py`).
- Tests (pytest), full CI/CD workflows, deployment docs.

Star/fork for updates! Contributions welcome.

