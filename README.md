# New York City Yellow Taxi Data — Exploratory Data Analysis

This project performs **Exploratory Data Analysis (EDA)** on the **2023 New York City Yellow Taxi Trip Records** to uncover patterns and insights that can help optimise taxi operations.

The analysis focuses on demand patterns, trip characteristics, fares and revenue, payment behaviour, passenger behaviour, and geographical demand across NYC Taxi Zones.

---

## Objective

The objective of this case study is to apply Exploratory Data Analysis techniques to NYC Yellow Taxi trip data and understand how EDA can be used to convert raw data into meaningful business insights.

The analysis aims to help a taxi operation:

- Improve service efficiency
- Maximise revenue
- Enhance passenger experience
- Understand taxi demand patterns
- Optimise taxi positioning and dispatching
- Identify high-demand geographical areas
- Support data-driven operational decisions

---

## Problem Statement

As an analyst at an upcoming taxi operation in New York City, the task is to use the **2023 Yellow Taxi trip data** to uncover insights that can help optimise taxi operations.

The goal is to analyse patterns in the data that can inform strategic decisions around:

- Taxi demand
- Driver and taxi allocation
- Peak-hour operations
- Geographic positioning
- Revenue generation
- Passenger behaviour
- Pricing and payment behaviour
- Overall service efficiency

---

## Repository Structure

The repository is organised into the following main directories:

```text
nyc-yellow-taxi-eda/
│
├── data/
│   └── 2023 Yellow Taxi trip data and supporting data
│
├── notebook/
│   └── EDA notebook containing the complete analysis
│
├── report/
│   └── Final EDA report
│
└── README.md
```

### Project Resources

- **[Data](./data/)** — Dataset and supporting data used by the analysis
- **[Notebook](./notebook/)** — Jupyter Notebook containing the EDA
- **[Report](./report/)** — Final project report
- **[README](./README.md)** — Project documentation

> The repository structure above reflects the folders currently present in the GitHub repository. The raw TLC files are large, so the README does not assume that every original monthly Parquet file is committed to GitHub.

---

## Data Understanding

The Yellow Taxi trip records contain information about taxi journeys, including:

- Pickup and drop-off date/time
- Pickup and drop-off locations
- Trip distance
- Passenger count
- Rate type
- Payment type
- Fare amount
- Tips
- Tolls
- Taxes and surcharges
- Total trip amount

The original TLC dataset contains data across multiple years. For this project, the analysis is restricted to the **twelve monthly files for 2023**.

The data is provided in **Parquet (`.parquet`) format** by the New York City Taxi and Limousine Commission (TLC).

---

## Dataset Source

The dataset is publicly available from the NYC Taxi & Limousine Commission.

**NYC TLC Trip Record Data:**

https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page

The TLC trip-record data page provides the monthly Yellow Taxi datasets and supporting information.

---

## Data Dictionary

The following table describes the main fields used in the Yellow Taxi trip records.

| Field Name | Description |
|---|---|
| `VendorID` | A code indicating the TPEP provider that provided the record. `1 = Creative Mobile Technologies, LLC`; `2 = VeriFone Inc.` |
| `tpep_pickup_datetime` | Date and time when the taxi meter was engaged. |
| `tpep_dropoff_datetime` | Date and time when the taxi meter was disengaged. |
| `Passenger_count` | Number of passengers in the vehicle. This is a driver-entered value. |
| `Trip_distance` | Elapsed trip distance in miles reported by the taximeter. |
| `PULocationID` | TLC Taxi Zone in which the taximeter was engaged. |
| `DOLocationID` | TLC Taxi Zone in which the taximeter was disengaged. |
| `RateCodeID` | Final rate code in effect at the end of the trip. |
| `Store_and_fwd_flag` | Indicates whether the trip record was held in vehicle memory before being sent to the vendor because the vehicle did not have a connection to the server. |
| `Payment_type` | Numeric code representing how the passenger paid for the trip. |
| `Fare_amount` | Time-and-distance fare calculated by the meter. |
| `Extra` | Miscellaneous extras and surcharges, including applicable rush-hour and overnight charges. |
| `MTA_tax` | MTA tax automatically triggered based on the metered rate in use. |
| `Improvement_surcharge` | Improvement surcharge assessed on the trip at the flag drop. |
| `Tip_amount` | Tip amount automatically populated for credit-card tips. Cash tips are not included. |
| `Tolls_amount` | Total amount of all tolls paid during the trip. |
| `total_amount` | Total amount charged to the passenger. Cash tips are not included. |
| `Congestion_Surcharge` | Total amount collected for the NYS congestion surcharge. |
| `Airport_fee` | Airport fee applicable to pickups at LaGuardia and John F. Kennedy Airports. |

