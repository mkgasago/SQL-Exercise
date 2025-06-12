# Superstore Regional Performance Analysis (SQL Project)

### Overview
This project simulates a real-world data analyst role within a retail company. You’ve been hired by Superstore HQ to help leadership make critical decisions about regional performance by analyzing transactional data from the past year. The primary goal is to extract, clean, and query the data to uncover insights that will shape business strategy and resource allocation.

### Objectives
	•	Identify key performance indicators (KPIs) across regions
	•	Use SQL to answer business questions and draw conclusions
	•	Create grouped summaries using GROUP BY, filtering using WHERE, and ordering/ranking results with ORDER BY and RANK()
	•	Analyze trends related to sales, profit, categories, customer behavior, and shipping
	•	Develop a SQL-driven final report that supports executive decision-making

### Dataset
The dataset used is superstore.csv, which includes over 9,000 sales transactions from a fictional office supply company. Each row represents a customer order and contains multiple dimensions and measures including:

	•	Customer & order details
	•	Product category & sub-category
	•	Ship mode & delivery data
	•	Sales & profit figures
	•	Region, state, and city

### Data Dictionary: 
 https://docs.google.com/document/d/1UhUyfFvQnZG2iDsy6LNNrTuezQ9wBtoAJI966IZNEpQ/edit?usp=sharing
 
### Tools & Technologies
	•	SQL (via SQLite or MySQL)
	•	Pandas (for initial data loading if needed)
	•	Jupyter Notebook / VS Code
	•	SQLAlchemy & ipython-sql (if run inside a notebook)
	•	Data visualization (optional): seaborn, matplotlib

### Setup Instructions
	1.	Clone the project repo:
```bash
git clone 
cd superstore-sql-project
```
	2.	Install dependencies (if using Python):
 ```bash
pip install pandas sqlalchemy ipython-sql matplotlib seaborn
```

	3.	Load the dataset:
 
     •	Option 1: Upload superstore.csv to your local SQL DB (MySQL or SQLite)
     •	Option 2 (Notebook users): Use pandas to load and push to SQLite:
```python
import pandas as pd
from sqlalchemy import create_engine

df = pd.read_csv(‘superstore.csv’)
engine = create_engine(‘sqlite:///superstore.db’)
df.to_sql(‘superstore’, engine, if_exists=‘replace’, index=False)
```

	4.	Run your SQL queries in Jupyter using:
```python
%load_ext sql
%sql sqlite:///superstore.db
```

### Analysis Tasks
Your tasks as a data analyst include

   	• Compare total sales, orders, and profits per region
	• Determine the most profitable categories by region
	• Identify shipping delays or preferred ship modes
	• Rank customer segments by sales and profitability
	• Spot high-performing states or cities
	• Detect potential losses or underperforming areas

Each query contributes to a “final showdown matrix” that the executive team will use to evaluate which region delivered the most value in the past year.

### Sample SQL Queries
<pre>
```sql
SELECT Region, SUM(Sales) AS TotalSales
FROM superstore
WHERE YEAR(Order_Date) = 2014
GROUP BY Region
ORDER BY TotalSales DESC;
```
</pre>


```sql
SELECT Category, Region, SUM(Profit) AS TotalProfit
FROM superstore
GROUP BY Category, Region
ORDER BY TotalProfit DESC;
```

### Deliverables
	•	A clean Jupyter notebook (or .sql file) with:
	•	At least 8–10 well-commented SQL queries
	•	Summary of insights from each query
	•	README file with full project documentation
	•	Optional: visualizations to support your conclusions

### Author
	•	Team 2
	•	Data Analyst – SQL & Business Intelligence Enthusiasts

### Notes
	•	Dataset is fictional but structured like real-world transactional data.
	•	Always validate assumptions before drawing conclusions.
	•	Clean data before uploading (e.g., check for NaNs or encoding issues).















