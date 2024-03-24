# Top Selling Product

### Report Link : https://drive.google.com/drive/folders/1QBT9-15-BNzs6ZGAfxGelLzUzzVLi80A?usp=sharing

## Problem Statement

This dashboard helps the company to understand their product sales better. It helps the company know how their products have been performing. Are there specific ones that stand out and consistently dominate the sales charts? Understanding this could guide them in inventory decisions, marketing pushes, and even future product development.


### Steps followed 

- Step 1 : Load data into Power BI Desktop, dataset is a csv file.
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- Step 4 : It was observed that in none of the columns errors & empty values were present.
- Step 5 : In the report view, text box was added where title "Top Selling Product" was mentioned.
- Step 6 : Since the data contains various product, thus in order to represent sales by products, a column chart was added from the visualizations pane in report view. 
- Step 7 : Visual filters (Slicers) were added for three fields named "Region", "Marketing Campaign" & "Sales Team".
- Step 8 : One card visual was added to the canvas, representing total sales.
- Step 10 : A line chart was also added to the report design area representing the sales of product per month.
- Step 11 : Matrix Visual was used to represent sales of product during different marketing campaigns.

- Step 12 : Calculated table was created in which there was date, month, year, quarter, etc.

for creating new column following DAX expression was written;
       
        Date = 
         VAR MinYear = YEAR(MIN(ExampleData_TopSellingProducts[Sale Date]))
         VAR MaxYear = YEAR(MAX(ExampleData_TopSellingProducts[Sale Date]))
         RETURN
         ADDCOLUMNS(
           FILTER(
               CALENDARAUTO( ),
           AND ( YEAR ( [Date] ) >= MinYear, YEAR ( [Date] ) <= MaxYear)
            ),
         "Year", YEAR( [Date] ),
         "Month Name", FORMAT([Date], "mmmm" ),
         "Month Name Short", FORMAT([Date], "mmm" ),
         "Month Number", MONTH([Date]),
         "Quarter Name", "Q" & FORMAT([Date], "Q YYYY"),
          "Quarter Number", FORMAT([Date], "YYYYQ")
        )   

        
Snap of new calculated table ,

![CalculatedTable_Date](https://github.com/vinodsrawat/Top-Selling-Products-Report/assets/161686865/829567d7-94ba-4fec-8603-45fd0720b369)

        
- Step 13 : New measure was created to find total sales of products.

Following DAX expression was written for the same,
        
       Total Sales = SUM(ExampleData_TopSellingProducts[Sales Amount])
        
A card visual was used to represent total sales.

![Card_TotalSales](https://github.com/vinodsrawat/Top-Selling-Products-Report/assets/161686865/a26e3b5a-faa9-472b-97de-059321798fba)

 # Report Snapshot (Power BI DESKTOP)

![Report](https://github.com/vinodsrawat/Top-Selling-Products-Report/assets/161686865/6c5a2e55-35ff-4d1c-9023-4c3e08485523)

# Insights

A single page report was created on Power BI Desktop.

Following inferences can be drawn from the dashboard;

### [1] Total Sales = 25.38M

   Sales of Laptop = 5.24M
   
   Sales of Smartwatch = 5.10M

   Sales of Desktop PC = 5.09M
    
   Sales of Tablet = 5.08M
    
   Sales of Smartphone = 4.86M

         Laptop is the most selling product
           
### [2] Sales by Month

         Maximum Sales were in October = 2.31M

         Minimum Sales were in February = 1.82M

  
### [3] Sales by Marketing Campaign 
  
Summer Sale 2022 = 5.33M

Spring Clearance 2023 = 5.23M

Back to School 2022 = 4.97M

Holiday Deals 2022 = 4.99M

Black Friday 2023 = 4.86M

         "Summer Sale 2022" is the most successful campaign
   

 ### [4] Sales by Region

North = 6.10M
East = 6.42M
South = 6.46M
West = 6.40M
        
         South has the maximum sales
 
 ### [4] Best Performing Team

Alpha = 6.38M

Beta = 6.21M

Gamma = 6.63M

Delta = 6.16M

         Gamma is the best performing team
