# gtc-ml-project1-hotel-bookings
Build a robust data preprocessing pipeline for a hotel booking cancellation prediction model.

## Project Overview

This project analyzes and models hotel booking data to **predict whether a reservation will be canceled**.  
The dataset contains detailed information about guest bookings, including stay details, customer type, market segment, deposit type, country, and reservation outcomes.

###  Goals
- Understand booking patterns and customer behavior.  
- Handle missing data, outliers, and categorical encoding correctly.    
- Provide insights to help hotels reduce cancellations and improve planning.  

---

## Dataset

- **File:** `hotel_bookings.csv`  
- **Size:** ~119,000 rows, 32 columns
  
## 🔑 Key Columns

- **hotel**: City Hotel / Resort Hotel  
- **is_canceled**: Target variable (1 = canceled, 0 = not canceled)  
- **lead_time**: Days between booking and arrival  
- **arrival_date_***: Arrival year, month, week, day  
- **stays_in_weekend_nights**, **stays_in_week_nights**: Length of stay  
- **adults**, **children**, **babies**: Number of guests  
- **meal**: Type of meal plan  
- **country**: Guest origin country  
- **market_segment**, **distribution_channel**: Booking source  
- **deposit_type**: Deposit required (None / Non-refundable / Refundable)  
- **reservation_status**: Check-Out / Canceled / No-Show  

---

## Data Preprocessing

###  Steps Applied

**1. Missing Values**  
- Visualized with `missingno` matrix & heatmap.  
- Imputed or dropped depending on column relevance.  

**2. Outliers**  
- Identified via IQR method in numerical features.  
- Winsorized or capped extreme values where appropriate.  

**3. Feature Engineering**  
- Created `is_family` feature → flag for children/babies > 0.  
- Extracted and grouped countries by frequency.  

**4. Categorical Encoding**  
- Low-cardinality columns → One-Hot Encoding (`pd.get_dummies`).  
- High-cardinality column (`country`) → Frequency grouping + One-Hot.  
- Binary columns (`hotel`, `is_family`) → Direct mapping to 0/1.  

**5. Leakage Removal**  
- Dropped `reservation_status` and `reservation_status_date` (reveal target outcome).  

**6. Train/Test Split**  
- 80/20 split using `train_test_split`.  

**7. Data Export**  
Preprocessed datasets saved as CSV for reproducibility:  
- `hotel_bookings_train_features.csv`  
- `hotel_bookings_test_features.csv`  
- `hotel_bookings_train_target.csv`  
- `hotel_bookings_test_target.csv`  

---

## Exploratory Data Analysis (EDA)

- Distribution of cancellations across hotels.  
- Impact of **lead time** on cancellations.  
- Customer segments more likely to cancel.  
- Seasonal trends and country-based behavior.  
- Visualization of missing data patterns.  
