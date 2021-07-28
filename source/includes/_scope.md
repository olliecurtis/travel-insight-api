# Scope of API

## Supported Dimensions (used in both filters and groupBy query parameter)

### On searches data: 
-	**market:** Name of the country user has selected or Skyscanner domain being used
-	**originCountry:** The country of the first leg's first segment
-	**destinationCountry:** The destination country of the first leg's last segment
-	**originIATA:** Origin IATA airport code
-	**destinationIATA:** Destination IATA airport code
-	**cabinClass:** Cabin class type, either ECONOMY, BUSINESS, PREMIUMECONOMY, FIRST
-	**departureDate:** Departure date
-	**returnDate:** Return date
-	**pax:** Passenger count
-	**route:** The first leg's origin city concatenated with the final leg's destination city.
-	**kind:** Trip type. Either 'RETURN', 'ONE_WAY' or 'MULTI_CITY'
- **daysBeforeTravel:** How many days before travel the search happened
- **travelMonth:** Date of travel of the oubound leg in the format YYYYMM
- **dayOfWeek:** Day of the week of the oubound leg (Monday is 1)
- **lengthOfTripInDays:** Difference in days between the outbound and return leg of the trip
- **travelType:** One of DOMESTIC or INTERNATIONAL
- **userCityLatitude:** Latitude of the user location
- **userCityLongitude:** Longitude of the user location
- **userCityName:** City name of the user
- **userCountryCode:** Country code of the user
- **userRegionCode:** Region name of the user
- **userRegionName:** Region code of the user
- **distanceToOriginInMetres:** Distance in meters between the user location and the departing airport


### On exits(**redirects**) data:
- **market:** Name of the country user has selected or Skyscanner domain being used
- **originCountry:** The country of the first leg's first segment
- **destinationCountry:** The destination country of the first leg's last segment
- **originIATA:** Origin IATA airport code
- **destinationIATA:** Destination IATA airport code
- **cabinClass:** Cabin class type, either ECONOMY, BUSINESS, PREMIUMECONOMY, FIRST
- **departureDate:** Departure date- **returnDate:** Return date
- **departureTimeOfDay:** Departure time of day. Either 'EARLY_MORNING', 'MORNING', 'AFTERNOON', 'EVENING'. Early Morning (0000 to 0600), Morning (0600 to 1200), Afternoon (1200 to 1800), Evening (1800 to 2400)
- **returnTimeOfDay:** Return time of day. Either 'EARLY_MORNING', 'MORNING', 'AFTERNOON', 'EVENING'. Early Morning (0000 to 0600), Morning (0600 to 1200), Afternoon (1200 to 1800), Evening (1800 to 2400)
- **kind:** Trip type. Either 'RETURN', 'ONE_WAY' or 'MULTI_CITY'
- **marketingCarriers:** Marketing carrier code
- **stops:** Number of stops
- **route:** The first leg's origin city concatenated with the final leg's destination city.
- **pax:** Passenger count
- **journeyDuration:** Journey duration in minutes
- **departureTimeOfDay:** One of MORNING, AFTERNOON, EVENING for the outbound leg
- **returnTimeOfDay:** One of MORNING, AFTERNOON, EVENING for the return leg
- **marketingCarriers:** List of carriers on the itinerary selected
- **daysBeforeTravel:** How many days before travel the redirect happened
- **travelMonth:** Date of travel of the oubound leg in the format YYYYMM
- **dayOfWeek:** Day of the week of the oubound leg (Monday is 1)
- **firstMarketingCarrier:** First carrier on the selected itinerary
- **lengthOfTripInDays:** Difference in days between the outbound and return leg of the trip
- **travelType:** One of DOMESTIC or INTERNATIONAL
- **userCityLatitude:** Latitude of the user location
- **userCityLongitude:** Longitude of the user location
- **userCityName:** City name of the user
- **userCountryCode:** Country code of the user
- **userRegionCode:** Region name of the user
- **userRegionName:** Region code of the user
- **distanceToOriginInMetres:** Distance in meters between the user location and the departing airport


## Supported Aggregations

### On searches data
-   **count:** Total number of rows matching given groupby combinations

### On redirects data
-   **count:** Total number of rows matching given groupby combinations
-   **averageFarePerPax:** Average fare price in USD per pax for rows matching given groupby combinations (can only be used alongside `count`)


## Supported Query Criteria 
-	Max number of `filter`s allowed in a query: 11
-	Max number of dimensions allowed in a `groupBy` query parameter: 3
-	Max date interval supported in a query: 30 days, by default
-	Max number of queries allowed in a minute: 1
-	Partner's API key must be available in `API-Key` request header
- Data is available for rolling 365 days in the past, by default.
-	Maximum number of results returned in an API call is 100000 and the API does not support paging at this stage.
-	Be aware that **searches** can be done on a city or airport level. Consider this when using the **originIATA** or **destinationIATA** filters. eg all searches for London should use the followings values: LHR, LCY, LGW, LTN, SEN (airport codes) **and** LON (IATA code for the city)
