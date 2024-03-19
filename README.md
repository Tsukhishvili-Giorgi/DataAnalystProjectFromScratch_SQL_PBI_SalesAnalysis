# Sales Analysis-Dashboard


## Problem Statement

Internet sales reports improvement, from static reports to visual dashbords. This dashboard helps the sales manager understand their customers better. It helps manager to know which product sold more to which client and how it has been over. Seeing as each salesperson works on different products and customers, dashboard should to be able to filter them also. Based on the budget, value should be compared on performance. The previous two years (2022/2023) should be analyzed.



### Steps followed 

- Step 1 : Load data into SQL, dataset is a SQL file.
- Step 2 : Cleaned data and saved it with csv file.
- Step 3 : Loaded data into Power BI Desktop, dataset is a csv file.
- Step 4 : Opened power query editor & created dimension and fact tables folder, also connected tables for data model.
- Step 5 : Imported Fact_Budget.
- Step 6 : Measures were created to calculate total Sales, Budget Amount, Sales minus Budget and Sales divided by Budget:    

        Sales = SUM (FACT_InternetSale[SalesAmount]);
        Budget Amount = SUM (FACT_Budget[Budget]);
        Sales - Budget = [Sales]-[Budget Amount];
        Sales / Budget Amount = DIVIDE( [Sales], [Budget Amount]);
- Step 7 : Created a Dashboard design for the first page "Sales Overview".
- Step 8 : Visual filters (Slicers) were added for four fields named: 

Customer City,

Sub Category, 

Category,

Product Name

also created two filter (slicers) for year and month.
- Step 9 : For creating dynamic card, created KPI measures:


        KPI Sales = FORMAT([Sales,"$#,0") & "" 

        KPI Sales vs Budget =
        VAR_var = [Sales - Budget]
        VAR _pct = DIVIDE([Sales], [Budget Amount] ) -1
        VAR _sign = IF( _var > 0, "+", "")
        RETURN
        _sign & FORMAT( _pct, "#0.0%") & " | " & _sign & FORMAT( _var, "#0,#")

        KPI Color = VAR _sel =SELECTEDVALUE(Comparisons[Comparisons Fields])
        VAR _var = SWITCH(
                TRUE()
                ,CONTAINSSTRING( _sel, "Budget"), [Sales - Budget]
                 ) 
         RETURN
         SWITCH(
                 TRUE()
                 , _var > 0, "Green"
                 , _var < 0, "Red", "Black"
                 )
- Step 10 : Created new field parameter "Comparisons" for KPI color measure.

![KPI Dynamic Card](https://github.com/Tsukhishvili-Giorgi/DataAnalystProjectFromScratch_SQL_PBI_SalesAnalysis/assets/117026869/be6e7c0b-6298-4fef-982d-4e8bfac4e078)

- Step 11 : Create Key meausre table for all measurement;
- Step 12 : A donut chart is used to show sales by product type. While creating this visual, a Column named "Product category" was also added to the Legends field, and Sales measure was added to the Value field.

![Sales_By_ProductCategory](https://github.com/Tsukhishvili-Giorgi/DataAnalystProjectFromScratch_SQL_PBI_SalesAnalysis/assets/117026869/807a70f3-8319-417f-a4ba-01a9c2c471ed)

- Step 13 : A line chart used to show the monthly dynamics of sales and budget.

![Sales Budget_By_Month](https://github.com/Tsukhishvili-Giorgi/DataAnalystProjectFromScratch_SQL_PBI_SalesAnalysis/assets/117026869/47b461f0-3af4-45c9-b1ca-71aa724982de)

- Step 14 : A Clustered bar chart used to show Sales by Top 10 customers and Sales by Pproduct.

![Sales_By_Top10_Customers ProductName](https://github.com/Tsukhishvili-Giorgi/DataAnalystProjectFromScratch_SQL_PBI_SalesAnalysis/assets/117026869/c8edf3cb-2ce2-478e-a27b-9c40dfbe9a0d)

- Step 15 : A Map used to show Sales by customer city.

![Sales_By_CustomerCity](https://github.com/Tsukhishvili-Giorgi/DataAnalystProjectFromScratch_SQL_PBI_SalesAnalysis/assets/117026869/97d2c064-91fa-4f47-b33b-e1b86dbae36c)

- Step 16 : Created a Dashboard design for the second page "Customer Details". Visual Filter (Slicers) are the same as on the first page.
- Step 17 : There were added two cards which show Budget and Sales.

![Sales Budget _Cards](https://github.com/Tsukhishvili-Giorgi/DataAnalystProjectFromScratch_SQL_PBI_SalesAnalysis/assets/117026869/996d0f88-2329-44fa-a582-ce9b11adcb40)

- Step 18 : Created matrix whcih show customer person sales by month.

![Sales_Matrix](https://github.com/Tsukhishvili-Giorgi/DataAnalystProjectFromScratch_SQL_PBI_SalesAnalysis/assets/117026869/ace311cd-ce40-4cf3-8629-803703711653)

- Step 19 : After this created Dashboard design for third page "Product Details".
- Step 20 : On the Prduct Details page created matrix whcih show productname sales by month.

![Sales_Matrix_By_Product](https://github.com/Tsukhishvili-Giorgi/DataAnalystProjectFromScratch_SQL_PBI_SalesAnalysis/assets/117026869/b82ee30a-6b63-4d29-bed8-d6324b1ce858)

 # Report Snapshot (Power BI DESKTOP)

 ## Sales Overview
![Sales_Overview](https://github.com/Tsukhishvili-Giorgi/DataAnalystProjectFromScratch_SQL_PBI_SalesAnalysis/assets/117026869/e513d34f-acf7-437c-8319-426a87d631e3)

## Customer Details
![Customer_Details](https://github.com/Tsukhishvili-Giorgi/DataAnalystProjectFromScratch_SQL_PBI_SalesAnalysis/assets/117026869/c1a5726e-4453-4672-9e86-633019757ab7)

## Product Details
![Product_Details](https://github.com/Tsukhishvili-Giorgi/DataAnalystProjectFromScratch_SQL_PBI_SalesAnalysis/assets/117026869/7f65193c-1635-47d4-bb50-967d9506719e)



# Insights

The following inferences can be drawn from the dashboard;

## [1] Total Sales = 22237203

### Sales by Product Category

 - Bikes = 21197765 (95.33 %)

 - Accessories = 700014 (3.15 %)

 - Clothing = 339424 (1.52 %)

           Thus, the higher number of products are Bikes.
           
## [2] Sales VS Budget

### Report of 2022

Budget = 15 300 000

Sales = 5 842 231

        Thus, in 2022, the company suffered an amount of 9 457 769 (-61.8%) USD.

### Report of 2023    

Budget = 5 800 000

Sales = 16 349 330

        Thus, in 2023, the company made a profit of 10549330 (181.9%) USD.
  
  
  ### [3] Top 3 Products by Sales
        
- Mountain - 200 Black, 46 (1 371 405)

- Mountain - 200 Black, 42 (1 363 128)

- Mountain - 200 Silver, 38 (1 339 394)


