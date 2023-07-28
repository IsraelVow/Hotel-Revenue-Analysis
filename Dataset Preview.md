# Hotel Revenue Analysis Dataset

## Overview
The dataset used for the Hotel Revenue Analysis project was extracted from the Hotel management system and stored in an Excel (.xlsx) file. The data was then utilized for analysis using SQL and Power BI to answer various business questions and create visualizations.

## Dataset Preview
Below is a preview of the dataset:

```
hotel        is_canceled  lead_time  arrival_date_year  arrival_date_month  ... reservation_status  reservation_status_date
Resort Hotel  1            85         2018               July               ... Canceled           06/05/2018
Resort Hotel  1            75         2018               July               ... Canceled           22/04/2018
Resort Hotel  1            23         2018               July               ... Canceled           23/06/2018
Resort Hotel  1            60         2018               July               ... Canceled           11/05/2018
Resort Hotel  1            96         2018               July               ... Canceled           29/05/2018
Resort Hotel  1            45         2018               July               ... Canceled           19/05/2018
Resort Hotel  1            40         2018               July               ... Canceled           19/06/2018
Resort Hotel  1            43         2018               July               ... Canceled           23/05/2018
Resort Hotel  1            45         2018               July               ... Canceled           18/05/2018
Resort Hotel  1            47         2018               July               ... Canceled           02/06/2018
... (more data rows)
```

## Data Summary
The Excel workbook contains the following sheets:

1. **Transaction for 2018:** 32 columns, 21,997 rows
2. **Transaction for 2019:** 32 columns, 79,265 rows
3. **Transaction for 2020:** 32 columns, 40,688 rows
4. **Meal_Cost:** 2 columns, 6 rows
5. **Market_Segment:** 2 columns, 9 rows

## Data Dictionary
The dataset includes the following columns with their respective data types:

1. `hotel`: Text
2. `is_canceled`: Integer
3. `lead_time`: Integer
4. `arrival_date_year`: Date
5. `arrival_date_month`: Date
6. `arrival_date_week_number`: Date
7. `arrival_date_day_of_month`: Date
8. `stays_in_weekend_nights`: Integer
9. `stays_in_week_nights`: Integer
10. `adults`: Integer
11. `children`: Integer
12. `babies`: Integer
13. `meal`: Text
14. `country`: Text
15. `market_segment`: Text
16. `distribution_channel`: Text
17. `is_repeated_guest`: Integer
18. `previous_cancellations`: Integer
19. `previous_bookings_not_canceled`: Integer
20. `reserved_room_type`: Text
21. `assigned_room_type`: Text
22. `booking_changes`: Integer
23. `deposit_type`: Text
24. `agent`: Integer
25. `company`: Text
26. `days_in_waiting_list`: Integer
27. `customer_type`: Text
28. `adr`: Integer
29. `required_car_parking_spaces`: Integer
30. `total_of_special_requests`: Integer
31. `reservation_status`: Text
32. `reservation_status_date`: Date

## Accessing the Dataset
You can access the complete dataset in the [hotel_revenue_historical_full.xlsx](https://github.com/IsraelVow/Hotel-Revenue-Analysis/raw/main/hotel_revenue_historical_full.xlsx) file.

Note: The dataset has undergone basic processing, such as replacing null values with random average values, removing duplicated values, and converting necessary data types.
