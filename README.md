
# 📊 Big Data in Finance – Preprocessing README
---

## 🧾 Objective of the Script

This R script is designed to **preprocess the Fama-French datasets** (daily and monthly) . It includes:  
- Importing raw data,  
- Cleaning and formatting dates and returns,  
- Handling missing values,  
- Exporting cleaned CSV files.

---

## 📂 Datasets Used

The following 8 datasets have been preprocessed:

| Frequency | Dataset                                 | Format | Source       |
|-----------|------------------------------------------|--------|--------------|
| Daily     | 25 Portfolios Size-BM                    | CSV    | Fama-French  |
| Daily     | 100 Portfolios Size-BM                   | CSV    | Fama-French  |
| Daily     | 10 Industry Portfolios                   | CSV    | Fama-French  |
| Daily     | 48 Industry Portfolios                   | CSV    | Fama-French  |
| Monthly   | 25 Portfolios Size-BM                    | CSV    | Fama-French  |
| Monthly   | 100 Portfolios Size-BM                   | CSV    | Fama-French  |
| Monthly   | 10 Industry Portfolios                   | CSV    | Fama-French  |
| Monthly   | 48 Industry Portfolios                   | CSV    | Fama-French  |

---

## 🧼 Cleaning Steps

1. **Date Conversion**:  
   - Monthly data (`YYYYMM`) converted to R dates (`ymd`) by appending "01" as the day.  
   - Daily data already in `YYYYMMDD` format is parsed directly.

2. **Return Adjustment**:  
   - All returns divided by 100 to convert percentages to decimals.  
   - Special missing value codes (`-99.99` and `-999`) replaced with `NA`.

3. **Date Filtering**:  
   - Only data from `1970-01-01` to `2024-12-31` was kept.

---

## 🔍 Missing Value Handling

Two datasets (100 Size-BM, daily and monthly) contained missing values.

We applied:
- **LOCF (Last Observation Carried Forward)**  
- **Backward fill** using the `zoo` package

 For the monthly dataset, 5 missing values remained after imputation. Since this is negligible, the affected rows were removed using `na.omit()`.

---

## 💾 Output

The following cleaned CSV files were exported:

- `vw_25_daily.csv`
- `vw_100_daily.csv`
- `vw_10_daily.csv`
- `vw_48_daily.csv`  
- `vw_25_monthly.csv`
- `vw_100_monthly.csv`
- `vw_10_monthly.csv`
- `vw_48_monthly.csv`

---


