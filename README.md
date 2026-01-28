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



	## Predictive Analysis

### Objective
The objective of this analysis was to identify high-value customers based on historical purchase behavior. A high-value customer was defined as a customer whose total revenue falls within the top 25% of all customers.

### Target Definition
A binary target variable was created:
- is_high_value_customer = 1 if the customer is in the top 25% by total revenue
- is_high_value_customer = 0 otherwise

All modeling was performed at the customer level, with one row representing one customer.

### Baseline Approach
A simple rule-based baseline model was implemented using the number of invoices (NumInvoices) as the sole predictor. Customers whose invoice count fell within the top 25% were classified as high-value.

*Baseline performance:*
- Accuracy: *0.8756*

This result shows that purchase frequency alone is a strong indicator of customer value.

### Logistic Regression Model
A logistic regression model was trained using customer-level behavioral features to predict high-value customers. The dataset was split into training (75%) and testing (25%) sets with stratification to preserve class balance.

*Model performance:*
- Accuracy: *~0.88*

The logistic regression model achieved a marginal improvement over the baseline rule-based approach.

### Model Interpretation
The minimal performance difference between the baseline and logistic regression models indicates that customer value in this dataset is largely driven by simple behavioral patterns, particularly purchase frequency. While the machine learning model provides a slight improvement, the baseline rule remains highly effective and easier to operationalize.

### Error Analysis
Confusion matrix analysis shows that false negatives (high-value customers incorrectly classified as non–high-value) represent a greater business risk than false positives. Missing high-value customers may lead to lost opportunities for retention and targeted engagement.

### Business Implications
This analysis can be used to:
- Identify high-value customers early in their lifecycle
- Support retention and loyalty program decisions
- Prioritize customer support and marketing resources
- Provide a simple, explainable customer value scoring approach

Both the baseline rule and the logistic regression model are viable in practice, with the choice depending on the desired balance between simplicity and predictive precision.