### Rate Code Reference

| RateCodeID | Meaning |
|---:|---|
| 1 | Standard rate |
| 2 | JFK |
| 3 | Newark |
| 4 | Nassau or Westchester |
| 5 | Negotiated fare |
| 6 | Group ride |

### Payment Type Reference

| Payment_type | Meaning |
|---:|---|
| 1 | Credit card |
| 2 | Cash |
| 3 | No charge |
| 4 | Dispute |
| 5 | Unknown |
| 6 | Voided trip |

The field definitions and code values are based on the official NYC TLC Yellow Taxi data dictionary.

---

## Taxi Zones

Each trip record contains a pickup and drop-off location represented by a **Taxi Zone ID**.

The location IDs correspond to NYC Taxi Zones and can be joined with the Taxi Zone lookup data to obtain the corresponding zone names and geographical information.

Taxi Zone information is used in the project to analyse:

- Pickup demand by zone
- Drop-off demand by zone
- Busiest pickup locations
- Busiest drop-off locations
- Popular pickup-to-drop-off combinations
- Geographic concentration of demand

The geographic analysis identifies where pickup demand is concentrated and provides the basis for zone-level dispatching and cab-positioning decisions.

---

## Data Preparation

Before performing the detailed analysis, the data is prepared by examining and handling potential data-quality issues.

The preparation process includes:

### Data Loading

The monthly 2023 Parquet files are loaded and combined for analysis.

### Data Quality Checks

The dataset is examined for:

- Missing values
- Duplicate records
- Invalid passenger counts
- Zero or invalid trip distances
- Invalid trip durations
- Negative or abnormal fare values
- Invalid timestamps
- Extreme outliers

### Feature Engineering

Additional variables are derived from the original fields where required, such as:

- Trip duration
- Pickup hour
- Drop-off hour
- Day of week
- Month
- Weekday/weekend classification
- Average trip speed
- Revenue-related metrics
- Taxi Zone names

These derived features make it easier to analyse demand, trip behaviour and operational patterns.

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook
- PyArrow / Parquet
- Geospatial analysis and visualisation tools where applicable

---

## How to Run the Project

### 1. Clone the repository

```bash
git clone https://github.com/narayan2187/nyc-yellow-taxi-eda.git
cd nyc-yellow-taxi-eda
```

### 2. Install the required Python packages

If a `requirements.txt` file is provided in the repository:

```bash
pip install -r requirements.txt
```

Otherwise, install the packages used by the notebook, for example:

```bash
pip install pandas numpy matplotlib seaborn pyarrow jupyter
```

### 3. Download the 2023 Yellow Taxi data

Download the required 2023 Yellow Taxi Parquet files from the NYC TLC Trip Record Data page:

https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page

Place the required data files under the repository's `data/` directory.

### 4. Open the EDA notebook

Navigate to the notebook directory:

```bash
cd notebook
```

Start Jupyter Notebook:

```bash
jupyter notebook
```

Open the EDA notebook and execute the cells sequentially.

### 5. Review the final report

The final analysis report is available under:

```text
report/
```

You can also open the **[Report](./report/)** directly from the repository.

---

## Project Files

| Resource | Location | Purpose |
|---|---|---|
| Data | [`data/`](./data/) | Dataset and supporting data |
| EDA Notebook | [`notebook/`](./notebook/) | Complete exploratory analysis |
| Final Report | [`report/`](./report/) | Consolidated analysis and findings |
| README | [`README.md`](./README.md) | Project documentation |

---

## Conclusion

This project demonstrates how Exploratory Data Analysis can be used to understand a real-world transportation dataset and convert raw taxi-trip records into meaningful business insights.

By analysing **time, geography, trip characteristics, fares, payment behaviour and passenger patterns**, the project provides a foundation for making data-driven decisions around taxi positioning, dispatching, resource allocation and service optimisation.

The analysis can also serve as a starting point for more advanced work such as demand forecasting, predictive modelling and optimisation.

---

## References

### NYC Taxi & Limousine Commission — Trip Record Data

https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page

### NYC TLC Yellow Taxi Data Dictionary

https://www.nyc.gov/assets/tlc/downloads/pdf/data_dictionary_trip_records_yellow.pdf

---

