# REST API Ingestion & Normalization Pipeline

## Overview
A production-grade pipeline that ingests data from public REST APIs, normalizes nested JSON structures, and loads results into PostgreSQL with a versioned schema. Designed for reliability with retry logic, idempotency, and incremental extraction.

## Architecture
- **Extract**: httpx-based async API client with OAuth/API key auth, rate limit handling, exponential backoff, and pagination
- **Transform**: JSON flattening, type casting, deduplication, and schema validation
- **Load**: PostgreSQL with upsert/merge patterns for idempotent reloads
- **Orchestration**: Airflow DAG with SLA monitoring and Slack alerting on failure
- **Infrastructure**: Docker Compose (Airflow + PostgreSQL), AWS S3 for raw JSON archival

## Tech Stack
- Python 3.11+, httpx, Pandas
- PostgreSQL 15, SQLAlchemy, Alembic
- Apache Airflow 2.x
- Docker & Docker Compose
- AWS S3 / MinIO

## What This Demonstrates
- REST API consumption with production-grade error handling
- JSON normalization and schema design
- Idempotent load patterns (upsert)
- Airflow DAG design with failure recovery
- Schema versioning with database migrations

## Status
🚧 In Development

## Project Structure
├── dags/
│   └── api_ingestion_dag.py
├── src/
│   ├── extract/
│   ├── transform/
│   └── load/
├── migrations/
├── tests/
├── docker-compose.yml
└── README.md
