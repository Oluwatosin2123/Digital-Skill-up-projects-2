# Digital-Skill-up-projects-2
# Kultra Inventory Analysis using SQL
## Table of Contents

1. [Project Overview](#project-overview)  
2. [Dataset Overview](#dataset-overview)
3. [Result Image Attach](#Result)
4. [Sql file](#Sql-file)  
5. [Analysis Questions & SQL Queries](#analysis-questions--sql-queries)  
    3.1. [Product Category with Highest Sales](#1-product-category-with-highest-sales)  
    3.2. [Top 3 and Bottom 3 Regions by Sales](#2-top-3-and-bottom-3-regions-by-sales)  
    3.3. [Total Sales of Appliances in Ontario](#3-total-sales-of-appliances-in-ontario)  
    3.4. [Most Valuable Customer & Their Common Purchases](#4-most-valuable-customer--their-common-purchases)  
    3.5. [Small Business Customer with Highest Sales](#5-small-business-customer-with-highest-sales)  
    3.6. [Corporate Customer with Most Orders (2009–2012)](#6-corporate-customer-with-most-orders-2009–2012)  
    3.7. [Customers Who Returned Items & Their Segment](#7-customers-who-returned-items--their-segment)  
    4.  [Recommendation](#contributing)
       


This project presents a comprehensive analysis of Kultra's inventory and sales data using SQL. 
The analysis answers key business questions related to sales performance, customer behavior, and product segmentation.

## Dataset Overview

* This analysis assumes data is available in a relational database with tables such as
( `sales`, `products`, `customers`, `orders`, and `returns`.) 

### Example Tables:
- `products(product_id, name, category, sub_category)`
- `customers(customer_id, name, segment, business_type, region)`
- `orders(order_id, customer_id, order_date, region, status)`
- `order_details(order_id, product_id, quantity, price)`
- `returns(order_id, return_date)`

### Image Result Attach

![image alt](https://github.com/Oluwatosin2123/Digital-Skill-up-Africa-Projects/blob/c869092e2d78794604ccf2c677b6a7136486f014/Average%20profit.png)

![image alt](https://github.com/Oluwatosin2123/Digital-Skill-up-Africa-Projects/blob/6d6e0934b91bca0b958bb9ca0d6a58cb8e7a7706/Count.png)
![image alt](https://github.com/Oluwatosin2123/Digital-Skill-up-Africa-Projects/blob/2fa903235d515d298656998760605c4fcf355387/Highest%20top%203%20Region.png)
![image alt]
### Sql file [Download Here]https://github.com/Oluwatosin2123/Digital-Skill-up-projects-2/blob/0b53ad6c646c8a2cc94b44351c0b708cd4172275/Kultra%20inventory%20Analysis.%20sql.txt


## Analysis Questions & SQL Queries

```sql
SELECT 
   Select * from [dbo].[KMS Sql Case Study2]

Update table [dbo].[KMS Sql Case Study2]
### 1. ---- correcting the data type---
Alter table [dbo].[KMS Sql Case Study2]
Alter column Sales decimal (18, 2)

Alter table [dbo].[KMS Sql Case Study2]
Alter column Discount decimal (18, 2)

Alter table [dbo].[KMS Sql Case Study2]
Alter column Product_Base_Margin decimal (18, 2)

Alter table [dbo].[KMS Sql Case Study2]
Alter column Product_Base_Margin decimal (18, 3)

Select * from [dbo].[KMS Sql Case Study2]

 
 -----count distinct-----
Select Customer_Segment, count(distinct Customer_Segment) as [Total Customer segment]
from [dbo].[KMS Sql Case Study2]
group by Customer_Segment
Order by [Total Customer Segment] desc
------ count----
Select Customer_Segment, count( Customer_Segment) as [Total Customer segment]
from [dbo].[KMS Sql Case Study2]
group by Customer_Segment
Order by [Total Customer Segment] desc

Select Customer_Segment, count( Customer_Segment) as [Total Customer segment]
from [dbo].[KMS Sql Case Study2]
group by Customer_Segment
Order by [Total Customer Segment] Asc
###  Product Category with Highest Sales
-----Top product category----
SELECT TOP 3 Product_Category, Customer_Segment, Sales  AS highest_Product
FROM [dbo].[KMS Sql Case Study2]
WHERE Product_Category = (SELECT MAX(Product_Category) 
FROM [dbo].[KMS Sql Case Study2])
ORDER BY Product_Category

 ### Product Category with Highest Sales 
SELECT TOP 3 Product_Category AS highest_Product
FROM [dbo].[KMS Sql Case Study2]
WHERE Product_Category = (SELECT MAX(Product_Category) 
FROM [dbo].[KMS Sql Case Study2])
ORDER BY Product_Category DESC

SELECT TOP 3 Product_Category,Customer_Segment, Sales  AS highest_Product
FROM [dbo].[KMS Sql Case Study2]
WHERE Product_Category = (SELECT MAX(Product_Category) 
FROM [dbo].[KMS Sql Case Study2])
ORDER BY Product_Category Asc;

 ### ----highest Top 3 Region in term of Sales---
SELECT Top 3 Region, Sales  AS highest_Sales
FROM [dbo].[KMS Sql Case Study2]
WHERE Product_Category = (SELECT MAX(Product_Category) 
FROM [dbo].[KMS Sql Case Study2])
ORDER BY Product_Category Asc

###  Top 3 and Bottom 3 Regions by Sales
SELECT Top 3 Region, Sales  AS Lowest_Sales
FROM [dbo].[KMS Sql Case Study2]
WHERE Product_Category = (SELECT Min(Product_Category) 
FROM [dbo].[KMS Sql Case Study2])
ORDER BY Product_Category Asc

### ----Top 3 region in term of Product Category
SELECT TOP 3 Product_Category, Region, Sales  AS highest_Product
FROM [dbo].[KMS Sql Case Study2]
WHERE Product_Category = (SELECT MAX(Product_Category) 
FROM [dbo].[KMS Sql Case Study2])
ORDER BY Product_Category Desc

SELECT TOP 3 Product_Category, Region, Sales  AS highest_Product
FROM [dbo].[KMS Sql Case Study2]
WHERE Product_Category = (SELECT MAX(Product_Category) 
FROM [dbo].[KMS Sql Case Study2])
ORDER BY Product_Category Asc
  
    3.6. [Corporate Customer with Most Orders (2009–2012)](#6-corporate-customer-with-most-orders-2009–2012)  
    3.7. [Customers Who Returned Items & Their Segment](#7-customers-who-returned-items--their-segment)  
###  ----highest Top 3 Product Category in term of Customer Segment and Sales---
SELECT top 3 Product_Category, Customer_Segment, Sales  AS highest_Sales
FROM [dbo].[KMS Sql Case Study2]
WHERE Product_Category = (SELECT MAX(Product_Category) 
FROM [dbo].[KMS Sql Case Study2])
ORDER BY Product_Category asc

###  -------Maximum product by Region, Profit and Sales
SELECT TOP 3 Product_Category, Region, Profit, Sales 
FROM [dbo].[KMS Sql Case Study2]
WHERE Product_Category = (SELECT MAX(Product_Category) 
FROM [dbo].[KMS Sql Case Study2])
ORDER BY Product_Category Asc

SELECT TOP 3 Product_Category, Region, Profit, Sales 
FROM [dbo].[KMS Sql Case Study2]
WHERE Product_Category = (SELECT MAX(Product_Category) 
FROM [dbo].[KMS Sql Case Study2])
ORDER BY Product_Category Asc

Select * from [dbo].[KMS Sql Case Study2]

### -----Total Sales by Region----
Select Region, sum(Sales) as [Total Sales]
from [dbo].[KMS Sql Case Study2]
group by Region
order by [Total sales] desc
Select * from [dbo].[KMS Sql Case Study2] 


### ---Total Sales by Ontario--

Select Region, sum(Sales) as [Total Sales]
from [dbo].[KMS Sql Case Study2]
Where Region = 'Ontario'
group by Region
order by [Total sales] 

Select * from [dbo].[KMS Sql Case Study]
### ----Total Profit----
Select Ship_Mode , Sum(Profit) as [Total Profit]
from [dbo].[KMS Sql Case Study2]
group by Ship_Mode
order by [Total Profit] Asc


### ----- Average Profit--
Select Ship_Mode , AVG(Profit) as [Average Profit]
from [dbo].[KMS Sql Case Study2]
group by Ship_Mode
order by [Average Profit] desc


### Most Valuable Customer & Their Common Purchases

Select Product_Category, count(Customer_Segment) as [Most Valuable Customer]
from [dbo].[KMS Sql Case Study2]
group by Product_Category
Order by [Most Valuable Customer] desc

Select * from [dbo].[KMS Sql Case Study2]

Select Product_Category, MAX(Customer_Segment)
AS [Most Valuable Customer],count(Customer_Segment) As[Total Customers]
from [dbo].[KMS Sql Case Study2]
group by Product_Category

Select * from [dbo].[KMS Sql Case Study2]

### Small Business Customer with Highest Sales
Select * from [dbo].[KMS Sql Case Study2]
Select  Product_Category, MAX(Sales) As [MaxSales]
from [dbo].[KMS Sql Case Study2]
Where Customer_Segment = 'Small Business'
group by Product_Category

Select * from [dbo].[KMS Sql Case Study2]

### -----Most shipping cost--

select Ship_Mode, count(Shipping_Cost) as [Most shipping cost]
from [dbo].[KMS Sql Case Study2]
group by Ship_Mode
order by Ship_Mode desc

select Ship_Mode, count(Shipping_Cost) as [Most shipping cost]
from [dbo].[KMS Sql Case Study2]
group by Ship_Mode
order by Ship_Mode Asc
----maximum order quantity corporate business between year 2009 and 2012

SELECT Product_Category, MAX(Order_Quantity) AS [Maximum Order Quantity]
FROM [dbo].[KMS Sql Case Study2]
WHERE Customer_Segment = 'Corporate'
  AND YEAR(Order_Date) BETWEEN 2009 AND 2012
group by Product_Category

Select * from [dbo].[KMS Sql Case Study2]

### ----- Total profit WHERE Customer Segment = 'Consumer'
SELECT Product_Category, Sum(Profit) AS [Total Profit]
FROM [dbo].[KMS Sql Case Study2]
WHERE Customer_Segment = 'Consumer'
group by Product_Category

### ----- Total profit WHERE Customer Segment = 'Small Business'
SELECT Product_Category, Sum(Profit) AS [Total Profit]
FROM [dbo].[KMS Sql Case Study2]
WHERE Customer_Segment = 'Small Business'
group by Product_Category

### ----- Total profit WHERE Customer Segment = 'Corporate'
SELECT Product_Category, Sum(Profit) AS [Total Profit]
FROM [dbo].[KMS Sql Case Study2]
WHERE Customer_Segment = 'Corporate'
group by Product_Category

### ------Profit WHERE consumer is more profitable'
SELECT Top 1 Product_Category, Max(Profit) AS [Maximum Profit]
FROM [dbo].[KMS Sql Case Study2]
WHERE Customer_Segment = 'Consumer'
group by Product_Category

Select * from  [dbo].[KMS Sql Case Study2]

### -----Small business customer with highest Sales---
SELECT Top 1 Product_Category, Max(Sales) AS [Maximum Sales]
FROM [dbo].[KMS Sql Case Study2]
WHERE Customer_Segment = 'Small business'
group by Product_Category

### ----- Corporate Customer that placed the most number of orders in 2009 – 2012---

SELECT Product_Category, YEAR(Order_Date) AS Order_Year,
  MAX(Order_Quantity) AS [Maximum Order Quantity]
FROM [dbo].[KMS Sql Case Study2]
WHERE Customer_Segment = 'Corporate'
  AND YEAR(Order_Date) BETWEEN 2009 AND 2012
GROUP BY Product_Category, YEAR(Order_Date)
ORDER BY Product_Category, Order_Year;

	
Select * From [dbo].[Order_Status]

### ----- Total Status-----
Select Status,
count(Status) AS Status_Count
 From [dbo].[Order_Status]
 GROUP BY Status
Order by Status;

### ------- Total Status by Order ID-----
Select Order_ID,
count(Status) AS Status_Count
 From [dbo].[Order_Status]
 GROUP BY Order_ID
Order by Order_ID Asc


### ---Join Main table with order status---
SELECT 
    os.Order_ID,
    os.Status,
    o.Customer_Name,
    o.Order_Date,
    o.Sales,
	o.Product_Category,
	o.Customer_Segment,
	o.Region
FROM 
    [dbo].[Order_Status] AS os
JOIN 
    [dbo].[KMS Sql Case Study2] AS o
    ON os.Order_ID = o.Order_ID
ORDER BY 
    os.Order_ID;

### -----Customer that returned items, Segment-----
SELECT 
    o.Customer_Segment,
    COUNT(o.Order_ID) AS Returned_Orders
FROM 
    [dbo].[KMS Sql Case Study2] AS o
JOIN 
    [dbo].[Order_Status] AS os
    ON o.Order_ID = os.Order_ID
WHERE 
    os.Status = 'Returned'
GROUP BY 
    o.Customer_Segment
ORDER BY 
    Returned_Orders DESC;
Select * from [dbo].[KMS Sql Case Study2]

 ## Recommendation
-----Recommendation
What the management of KMS can do to increase the revenue from the bottom 
10 customers -----
* Set a target for the top 4 from the bottom Revenue---
* Revenue_Gap AS (
    SELECT 
        5500000.0 * 4 AS Target_Revenue,
        t.Bottom_Total_Revenue,
        (5500000.0 * 4) - t.Bottom_Total_Revenue AS Revenue_Gap
    FROM Total_Bottom_Revenue t
)
-- Final Output
  ----  Target_Revenue,
 ---- Bottom_Total_Revenue,
 --- Revenue_Gap
  ---FROM Revenue_Gap;
----Recommendation
If the delivery truck is the most economical but the slowest shipping method and 
* Express Air is the fastest but the most expensive one, do you think the company appropriately spent shipping costs based on the Order Priority? Explain your answer

*Since the Express Air and Regular Air has more high order priority and order count Kultra Iventory should increase the shipping costbase on the Order Quantity so that the company will have a profitable gain and not lost.

    
