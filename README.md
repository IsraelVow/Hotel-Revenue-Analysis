# Hotel Revenue Analysis - Data Analyst Readme

## Overview
This project focuses on analyzing hotel revenue using SQL and Power BI integrations. The goal is to build an end-to-end visual project to answer various business questions posed by stakeholders. The analysis involves creating an SQL database, uploading Excel data to the database, connecting it to Power BI, and building visualizations to present key insights.

## Business Questions
The stakeholders have raised the following questions that need to be addressed through the data analysis:

1. **Is our hotel revenue growing year over year?**
   - To answer this, revenue will be segmented by year, and further segmented by two hotel types.
   
2. **Should I increase the parking lot size?**
   - This question aims to ascertain if there is a trend in guests with personal cars.

3. **What trends can be seen in the data?**
   - The focus will be on the average daily rate and guests' exploration of seasonality.

## Solutions/Pipeline
The data analyst will follow these steps to conduct the analysis and provide meaningful insights:

1. **Build a Database:**
   - Create an SQL database using SQL Server to store the hotel data.

2. **Develop the SQL Query:**
   - Import the Excel data into the SQL database, ensuring compatibility with the Access database engine (32-bit version).

3. **Connect Power BI to the Database:**
   - Establish a connection between the SQL database and Power BI to fetch data.

4. **Visualize:**
   - Build a visual data story or dashboard in Power BI to present the analysis.

5. **Summarize Findings:**
   - Provide clear and concise conclusions based on the insights derived from the visualizations.

Download the raw [Dataset](https://github.com/IsraelVow/Hotel-Revenue-Analysis/raw/main/hotel_revenue_historical_full.xlsx)

## Issue Encountered
During the process of importing all Excel files to the SQL database, a compatibility issue arose with the Access database engine. As the default installation is 64-bit, it did not match the 32-bit version required by the SQL Import and Export Wizard. The solution involved downloading and installing the 32-bit version of the Access database engine. The command prompt was then used to run the installation quietly.

## SQL Queries
The following SQL queries were used to perform the analysis:

1. **Appending Tables and Creating a Table Function:**
   ```sql
   SELECT * FROM dbo.[2018$]
   UNION
   SELECT * FROM dbo.[2019$]
   UNION
   SELECT * FROM dbo.[2020$]
   ```
   The `UNION` command is used to append all the tables together. A table function named `T_hotels` was created to store the result.

2. **Calculating Total Revenue:**
   ```sql
   SELECT (stays_in_week_nights + stays_in_weekend_nights) * adr AS revenue FROM T_hotels
   ```
   This query calculates the revenue by multiplying the sum of nights stayed with the average daily rate (ADR).

3. **Grouping Revenue by Year:**
   ```sql
   SELECT arrival_date_year, SUM((stays_in_week_nights + stays_in_weekend_nights) * adr) AS revenue
   FROM T_hotels
   GROUP BY arrival_date_year
   ```
   The revenue is grouped by year to analyze revenue growth over time.

4. **Segmenting Revenue by Hotel Type:**
   ```sql
   SELECT arrival_date_year, hotel, ROUND(SUM((stays_in_week_nights + stays_in_weekend_nights) * adr), 2) AS revenue
   FROM T_hotels
   GROUP BY arrival_date_year, hotel
   ```
   This query further segments the revenue by hotel type in addition to the year.

5. **Joining Tables for Additional Analysis:**
   ```sql
   SELECT *
   FROM T_hotels
   LEFT JOIN dbo.market_segment$ ON T_hotels.market_segment = market_segment$.market_segment
   LEFT JOIN dbo.meal_cost$ ON meal_cost$.meal = T_hotels.meal
   ```
   The tables `market_segment$` and `meal_cost$` are joined with `T_hotels` to perform additional analysis and understand the impact on revenue.

## Visualizations and Charts in Power BI:

1. **Cards**
2. **Sparkline Line Chart**
3. **Slicers for Filtering**
4. **Line Chart**
5. **Matrix Table**
6. **Donut Chart**

These visualizations and charts have been carefully designed to provide a comprehensive overview of the hotel revenue analysis. The combination of cards, sparklines, line charts, matrix tables, and donut charts allows stakeholders to quickly grasp key insights, and trends, and make data-driven decisions to optimize revenue and improve services. The interactive slicers further enhance the user experience by enabling dynamic filtering of data to focus on specific segments and time periods.

## Conclusion
By following the outlined steps and running the SQL queries mentioned above, the data analyst has successfully generated meaningful insights into the hotel's revenue. These insights are presented in a visually appealing manner using Power BI, allowing stakeholders to make informed decisions based on the analysis.

The analysis showcases trends in hotel revenue growth over the years, the impact of hotel type on revenue, and valuable information on guest behaviors related to personal cars. The analysis also explores the seasonality aspects of average daily rates and guests. These findings will help the stakeholders to make data-driven decisions, optimize revenue streams, and improve guest experiences.
