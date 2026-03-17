# 🏏 T20-World-Cup-2026-Data-Engineering-Pipeline-using-Azure-Databricks


## 📌 Project Overview

This project demonstrates an **end-to-end Data Engineering pipeline** built using **Azure Data Lake and Azure Databricks**.
The pipeline processes cricket tournament data and generates analytical insights using the **Medallion Architecture (Bronze, Silver, Gold layers)**.

---

## 📊 Dataset

The dataset is based on the **ICC Men's T20 World Cup 2026** and contains multiple CSV files including:

* matches.csv
* batting_stats.csv
* bowling_stats.csv
* points_table.csv
* venues.csv
* squads.csv
* awards.csv

---

## 🏗️ Architecture

The project follows **Medallion Architecture**:

### 🔹 Bronze Layer

* Raw data stored in Azure Data Lake
* No transformations

### 🔹 Silver Layer

* Cleaned and processed data
* Removed null values and duplicates

### 🔹 Gold Layer

* Business insights and analytics

---

## ⚙️ Technologies Used

* Azure Data Lake Storage
* Azure Databricks
* Apache Spark (PySpark)
* Unity Catalog
* Delta Lake

---

## 🔄 Data Pipeline Flow

```
Raw CSV Data
     ↓
Azure Data Lake (Bronze Layer)
     ↓
Data Cleaning (Silver Layer)
     ↓
Analytical Tables (Gold Layer)
     ↓
Dashboard Visualization
```

---

## 📈 Key Insights Generated

* Top 10 Batsmen by Runs
* Top 10 Bowlers by Wickets
* Team Performance (Win Percentage)
* Best All-Rounders
* Matches by Venue
* Teams with Most Awards
* Final Match Result

---

## 📊 Dashboard

A dashboard was created using Databricks to visualize:

* Player performance
* Team performance
* Venue statistics
* Award distribution

---

## 🔐 Data Governance

* Implemented using **Unity Catalog**
* Used **External Locations and Storage Credentials**
* Ensured secure access to data

---

## ⚡ Features

* Scalable data processing using Apache Spark
* ACID transactions using Delta Lake
* Clean architecture using Medallion design pattern

---

## 🚀 Conclusion

This project demonstrates how to build a scalable and reliable data pipeline using Azure cloud services and Databricks to transform raw data into meaningful insights.

---

## 👤 Author

Your Name
