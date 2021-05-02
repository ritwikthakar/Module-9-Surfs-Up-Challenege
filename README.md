# Module-9-Surfs-Up-Challenege
## Overview of Analysis
The purpose of this analysis is to obtain more information about temperature trends before opening the surf shop. As requested, we are specifically, looking for temperature data for the months of June and December in Oahu, to determine if the surf and ice cream shop business is sustainable year-round.
## Results
Listed below are the three key differences in weather between June and December.
-	There is merely a difference of 3 units between the mean temperatures obtained for the month of June and December. The average temperature tends to be 3 degrees higher in the month of June based on the last 7 years data.
-	In both months for the last 7 years, the difference in the standard deviation of the temperature has been less than 0.5 units with uncertainty being higher only by 0.5 units in the month of December.
-	The lowest recorded temperature in December has been 56 degrees while the highest recorded has been 83 degrees. The lowest recorded temperature for June is 64 degrees while the highest recorded has been 85 degrees for the last 7 years.  This data tells us that extreme temperature conditions are normally seen in the month of December.
![June Temperatures]()
![Dec Temperatures]()
## Summary
Based on the results above, we can see that temperature wise, the difference between temperatures in June & December has been negligible. Temperatures have been mostly high. The lowest temperature recorded over the last 7 years has been 56 degrees which reassures us that the ice cream & Surf Shop business could be done through the year.
## Recommendations
-	Precipitation: We can run the following query to check for precipitation. 
After importing all dependencies to and then preparing an engine, we can
use the following code to shortlist for June & December measurements.
```python
 june_precp = session.query(Measurement).filter(extract('month', Measurement.date) == 6)
 dec_precp = session.query(Measurement).filter(extract('month', Measurement.date) == 6)
 ``` 
 After this, we need to pass the precipitation data through a list
```python
june_precp_list = [precip.prcp for prcp in june_precp]
dec_precp_list = [precip.prcp for prcp in dec_precp]
```
Finally, we can pass the above two lists through 2 separate data frames to get an idea as to how
the precipitation levels might affect the business.

-	Stations: We can use the following code to analyse by stations.
```python
session.query(func.count(Station.station)).all()
```
This will give us the number of stations.
```python
session.query(Measurement.station, func.count(Measurement.station)).\
group_by(Measurement.station).order_by(func.count(Measurement.station).desc()).all()
```
This will group data by stations and arrange it in descending order. We can further enchance our analysis based on stations.
