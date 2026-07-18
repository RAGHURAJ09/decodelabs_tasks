# Project 1: Data Cleaning & Preparation

## Objective
Clean a raw retail order dataset by handling missing values, duplicates,
and formatting inconsistencies — transforming it into a reliable,
analysis-ready source of truth.

## Dataset
- **Raw file:** `raw_dataset.csv` (Dataset_for_Data_Analytics — Sheet1)
- **Rows / Columns:** 1,200 rows × 14 columns
- **Columns:** OrderID, Date, CustomerID, Product, Quantity, UnitPrice,
  ShippingAddress, PaymentMethod, OrderStatus, TrackingNumber,
  ItemsInCart, CouponCode, ReferralSource, TotalPrice

## Issues Found (Initial Audit)
- Missing values in `CouponCode` (309 rows) — orders where no coupon was used
- No duplicate `OrderID`s found (verified, not assumed)
- No full-row duplicates found (verified, not assumed)
- Dates already in valid format — standardized to ISO 8601 as a safeguard
- Verified `TotalPrice = Quantity x UnitPrice` for consistency
- Trimmed whitespace across all text columns

## Approach
1. **Missing values:** Filled missing `CouponCode` entries with `"NONE"`,
   since a blank coupon code logically means no coupon was applied — not
   a data entry error.
2. **Duplicates:** Checked `OrderID` and full rows for duplicates using
   `duplicated()`; none were found, confirming data integrity.
3. **Formatting:** Standardized `Date` to `YYYY-MM-DD` (ISO 8601), trimmed
   whitespace on all text fields, and rounded `UnitPrice`/`TotalPrice`
   to 2 decimal places.
4. **Verification:** Recalculated `Quantity x UnitPrice` and compared
   against `TotalPrice` to catch any silent calculation errors.

## Verification Gate (Passed)
- 0% duplicate Order IDs
- 0% incorrectly formatted dates
- 0% missing values in final dataset
- 0% mismatches between TotalPrice and Quantity × UnitPrice

## Tools
Python (Pandas) — Google Colab

## Files in this Project
```
Project1_DataCleaning/
├── raw_dataset.csv       # Original, untouched source data
├── cleaned_dataset.csv   # Final cleaned output
├── cleaning.ipynb        # Notebook with code + saved outputs
├── Change_Log.pdf        # Documented record of every change made
└── README.md             # This file
```

## How to Reproduce
1. Open `cleaning.ipynb` in Google Colab
2. Upload `raw_dataset.csv` when prompted
3. Run all cells (`Runtime → Run all`)
4. Verify the printed "✅ VERIFICATION PASSED" message
5. `cleaned_dataset.csv` and `change_log.csv` will be generated as output

## Notes
`cleaning.ipynb` contains both the code and its executed output (missing
value audits, verification checks, change log), so it renders fully on
GitHub without needing to be re-run — it serves as both the script and
the proof of execution.
