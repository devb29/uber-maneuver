## **“Uber Maneuver”**
### **How taxis can better position themselves in NYC**

By Devra Alper<br>

*Interact with my data on [Tableau](https://public.tableau.com/app/profile/devra2843/viz/UberManeuver/UberManuever)*

#### **Abstract**
<p>TLC taxi ridership has decreased since ridesharing companies like Uber have gained popularity in NYC. This trend has fluctuated during the COVID-19 pandemic. When increasing demand in 2021 was met with less Uber and taxi drivers, Uber surge pricing shifted New Yorkers towards taxis and their more stable pricing. As surge prices settle, TLC and cab companies can capitalize further by positioning their taxis in high-demand areas.</p>

<p>The effect of gas on both drivers’ wallets and the environment is another factor to consider. Positioning taxis in areas that are likely to result in passenger pick-ups, versus driving in areas with low passenger pick-up rates, will decrease personal and environmental costs.</p>

<p>This analysis seeks to identify areas when and where its competitor, Uber, is picking up passengers more than taxis. The analysis is a Proof of Concept, utilizing data from one day (4/18/2014) to demonstrate its feasibility on a larger scale. This information will inform TLC of where to position its drivers as another option for passengers in these areas. Hopefully, having more visible taxis will encourage people to utilize them more, either by hailing on the street or through other taxi hailing apps.</p>

*Sources:*<br>
<p>[Uber and Lyft drivers get squeezed by high gas prices: ‘I barely broke even’](https://nypost.com/2022/03/14/uber-and-lyft-drivers-get-squeezed-by-high-gas-prices-i-barely-broke-even/), March 14, 2022<br>
[As Uber and Lyft fares surge, NYC taxis are becoming popular again, August 27](https://www.businessinsider.com/e-hailing-taxis-curb-increasing-faster-than-uber-lyft-nyc-2021-8), 2021<br>
[Uber and Lyft are cutting even further into the taxi market during the pandemic](https://citymonitor.ai/transport/uber-lyft-rides-during-coronavirus-pandemic-taxi-data-5232), July 20, 2021<br>
[You Can’t Find a Cab. Uber Prices Are Soaring. Here’s Why](https://www.nytimes.com/2021/06/15/nyregion/uber-prices-rise-yellow-taxis.html), June 16, 2021</p>

#### **Solution Path & Design**
*Solution Path:*
1. Exploratory data analysis of Uber and taxi data to identify when and where Uber is outperforming taxis on 4/18/2014, using more recent data for future modeling if possible.
2. Modeling
	1. Time series regression modeling to determine relationships associated with when and where taxis pick up more passengers and predict optimal times and places for pick-up.
	2. Reinforcement learning via Q-learning, to teach an algorithm to find optimal pick-up times and places by rewarding for correct solutions and punishing for wrong ones.
	
*Design:*
<p>This analysis will identify when and where TLC should allocate more of its fleet and resources, with the goal of increasing revenue. Ideally, it would be beneficial to know if Uber ridership decreases in the areas where taxi presence increases, but obtaining more ridership data from Uber may be difficult.</p>

<p>Rides per hour, rides per zipcode, and rides per hour per zipcode were calculated after data cleaning to determine when and where taxis should pick up passengers. Green and yellow taxi data was explored separately, but combined for comparative analyses with Uber. Since the number of overall pick-ups varied between each dataset, data was compared via proportions of total pick-ups.</p>

#### **Data**
Uber data: https://github.com/fivethirtyeight/uber-tlc-foil-response/blob/master/uber-trip-data/uber-raw-data-apr14.csv<br>
Green taxi data: https://data.cityofnewyork.us/Transportation/2014-Green-Taxi-Trip-Data/2np7-5jsg<br>
Yellow taxi data: https://data.cityofnewyork.us/Transportation/2014-Yellow-Taxi-Trip-Data/gkne-dk5s<br>

<p>The Uber data used in this analysis was gathered from a Freedom of Information Law request from FiveThirtyEight in 2015. Taxi data was downloaded from NYC Open Data. I intended to analyze one week of rides in 2014; however, the taxi subsets were still too large to use with limited resources at hand (Google Sheets as a preferred method for EDA, limited computer memory). I opted to use Python to subset the data prior to importing to Google Sheets. Instead of analyzing a full week, I decided to focus on one day – Friday 4/18/2014. I’ve assumed that a Friday date will capture both commuter and nightlife demand. Also, there was no adverse weather that day or any major events.</p>

<p>All data share the following information: passenger pick-up date and time, as well as the latitude and longitude of the pick-up. Taxi data also includes drop-off information and other transaction data. Zipcodes were retrieved from latitude and longitude using Python and, partially, Google Sheets App Script function, then added to the datasets.</p>

#### **Tools**
* Beautiful Soup and Selenium for web scraping
* Numpy and Pandas for data manipulation
* Scikit-learn for modeling
* Matplotlib and Seaborn for plotting