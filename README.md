# 🧹 Data Cleaning Portfolio — Python & Pandas

A collection of end-to-end data cleaning notebooks using Python, pandas, and plotly. Each project takes a raw, messy real-world dataset and produces a fully documented, model-ready output.

---

## 📁 Projects

### 1. Airline Pricing Dataset

Cleans a 10,000+ row airline flight pricing dataset sourced from Kaggle.

**Key challenges handled:**
- Parsed `Duration` from strings (`"2h 30m"`) into numeric minutes using `re`
- Handled `Arrival_Time` with next-day suffix (`+1`) before datetime conversion
- Applied tiered missing value strategy: mode for categoricals, median for numerics, drop for dates
- Ordinal-encoded `Total_Stops` (non-stop → 4 stops) preserving natural order
- Detected and Winsorized price outliers at 3×IQR bounds

**Tools:** `pandas` · `numpy` · `plotly` · `re`

---

### 2. Café Sales Dataset


Cleans a café point-of-sale dataset containing sentinel errors, mixed types, and interdependent numeric columns.

**Key challenges handled:**
- Replaced `"UNKNOWN"` and `"ERROR"` sentinel strings with `NaN` before any imputation
- Applied business-rule imputation: derived missing values from `Total Spent = Quantity × Price Per Unit`
- Validated business rule consistency on complete rows before filling gaps
- Dropped missing `Transaction Date` rows instead of mode-imputing (mode is meaningless for time data)
- Detected extreme outliers (3×IQR) and documented the decision to retain valid high-value transactions

**Tools:** `pandas` · `numpy` · `plotly`

---

## 🔧 Cleaning Steps — Standard Pipeline

Each notebook follows this structured pipeline:

```
Raw Data
   │
   ├── 1. Inspect         → shape, dtypes, nulls, value counts
   ├── 2. Invalid values  → sentinel strings → NaN
   ├── 3. Fix types       → datetime, numeric coercion
   ├── 4. Business rules  → validate / derive from domain logic
   ├── 5. Missing values  → business logic → median/mode fallback
   ├── 6. Standardize     → whitespace stripping, encoding
   ├── 7. Duplicates      → detect and remove (with counts)
   └── 8. Outliers        → IQR detection + documented decision
         │
      Model-ready dataset
```

---
 the dataset files**

| Notebook | Dataset | Source |
|----------|---------|--------|
| Airline | `Airline dataset.xlsx` | [Kaggle — Flight Price Prediction](https://www.kaggle.com/datasets/shubhambathwal/flight-price-prediction) |
| Café Sales | `cafe_sales.csv` | [Kaggle — Cafe Sales](https://www.kaggle.com/datasets/ahmedmohamed2003/cafe-sales-dirty-data-for-cleaning-training) |

**4. Open in Jupyter**
```bash
jupyter notebook
```

---

## 📊 Results at a Glance

| Dataset | Raw Rows | Clean Rows | Nulls Remaining | Duplicates Removed |
|---------|----------|------------|-----------------|-------------------|
| Airline | 10,683 | ~10,640 | 0 | ✓ |
| Café Sales | ~10,000 | ~9,950+ | 0 | ✓ |

---

## 👤 Author

**Deghfel Nassir**
