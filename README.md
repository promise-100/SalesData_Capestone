# Sales Data Project
---
### Project Title: Sales Analysis
---

[Project Overview](#project-overview)

[Data Sources](#data-sources)

[Data Structure](#data-structure)

[Tools Used](#tools-used)

[Data Cleaning and Preparation](#data-cleaning-and-preparation)

[Exploratory Data Analysis](#exploratory-data-analysis)

[Data Analysis](#data-analysis)

[Data Visualization](#data-visualization)

[View of my Dashboards](#view-of-my-dashboards)

[Conclusion](#conclusion)

### Project Overview:
---
In this project, i will dive into a large sales dataset to extract valuable insights. The project aims to analyse the sales performance of a business, uncover key insights such as product performance, regional performance and sales trend.
This project showcases my ability to manipulate and derieve insight from large dataset, enabling me to make data driven recommendations for optimizing sales strategies.

### Data Sources:
---
Considering this is a capestone project, my trainer, The Incubator Hub provided the sales dataset for this analysis.

### Data Structure:
---
The original dataset is an excel file with 50,000 rows and 7 columns which includes: OrderID, CustomerID, Product, Region, OrderDate, Quantity and Unit Price.

### Tools Used:
---
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
---
The dataset went through some processes of data cleaning and preparations to ensure accuracy and consistency. This involves;
- Data Inspection.
- Addressing missing values.
- Removing Duplicates.
 During this process of cleaning the data. i descovered that my data contains a quite number of duplicates which i removed and this action made the rows of my data to reduce to 9,901 rows.

### Exploratory Data Analysis:
---
EDA involved the exploring of the data to answer some questions about the data such as;
- Retrieve the total sales for each product category.
- Find the number of sales transactions in each region.
- Find the highest-selling product by total sales value
- Calculate total revenue per product.
- Calculate monthly sales totals for the current year.
- Find the top 5 customers by total purchase amount.
- Calculate the percentage of total sales contributed by each region.
- Identify products with no sales in the last quarter.

### Data Analysis:
---
This is where I include some Excel Formulars, SQL Queries and DAX Functions used during the analysis.
#### Analysis using Excel Formulars used:
  1. I starated by creating tha sales column which was not originally on my dataset. i did that using this formular: 
     =F:F*G:G.
  2. Total Sales = SUM(SalesData!H:H)
  2. Total Sales by each Region = SUMIF(D:D,D2,H:H)
  3. Average Sales for each product using AverageIF = AVERAGEIF(C:C,C2,H:H)
    
Below are the screenshot of the microsoft excel formulars:

![My Excel Formulars](https://github.com/user-attachments/assets/e9d85d79-2cf3-4ce6-889c-cdd42f101cac)

![Addition fo 2 columns](https://github.com/user-attachments/assets/36e158ab-f194-463e-abdb-3d3f42d0f1eb)

After the analysis on the microsoft excel worksheet, I summarized the data using pivot table.
Beow is the screenshot of the pivot tables created.

![Salesdata pivottable](https://github.com/user-attachments/assets/a05cceb6-7c44-4b98-a42d-63f5840b68e2)


#### Analysis using SQL Queries used:
  I used SQL Queries to answer the questions below:
1. Retrieve the total sales for each product category.
     
    ```
    SELECT PRODUCT, SUM(SALES) AS TOTALSALES FROM [dbo].[SALESDATA_CAPESTONE]
    GROUP BY PRODUCT
    ORDER BY TOTALSALES DESC
    ```

2. Find the number of sales transactions in each region
     ```
     SELECT REGION, COUNT(ORDERID) AS NUMBER_OF_SALES_TRANSACTION
     FROM [dbo].[SALESDATA_CAPESTONE]
     GROUP BY REGION
     ORDER BY NUMBER_OF_SALES_TRANSACTION
     ```

3. Find the highest-selling product by total sales value.
     ```
     SELECT TOP 1 PRODUCT, SUM(SALES) AS HIGHEST_SELLING_PRODUCT
     FROM [dbo].[SALESDATA_CAPESTONE]
     GROUP BY PRODUCT
     ORDER BY HIGHEST_SELLING_PRODUCT DESC
     ```

 4. Calculate total revenue per product.
     ```
     SELECT PRODUCT, SUM(SALES) AS TOTAL_REVENUE
     FROM [dbo].[SALESDATA_CAPESTONE]
     GROUP BY PRODUCT
     ORDER BY TOTAL_REVENUE DESC
     ```

 5. Calculate monthly sales totals for the current year
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

 7. Calculate the percentage of total sales contributed by each region.
    ```
     SELECT REGION, SUM(SALES) AS REGIONAL_SALES_TOTAL,
     (SUM(SALES) * 100) / (SELECT SUM(SALES) FROM SALESDATA_CAPESTONE) AS SALES_PERCENTAGE
     FROM [dbo].[SALESDATA_CAPESTONE]
     GROUP BY REGION
    ```

 8. Identify products with no sales in the last quarter.
    ```
     SELECT DISTINCT PRODUCT
     FROM [dbo].[SALESDATA]
     WHERE PRODUCT NOT IN(
     SELECT PRODUCT
     FROM [dbo].[SALESDATA]
     WHERE ORDERDATE >= DATEADD(QUARTER, -1, GETDATE())
     )
     ```



#### Analysis using Microsoft Powerbi:
I loaded the data into powerbi for further analysis and visaulization. After loading the dataset, i took it to transform in power query where i will clean the data to ensure data intergrity.

 ![Column Quality](https://github.com/user-attachments/assets/11f53443-cc02-4a25-80a8-f54daa817b1c)

After i have ascertained the quality of the data, i began my analyss in microsoft powerbi.  I started by creating a custom column for Total Sales since Total Sales is not originally in my data.

 ![Creating a custom column](https://github.com/user-attachments/assets/7c51cc99-8bcd-4d6f-83e4-b835e79e55b1)

I also created some measures using DAX functions.
 ![DAX Formulars](https://github.com/user-attachments/assets/bfb88dcf-e391-4568-a74e-e080fd71355c)

 ![Measures Created](https://github.com/user-attachments/assets/fa6e9f4e-48fb-4daf-a3d3-c4b74f292226)

### Data Visualization.
---

#### 1.  Sales Performance by Region:

   ![Sales Performance by Region](https://github.com/user-attachments/assets/e72d8304-a668-4b4e-94ab-b766d4f0060e)

   ##### Key Insight:
   This visual aims at evaluating the sales performance of regions. From the visual, we can see that the south region leads and is the key driver of the sales revenue generating $927,820.The east region follows 
   closely contributing $485,925, the north region accounts for $387,000 while west region has the lowest revenue at $300,345.
   The south region's strong performance suggests a well established market presence or effective sales strategies.
   There is opprotunity for growth in the east region.
   The north and West regions requires attention to improve sales performance.

   ##### Recommendation:
   -  The success factor of the South region should be analysed and replicated in other region.
   -  Invest in targetted marketing campaign
   -  Review sales strategies

#### 2.  Sales performance by product: 

   ![Sales performance by product](https://github.com/user-attachments/assets/7969ce4d-9c12-4a0e-a264-7c8820219d46)

   ##### Key Insight:
   Shoes genrated the highest revenue of $613,380(28% of total sales), Shoes follows closely generating $485600(22% of total sales, Hats and Gloves have similar sales accounting for $316,195(14%) and 
   $296,900(13%). Jacket and socks have lower sales at #208,230(9%) and $180,785(8%) respectively.
   Shoes and Shirt drives the majority of sales, Hats and gloves have potential to grow while Jacket and socks are under performing and need to be reviewed.

   ##### Recommendation:
   - Continue investing in shoes and shirts marketing campaign
   - Improve on the marketing stategies of Hat and Gloves
   - Review Jackets and socks cosidering adding promotion or price adjustments.
   - Expand the products line by introducing new styles, designs and collections.

#### 3.  Top 3 Selling Product.

   ![3 top performing product](https://github.com/user-attachments/assets/e7c4b6d1-7086-488b-8e7f-318f01ecffc3)

   ##### Key Insight:
   Shoes and Shirt account generates total sales of $613,380 and $485,600 as the first and second selling product respectively while Hats amounts to $316,195 as the third selling product.

   ##### Recommendation:
   - Continue investing in marketing campaigns for these 3 products.
   - Analyse their success factors so that it can be replicated for other products. 
   - Bundle top selling products and low selling products for promotional offers.

#### 4.   2023 and 2024 Sales Trend:

   ![monthly sales trend](https://github.com/user-attachments/assets/c13050f2-4a6e-491f-a25b-4f82d6f14d36)

 ##### Key Insights:
  Exploring of sales trend of the current year and previous year provides insight of sales growth or decline.
  In 2023, February has the highest sales of $247500 and followed by July with the sales of July with the sales of $237600.
  In 2024, February has the highest sales of $298800 and then followed by August with the sales of $174300.

   ##### Recommendations:
  February is the peak selling period for the year 2023 and 2024. Such period should be maximized to yield high sales by engaging in strong markrting campaigns.

#### 5.   Product sold by Region:

   ![Product sold by Region](https://github.com/user-attachments/assets/33596849-9bac-4a59-a181-4fbaf33b5070)

   ##### Key Insights:
   South has 2,480 units sold, North has 2481 units sold, East has 2483 units sold while West has 2,477 units sold.
   This shows that sales are remarkably balanced across regions.

   ##### Recommendation:
   - Maintain consistent marketing efforts across regions.
   - More product lines shoul be introduced.

  ### View of my Dashboards.
  ---

 ![Dashboard 11](https://github.com/user-attachments/assets/4a613608-38ef-4599-8998-5b48645eaea6)

 ![Dashboard 22](https://github.com/user-attachments/assets/4301d4b5-9805-4795-83b1-105aa68c4b35)

 ![Dasboard 33](https://github.com/user-attachments/assets/52b3e0d0-8096-402f-8ff9-057c09c9c1f6)

 ### Conclusion:
 ---
 The sales data analysis reveals clear pattern related to time, product,region.
 ##### Key Takeaways:
 - The peak sales month is the month of Feruary. It is advised to capitalize on the peak month by strategizing marketing campaigns and product promotion. During off-peak sles period,targetted promotional 
   campaign that offers enticing discouns or bundled deals can help to promote sales.
 - Total revenue of $2,001,090 was generated and 68,961 units sold
 - Shoes, Hats, Shirts drives the majority of sales revenue.
 - Hats, shoes and Gloves have the highest sales volume
 - Hats and Shoes has the most customers.
 ##### Recommendations:
 - Enhance online presence through social media and e commerce optimization
 - Develop targeted marketing campaigns.
 - Offer loyalty discounts to retain customers.
 - Expand product lines,introduce more designs and collections.
 - Conduct surveys and review feedback to understand customers preference.
 - Regional marketing campaigns should be introduced.

This structured report presents a comprehensive analysis of the sales dataset, offering valuable insights to optimize sales strategies and derive business growth.







   



   
   
