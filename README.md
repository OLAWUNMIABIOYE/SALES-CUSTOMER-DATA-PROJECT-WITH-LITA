## SALES-AND-CUSTOMERS-DATA-PROJECT-WITH-LITA

### MY-FIRST-PROJECT-DURING-MY-DATA-ANALYSIS-TRAINING-WITH-THE-INCUBATOR-HUB.
---

#### PROJECT OVERVIEW.
This data analysis project is base on the sales and customer's operations of a medium scale company (TAMELA AND CO LIMITED), located in the Western part of Nigeria. It focuses on a typical day-day transactions of an indigenous business in a developing country. All basic parameters ranging from Customer's ID, Customer's location, Products mostly purchase and minimally purchase,Quantities bought and their Unit prices etc wrere all analyse. This aqre some of the information that helps to derive at a compelling story and performance of Tamela aand CO. Tamela and co is one of the few indigenous company in Nigeria that that boast of making good profit despite the very bad economic condition in Nigeria.
And one of their testimonies is the frequent datsa accessment that guides / analysis the company on profit making products and other tactical solutions that prevents losses

### DATA SOURCES
The primary data tools used in analysing this project are DataSalescsv and they are downloaded freely on the internet because they are all open sources of data analysing tools.

TOOLS USED;-
_ MICROSOFT EXCEL- [Download Here][https://www.microsoft.com]
1. For data cleaning.
2.  For data entry.
3.  For data analysing.
4.  For data summarisation using pivot tables.
  
- STUCTURE QUERY LANGUAGE- for data quering and presentatiofon,
- POWER BUSINESS INTELLIGENCE - for data cleaning , entry, presentation and summarization.
- GITHUB - for portfolio building.
  
### DATA CLEANING AND PREPARATIONS .
1. At the intial stage of this project, data gathering, cleaning, entry are done.
2. Data inspection and adding variables using techniques such as measures, conditional andcalculated datas are generated.

### Exploratory Data Analysis; 
  This helps in data exploration,  summarized, facts such as best and worst performing products , customers and regions are presentated.
  
### DATA ANALYSIS AND PRESENTATIONS.
 Data are summarized, facts such as best and worst performing products , customers and regions are presentated.

 ```SQL

	create database PROJECT_DB

select * from [dbo].[Sales Data For Sql Ikeja]
	
----1. RETRIEVE TOTALSALES FOR EACH PRODUCT CATEGORY----

	select Product,Sum(Quantity*UnitPrice) as totalsale
	from [dbo].[Sales Data For Sql Ikeja]
	Group By Product

	RENAME SALES COLUMN AS TOTALSALES


	----2, FIND NUMBERS OF SALES TRANSACTIONS IN EACH REGION---

	select Region, COUNT(OrderID) as NumberOfSalesTransactions
	from [dbo].[Sales Data For Sql Ikeja]
	Group By Region;


	----3. FIND THE HIGHEST SELLING PRODUCT BY TOTALSALES VALUE---

	select Top 1 PRODUCT, SUM(Quantity*UnitPrice) as TotalSales
	from [dbo].[Sales Data For Sql Ikeja]
	Group By Product
	Order By TotalSales Desc;


	---4. CALCULATE TOTAL REVENUE PER PRODUCT---

	select PRODUCT, SUM(Quantity*UnitPrice) as TotalRevenue
	from[dbo].[Sales Data For Sql Ikeja]
	Group By Product;


	---5. CALCULATE MONTHLY SALES TOTALS FOR CURRENT YEAR---
		
		select Month(OrderDate) as Month, SUM(Quantity*UnitPrice) as MonthlySalesTotals
		from [dbo].[Sales Data For Sql Ikeja] 
		Where Year(OrderDate) = 2024
		Group By MONTH(OrderDate)
		Order By Month;


		----6. FIND TOP FIVE CUSTOMERS BY TOTALPURCHASE AMOUNT---

		select Top 5 Customer_id, SUM(Quantity*UnitPrice) as TotalPurchaseAmount
		From [dbo].[Sales Data For Sql Ikeja]
		Group By Customer_id
		Order By TotalPurchaseAmount Desc;
					   

		---7. CALCULATE THE PERCENTAGE OF TOTALSALES PER REGION----

		calculate the PercentageOfTotalSales contributed by each region,-
		select Region. SUM(Sales) As RegionTotalSales,-
		FORMAT(ROUND((SUM(Sales)/CAST((SELECT SUM(Sales)
		FROM [dbo].[Sales Data For Sql Ikeja] AS DECIMAL (10,2)) * 100),1),'0.#')
		AS PercentageOfTotalSales
		FROM[dbo].[Sales Data For Sql Ikeja]
		GROUP BY Region
		ORDER BY PercentageOfTotalSales
		DESC

		8--- IDENTIFY PRODUCTS WITH NO SALES IN THE LAST QUATER---

		SELECT PRODUCT
		FROM [dbo].[Sales Data For Sql Ikeja]
		GROUP BY Product
		HAVING SUM(CASE
		WHEN OrderDate BETWEEN '2024-06-01' AND '2024-08-31'
		THEN 1 ELSE 0 END) =0
```SQL

 
