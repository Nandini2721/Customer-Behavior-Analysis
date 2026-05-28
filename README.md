# Customer Shopping Behavior Analysis

An end-to-end data analytics project analyzing transactional data from **3,900 customers** to uncover spending patterns, customer segments, product preferences, and subscription behavior — using Python, SQL Server, and Power BI.

---

## Dashboard Preview

<img width="4872" height="2656" alt="Customer Behavior Dashboard" src="https://github.com/user-attachments/assets/70f44973-0081-47fd-afb7-cc61e163ad05" />

---

## Project Structure

```
├── customer_shopping_behavior.csv           # Raw dataset (3,900 rows, 18 columns)
├── customer_shopping_behavior-checkpoint.ipynb  # Python EDA & ETL notebook
├── SQLQuery1.sql                            # SQL analysis queries
├── customer_behavior_dashboard.pbix         # Power BI dashboard file
├── Customer Shopping Behavior Analysis.pdf  # Project report
├── Customer-Shopping-Behavior-Analysis.pptx # Presentation
└── Business Problem Document.pdf           # Problem statement
```

---

## Dataset

- **Rows:** 3,900 | **Columns:** 18
- **Key features:** Customer ID, Age, Gender, Location, Item Purchased, Category, Purchase Amount (USD), Season, Review Rating, Subscription Status, Shipping Type, Discount Applied, Promo Code Used, Previous Purchases, Frequency of Purchases
- **Missing data:** 37 null values in `review_rating` column

---

## Tools & Technologies

| Tool | Purpose |
|------|---------|
| Python (Pandas, NumPy) | Data cleaning, feature engineering, EDA |
| SQLAlchemy | Loading cleaned data into SQL Server |
| SQL Server | Business queries and aggregations |
| Power BI | Interactive dashboard and DAX measures |
| Jupyter Notebook | Development environment |

---

## Workflow

### 1. Data Cleaning & Feature Engineering (Python)
- Loaded dataset using Pandas and inspected structure with `df.info()` and `df.describe()`
- Imputed **37 missing Review Ratings** using category-wise median
- Renamed columns to snake_case for consistency
- Engineered two new features:
  - `age_group` — binned customer ages into Young Adult, Adult, Middle-aged, Senior
  - `purchase_frequency_days` — derived from purchase frequency data
- Dropped redundant `promo_code_used` column after verifying overlap with `discount_applied`
- Loaded cleaned DataFrame into SQL Server using SQLAlchemy

### 2. SQL Analysis (10 Business Queries)
Ran structured queries in SQL Server to answer key business questions:

| # | Query | Insight |
|---|-------|---------|
| 1 | Revenue by Gender | Male: $157,890 / Female: $75,191 |
| 2 | High-Spending Discount Users | 839 customers spent above avg. despite discounts |
| 3 | Top 5 Products by Rating | Gloves (3.86), Sandals (3.84), Boots (3.82) |
| 4 | Shipping Type Comparison | Express ($60.48) vs Standard ($58.46) avg. spend |
| 5 | Subscribers vs Non-Subscribers | Similar avg. spend (~$59.49 vs $59.87) |
| 6 | Discount-Dependent Products | Hat (50%), Sneakers (49.66%), Coat (49.07%) |
| 7 | Customer Segmentation | Loyal: 3,116 / Returning: 701 / New: 83 |
| 8 | Top 3 Products per Category | Used window functions (RANK/PARTITION BY) |
| 9 | Repeat Buyers & Subscriptions | 958 repeat buyers subscribed vs 2,518 not |
| 10 | Revenue by Age Group | Young Adults contributed highest: $62,143 |

### 3. Power BI Dashboard
Built an interactive dashboard with:
- **KPI Cards:** 3.9K customers, $59.76 avg. purchase amount, 3.75 avg. review rating
- **DAX Measures:** Customer count (`COUNT`), average purchase amount (`AVERAGE`)
- **Visuals:** Revenue by Category, Sales by Category, Revenue by Age Group, Sales by Age Group
- **Donut Chart:** Subscription status breakdown (Yes 27% / No 73%)
- **Slicers:** Gender, Category, Subscription Status, Shipping Type

---

## Key Insights

- **Young Adults** are the highest revenue-contributing age group ($62,143)
- **Male customers** generate 2x the revenue of female customers
- **Express shipping** users spend slightly more on average than standard shipping users
- **839 customers** used discounts but still spent above average — high-value discount users
- Only **27% of customers** are subscribers despite similar spending levels — opportunity to grow subscriptions
- **Hat, Sneakers, and Coat** are the most discount-dependent products

---

## Business Recommendations

- **Boost Subscriptions** — promote exclusive benefits; subscribers and non-subscribers spend similarly, so conversion has low friction
- **Reward Loyal Customers** — 3,116 loyal customers are the core segment; prioritize retention programs
- **Review Discount Policy** — discount-heavy products (Hat, Sneakers) may be eroding margins unnecessarily
- **Target Young Adults** — highest revenue group; focus marketing campaigns accordingly
- **Highlight Top-Rated Products** — Gloves, Sandals, Boots have highest ratings; use in promotional content

---

## Credits

This project was inspired and guided by **[Amlan Mohanty](https://youtu.be/5PrZvPeUw60?si=r1ZoPZfNiCRQ36I4)**.  
Dataset and learning material sourced from his tutorial.
