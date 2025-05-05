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

IN this analysis we are gonna understand trip location locations is crucial for optimizing ride distribution, demand forecasting, and operational efficiency. This analysis focuses on:
	Most Frequent Pickup Point
•	Identify the most common starting locations for trips.
•	Helps in optimizing driver availability and dynamic pricing strategies.

![Screenshot 2025-04-25 005205](https://github.com/user-attachments/assets/b51b0d7f-35fa-4f90-ac5e-84684583cb55)


(Most Frequent Pickup Point = 
 var pickpoint = TOPN(1,SUMMARIZE('Trip Details','Location Table'[Location],"pickpoint",COUNT('Trip Details'[Trip ID])),[pickpoint],DESC)
     RETURN CONCATENATEX(pickpoint,'Location Table'[Location], " , "))
























