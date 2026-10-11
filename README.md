# Retail Sales Analysis (SQL)

An end-to-end SQL project on 2,000 retail transactions: set up the database, clean the data, and answer 10 business questions about sales, customers and buying patterns.

**Database:** PostgreSQL 18 | **Tool:** pgAdmin 4 | **Dataset size:** 2,000 rows, 11 columns

---

## Problem Statement

A retail business records every sale but has no clear view of how it is performing. Management wants to know:

- Which product categories bring in the most revenue?
- Who are the best customers, and what does the typical customer look like?
- Which months and times of day are strongest, so staffing and promotions can be planned?
- Is the underlying data reliable enough to trust these numbers?

This project answers those questions using SQL only.

---

## Dataset

One row per transaction, covering January 2022 to December 2023.

| Column | Description |
|---|---|
| `transactions_id` | Unique transaction ID (primary key) |
| `sale_date` | Date of sale |
| `sale_time` | Time of sale |
| `customer_id` | Customer identifier |
| `gender` | Male / Female |
| `age` | Customer age |
| `category` | Clothing, Electronics or Beauty |
| `quantity` | Units sold |
| `price_per_unit` | Price of one unit |
| `cogs` | Cost of goods sold |
| `total_sale` | Total sale amount |

---

## Project Workflow

1. **Database setup:** create the database and the `retail_sales` table with proper data types.
2. **Data import:** load the CSV into a text staging table, then convert into the typed table. The raw file had dates as `DD-MM-YYYY`, times written with dots (`10.47.00`), and two empty trailing columns, so a direct import failed.
3. **Data cleaning:** find and delete rows with missing values (about 3 rows with missing sales figures; 10 more are missing only `age`).
4. **Exploration:** count sales, unique customers and categories.
5. **Analysis:** answer 10 business questions (below).

---

## Business Questions and Findings

| # | Question | Result |
|---|---|---|
| 1 | All sales on 2022-11-05 | Retrieved with a date filter |
| 2 | Clothing sales with quantity of 4 or more in Nov 2022 | Filter by category, quantity and month (`TO_CHAR`) |
| 3 | Total sales and orders per category | Electronics ₹313,810 (684 orders), Clothing ₹311,070 (701), Beauty ₹286,840 (612) |
| 4 | Average age of Beauty customers | About 40.4 years |
| 5 | Transactions above 1,000 | 306 transactions |
| 6 | Transactions by gender in each category | Beauty is female-led (330 vs 282); Clothing and Electronics are almost even |
| 7 | Best month in each year by average sale | July in 2022 (about 541) and February in 2023 (about 536) |
| 8 | Top 5 customers by total sales | Customers 3, 1, 5, 2 and 4 (customer 3 spent 38,440) |
| 9 | Unique customers per category | Clothing 149, Electronics 144, Beauty 141 (155 customers in total) |
| 10 | Orders by shift | Evening 1,062, Morning 558, Afternoon 377 |

### Key Insights

- **Revenue is spread evenly.** All three categories earn within about 10% of each other, so no single category carries the business.
- **Evenings are the busiest period.** More than half of all orders (about 53%) are placed after 17:00, which matters for staffing and promotions.
- **A small group of customers spends the most.** The top 5 customers each spent between about 23,600 and 38,400, far above a typical customer.
- **Beauty skews female.** It is the only category with a clear gender gap.

*Figures come from the 1,997 rows left after the cleaning step in the script.*

---
## How to Run

1. Create a database named `sql_project_p2` in PostgreSQL.
2. Run the table creation section of `retail_sales_analysis.sql`.
3. Import `data/retail_sales.csv`. The raw file needs the staging-table steps in the script, because of its date and time formats and two empty trailing columns.
4. Run the cleaning section, then each analysis query.

---

## Repository Structure

```
retail-sales-sql-analysis/
├── README.md
├── retail_sales_analysis.sql
└── data/
    └── retail_sales.csv
```

---

## Author

Prajwal Mahajan | [GitHub](https://github.com/mahajanprajwal-1/) | [LinkedIn](www.linkedin.com/in/prajwalmahajan0055)
