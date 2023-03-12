# Hotel-Revenue-Analysis
 SQL &amp; PowerBI Integration

# Using Hotel Data

# Goal
	
I created an SQL Database with SQL server 
uploading excel datas to this database that i created 
and connect this database to powerbi and answer some business questions
and have a visual project end to end

# Questions asked by stakeholders.
1. Build a visual data story or dashboard using Power BI to present to your stakeholders.
	is our hotel revenue growing by year?
	(There are two hotel types,so i segmented revenue by hotel type.)

	Should i increase our parking lot size?
	(Ascertain if there is a trend in guest with personal cars.)

	What trends can be seen in the data?
	(Focus on average daily rate and guests to explore seasonality.)


# Solutions/pipeline.
- Build a Database
- Develop the SQL Query
- Connect Power BI to the Database
- Visualize
- Summarize findings.


####issue encountered#### 
(During importing all excel files to Sql database, Access database engine needed to be the same version with SQl 
Import and export Wizard, which comes in 32bits, by default Access database engine is installed based on your 
office version, which is 64bits... solution was to download the 32bits version of Access database engine and install 
and run it in command prompt as quiet C:\Users\user\Downloads\Programs\accessdatabaseengine/quiet)



Querying the database by writing SQL queries

select * from dbo.['2018$']
Union
select * from dbo.['2019$']
union
select * from dbo.['2020$']

( * all columns)... from table
"Union" command is to append all tables

Above set select statements is a query that runs everytime you press execute and you want to refer to all the select statement
in one go.
You create a table function... to make all the appended selected tables to be one table

with T_hotels as (
select * from dbo.['2018$']
Union
select * from dbo.['2019$']
union
select * from dbo.['2020$'])

t_hotel is now like a variable...storing all the select statements


To get the total revenue of the hotel
we'll add both stay_in-weekend + stay_in-nights to become one column as the quantity
then multiply the  adr, that is the total cost per day
to get the total revenue

Select (stays_in_week_nights + stays_in_weekend_nights)*adr from T_hotels

to give this column a header (give it an Alias) 

Select (stays_in_week_nights + stays_in_weekend_nights)*adr as revenue from T_hotels

To categorize this revenue column by year (inother to see how it behaves)
so we'll bring arrivaldateyear column
 	
Select arrival_date_year,
 (stays_in_week_nights + stays_in_weekend_nights)*adr as revenue 
from T_hotels


so we'll group the arrivaldateyear column and sum the revenue by year

Select arrival_date_year,
 Sum((stays_in_week_nights + stays_in_weekend_nights)*adr) as revenue 
from T_hotels
Group by arrival_date_year

so the stakeholders required to know if their revenue were growing per year.. and this query gives that

now the stakeholders also wanted to broken down by hotel type

we'll now add one more column
note; since youre adding hotel type column, youll need to add hotel type to the groupby statement as well

Select arrival_date_year, hotel,

 Round(Sum((stays_in_week_nights + stays_in_weekend_nights)*adr),2) as revenue 

from T_hotels

Group by arrival_date_year, hotel

basically, we've given the stakeholders analysis on thier revenue per year based on hotel type 
but we havent made effect to the other tables in our database (market_segment & meal cost)
in the marketsegment table, it gives a discount to the segment charge.. 

so we need to perform a join to our initial table

Select * from T_hotels
left Join dbo.market_segment$
on T_hotels.market_segment = market_segment$.market_segment

left join brings all the information on the table whether theres a match or not

we want to do the same left join to meal cost table

Select * from T_hotels
left Join dbo.market_segment$
on T_hotels.market_segment = market_segment$.market_segment
left join dbo.meal_cost$
on meal_cost$.meal = T_hotels.meal
