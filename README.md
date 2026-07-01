# Real-Time Cryptocurrency Analysis Pipeline

![Python](https://img.shields.io/badge/Python-3.x-blue)
![MySQL](https://img.shields.io/badge/Database-MySQL-orange)
![Power BI](https://img.shields.io/badge/Dashboard-Power%20BI-yellow)
![ETL](https://img.shields.io/badge/Pipeline-ETL-green)

## Overview

**Real-Time Cryptocurrency Analysis Pipeline** is a data engineering and analytics project that collects cryptocurrency market data from public APIs, processes it using Python, stores it in a MySQL data warehouse, and visualizes insights through a Power BI dashboard.

The project demonstrates a complete data pipeline workflow: **data extraction → transformation → storage → analysis → dashboard reporting**. It is designed for learning and showcasing skills in ETL development, data warehousing, API integration, SQL, and business intelligence.

---

## Project Objective

The main objective of this project is to design and implement a data-driven cryptocurrency analysis pipeline that can:

* Fetch real-time and historical cryptocurrency market data
* Transform raw API data into structured analytical tables
* Store processed data in a MySQL data warehouse
* Support reporting and analysis using Power BI
* Provide a foundation for future machine learning-based price prediction

---

## Key Features

* **API Data Extraction**
  Fetches cryptocurrency data from APIs such as CoinGecko and CoinDesk.

* **ETL Pipeline**
  Extracts, transforms, and loads cryptocurrency market data into a structured database.

* **MySQL Data Warehouse**
  Stores market data using dimension and fact tables.

* **Star Schema Design**
  Includes dimension tables for currency and date, along with fact tables for market metrics.

* **Power BI Dashboard**
  Provides interactive visual analysis of cryptocurrency prices, market cap, volume, and market trends.

* **Notebook-Based Analysis**
  Includes Jupyter notebooks for API extraction, cleaning, exploration, and CSV generation.

---

## Pipeline Architecture

```text
Crypto APIs
   |
   v
Python ETL Scripts / Jupyter Notebooks
   |
   v
Pandas Data Cleaning & Transformation
   |
   v
MySQL / MariaDB Data Warehouse
   |
   v
Power BI Dashboard
```

---

## Tech Stack

| Category                | Tools / Technologies            |
| ----------------------- | ------------------------------- |
| Programming Language    | Python                          |
| Data Processing         | Pandas, NumPy                   |
| API Requests            | Requests                        |
| Database                | MySQL / MariaDB                 |
| Database Connector      | SQLAlchemy, PyMySQL             |
| Local Server            | XAMPP                           |
| Visualization           | Power BI                        |
| Development Environment | Jupyter Notebook / Google Colab |

---

## Repository Structure

```text
Real-Time-Cryptocurrency-Analysis-Pipeline/
│
├── APItoCSV.ipynb                 # Fetches historical crypto OHLC data and exports it to CSV
├── CryptoAPIETL (1).ipynb         # API extraction, cleaning, and exploratory analysis
├── Final (1).ipynb                # Final notebook for API-based data analysis
├── ETL script.py                  # Loads CSV data into MySQL data warehouse tables
├── etl_crypto_data.py             # Fetches CoinGecko market data and loads it into MySQL
├── Star schema.py                 # Creates star schema tables in MySQL
├── connecting with xampp.py       # Tests MySQL/XAMPP database connection
├── crypto_dw.sql                  # SQL dump for the crypto data warehouse
├── coingecko_market.csv           # Sample CoinGecko market data
├── coins.xlsx                     # Coin-related dataset/file
├── Proj Dashboard.pbix            # Power BI dashboard file
├── requirments.txt                # Python dependencies file
└── pip install -r requirements.txt # Text note for installation command
```

---

## Data Sources

This project uses public cryptocurrency market data sources, including:

* **CoinGecko API** for current market data such as price, market cap, volume, 24-hour high, and 24-hour low.
* **CoinDesk API** for historical OHLC data used in notebook-based extraction.

---

## Database Design

The project follows a data warehouse-style structure using dimension and fact tables.

### Main Tables

| Table                              | Description                                                                                    |
| ---------------------------------- | ---------------------------------------------------------------------------------------------- |
| `dim_currency`                     | Stores cryptocurrency information such as ID, symbol, and name                                 |
| `dim_date`                         | Stores date-related attributes such as day, month, year, and weekday                           |
| `fact_market` / `fact_market_data` | Stores market metrics such as current price, market cap, volume, 24-hour high, and 24-hour low |
| `fact_price`                       | Stores coin price data with timestamp information                                              |

### Example Star Schema

```text
           dim_currency
                |
                |
          fact_market_data
                |
                |
             dim_date
```

---

## Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/hassan-069/Real-Time-Cryptocurrency-Analysis-Pipeline.git
cd Real-Time-Cryptocurrency-Analysis-Pipeline
```

### 2. Create a Virtual Environment

```bash
python -m venv venv
```

Activate it:

**Windows:**

```bash
venv\Scripts\activate
```

**macOS / Linux:**

```bash
source venv/bin/activate
```

### 3. Install Dependencies

The repository currently contains a dependency file named `requirments.txt`.

```bash
pip install -r requirments.txt
```

Recommended improvement:

```bash
ren requirments.txt requirements.txt
pip install -r requirements.txt
```

For macOS / Linux:

```bash
mv requirments.txt requirements.txt
pip install -r requirements.txt
```

---

## MySQL / XAMPP Setup

### 1. Start XAMPP

Open XAMPP Control Panel and start:

* Apache
* MySQL

### 2. Create Database

Create a MySQL database named:

```sql
crypto_dw
```

You can create it manually in phpMyAdmin or by running:

```sql
CREATE DATABASE crypto_dw;
```

### 3. Import SQL Dump

You can import `crypto_dw.sql` into phpMyAdmin to restore the database structure and sample data.

### 4. Test Database Connection

Run:

```bash
python "connecting with xampp.py"
```

Expected output:

```text
Connected to: crypto_dw
```

---

## How to Run the Pipeline

### Option 1: Create Star Schema Tables

```bash
python "Star schema.py"
```

This creates the required dimension and fact tables in the MySQL database.

### Option 2: Run CoinGecko ETL Pipeline

```bash
python etl_crypto_data.py
```

This script:

1. Connects to the MySQL database
2. Fetches current cryptocurrency market data from CoinGecko
3. Creates currency and date dimension tables
4. Creates a market fact table
5. Loads the processed data into MySQL

### Option 3: Load CSV Data into MySQL

```bash
python "ETL script.py"
```

This script loads local CSV data into the MySQL data warehouse.

> Before running this file, update the local CSV path inside the script according to your system.

---

## Power BI Dashboard

The repository includes a Power BI dashboard file:

```text
Proj Dashboard.pbix
```

Use Power BI Desktop to open this file and explore cryptocurrency insights such as:

* Current price comparison
* Market capitalization trends
* Trading volume analysis
* Top-ranked cryptocurrencies
* High and low price movement

---

## Jupyter Notebooks

### `APItoCSV.ipynb`

Fetches historical cryptocurrency OHLC data and exports it into CSV format.

### `CryptoAPIETL (1).ipynb`

Performs API data extraction, data inspection, missing value checking, and data cleaning.

### `Final (1).ipynb`

Contains final data analysis steps using cryptocurrency market data.

---

## Example Output Fields

The extracted cryptocurrency dataset may include fields such as:

| Field             | Description                        |
| ----------------- | ---------------------------------- |
| `id`              | Cryptocurrency ID                  |
| `symbol`          | Coin symbol                        |
| `name`            | Coin name                          |
| `current_price`   | Current market price in USD        |
| `market_cap`      | Total market capitalization        |
| `market_cap_rank` | Ranking by market capitalization   |
| `total_volume`    | Trading volume                     |
| `high_24h`        | Highest price in the last 24 hours |
| `low_24h`         | Lowest price in the last 24 hours  |
| `last_updated`    | Last data update timestamp         |

---

## Future Improvements

* Rename `requirments.txt` to `requirements.txt`
* Remove hard-coded local file paths and use relative paths
* Align table names across scripts, such as `fact_market` and `fact_market_data`
* Add environment variables for database credentials
* Add a machine learning model for cryptocurrency price prediction
* Add automated scheduling for periodic ETL runs
* Add dashboard screenshots to the README
* Add error handling for API rate limits and failed requests

---

## Author

**Hassan Hayat**
GitHub: [hassan-069](https://github.com/hassan-069)

---
