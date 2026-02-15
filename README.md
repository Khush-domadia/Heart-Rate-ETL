# Heart Rate ETL Pipeline

Modern data pipeline processing synthetic heart rate streams from generation to analytics-ready warehouse.

## Current Progress (Initial Setup)
- **Project structure** with `.github/workflows` for CI/CD
- **`.gitignore`** for clean repository management
- **Mock data generation** structure in `mock-data/` folder
- **Dependencies** listed in `requirements.txt`

## Tech Stack (Planned)
- **Data Generation**: Python + Faker library
- **Streaming**: Kafka + Confluent Cloud
- **Storage**: AWS S3 data lake
- **Ingestion**: Airbyte (S3 → Snowflake)
- **Transformation**: dbt (staging → serving layers)
- **Orchestration**: Dagster (asset-based workflows)
- **Visualization**: Tableau semantic layer

## Next Steps
1. Data generation scripts (`producer.py`, user/activity generators)
2. Streaming pipeline (Kafka → S3)
3. dbt transformation models
4. Dagster orchestration
5. Full deployment configs and docs

Stay tuned for incremental updates!
