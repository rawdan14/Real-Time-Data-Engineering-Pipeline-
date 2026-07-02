# Real-Time OpenAQ Data Pipeline

A scalable, end-to-end data engineering project designed to ingest, process, and visualize environmental data in real-time while maintaining a historical batch archive.

## Architecture
![Architecture Diagram]()

## Overview
This pipeline follows a Lambda architecture to handle data in two ways:
1. **Speed Layer:** Real-time ingestion via Flume -> Kafka -> Spark -> InfluxDB -> Grafana.
2. **Batch Layer:** Long-term historical archiving via Flume -> Hadoop (HDFS).

## Tech Stack
* **Language:** Python
* **Data Ingestion:** Apache Flume
* **Message Broker:** Apache Kafka
* **Stream Processing:** Apache Spark
* **Databases:** InfluxDB (Time-series), Hadoop/HDFS (Batch)
* **Visualization:** Grafana

## Getting Started
1. **Producer:** Run `src/producer.py` to begin streaming data from the OpenAQ API.
2. **Pipeline:** Ensure your Kafka broker is active and your Flume agent is configured to tail the log output (`openaq_stream.log`).
3. **Analytics:** The data is pushed to InfluxDB; configure your Grafana data source to point to your InfluxDB instance.

## Security Warning
This repository uses an API Key. **Do not commit your real API Key.** Ensure you are using environment variables (e.g., `OPENAQ_API_KEY`) and that your `.env` file is listed in your `.gitignore`.
