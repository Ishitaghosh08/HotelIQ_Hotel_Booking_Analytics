# HotelIQ – Hotel Business Intelligence & Cancellation Risk Analytics

**Student / Author:** Ishita Ghosh  
**Internship Program:** AICTE | IBM SkillsBuild Data Analytics with AI Internship 2026 | BharatCares  
**Project Title:** HotelIQ – Hotel Booking Analytics  

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Status](https://img.shields.io/badge/Project-Complete-brightgreen.svg)]()

## 📌 Project Overview

**HotelIQ** is an end-to-end Business Intelligence (BI) and Machine Learning (ML) analytics platform designed to solve one of the most critical challenges in the hospitality industry: **booking cancellation risk management**.

Using real-world operational data from **119,203 hotel bookings**, HotelIQ provides a complete data pipeline, exploratory statistical analysis, cancellation driver identification, and predictive machine learning models (**Logistic Regression** and **Random Forest**) to score cancellation risk and protect hotel revenue.

---

## 📊 Dataset Summary

* **Dataset Source:** `hotel_bookings.csv` ([Kaggle Hotel Booking Demand Dataset](https://www.kaggle.com/datasets/jessemostipak/hotel-booking-demand))
* **Raw Volume:** 119,390 rows × 32 columns
* **Cleaned Volume:** 119,203 rows × 34 columns (187 invalid/zero-guest records removed)
* **Deduplicated Volume (for ML):** 87,223 records (prevents train-test leakage)
* **Hotels Included:**
  * **City Hotel:** 79,158 bookings (66.41%)
  * **Resort Hotel:** 40,045 bookings (33.59%)
* **Timeframe Covered:** July 1, 2015 – August 31, 2017
* **Overall Cancellation Rate:** **37.07%** (44,194 cancelled bookings)
* **Total Estimated Booking Value:** **$42,707,642.15**
* **Estimated Booking Value Lost to Cancellations:** **$16,721,229.62 (39.15%)**

---

## 🎯 Key Objectives

1. **Data Cleaning & Quality Pipeline:** Handle missing values (`children`, `agent`, `company`, `country`), standardize meal categories, and filter out zero-guest or invalid financial records.
2. **Feature Engineering:** Calculate total stay nights, total guests, composite arrival dates, room change indicators (`is_room_changed`), lead time bins, and estimated booking value (`adr * total_stay_nights`).
3. **Exploratory Business Intelligence (BI):** Analyze booking trends across deposit types, customer segments, market channels, and seasonality.
4. **Cancellation Driver Identification:** Evaluate how lead time, room upgrades, deposit types, and agency channels correlate with cancellation probability.
5. **Machine Learning Risk Prediction:** Train interpretable classification models (Logistic Regression & Random Forest) to predict cancellation risk without target leakage.

---

## 🛠️ Technology Stack

* **Programming Language:** Python 3.10+
* **Data Processing & Analytics:** Pandas, NumPy
* **Machine Learning & Modeling:** Scikit-Learn
* **Visualization & Reporting:** Matplotlib, Seaborn, Python-Docx
* **Frontend Web Dashboard:** React + Vite (Web App / Interactive BI Dashboard)

---

## 💻 Installation & Setup

1. **Clone or Download the Repository:**
   ```bash
   git clone https://github.com/your-username/HotelIQ_Hotel_Booking_Analytics.git
   cd HotelIQ_Hotel_Booking_Analytics
   ```

2. **Install Dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

---

## 🚀 How to Run

### 1. Run Data Pipeline & Analytics
To execute data cleaning, feature engineering, and model training:
```bash
python src/clean_and_engineer.py
python src/analyze_and_train.py
```

### 2. Generate Report & Notebook Files
```bash
python src/create_notebook.py
python src/create_report.py
```

### 3. Open Jupyter Notebook
```bash
jupyter notebook HotelIQ.ipynb
```

---

## 📁 Project Structure

```
HotelIQ_Hotel_Booking_Analytics/
├── hotel_bookings.csv                            # Raw dataset
├── requirements.txt                              # Project dependencies
├── Ishita Ghosh_HotelIQ_Hotel_Booking_Analytics.ipynb # Executable Jupyter Notebook submission file
├── Ishita Ghosh_ProjectReport.docx       # Structured Word Project Report submission file
├── README.md                                     # Project documentation
├── data/
│   ├── hotel_bookings_cleaned.csv   # Cleaned dataset (for BI & EDA)
│   ├── hotel_bookings_dedup.csv     # Deduplicated dataset (for ML)
│   └── analytics_results.json       # Extracted KPI & ML metrics
├── src/
│   ├── clean_and_engineer.py        # Data cleaning & feature engineering script
│   ├── analyze_and_train.py         # Statistical analysis & ML training script
│   ├── create_notebook.py           # Notebook generator
│   └── create_report.py             # Docx report generator
└── dashboard/                       # Interactive Web BI Dashboard
```

---

## 📈 Key Findings & Business Insights

### 1. Lead Time Speculation Risk
* **Fact:** Bookings made **>180 days in advance** have a **55.46% cancellation rate**, rising to **67.65% for >365 days**, compared to **10.96% for 1-7 days**.
* **Insight:** Long lead times foster low-commitment speculative bookings.
* **Action:** Implement automated re-confirmation touchpoints at 90, 60, and 30 days prior to arrival.

### 2. Non-Refundable Deposit Paradox
* **Fact:** Non-refundable deposit bookings show a **99.36% cancellation rate** (14,493 out of 14,586 canceled).
* **Insight:** Wholesale tour operators block non-refundable group allocations far in advance and relinquish unallocated blocks when demand falls.
* **Action:** Enforce strict release deadlines and pre-payment terms for wholesale agency contracts.

### 3. Room Assignment Retention Effect
* **Fact:** Bookings with room assignment changes (`is_room_changed == 1`) have a cancellation rate of only **5.41%** vs **41.56%** for unchanged rooms.
* **Insight:** Guests who receive room upgrades or proactive reassignments demonstrate high satisfaction and commitment.

---

## 🤖 Machine Learning Model Performance

Models were evaluated on a **20% holdout test set** from the deduplicated dataset (87,223 rows):

| Model | Accuracy | Precision | Recall | F1-Score | ROC-AUC |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Logistic Regression** | **81.01%** | 70.18% | 53.93% | 60.99% | **0.8666** |
| **Random Forest** | **82.91%** | **81.58%** | 48.97% | **61.20%** | **0.8956** |

---

## ⚠️ Limitations & Academic Defensibility

* **No Causation Claim:** All driver findings represent statistical correlations rather than direct causal proofs.
* **Estimated Booking Value:** `adr * total_stay_nights` is explicitly labeled as an estimated value, not audited accounting revenue.
* **Target Leakage Prevention:** `reservation_status` and `reservation_status_date` were excluded during model training as they are post-outcome indicators.

---

## 📝 License
This project is licensed under the MIT License - see the LICENSE file for details.
