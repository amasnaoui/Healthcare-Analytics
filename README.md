# Healthcare-Analytics-Dashboard
![Screenshot of Summary Page from my Dashboard](https://github.com/amasnaoui/Healthcare-Analytics/blob/master/Reports/Summary%20Page.png)
![Screenshot of Deitail Page from my Dashboard](https://github.com/amasnaoui/Healthcare-Analytics/blob/master/Reports/Detail%20Page.png)
## Overview

This project demonstrates the end-to-end development of an interactive Power BI dashboard using publicly available healthcare data on patient waiting lists. It covers the entire process from requirement gathering and data collection to visualization, interactivity, and deployment considerations.

## Data Collection:
- Choose data sources from Power BI's wide range of connectors (Excel, CSV, databases, cloud platforms, ERP systems, SharePoint, web, etc.).
- For this example, we'll use a central folder containing the required data files.
## Data Transformation:
- Transform data structure and clean/process it using Power Query Editor. Common transformations include renaming, rearranging columns, appending tables, replacing/trimming values, pivoting/unpivoting, merging, and filtering.
- We rename columns, rearranging columns, appending inpatient and outpatient data tables, and cleaning redundant data in Age_Profile and Time_Band columns.
## Data Modeling:
- Establish relationships between tables to fetch relevant information for reporting.
- We create a relationship between the "All_Data" table and a separate "Mapping" table based on the "Specialty_Name" column.
## Dashboard Layout & Design:
- Enable gridlines and snap-to-grid for easier visual alignment.
- Create DAX measures using calculations. In this example, we'll create measures for "Latest Month Wait List" and "PY Latest Month Wait List".
- Use buttons for users to toggle between calculation methods (average or median).
- Create additional measures for dynamic chart titles and handling potential lack of data scenarios.
- Design the summary page with visuals like doughnuts, clustered column charts, and top five multi-row cards.
- Create a line chart with visual filters for "Case_Type" and slicers for various dimensions.
- Design a detailed view with a matrix and a tooltip page with a chart and card.
- Apply visual aesthetics using a reference dashboard for inspiration and tools like PowerPoint, Canva, and Color.Adobe.com.
### DAX measures Used :
We will create 2 measures which will be used in our visuals for calculating Latest Month & Previous Year Wait List
```
Latest Month Wait List = CALCULATE(SUM(All_Data[Total]),All_Data[Archive_Date] = MAX(All_Data[Archive_Date])) + 0

PY Latest Month Wait List = CALCULATE(SUM(All_Data[Total]),All_Data[Archive_Date]= EDATE(MAX(All_Data[Archive_Date]),-12)) + 0
```
Now create below measures which will help us get the calculation we need and also to make few chart titles dynamic
```
Median Wait List = MEDIAN(All_Data[Total]) 

Average Wait List = AVERAGE(All_Data[Total]) 

Avg/Med Wait List = SWITCH(VALUES('Calculation Method'[Calc Method]),"Average",[Average Wait List],"Median",[Median Wait List]) 

Dynamic Title = SWITCH(VALUES('Calculation Method'[Calc Method]),"Average","Key Indicators - Patient Wait List (Average)","Median","Key Indicators - Patient Wait List (Median)") 

NoDataLeft = IF(ISBLANK(CALCULATE(SUM(All_Data[Total]),All_Data[Case_Type]<>"Outpatient")),"No data for selected criteria","")  

NoDataRight = IF(ISBLANK(CALCULATE(SUM(All_Data[Total]),All_Data[Case_Type]="Outpatient")),"No data for selected criteria","")  
```
## Adding Interactivity:
- Enhance the dashboard with interactive elements like navigation buttons, chart alternative display text, and hover information.
## Sharing:
- Conduct User Acceptance Testing (UAT) to identify bugs and data issues.
## Routine Refresh & Maintenance:
- Implement a routine process for monthly data refresh and maintenance.
## Contact me!
If you have any questions, suggestions, or just want to say hello, you can reach out to me at [LinkedIn](https://www.linkedin.com/in/abdelghani-masnaoui/). I would love to hear from you!
