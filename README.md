## LITA-Captone Project One Documentation

### Project Title: Sales Performance Analysis of a Retail Store : Trends and Insights.
  [Project Overview](project-overview)
  
  Data Source
  
  Tools Used
  
  Data Cleaning and Preparation
  
  Exploratory Data Analysis
  
  [Data Analysis](data-analysis)

### Project Overview
---
This project focuses on analyzing the sales performance of Retail Store,using historical sales data. The analysis will uncover key trends in product sales, customer preferences, and seasonal variations. By examining metrics such as total revenue, average transaction value, and sales by category, region, the project aims to identify factors driving sales growth and opportunities for improving profitability. The insights gained will help the retail store optimize inventory management, promotional strategies, and customer engagement for increased sales performance.

### Data Source
---
This is the primary source of data used here is Sales Data. xlxs and  this is an open data that can be freely downloaded online such as Kaggle or FRED or any other resprespostry site. 

### Tools Used
---
- Microsoft Excel[Download Here](https://wwww.microsoft.com)
1. For Data cleaning
3. For Anaysis
4. For Data Visualization
- SQL-Structured Query Language for Querying Data.
- GitHub for Portfolio building
- Data Visualizatio(Power Business Intelligence)
  
### Data Cleaning and Preparation
---
This process focuses on preparing the dataset for analysis by identifying and rectifying inaccuracies, inconsistencies, and errors. Key steps include:

1. Handling Missing Values: Identifying and addressing missing data through removal or imputation.

2. Removing Duplicates: Ensuring that each record is unique by eliminating duplicate entries.

3. Correcting Errors: Fixing typographical errors, formatting issues, and out-of-range values.

4. Filtering Outliers: Identifying and deciding how to manage outliers that may skew results.

5. Data Transformation: Converting data types and normalizing values as needed.

### Exploratory Data Analysis
---
Its involves the ecploring of data to answer some question such as
- What  is the overall trendstrends? 
- which product are the top seller?
- What is the sum of revenue by region?
- what is the average revenue by products?


### Data Analysis
---
This is where we conclude some basic lines of type codes, Queries or even DAX expressions use during the analysis

```` SQL
CREATE DATABASE LITA_CAPSTONE_PROJECT_ONE
Select*from[dbo].[Sales Data 1]

Select Product,sum(total_Revenue) AS 'total_sales'
from [dbo].[Sales Data 1]
group by product

..... 2 The number of sales transactions in each region...
Select Region, count(*) As Total_Transaction
from[dbo].[Sales Data 1]
group by Region

...3 The highest-selling product by total sales value.
select top 1 Product,sum(Total_Revenue) as Total_revenue
from[dbo].[Sales Data 1]
group by product

.... 4 The total revenue per product

Select Product,sum(total_Revenue) AS Total_Revenue
from [dbo].[Sales Data 1]
group by product
.....5 monthly sales totals for the current year
 select Month(Orderdate) as month,
 sum([Total_revenue]) As monthly_sales
 from[dbo].[Sales Data 1]
 Where
 year(Orderdate)=YEAR(getdate())
 Group by MONTH(OrderDate)
 ORDER BY MONTH;

 ..... 6  The top 5 customers by total purchase amount....
 Select top 5 Customer_Id,
 SUM(total_revenue) AS 'Total_PurchaseAmount'
 from[dbo].[Sales Data 1]
 Group by Customer_Id
 ORDER BY Total_PurchaseAmount DESC;


 .... 7 The percentage of total sales contributed by each region.

 Select Region,
 sum(Total_Revenue) As total_revenue
 'sum'(Total_Revenue)* 1.0/(select 
 SUM((Total_Revenue)
 from[dbo].[Sales Data 1]*100 as percentageoftotalsales'
 from[dbo].[Sales Data 1]
 GROUP BY Region;

 ...... 8 identify products with no sales in the last quarter
 Select DISTINCT s1.[product]
 FROM [dbo].[Sales Data 1]s1
LEFT JOIN[dbo].[Sales Data 1]s2 ON s1.
[product]=s2.[Product]AND s2.OrderDATE
>=DATEADD(QUARTER,-1,GETDATE())
WHERE
s2.[product] IS NULL;

###Data Visualizaion

![Dashboard for Sales Performannce](https://github.com/user-attachments/assets/6f3c06bf-cca1-46f4-8d0d-98150ee7e30e)
