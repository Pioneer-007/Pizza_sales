# Pizza_sales

## Table of Content

- [Project Overview](#project-overview)

### Project Overview
This data analysis project aims at providing insights insight into the sales performance of a company over the past years, by analyzing various aspects of the pizza sales data , we seek to calculate profits, identify trends and make data driven recommendation for decision in the future.

### Data Source

Ths primary dataset used for this analysis is the "pizza_sales.csv" it contains detailed information about the sales made by the company.

### Tools
- Excel - Data Cleaning and Visualization.
    - [Download Here](https://microsoft.com)
- SQL Server - Data Analysis.
     - [Download Here](https://microsoft.com)

### Data Cleaning and Preparation
In the initial data preparation phrase ,we performed the following tasks:
1. Data loading and inspection.
2. Handling missing values.
3. Data cleaning and formatting


### Exploratory Data Analysis
Exploring the pizza sales data to answer key question such as:
- What is the total revenue ?
- what is the total pizza sold ?
- what is the total and average pizza per order ?
- what is the total pizza sold by pizza category ?
- what are the five top and five bottom pizza sold ?
- what is the daily trend for total order?
- what is the percentage sales by pizza size and pizza category ?


### Data Analysis 
```sql
1.TOTAL REVENUE: 
SELECT SUM(total_price) as Total_Revenue FROM pizza_sales

2.AVERAGE ORDER VALUE:
SELECT SUM(total_price)/COUNT(DISTINCT order_id) as Avg_order_value FROM pizza_sales

3.TOTAL PIZZAS SOLD:
 SELECT SUM(quantity) as Total_pizza_sold FROM pizza_sales

4.  TOTAL ORDERS: 
SELECT COUNT(DISTINCT order_id) AS Total_orders FROM pizza_sales

5. AVERAGE PIZZAS PER ORDER:
SELECT CAST(CAST(SUM(quantity) as DECIMAL (10,2))/CAST(COUNT(DISTINCT order_id)AS DECIMAL(10,2)) AS DECIMAL(10,2)) AS Average_pizzas_per_orders FROM pizza_sales

 1. Daily Trends For Total Orders:
SELECT DATENAME(DW,order_date) AS ORDER_DAY,COUNT(DISTINCT order_id) AS Total_order FROM pizza_sales GROUP BY DATENAME(DW,order_date) ORDER BY Total_order ASC

2. Percentage Sales By Pizza Category
  SELECT pizza_category, CAST(SUM(total_price) AS DECIMAL(10,2)) AS Total_Revenue,
  CAST(SUM(total_price)*100/(SELECT SUM(total_price)FROM pizza_sales) AS DECIMAL(10,2))  AS PSPC FROM pizza_sales group by pizza_category

3. Percentage Sales by Pizza Size:
   SELECT pizza_size, SUM(total_price) AS Total_Sales,CAST(SUM(total_price)*100/ (SELECT SUM(total_price) FROM pizza_sales) AS DECIMAL(10,2)) AS PSPS
    FROM pizza_sales GROUP BY pizza_size ORDER BY PSPS DESC

4. Total Pizza Sold By Pizza Category:
   SELECT pizza_category, SUM(quantity) AS TOTAL_PIZZA_SOLD FROM pizza_sales GROUP BY pizza_category ORDER BY TOTAL_PIZZA_SOLD

5. TOP 5 BEST Sellers By Total Pizza Sold:
   SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold FROM pizza_sales GROUP BY pizza_name ORDER BY SUM(quantity)DESC

6.  BOTTOM 5 WORST Sellers By Total Pizza Sold:
   SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold FROM pizza_sales GROUP BY pizza_name ORDER BY SUM(quantity)ASC
```

### Result and Findings
BUSIEST DAYS are THURSDAYS ,FRIDAYS and SATURDAYS orders are highest on these days.
SALES BY CATEGORIES : CLASSIC CATEGORY contributes to MAXIMUM SALES and TOTAL ORDER.
SALES BY SIZE: LARGE SIZE pizza contributes to MAXIMUM SALES.
BEST SELLERS are CLASSIC DELUX PIZZA is the BEST sellers and revenue generators
WORST SELLER IS BRIE CARRIE is at the BOTTOM in both orders and revenue. 

### Recommendations 
the pizza sales company should produce more of classic delux pizza large size and open for sales on thursays friday and saturday   

### Limitatons
we had to get the daily trend form the order_id and pizza_id was not used.

### References
- sql for business





















