# E-commerce Customer & Revenue Analysis (EDA + SQL)

This project analyzes e-commerce customer and transaction data to understand revenue drivers, customer value, and product performance.

## Goals
- Clean and prepare the dataset
- Perform exploratory data analysis (EDA)
- Answer business questions (revenue trends, top products, top customers)
- Reproduce key insights using SQL (SQLite)

## Tools
- Python (pandas, numpy)
- SQL (SQLite)
- Jupyter Notebook



E-commerce Customer & Revenue Analysis (EDA)

Project Overview
This project analyzes transactional e-commerce data to understand customer purchasing behavior and revenue patterns. The goal is to transform raw transaction-level data into meaningful business insights related to customers, invoices, and revenue distribution.

⸻

Dataset
	•	Source: Online retail transactional dataset
	•	Granularity: One row per product per invoice
	•	Key fields:
	•	InvoiceNo
	•	InvoiceDate
	•	CustomerID
	•	Country
	•	Quantity
	•	UnitPrice

⸻

Data Cleaning
The following steps were applied:
	•	Removed transactions with non-positive quantity or unit price
	•	Handled missing customer IDs where necessary
	•	Created a new feature LineRevenue = Quantity × UnitPrice

⸻

Feature Engineering & Aggregations
Three core datasets were created:
	1.	Cleaned Transactions (df_clean)
	•	Line-level sales with revenue calculated per item
	2.	Invoice Summary
	•	One row per invoice
	•	Total invoice revenue
	•	Number of line items
	•	Customer and country information
	3.	Customer Summary
	•	One row per customer
	•	Total revenue contributed
	•	Number of invoices
	•	First and last purchase dates

⸻

Key Business Insights
	•	Revenue distribution is highly skewed:
	•	A small number of customers contribute a large portion of total revenue
	•	Many customers are one-time buyers, indicating potential churn risk
	•	Invoice values vary significantly, with a long tail of high-value invoices
	•	Revenue concentration suggests opportunities for customer segmentation and retention strategies

⸻

Tools Used
	•	Python
	•	Pandas
	•	NumPy
	•	Matplotlib
	•	Jupyter Notebook

⸻

Next Steps
	•	Perform deeper customer segmentation
	•	Translate analysis logic into SQL
	•	Apply predictive modeling for churn or lifetime value