# FedEx Tracking Analytics Pipeline using Microsoft Fabric

##  Overview
This project demonstrates an **end-to-end data engineering pipeline** built using **Microsoft Fabric** to ingest, process, and visualize FedEx shipment tracking data.

The solution integrates with the **FedEx API**, processes data using a **Medallion architecture (Bronze, Silver, Gold)**, and delivers insights through a dashboard.

---

##  Problem Statement
Tracking shipments manually for IT equipment  via the FedEx portal which is inefficient and lacks centralized visibility.

Organizations need:
- Real-time shipment tracking for sending and returing IT equipment.
- Centralized reporting
- Actionable insights on delivery performance

---

## Solution
This project automates shipment tracking by:
- Extracting tracking numbers from source data (FedEx portal export)
- Calling the FedEx Tracking API using OAuth authentication
- Processing and transforming data using PySpark
- Storing data in a Lakehouse using Medallion architecture
- Creating dashboard-ready tables for reporting

---

## Architecture

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/0b527f94-c364-4098-8be4-c6cf4aeec1b9" />


---

## Tech Stack

- Microsoft Fabric (Data Factory, Lakehouse)
- PySpark (Notebooks)
- REST API (FedEx API)
- Delta Tables
- Power BI

---

## Data Pipeline Flow

### 1. Data Ingestion
- Tracking numbers are loaded into `input_tracking_numbers`
- Source: FedEx portal export (CSV)

### 2. API Integration
- OAuth token generated using Web Activity
- Notebook calls FedEx Tracking API
- Supports batching (up to 30 tracking numbers per request)

### 3. Data Storage

#### 🥉 Bronze Layer
- Stores raw API response
- Table: `bronze_fedex_tracking_raw`

#### 🥈 Silver Layer
- Parsed and structured tracking data
- Table: `silver_fedex_tracking`

#### 🥇 Gold Layer
- Aggregated metrics for reporting
- Tables:
  - `gold_fedex_dashboard`
  - `gold_fedex_status_breakdown`

---

## Key Features

- OAuth-based API authentication
- Batch processing for scalability
- Medallion architecture (Bronze → Silver → Gold)
- Incremental data loading (snapshot-based history)
- Automated pipeline orchestration
- Dashboard-ready data models

---

## Project Structure

/notebooks
└── fedex_tracking_pipeline.ipynb

/pipeline
└── fedex_pipeline.json

/data
└── sample_tracking_numbers.csv

/README.md


---

## Limitations

- FedEx Tracking API requires tracking numbers as input  
- Cannot directly fetch all shipments from FedEx portal  
- Requires external source (CSV/API) for tracking numbers  

---

## Future Enhancements

- Automate ingestion of portal export files  
- Integrate with FedEx Ship API  
- Add incremental processing & deduplication  
- Build SLA and delivery performance metrics  
- Enable real-time tracking via webhooks  

## Author
Sridhar Gundumalla

