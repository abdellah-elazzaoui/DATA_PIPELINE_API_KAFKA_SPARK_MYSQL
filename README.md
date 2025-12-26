# DATA_PIPELINE_API_KAFKA_SPARK_MYSQL
This project builds a real-time data pipeline using Airflow, Kafka, and Spark. It streams user data from an API to Kafka, processes it with Spark Streaming, and stores results in MySQL. The entire system runs in Docker containers for easy deployment and scalability, enabling efficient data ingestion and transformation workflows.


Real-Time Data Pipeline with Airflow, Kafka, and Spark
📋 Project Overview
A scalable real-time data pipeline that streams user data from external APIs, processes it through Kafka, transforms with Spark, and stores in MySQL. The entire system runs in Docker containers for easy deployment.

🏗️ Architecture
text
API → Airflow → Kafka → Spark Streaming → MySQL
🚀 Features
Real-time Data Ingestion: Stream user data from randomuser.me API

Event Streaming: Apache Kafka for message queuing and distribution

Data Processing: Apache Spark for real-time transformations

Orchestration: Apache Airflow for workflow management

Containerized: Full Docker deployment with isolated services

Data Storage: MySQL for structured data persistence

Interactive Analytics: Jupyter notebooks for data exploration

🛠️ Tech Stack
Apache Airflow 2.6.0 - Workflow orchestration

Apache Kafka 7.4.0 - Event streaming platform

Apache Spark 3.5.1 - Data processing engine

MySQL 8.0 - Relational database

Docker & Docker Compose - Containerization

Python 3.9 - Programming language

Jupyter Notebook - Interactive development

📁 Project Structure
text
data-platform/
├── docker-compose.yml          # Multi-container setup
├── airflow/
│   ├── dags/                   # Airflow workflows
│   ├── logs/                   # Airflow execution logs
│   └── plugins/                # Custom Airflow plugins
├── notebooks/                  # Jupyter notebooks
├── data/                       # Sample datasets
└── requirements.txt            # Python dependencies
🚦 Quick Start
Prerequisites
Docker & Docker Compose

8GB+ RAM recommended

Git

Installation
bash
# Clone the repository
git clone <repository-url>
cd data-platform

# Start all services
docker-compose up -d

# Wait for services to initialize (2-3 minutes)
docker-compose logs -f
🌐 Services & Ports
Airflow UI: http://localhost:8080 (admin/admin)

Kafka: localhost:9092 (external), ed-kafka:29092 (internal)

Spark Master: http://localhost:8082

Jupyter: http://localhost:8888 (no password)

MySQL: localhost:3306

Zookeeper: localhost:2181

📊 Data Pipeline Flow
Data Generation: Airflow DAG fetches random user data from API

Message Queue: Data published to Kafka topic users

Stream Processing: Spark reads from Kafka, transforms data

Data Storage: Processed data saved to MySQL users table

Monitoring: Airflow monitors pipeline health and execution

🧪 Running the Pipeline
Access Airflow at http://localhost:8080

Enable KAFKA_STREAM_API DAG

Trigger the DAG manually or let it run on schedule

Monitor Spark processing in Jupyter notebooks

Query results in MySQL: SELECT * FROM kafka_spark.users;

🔧 Configuration
Airflow Connections
Create MySQL connection in Airflow:

Connection ID: mysql_conn

Host: host.docker.internal

Schema: kafka_spark

Login: root

Password: YOUR_PASSWORD

Port: 3306

Kafka Topics
bash
# Create topic manually
docker exec ed-kafka kafka-topics --create \
  --topic users \
  --partitions 3 \
  --replication-factor 1 \
  --bootstrap-server ed-kafka:29092
🐛 Troubleshooting
Common Issues
Kafka connection errors: Check if ed-kafka:29092 is accessible

MySQL connection failed: Verify MySQL is running on host

Spark driver issues: Ensure sufficient memory allocation

DAG not triggering: Check Airflow scheduler logs

Useful Commands
bash
# Check service status
docker-compose ps

# View logs
docker-compose logs -f <service_name>

# Restart services
docker-compose restart airflow-webserver

# Scale Spark workers
docker-compose up -d --scale spark-worker=2
📈 Monitoring
Airflow: Built-in UI with task execution graphs

Spark: Web UI at http://localhost:8082

Kafka: Use kafka-console-consumer for message inspection

MySQL: Monitor with SHOW PROCESSLIST;

🔄 Extending the Project
Add data validation steps in Spark

Implement error handling and retry logic

Add data quality checks

Extend to additional data sources

Implement alerting for pipeline failures

📚 Learning Resources
Apache Airflow Documentation

Apache Kafka Docs

Spark Streaming Guide

Docker Compose Reference

👥 Contributors
Abdellah - Project Architect & Developer

📄 License
MIT License - See LICENSE file for details

🤝 Contributing
Fork the repository

Create a feature branch

Commit changes

Push to the branch

Open a Pull Request

Note: This is a demonstration project for educational purposes. For production use, consider security hardening, monitoring, and scalability improvements.

🆘 Support
For issues and questions:

Check the troubleshooting section

Review service logs

Open an issue in the repository

⭐ If you find this project useful, please give it a star! ⭐

