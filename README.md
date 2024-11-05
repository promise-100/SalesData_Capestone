# SalesData_Capestone

### Project Title: Sales Analysis

### Project Overview:
In this project, i will dive into a large sales dataset to extract valuable insights. The project aims to analyse the sales performance of a business, uncover key insights such as product performance, regional performance and sales trend.
This project showcases my ability to manipulate and derieve insight from large dataset, enabling me to make data driven recommendations for optimizing sales strategies.

### Data Sources:
Considering this is a capestone project, my trainer, The Incubator Hub provided the sales dataset for this analysis.

### Data Structure:
The original dataset is an excel file with 50,000 rows and 7 columns which includes: OrderID, CustomerID, Product, Region, OrderDate, Quantity and Unit Price.

### Tools Used:
- Microsoft Excel [Download Here](https:www.microsoft.com)
   1. For Data Cleaning and Analysis.
   2. For Data Analysis.
- SQL - Structured Query Language
   1. For Querying of Data.
- Microsoft Powerbi [Download Here](https:www.microsoft.com)
   1. For Data Analysis
   2. For Data Visualization.
- GitHub
   1. For Portfolio Building.

### Data Cleaning and Preparation:
The dataset went through some processes of data cleaning and preparations to ensure accuracy and consistency. This involves;
- Data Inspection.
- Removing Duplicates.
- Addressing missing values.

### Exploratory Data Analysis(EDA).
EDA involved the exploring of the data to answer some questions about the data suc as;
- Retrieve the total sales for each product category.
- Find the number of sales transactions in each region.
- Find the highest-selling product by total sales value
- Calculate total revenue per product.
- Calculate monthly sales totals for the current year.
- Find the top 5 customers by total purchase amount.
- Calculate the percentage of total sales contributed by each region.
- Identify products with no sales in the last quarter.

### Data Analysis:
This is where I include some Excel Formulars, SQL Queries and DAX Functions used during the analysis.
- Excel Formulars used:
  1. I starated by creating tha sales column which was not originally on my dataset. i did that using this formular: 
     =F:F*G:G.
  2. Total Sales = SUM(SalesData!H:H)
  2. Total Sales by each Region = SUMIF(D:D,D2,H:H)
  3. Average Sales for each product using AverageIF = AVERAGEIF(C:C,C2,H:H)
    
Below are the screenshot of the microsoft excel formulars:
![My Excel Formulars](https://github.com/user-attachments/assets/590be75e-00d6-4160-9c9b-32cb82d12083).

![Addition fo 2 columns](https://github.com/user-attachments/assets/028fb53d-6e99-488a-9450-3be5b9575c45)


After the analysis on the microsoft excel worksheet, I summarized the data using pivot table.
Beow is the screenshot of the pivot tables created.

![Salesdata pivottable](https://github.com/user-attachments/assets/a05cceb6-7c44-4b98-a42d-63f5840b68e2)




 - SQL Queries used:
  I used SQL Queries to answer the above listed questions:
  1. Retrieve the total sales for each product category.
     
    ```
    SELECT PRODUCT, SUM(SALES) AS TOTALSALES FROM [dbo].[SALESDATA_CAPESTONE]
    GROUP BY PRODUCT
    ORDER BY TOTALSALES DESC
    ```

  2. find the number of sales transactions in each region
     ```
     SELECT REGION, COUNT(ORDERID) AS NUMBER_OF_SALES_TRANSACTION
     FROM [dbo].[SALESDATA_CAPESTONE]
     GROUP BY REGION
     ORDER BY NUMBER_OF_SALES_TRANSACTION
     ```

  3.  find the highest-selling product by total sales value.
     ```
     SELECT TOP 1 PRODUCT, SUM(SALES) AS HIGHEST_SELLING_PRODUCT
     FROM [dbo].[SALESDATA_CAPESTONE]
     GROUP BY PRODUCT
     ORDER BY HIGHEST_SELLING_PRODUCT DESC
     ```

 4.  calculate total revenue per product.
     ```
     SELECT PRODUCT, SUM(SALES) AS TOTAL_REVENUE
     FROM [dbo].[SALESDATA_CAPESTONE]
     GROUP BY PRODUCT
     ORDER BY TOTAL_REVENUE DESC
     ```

 5. calculate monthly sales totals for the current year
    ```
     SELECT MONTH(ORDERDATE) AS [MONTH], SUM(SALES) AS SALES_PER_MONTH
     FROM [dbo].[SALESDATA]
     WHERE YEAR(ORDERDATE) = 2024
     GROUP BY MONTH(ORDERDATE)
     ORDER BY 1 DESC
    ```

 6. Find the top 5 customers by total purchase amount.
    ```
     SELECT TOP 5 Customer_Id, SUM(SALES) AS TOTAL_PURCHASE_AMOUNT
     FROM [dbo].[SALESDATA_CAPESTONE]
     GROUP BY Customer_Id
     ORDER BY TOTAL_PURCHASE_AMOUNT DESC
    ```

 7. calculate the percentage of total sales contributed by each region.
    ```
     SELECT REGION, SUM(SALES) AS REGIONAL_SALES_TOTAL,
     (SUM(SALES) * 100) / (SELECT SUM(SALES) FROM SALESDATA_CAPESTONE) AS SALES_PERCENTAGE
     FROM [dbo].[SALESDATA_CAPESTONE]
     GROUP BY REGION
    ```

 8. identify products with no sales in the last quarter.
    ```
     SELECT DISTINCT PRODUCT
     FROM [dbo].[SALESDATA]
     WHERE PRODUCT NOT IN(
     SELECT PRODUCT
     FROM [dbo].[SALESDATA]
     WHERE ORDERDATE >= DATEADD(QUARTER, -1, GETDATE())
     )
    ```
     



