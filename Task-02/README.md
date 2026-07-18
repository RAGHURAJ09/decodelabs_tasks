# Project 2: Exploratory Data Analysis (EDA)

## Objective
Analyze the cleaned retail order dataset to uncover patterns, trends,
distributions, and relationships between variables — transforming a
static table of numbers into meaningful business insight.

## Dataset
- **Input file:** `Cleaned_Dataset for Data Analytics - Sheet1.csv` (output of Project 1)
- **Rows / Columns:** 1,200 rows × 14 columns
- **Numeric columns analyzed:** Quantity, UnitPrice, TotalPrice, ItemsInCart
- **Categorical columns analyzed:** Product, PaymentMethod, OrderStatus, ReferralSource

## Methodology

### 1. Descriptive Statistics
Calculated mean, median, standard deviation, and the five-number summary
(min, Q1, median, Q3, max) for all numeric columns using `df.describe()`.

### 2. Distribution Analysis
Compared mean vs. median for each numeric column to check for skew, and
visualized distributions using histograms.

### 3. Outlier Detection
Applied the IQR method:
```
Outlier < Q1 - 1.5 * IQR
Outlier > Q3 + 1.5 * IQR
```
Outliers were visualized using boxplots and investigated individually to
distinguish noise (data errors) from signal (genuine high-value orders).

### 4. Correlation Analysis
Calculated the Pearson correlation coefficient between all numeric
variables and visualized the results as a correlation heatmap.

### 5. Categorical Breakdown
Summarized frequency counts for Product, PaymentMethod, OrderStatus, and
ReferralSource, and analyzed total revenue by product category.

## Key Findings
- Average order value (`TotalPrice`) is approximately $1,054, with a
  median of $824 — indicating a right-skewed distribution driven by a
  small number of high-value orders.
- 8 outlier orders detected in `TotalPrice` using the IQR method; these
  represent unusually high-value transactions and were investigated
  individually rather than removed.
- Strongest correlation found between `UnitPrice` and `TotalPrice`
  (r ≈ 0.72), and between `Quantity` and `ItemsInCart` (r ≈ 0.65) — both
  expected, logical relationships.
- Product sales are fairly evenly distributed across categories
  (Printer, Tablet, Chair, Laptop, Desk each ~170-180 orders), with no
  single dominant product line.
- Payment methods and order statuses are also evenly distributed,
  suggesting no single channel or status dominates order behavior.

## Tools
Python (Pandas, Matplotlib, Seaborn) — Google Colab

## Files in this Project
```
Project2_EDA/
├── cleaned_dataset.csv        # Input dataset (from Project 1)
├── eda_analysis.ipynb         # Notebook with code + outputs
├── eda_summary.csv            # Summary of key metrics
├── distributions.png          # Histogram of numeric columns
├── boxplots.png               # Outlier visualization
├── correlation_heatmap.png    # Correlation matrix visualization
├── revenue_by_product.png     # Revenue breakdown chart
└── README.md                  # This file
```

## How to Reproduce
1. Open `EDA_Analysis.ipynb` in Google Colab
2. Upload `Cleaned_Dataset for Data Analytics - Sheet1.csv` when prompted
3. Run all cells (`Runtime → Run all`)
4. Review printed statistics and generated charts
5. `eda_summary.csv` and chart images will be generated as output
