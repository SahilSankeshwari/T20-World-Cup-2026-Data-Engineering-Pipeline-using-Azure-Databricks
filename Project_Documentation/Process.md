# 📘 End-to-End Project Process – T20 Data Engineering Pipeline

## 📌 Step 1: Dataset Collection

* Dataset taken from Kaggle : https://www.kaggle.com/code/ibrahimqasimi/data-analysis-icc-men-s-t20-world-cup-2026/input?select=venues.csv
* Contains cricket data:

  * matches.csv
  * batting_stats.csv
  * bowling_stats.csv
  * points_table.csv
  * venues.csv
  * squads.csv
  * awards.csv

👉 Purpose: Raw data for pipeline

---

## 📌 Step 2: Azure Resource Setup

### 🔹 Created Resource Group

* Name: RG_Project
* Purpose: To manage all Azure services in one place

<img width="940" height="508" alt="image" src="https://github.com/user-attachments/assets/147ed8cc-6336-4fd4-9f00-73cc82aa3846" />

---

### 🔹 Created Storage Account

* Used for storing data lake files
* Created containers:

  * bronze → raw data
  * external → managed storage for Unity Catalog

<img width="940" height="506" alt="image" src="https://github.com/user-attachments/assets/05aa0a8b-d5c8-4b70-9122-9bdd6ca72223" />

---

### 🔹 Uploaded Data

* Uploaded all CSV files into:

```bash
bronze container
```

<img width="940" height="508" alt="image" src="https://github.com/user-attachments/assets/fae74045-1690-47b8-85d5-223e32bb8133" />

---

## 📌 Step 3: Azure Databricks Setup

* Created Azure Databricks service
* Workspace launched successfully

---

## 📌 Step 4: Access Connector (Important)

* Created Access Connector for Databricks
* Connected Storage Account using IAM

👉 Purpose:

* Allow Databricks to access Azure Storage securely

---

## 📌 Step 5: Unity Catalog Setup

### 🔹 Login

* Logged into:

```bash
accounts.azuredatabricks.net
```

---

### 🔹 Created Metastore

* Name: project_metastore

👉 Purpose:

* Central metadata management

<img width="940" height="502" alt="image" src="https://github.com/user-attachments/assets/64584fea-32a5-4c3c-b6a8-5e46fbc39b01" />

---

### 🔹 Assigned Storage Path

* Connected external container path

👉 Purpose:

* Store table data (Delta files)

---

### 🔹 Assigned Admin

* Set my account as metastore admin

---

## 📌 Step 6: Databricks Configuration

### 🔹 Created Catalog

```sql
CREATE CATALOG t20_catalog;
```

---

### 🔹 Created Schemas

```sql
CREATE SCHEMA bronze;
CREATE SCHEMA silver;
CREATE SCHEMA gold;
```

---

### 🔹 Created Storage Credential

👉 Purpose:

* Secure authentication to storage

---

### 🔹 Created External Locations

* bronze location
* silver location
* gold location

👉 Purpose:

* Connect Databricks to Azure storage paths

---

## 📌 Step 7: Bronze Layer

* Loaded raw data from storage
* Stored as Delta tables

Example:

```python
df.write.format("delta").saveAsTable("bronze.matches")
```

👉 No transformation

---

## 📌 Step 8: Silver Layer (Data Cleaning)

Performed:

* Null value handling
* Duplicate removal
* Data type correction

Example:

```python
df.fillna().dropDuplicates()
```

👉 Clean structured data

---

## 📌 Step 9: Gold Layer (Insights)

Created analytical tables:

* Top Batsmen
* Top Bowlers
* Team Performance
* Best All-Rounders
* Matches by Venue
* Final Match Result

👉 Business insights layer

---

<img width="940" height="505" alt="image" src="https://github.com/user-attachments/assets/f092e6af-9ed8-4a2f-92b0-001282e5b9d5" />

---

## 📌 Step 10: Dashboard Creation

* Created dashboard in Databricks
* Used gold tables

👉 Visualizations:

* Bar charts
* Player analysis
* Team performance

---

<img width="1915" height="1030" alt="image" src="https://github.com/user-attachments/assets/6f43201f-2f75-4091-87e6-0af6dfeab5bf" />

---

## 📌 Step 11: Data Storage Format

Used:

* Delta Lake format

👉 Benefits:

* ACID transactions
* Faster queries
* Version control

---

## 📌 Step 12: Project Architecture

```bash
Raw Data → Bronze → Silver → Gold → Dashboard
```

---

## 📌 Step 13: Key Learnings

* Azure Data Lake
* Databricks & PySpark
* Unity Catalog
* Delta Lake
* Medallion Architecture

---

## 📌 Step 14: Challenges Faced

* Understanding Unity Catalog
* Setting external locations
* Handling schema issues

👉 Resolved using practice and debugging

---

## 📌 Step 15: Conclusion

Successfully built an end-to-end data pipeline using Azure and Databricks to transform raw cricket data into meaningful insights.

---
## 📊 Step 16: Insights Explanation

After processing the data through Bronze, Silver, and Gold layers, meaningful insights were generated to understand player performance, team performance, and match statistics.

---

### 🔹 Top Batsmen

This insight identifies players who scored the highest runs in the tournament.

**Example:**
If Sahibzada Farhan scored the highest runs, he is considered the top batsman.

---

### 🔹 Top Bowlers

This insight shows players who took the most wickets.

**Example:**
A player with the highest number of wickets is considered the best bowler.

---

### 🔹 Team Performance

This shows how well each team performed based on matches won.

**Example:**
If a team played 10 matches and won 7, it indicates strong performance.

---

### 🔹 Best All-Rounders

This identifies players who performed well in both batting and bowling.

**Example:**
A player who scored high runs and also took multiple wickets is considered an all-rounder.

---

### 🔹 Matches by Venue

This shows which stadiums hosted the most matches.

**Example:**
If Mumbai hosted the highest number of matches, it is considered the most active venue.

---

### 🔹 Final Match Result

This shows which teams played the final and who won the tournament.

**Example:**
India vs New Zealand → India won the final match.

---

### 🔹 Team Awards Summary

This shows which team received the highest number of awards.

**Example:**
If India has the most awards, it reflects strong overall team performance.

---

## 📌 Summary

These insights help convert raw cricket data into meaningful information that can be used for performance analysis and better decision-making.

