# Surfs up: data storage and retrieval with 

Exploring Weather data: data storage and retrieval with SQLite, SQLAlchemy, and Flask

## Overview

While surfing in Oahu we came up with the idea to open a combination surf shop and ice cream
parlor. After developing a business model, we approached W. Avy to consider investing in our 
business. Before he would agree to invest in our business, he wanted us to run an analysis of 
the Oahu weather to determine if the weather in the vicinity of the shop was appropriate for a 
year-round surf shop. 

## Results 

Our analysis of the June and December weather yielded the following results:

- With 1,700 June temperature readings from our sample, the mean June temperature was 74.94 degrees,
with a median temperature of 75 degrees. The low temperature recorded was 64 degrees, and the high
temperature recorded was 85 degrees.

![June Temperature Readings](https://github.com/greensleeves8/surfs_up/blob/main/Resources/June_Temps.png)

- With 1,517 December temperature readings from our sample, the mean December temperature was 71.04
degrees, with a median temperature of 71 degrees. The low temperature recorded was 56 degrees, and 
the high temperature recorded was 83 degrees. 

![December Temperature Readings](https://github.com/greensleeves8/surfs_up/blob/main/Resources/Dec_Temps.png)

- While the overall temperatures between June and December were fairly similar, the December temperatures
had a wider range than the June temperatures. 

## Summary

Overall, the difference between the June and December temperatures were rather slight, with the December
average temperatures just outside of a standard deviation of the June temperatures. The range in 
temperatures was slightly wider in December, and also skewed slightly colder, but the difference between
the mean and median June and December temperatures was right around 4 degrees, which doesn't seem like it
would have a substantial affect on business. In fact, it's possible that the December business may have a
wider range of potential customers due to tourism rates. 

To further explore the differences in the June and December weather, it's a good idea to take a closer look
at the rainfall data from the different weather stations. To query for the June rainfall, I included the
following code:

	june_rain = session.query(Measurement.station, func.sum(Measurement.prcp).group_by(Measurement.station).\
		filter(extract('month', Measurement.date) == 6).all()

