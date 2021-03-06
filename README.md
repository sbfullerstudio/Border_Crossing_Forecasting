![ ](./visualizations/cover.jpg)

# New England Border Crossing Comparative Analysis and Time Series Forecasting

Of the New England states that are along the US-Canada border, Maine and New York have the highest number of border crossing locations and the highest amount of traffic. I wanted to see if, in a single day, I could better understand which locations had the highest amount of traffic in terms of passenger vehicle passengers, identify any trends or seasonality, and ultimately train a forecasting model for predicting passenger vehicle passenger traffic for any given date into the future. 

For starters, I downloaded a data set from the Bureau of Transportation statisics on Border Crossing Entry Data (https://www.bts.gov/browse-statistical-products-and-data/border-crossing-data/border-crossingentry-data). With a bit of cleaning, I was able to parse out just the passenger vehicle passenger data for border crossings in the states Maine and New York.

The plots below show that both Maine and New York have similar seasonality when it comes to passenger vehicle passenger border crossings. In both states, among all border crossings, Summer brings an increase in border crossing traffic.

![ ](./visualizations/me_avg_pvp_month.png)
![ ](./visualizations/ny_avg_pvp_month.png)
  
Furthermore, the below plots show that both Maine and New York have similar trends when it comes to passenger vehicle passenger border crossings. In both states, among all border crossings, passenger vehicle passenger count has been gradually decreasing for the past 20 years.

![ ](./visualizations/me_avg_pvp_year.png)
![ ](./visualizations/ny_avg_pvp_year.png)

This data set stops at 2019, and thankfully so. As the US-Canadian border has been mostly closed from 2020-2021 because of the covid pandemic, passenger vehicle passenger traffic across this border has been miniscule if not zero. This would have certainly skewed the data and distracted from the otherwise noticable seasonality and trend.

The busiest border crossings of each state, Buffalo-Niagara Falls, NY and Calais, ME, were singled out and plotted in sktime showing their shared trends and seasonality, but also their dramatic differences in volume.

![ ](./visualizations/me_ny_comb3.png)

Finally, I experimented with a range of different sktime models (), and found the Manual AutoETS estimator to be the best peforming. With Calais data, this model returns a mean squared error around 22,546 and a mean absolute percentage error of 20%. With Buffalo data, the model performs even better with a mean squared error around 60,511 and a mean absolute percentage error of 6%. The plots below show the performance of the Manual AutoETS estimator again the test data and the baseline...first with the Calais border crossing, and second with the Buffalo border crossing. 

![ ](./visualizations/cal_bestmodel.png)
![ ](./visualizations/buf_bestmodel.png)

### Conclusion:

In conclusion, these models perform well in terms of estimating the number of passenger vehicle passengers that will pass through either border crossing on any given day into the future. This could be used by border crossings to appropriately staff themselves, and could also be used by travelers looking to avoid long lines at border crossings.



