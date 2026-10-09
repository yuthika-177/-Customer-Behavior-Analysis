# -Customer-Behavior-Analysis
End-to-end customer behavior analytics on 3,900 shoppers using Python (pandas), MySQL and Power BI: data cleaning, SQL business queries, an interactive dashboard and actionable recommendations.

Project overview

 The dataset describes 3,900 customers and 18 attributes (demographics, product, purchase amount, subscription, shipping, discounts,   purchase history and more). The goal is to understand who the customers are, what drives revenue, and where the business can grow.

Metric	Value

Customers	3,900
Total revenue	$233,081
Average purchase amount	$59.76
Average review rating	3.75 / 5

Tools and technologies

Python: pandas, SQLAlchemy, PyMySQL (Jupyter Notebook)
MySQL: aggregation, subqueries, CASE, CTEs, window functions
Power BI Desktop: KPI cards, slicers, charts

Workflow

Prepare (Python): load the CSV, handle missing values, standardise column names, create new features, drop redundant data.
Store (MySQL): write the cleaned DataFrame to the customer table in the customer_shopping database.
Analyse (SQL): answer ten business questions.
Visualise (Power BI): build a one-page interactive dashboard.

Data cleaning and feature engineering

Filled 37 missing review ratings with the median rating of each product category.
Renamed columns to lower-case snake_case (for example Purchase Amount (USD) to purchase_amount).
Created age_group using four quartile bins: Young Adult (18-31), Adult (32-44), Middle_aged (45-57), Senior (58-70).
Created purchase_frequency_days from the purchase frequency labels.
Dropped promo_code_used, which was identical to discount_applied in every row.
 
 SQL analysis

The  questions in customer.sql:

 Total revenue by gender?
 Discount users who still spent more than the average purchase amount?
 Top 5 products by average review rating?
 Average purchase amount: Express vs Standard shipping?
 Do subscribers spend more? (average spend and total revenue)
 Top 5 products by share of purchases with a discount?
 Customer segments (New, Returning, Loyal) by previous purchases?
 Top 3 most purchased products within each category?
 Are repeat buyers more likely to subscribe?
 Revenue contribution of each age group?
 
 
 Key findings
 
Clothing and Accessories generate 76.5% of revenue; Outerwear contributes only 7.9%.
Men account for 67.7% of revenue because they are 68% of customers. Spend per customer is almost identical (Male $59.54, Female $60.25), so the gap is about acquisition, not spending.
Subscribers do not spend more. Average spend is $59.49 for subscribers and $59.87 for non-subscribers; only 27% of customers are subscribed.
Repeat buyers are not more likely to subscribe: 27.6% of repeat buyers subscribe versus 27.0% overall.
43% of purchases use a discount, and half of discounted customers (839 of 1,677) still spent at or above the average.
80% of customers are loyal (11+ previous purchases), but only 2.1% are new, which points to weak new-customer acquisition.
Spend is balanced across age groups (23.9% to 26.7% of revenue each).

Recommendations

Redesign the subscription program and target the 2,518 loyal non-subscribers.
Move from blanket discounts to targeted ones, starting with the five most-discounted products.
Invest in acquiring new customers, especially female customers.
Grow Outerwear through bundles and seasonal campaigns.

Power BI dashboard

The dashboard includes KPI cards (customers, average purchase amount, average review rating), a subscription split, revenue and sales by category, revenue and sales by age group, and slicers for subscription status, gender, category and shipping type.

Repository structure

customer-behavior-analytics/
├── data/
│   └── customer_shopping_behavior.csv
├── notebooks/
│   └── customer.ipynb
├── sql/
│   └── customer.sql
├── powerbi/
│   └── customer_behaviour_dashboard.pbix
├── images/
│   └── dashboard.png
├── reports/
│   ├── Customer_Behavior_Analytics_Report.docx
│   └── Customer_Behavior_Analytics_Presentation.pdf
└── README.md

How to run

Clone the repository and install the dependencies:
bash
   pip install pandas sqlalchemy pymysql jupyter
Create a MySQL database named customer_shopping.
Set your database password as an environment variable instead of writing it in the notebook:
bash
   export DB_PASSWORD="your_password"
Open notebooks/customer.ipynb, update the CSV path, and run all cells. This cleans the data and writes the customer table to MySQL.
Run the queries in sql/customer.sql against the customer_shopping database.
Open powerbi/customer_behaviour_dashboard.pbix in Power BI Desktop and refresh the data source if needed.

Limitations

Each customer appears once and there is no purchase date, so trends over time cannot be analysed.
Findings show association, not causation, and group differences were not tested for statistical significance.

Future work

Add purchase dates for trend and seasonality analysis.
Segment customers with RFM or clustering.
Build a model to predict which customers are likely to subscribe.
Publish the dashboard to Power BI Service with scheduled refresh.

Author
Yuthika
