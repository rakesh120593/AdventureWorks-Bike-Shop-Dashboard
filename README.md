# AdventureWorks Bike Shop-Dashboard

### Dashboard Video Link : https://www.loom.com/share/21df513eb9dd42a58ff7de8d52ef378c?sid=16e07094-1006-46bf-bb2e-98700bb76968

## Project Summary

The AdventureWork Bike Shop Dashboard is a comprehensive Power BI solution designed to provide executives with granular insights into business performance. Built using DAX queries, data modeling techniques, and the AdventureWorks raw dataset, the dashboard delivers a detailed analysis of key metrics such as:

- Total Revenue Orders, Profit, and Returns
- Return Rates to track product performance
- Trends by Country, Product Category, and Subcategory
- Year-over-year comparisons for better strategic planning

This dashboard simplifies complex data, enabling stakeholders to make data-driven decisions and identify opportunities for growth across product lines and regions.


### Steps followed 

- Step 1 : Load data into Power BI Desktop, dataset is a csv file.
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- Step 4 : It was observed that in none of the columns errors & empty values were present.
- Step 5 : Added new columns using Power Query for Start of month,  Start of week, weekends, year, income level etc.
- Step 6 : Modify global settings and disabled automatic relationship detection after loading data, deactivate time intellegence and in regional settings selected English US.
- Step 7 : Created Four Different reports for Executive, Map, Customers and Product for detailed view and insights.
- Step 8 : Used Card, line chart, matrix, Map, slicers, guage, horizontal bar charts, area charts and filters for data visualizations.
- Step 9 : Four card visuals were added to the Executive canvas, representing Total Revenue, Orders, Profit and Return rate.
- Step 10 : A line chart added to showcase revenue per month, utilized horizontal bar chart to represent total orders per category.

    Matrix view to showcase Top 10 Products with comparision of    Total orders, revenue and return rate.

    Used Single card to represent Most ordered product type and  Most returned product type
- Step 11 : For Product report used drill through option to review specifi product performance and utilized three guage charts to represent monthly orders, monthly revenue, monthly profit in comparision with Monthly Target for each matrics. 
    
    Created line chart to showcase total profit, also added slicer to represent profit trends as per the price adjustment. 

    Used Area chart to represent specific product performance with granularity of day, month, quarter and years as per the matrics Order, Revenue,Profit,Returns,Return % (Slicer used for matrics)
- Step 12 : In Customer report page, used line chart to represent Toatl Customers and Revenue Per Customer trends over the time.
    Also added, donut chart to represent Order by Occupation and Orders by Income Level.
    Used Matrix view to represent data of Top 100 Customers by Orders also represent their revenue.
    Slicer Added to filter data by Years, to represent Top Customers, their orders, and thier revenue. 
    
- Step 13 : Map used to represent total orders by Country.
- Step 14 : Multiple Measures were created in order to get deeper insights from data for examples. Total Returns, Total revenue, Total orders, Total profits, YTD revenue, Weekends orders, Total orders, revenue target gap, Revenue target, return rate, quantity sold, quantity returned, profit target, profit target gap, previous month revenue, previous month return, previous month profit, previous month orders, overall average, order target, order target gap, hight ticket orders, bulk order, Adjusted profit, Adjusted price, Adjusted revenue, 90 days rolling profit, 10 Days rolling revenue, % of all orders, % of all returns, etc.  

for creating new column for Weekend following DAX expression was written;
       
        Weekend = 
        
        Weekend = IF(
        'Calendar Lookup'[Day of week] IN {6,7},
        "Weekend",
        "Weekday"
        )  
        
Snap of new calculated column ,

![Image](https://github.com/user-attachments/assets/4a288e12-7c3b-4c10-bb03-497d84d7548a)

        
- Step 15 : New measure was created to find 90-Days Rolling Profit.

Following DAX expression was written for the same,
        
        Weekend = CALCULATE(
            [Total Profit],
            DATESINPERIOD(
            'Calendar Lookup'[Date],
            MAX('Calendar Lookup'[Date]),
            -90,
            DAY)
        )
        

        
 - Step 16 : New measure was created to find  Adjusted Price,
 
 Following DAX expression was written to find % of customers,
 
         Adjusted Price = [Average Retail Price] * (1 + 'Price  Adjustment (%)'[Parameter Value])
 
 


 
 - Step 17 : New measure was created to calculate Previous Month Revenue.
 
 Following DAX expression was written to find the same,
 
         Previous Month Revenue = 
        CALCULATE(
            [Total Revenue],
            DATEADD('Calendar Lookup'[Date],
            -1,
            MONTH
            )
        )
    
 Step 18 : New Calculated column was created for Month Number.
    Following DAX expression was written to find the same,


    Month Number (DAX) = 
        SWITCH(
        'Calendar Lookup'[Month Name],
        "January","1",
        "February", "2",
        "March","3",
        "April", "4",
        "May", "5",
        "June", "6",
        "July", "7",
        "August", "8",
        "September", "9",
        "October", "10",
        "November", "11",
        "December", "12",
        "Other"
    )

  ![Image](https://github.com/user-attachments/assets/ffb6789c-e4b3-4b72-a0eb-c71c20759ea3)  
 
 - Step 19 : The report was then published to Power BI Service.
 

# Snapshot of Executive Dashboard 

![Image](https://github.com/user-attachments/assets/284d18d6-dcf1-4a33-b5ec-79fd83e41fa8)

 
 # Snapshot Map Report

 
![Image](https://github.com/user-attachments/assets/f7ee854c-a094-49bc-ad04-17d753c6a21c)

 # Snapshot Product Report

 ![Image](https://github.com/user-attachments/assets/5c6dd819-8df5-4e7b-8bb8-4ac1ac11ccca)

 # Snapshot Customer Report

 ![Image](https://github.com/user-attachments/assets/60071626-b83e-44fd-b54f-84f98bf3d502)

# Insights

Four pages report was created on Power BI Desktop & it was then published to Power BI Service.

Following inferences can be drawn from the dashboard;

### [1] Executive Dashbord Key Insights:

   Total Revenue Was: $24.9M

   Total Profit Was: $10.5M

   Total Orders Were: 25.2K

   Total Return Rate Was: 2.2%

   Top Category was Accessories with 17.0k Orders.

   Maximum Revenue was $16,35,309  generated on 12/01/2021  
           
### [2] Top 3 Countries with Total Numbers of Order :

    1) UNITED STATES - 8700 
    2) AUSTRALIA - 6060
    3) CANADA - 3024
    
  
  ### [3] Top 5 Product:
  
      a) Water bottles - 30 oz - 3983 orders, $39,755 Revenue with return rate of 1.95% 
      b) Patch Kit 8 patches - 2952 orders, $13,506 Revenue with return rate of 1.61%
      c) Mountain Tire Tube - 2846 orders, $28,333 Revenue with return rate of 1.64%
      d) Road Tire Tube - 2173 orders, $17,265 Revenue with return rate of 1.55%
      e) Sport 100 Helmet Red - 2099 orders, $73,444 Revenue with return rate of 3.33%

Most Ordered Product Type: Tires and Tube

Most Returend Product Type: Shorts
        
 ### [4] Customer insights
 
    1. Revenue Per Customer: $1,431
    2. Unique Customers: 17.4K
    3. Top Customer: Maurice Shan with 6 orders and $12.4K Revenue.


 
 
 ## Thank you for reviewing the report!!!
