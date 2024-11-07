## SALES-AND-CUSTOMERS-DATA-PROJECT-WITH-LITA

### MY-FIRST-PROJECT-DURING-MY-DATA-ANALYSIS-TRAINING-WITH-THE-INCUBATOR-HUB.
---
[PROJECT OVERVIEW](#project-overview)

[DATA SOURCES](#data-sources)

[DATA CLEANING AND PREPARATIONS](#data-cleaning-and-preparations)

[EXPLORATORY DATA ANALYSIS](#exploratory-data-Analysis)

[DATA ANALYSES](#data-analyses)

[DATA SUMMARIZATION PRESENTATION AND VISUALIZATION](#data-summarization-presentation-and-visualization)




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
  
- STUCTURE QUERY LANGUAGE-[Download Here] [https://www.microsoft.com]
1.  Data quering.
2. Data presentatiofon.

- POWER BUSINESS INTELLIGENCE - for data cleaning , entry, presentation and summarization.
- GITHUB - for portfolio building.
  
### DATA CLEANING AND PREPARATIONS .
1. At the intial stage of this project, data gathering, cleaning, entry are done.
2. Data inspection and adding variables using techniques such as measures, conditional andcalculated datas are generated.

### EXPLORATORY DATA ANALYSIS; 
  This helps in data exploration,  summarized, facts such as best and worst performing products , customers and regions are presentated.
  
### DATA ANALYSIS AND PRESENTATIONS.
 Data are summarized, facts such as best and worst performing products , customers and regions are presentated.

### MICFROSOFT EXCEL ANALYSES ; filters, slicer, Auto fill (for getting totals, =) control z, 
The STRUCTURE QUERY LANGUGE Codes useD im this DATA ANALYSIS icludes ``sql for  



```SQL

create database PROJECT_DB
	
	select * from [dbo].[Sales Data For Sql Ikeja]

	----SALES DATA EXPLORATION----
	
----1. RETRIEVE TOTALSALES FOR EACH PRODUCT CATEGORY----

	select Product,Sum(Quantity*UnitPrice) as totalsale
	from [dbo].[Sales Data For Sql Ikeja]
	Group By Product

		RENAME SALES COLUMN AS TOTALSALES


	----2. FIND NUMBERS OF SALES TRANSACTIONS IN EACH REGION---

	select Region, COUNT(OrderID) as NumberOfSalesTransactions
	from [dbo].[Sales Data For Sql Ikeja]
	Group By Region;


	----3. FIND THE HIGHEST SELLING PRODUCT BY TOTALSALES VALUE---

	select Top 1 PRODUCT, SUM(Quantity*UnitPrice) as TotalSales
	from [dbo].[Sales Data For Sql Ikeja]
	Group By Product
	Order By TotalSales Desc;


	---4. CALCULATE TOTAL REVENUE PER PRODUCT---

	select PRODUCT, SUM(Quantity*UnitPrice) as TotalSales
	from[dbo].[Sales Data For Sql Ikeja]
	Group By Product;


	---5. CALCULATE MONTHLY SALES TOTALS FOR CURRENT YEAR---
		
		select Month(OrderDate) as Month, 
		SUM(Quantity*UnitPrice) as MonthlySalesTotals
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

	SELECT Region, 
		SUM(Quantity*UnitPrice) 
		*00.1 AS Percebtage_of_Total_Sales
		FROM [dbo].[Sales Data For Sql Ikeja]
		GROUP BY Region
		ORDER BY Percebtage_of_Total_Sales

	8--- IDENTIFY PRODUCTS WITH NO SALES IN THE LAST QUATER---

		SELECT PRODUCT
		FROM [dbo].[Sales Data For Sql Ikeja]
		GROUP BY Product
		HAVING SUM(CASE
		WHEN OrderDate BETWEEN '2024-06-01' AND '2024-08-31'
		THEN 1 ELSE 0 END) =0
		
		----CUSTOMER DATA EXPLORATION----

		SELECT * FROM[dbo].[CSV CUSTOMER DATA now]

			1. --RETRIVE THE TOTAL REVENUE FOR EACH SUBSCRIPTION TYPE---

		SELECT SubscriptionType ,
			SUM (REVENUE) AS TOTALREVENUE
			FROM [dbo].[CSV CUSTOMER DATA now]
			GROUP BY SubscriptionType  

	2.---NUMBER OF SALES TRANSACTIONS IN EACH REGION---

	select Region,
	COUNT(CustomerID) as NumberOfSalesTransactions
	from [dbo].[CSV CUSTOMER DATA now]
	Group By Region;

	3. ---HIGHEST SELLING SUBSCRIPTION TYPE BY TOTAL REVENUE----

	select Top 1 SubscriptionType, 
	SUM (REVENUE) AS TOTALREVENUE
	from [dbo].[CSV CUSTOMER DATA now]
	Group By SubscriptionType
	Order By TOTALREVENUE Desc;
	
	  4.---CALCULATE TOTAL REVENUE BY SUBCRIPTION TYPE----

	Select SubscriptionType, 
		SUM (REVENUE) AS TOTALREVENUE
		from [dbo].[CSV CUSTOMER DATA now]
		Group By SubscriptionType

	5. ----MONTHLY TOTAL REVENUE FOR THE CURRENT YEAR---

	select Month(2024-01-01) as Month, 
		SUM(Revenue) as MonthlySalesTotals
		from [dbo].[CSV CUSTOMER DATA now]
		Group By Revenue

		6. ----FIND THE TOP FIVE CUSTOMERS BY TOTAL PURCHASE AMOUNT---

	Select Top 5 CustomerID, 
		SUM(Revenue) as TotalPurchaseAmount
		FROM [dbo].[CSV CUSTOMER DATA now]
		Group By CustomerID
		Order By TotalPurchaseAmount Desc;

	7. ---THE PERCENTAGE OF TOTAL REVENUE CONTRIBUTED  BY EACH REGION---

	SELECT Region, 
		SUM(Revenue) 
		*00.1 AS Percebtage_of_Total_Revenue
		FROM [dbo].[CSV CUSTOMER DATA now]
		GROUP BY Region
		ORDER BY Percebtage_of_Total_Revenue


	8--- IDENTIFY PRODUCTS WITH NO SALES IN THE LAST QUATER---

		SELECT SubscriptionType
		FROM [dbo].[CSV CUSTOMER DATA now]
		GROUP BY SubscriptionType
		HAVING SUM(CASE
		WHEN SubscriptionStart BETWEEN '2024-06-01' AND '2024-08-31'
		THEN 1 ELSE 0 END) =0	

	SELECT * FROM[dbo].[CSV CUSTOMER DATA now]
```SQL
 👍✔👍HEADING 1HEADING
-----1---------2-------
:
;
