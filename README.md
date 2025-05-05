# Uber-analysis-project

                                              UBER TRIP ANALYSIS

DAHBOARD 1: OVERVIEW ANALYSIS
In this Project we have analysed the Using Power BI Insights that is showing the trends, revenue, trip, efficiency
Helping stake holder make data-driven decision

So In this project we have created first of all the KPIs Showing the respective 
1.	Total Bookings – How many trips were booked over a given period?
2.	Total Booking Value –  What is the total revenue generated from all bookings?
3.	Average Booking Value – What is the average revenue per booking?
4.	Total Trip Distance – What is the total distance covered by all trips?
5.	Average Trip Distance – How far are customers traveling on average per trip?
6.	Average Trip Time – What is the average duration of trips?
To show this insights we have used the NEW CARD To showcase all the requirements in a easy manner  It Goes like

![Screenshot 2025-04-24 091230](https://github.com/user-attachments/assets/ba5645a2-2c0c-4e1e-8349-c57a52379084)

These all are calculated using a simple DAX formula
Created a dynamic measure selector to update the visualization on user selected they are
Total booking ,Total booking value , Total trip distance which changes the visualization in its accordance 

![Screenshot 2025-04-24 091717](https://github.com/user-attachments/assets/c055a2e9-671f-4d0d-b898-c02849bd6f36)

Then,  we used the  measure to dynamically update the visualizations based on user selection.

By Payment Type (Card, Cash, Wallet, etc.)

By Trip Type (Day/Night) for these we have used pie charts visualization 

Additional Enhancements:

	Dynamic Title– Updated the chart title based on the selected measure.

	Slicers – Added filters for Date, City, and other interactive filters for deeper analysis.

	Tooltips – Showed additional details like Average Booking Value or Trip Distance.

![Screenshot 2025-04-24 092135](https://github.com/user-attachments/assets/2f3c564f-6888-469a-a0db-6cefde7eacfd)

![Screenshot 2025-04-24 092527](https://github.com/user-attachments/assets/151f8ebb-ea22-4d84-9905-48ce30fa2584)

Total Bookings by Day

Detecting trends and fluctuations in daily trip volumes.

Identifying peak and off-peak booking days.

Understanding the impact of external factors (holidays, events, weather) on ride demand.

Supporting strategic planning for resource allocation and pricing adjustments

![Screenshot 2025-04-24 092937](https://github.com/user-attachments/assets/2db1b70b-eb45-4026-9fe9-bd9946817eb9)

Vehicle Type Analysis - Grid View in Power BI
Created a grid table (matrix or table visual) to analyse key performance indicators like Total Bookings, Total Booking Value, Avg Booking Value, Total Trip Distance across different Vehicle Types in Uber trips.

Additional Enhancements:

•	Used a Table or Matrix Visual to display Vehicle Type with the KPIs.

•	Applied Conditional Formatting to highlight high and low values.

•	Enabled Sorting & Filtering for user interaction.

![Screenshot 2025-04-25 010807](https://github.com/user-attachments/assets/7798a22e-daca-4ae4-9fc5-6c3fbaf3c17d)

                                                 Location Analysis

IN this analysis we are gonna understand trip location locations is crucial for optimizing ride distribution, demand forecasting, and operational efficiency. This analysis focuses on:

	Most Frequent Pickup Point

•	Identify the most common starting locations for trips.

•	Helps in optimizing driver availability and dynamic pricing strategies.

![Screenshot 2025-04-25 005205](https://github.com/user-attachments/assets/b51b0d7f-35fa-4f90-ac5e-84684583cb55)

For this Output we have Usewd the DAX formula 

            Most Frequent Pickup Point = 
  
         var pickpoint = 
                           TOPN(1,SUMMARIZE('Trip Details','Location Table'[Location],"pickpoint",COUNT('Trip Details'[Trip ID])),[pickpoint],DESC)
                     RETURN CONCATENATEX(pickpoint,'Location Table'[Location], " , ")

	Most Frequent Drop-off Point

•	Find the most common drop-off locations.

•	Requires activating an inactive relationship in Power BI between Pickup Location and Drop-off 

![Screenshot 2025-04-25 005633](https://github.com/user-attachments/assets/332e24d8-b400-4a73-9075-7b5c78715e3f)

              Most Frequent Drop of = 

                var dropoffcounts= 
                ADDCOLUMNS(
                    SUMMARIZE(
                        'Trip Details',
                        'Location Table'[Location]
                    ),
                    "dropoffcounts",
                    CALCULATE(
                        COUNT('Trip Details'[Trip ID]),
                        USERELATIONSHIP('Trip Details'[DOLocationID],'Location Table'[LocationID])
                    )
                    )

    var rankeddropoff=
    ADDCOLUMNS(
        dropoffcounts,
        "rank",
        RANKX(dropoffcounts,[dropoffcounts],,DESC,Dense)
    )

    var topdropoff =
        FILTER(rankeddropoff, [rank]=1) 

        RETURN
        CONCATENATEX(topdropoff,'Location Table'[Location], " , ")

# To be honest this is a advance Dax calculation but tried to undersatnd this practiced many time to get the output  

Total Bookings by Location (Top 5)

•	Identify the top 5 locations with the highest trip bookings.

•	Helps in demand forecasting and optimizing driver availability in high-traffic areas.

![Screenshot 2025-04-25 005900](https://github.com/user-attachments/assets/2d57347a-615e-4319-b2b5-6455749b931d)

For this all we have used the  TOPn Function for the top five locations 

Most Preferred Vehicle for Location Pickup

•	Determine the most frequently booked vehicle type at each pickup location.

•	Supports strategic vehicle distribution based on customer preferences and location demand.

![Screenshot 2025-04-25 005918](https://github.com/user-attachments/assets/73fc50d7-7ebd-4c0b-8a72-4baae12d7315)

For this all we have used the  TOPn Function for the top five Cars

	Bookmark for Data Details

•	Added a "Data Details" bookmark to display a pop-up or side panel explaining:

o	Meaning of key metrics (Total Bookings, Total Trip Distance, etc.).

o	Description of tables used in the analysis.

o	Data source and refresh frequency.

	Clear Slicer Button

•	Added a "Clear Filters" button using a blank button with a Reset Slicers action to reset all selections in one click.

•	Improves user experience for quick dashboard resets.

	
                                        Dashboard 2 Time analysis

To understand trip patterns based on time, Uber needs to analyse ride demand and trends across different time intervals. This dashboard will help in optimizing operations, pricing, and driver availability.

A measure selector will be created for:

✔Total Bookings
✔Total Booking Value
✔Total Trip Distance

Visualizations:

By Pickup Time (10-Minute Intervals) - Area Chart

•	Groups trip bookings into 10-minute intervals throughout the day.

•	Helps in identifying peak and off-peak demand periods.

![Screenshot 2025-04-25 011229](https://github.com/user-attachments/assets/c42146bf-b2ee-4d33-932f-13300ce33de0)

By Day Name - Line Chart

•	Shows booking trends across Monday to Sunday.

•	Useful for analysing weekday vs. weekend demand.

![Screenshot 2025-04-25 011353](https://github.com/user-attachments/assets/90b8ad57-0fd9-4bc9-b3fa-9aacc5a72def)

By Hour and Time - Heatmap (Matrix Grid)

•	Rows: Hours of the Day (0–23)

•	Columns: Days of the Week (Mon-Sun)

•	Values: Selected Dynamic Measure (e.g., Total Bookings)

•	Highlights peak booking hours across different days.

![Screenshot 2025-04-25 011509](https://github.com/user-attachments/assets/fe92cbc1-5c97-45f7-8edc-4b1be234371a)

                                  DAHBOARD 3: DETAILS TAB

Created a detail tab for the data to look for reference 

In this we have connected the charts with the grid tab by drill through to understand the data easily
And also created bookmarks 

![Screenshot 2025-04-22 102634](https://github.com/user-attachments/assets/bdf5b2e9-7786-4268-bfe4-3635f17db872)

                                        The final dashboard 

                                      	Overview dashboard

![Screenshot 2025-04-22 102437](https://github.com/user-attachments/assets/56e79402-388d-478a-9f11-b856266e6424)

                                      Time analysis dashboard

![Screenshot 2025-04-22 102538](https://github.com/user-attachments/assets/0fcf2339-1314-4bc0-8983-d18d774dc60e)























     
























