# Dataset Exploration Airline On-Time Performance Data
## by LARIANE Mohcene Mouad


## Dataset

> **Introducing the dataset** 
This dataset reports flights in the United States in 2007, including carriers, arrival and departure delays, and reasons for delays and many other variables

**Variables Description**
- **Year**: 1987 - 2008 (since we're studying only flight_2007 dataset, all years will be set to 2007)
- **Month**: 1 (Jan) - 12 (Dec)
- **DayofMonth**: 1 - 31
- **DayOfWeek**: 1 (Monday) - 7 (Sunday)
- **DepTime**: actual departure time (local, hhmm)
- **ArrTime**: actual arrival time (local, hhmm)
- **CRSDepTime**: scheduled departure time (local, hhmm)
- **CRSArrTime**: scheduled arrival time (local, hhmm)
    - **CRS**: Computer Reservation System. CRS provide information on airline schedules, fares and seat availability to travel agencies and allow agents to book seats and issue tickets.
- **UniqueCarrier**: unique carrier code which is the Carrier Code most recently used by a carrier. A numeric suffix is used to distinguish duplicate codes, for example, PA, PA (1), PA (2). Use this field to perform analysis of data reported by one and only one carrier.
- **FlightNum**: flight number
- **TailNum**: plane tail number
- **ActualElapsedTime**: The time computed from gate departure time to gate arrival time in minutes
- **CRSElapsedTime**: scheduled elapsedTime in minutes
- **AirTime**: Flight Time, in Minutes
- **ArrDelay**: Difference in minutes between scheduled and actual arrival time. Early arrivals show negative numbers.
- **DepDelay**: Difference in minutes between scheduled and actual departure time. Early departures show negative numbers.
- **Origin**: origin IATA airport code
- **Dest**: destination IATA airport code
- **Distance**: The distance between the Origin and the destination in miles
- **TaxiIn**: taxi in time which is the time elapsed between wheels down and arrival at the destination airport gate in minutes
- **TaxiOut**: taxi out time which the time elapsed between departure from the origin airport gate and wheels off in minutes
- **Cancelled**: was the flight cancelled? "1 = yes, 0 = no"
- **CancellationCode**: "reason for cancellation (A = carrier, B = weather, C = NAS, D = security)" 
    - **NAS** : National Aviation System is a broad term for a set of situations that can affect flight times. These include airport operations, non-risky weather conditions, high air traffic volume, and air traffic control delays. For unknown reasons.
    - **Weather**: Flight cancellation due to weather conditions
    - **security**: it’s a result of terminal or concourse evacuation, a security breach on an aircraft, long lines at screening areas, or defective screening equipment
- **Diverted**: A flight that is required to land at a destination other than the original scheduled destination for reasons beyond the control of the pilot/company "1 = yes, 0 = no"
- **CarrierDelay**: in minutes, usually pertains to the status within the airline's control. For example, problems with maintenance and crew, cleaning within the cabin, fueling, and baggage loading could all be contributing factors of a delayed flight 
- **WeatherDelay**: in minutes
- **NASDelay**: in minutes
- **SecurityDelay**: in minutes
- **LateAircraftDelay**: in minutes

**References:**
- [Different Types of Flight Delays](https://www.sheffield.com/2019/different-flight-delays.html#:~:text=of%20flight%20delays.-,Air%20Carrier,factors%20of%20a%20delayed%20flight.)    
- [Dataset official website](https://www.transtats.bts.gov/DatabaseInfo.asp?QO_VQ=EFD&Yv0x=D)
- [Definitions](https://www.transtats.bts.gov/Fields.asp?gnoyr_VQ=FGJ)

> **The structure of the dataset:**
There are 7453215 flight records in the dataset with 29 features including carriers, arrival and departure delays, and reasons for delays and many other variables. Most variables are numeric in nature, and the rest of them are none-numeric. 

> **Note:**
**Selecting a random sample from the dataset to work on**
Since the original dataset is too large ( + 7m rows ), I will do my study on only a random 1.5m records sample that was created in the ``Part_0_wrangling_and_creating_a_sub_sample_to_work_on.ipynb`` notebook where I've delt with the following issues :
**Quality issues** : 
    - ``DepTime`` ``CRSDepTime`` ``ArrTime`` ``CRSArrTime`` fix these features values time format
    - Replace DayOfWeek values by the actual days names
    - Replace the bool features values by their actual values
**Tidiness issues**:
    - ``Year`` ``Month`` ``DayofMonth`` should be in one column named ``Date``
    
**I did my analysison this sample of 1.5m record instead of the original, in order to reduce execution time for this project.**


## Summary of Findings

> During this analysis, I managed to fogured out when do people often travel and What flights are more likely to be cancelled or delayed and the reasons behind this cancellation, and how well the carriers are handling and managing their flights. And these are some main fondings ?

**About the passengers and airports**
- people are more likely to travel during the weekend, but they avoid traveling at the end of the month, also they travel a lot during the months of July and August
- Airports/cities such us PSE, SJU, BQN are considered one of the most far distances that people travel to, and TYR, ACT, EAU are considered one of the closest destinations that people do actually bother to travel to on place
- Atlanta, Chocago, Dallas are the most three active air traffic cities (airports) in our records


**About the flights**
- Most flights take off from 6am to 7am and arrive at 6am to midnight
- Most distances are between 100-3000 miles
- Most flights take between 30-300 minutes (half an hour to 5 hours) to arrive to their destination, with an air time less than 200 minutes (3.5 hours)
- Early arrival flights tend to arrive 5-30 minutes earlier than the Scheduled arrival time, and late arrival flights tend to arrive 5-300 minutes late than the Scheduled arrival time. Where Only 2.74% of the flights arrive in time which indicates that flights rarely arrive exactly in time, where the number of flights with early arrival is slightly higher than flights with late arrival, because the number of flights that leave early is slightly higher than the number of flights that leave late
- Only 2.17% of the flights were cancelled and only 0.23% of the flights were diverted
- Almost all cancellation are bacause of the weather conditions or the carrier, around only 6000 cancellations are a result of National Aviation System situation, where only 7 fights were cancelled because of security reasons.

**About carriers**
- WN (Southwest Airlines) dominates the market, where it covers 16% of it, x2 ahead from its best competitor which is The American Airlines.
- Carriers with the highest flights cancelation ratio are : MQ, OH, YV where almost 4% of their intire flights were cancelled. On the other hand carriers such as HA, F9 have the lowest cancellation ratio with less than 0.5% of their flights not beeing cancelled.
- Carriers with the highest flights divertion ratio are : XE, B6, CO where about 0.35% of their intire flights were diverted. On the other hand carriers such as AQ, HA have the lowest flights divertion ratio with less than 0.05% of their flights not beeing diverted.
- Carriers with the highest flights divertion ratio are : XE, B6, CO where about 0.35% of their intire flights were diverted. On the other hand carriers such as AQ, HA have the lowest flights divertion ratio with less than 0.05% of their flights not beeing diverted.
- Where carriers such as EV and B6 always suffer from long delays during its flights (mean of 18-19min per flight) whether the long or short which indicates that these carriers are having problems managing their flights, there carriers are considered the worst carriers in matter of delay time.
- Carriers such as HA and AQ often handle short distance flights (max 600 miles long ) where these carriers makes sure that their flights aways take off and arrive in time. These carriers are happen to be the best choice for short distance flights where they're doing a good job handeling short distance flights.

## Key Insights for Presentation

For the presentation, I focused on just the features related to flights cancellation/divertion/delayed.

I started by the distriburion of the flights arrive/departure delay, followed by a pie graph of flights early/late/Intime for both arrival and depature, gathering all these informations (plots) in one plot.

Afterwards, I introduced the propostions of flights cancellations and divertion.

Now after focusing on these features related to flights cancellation/divertion/delayed regardless of the air carrier, it's time to start focusing on this latter, where I started by distribution of the air carriers showing the flights domination for each carrier. then I wanted to see the cancellation distribution in relation with the air carriers, not only but also the reasons behind each cancellation too see which carriers suffer from a particular reason that can lead to an eventual cancellation of their flights.

And finally, I wanted to see what kind of flights each carrier usually handle (cover) and how well each carrier manage these flights in matter of delay time.