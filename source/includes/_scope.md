# Scope of API for Beta Release

## Supported Dimensions (used in both filters and groupBy query parameter)

### On searches data: 
- **market:** Name of the country user has selected or Skyscanner domain being used
- **originCountry:** The country of the first leg's first segment
- **destinationCountry:** The destination country of the first leg's last segment
- **originIATA:** Origin IATA airport code
- **destinationIATA:** Destination IATA airport code
- **cabinClass:** Cabin class type, either ECONOMY, BUSINESS, PREMIUMECONOMY, FIRST
- **departureDate:** Departure date
- **returnDate:** Return date
- **pax:** Passenger count
- **route:** The first leg's origin city concatenated with the final leg's destination city.
- **kind:** Trip type. Either 'RETURN', 'ONE_WAY' or 'MULTI_CITY'

(Queryable for data from 17 May 2020 onwards)

- **daysBeforeTravel:** Number of days between departure date and search date
- **travelMonth:** Month of departure date
- **dayOfWeek:** Day of departure date (1 represents Monday, 7 represents Sunday)
- **lengthOfTripInDays:** Number of days between return date and departure date
- **travelType:** Travel type. Either 'INTERNATIONAL' or 'DOMESTIC'


### On exits(**redirects**) data:
- **market:** Name of the country user has selected or Skyscanner domain being used
- **originCountry:** The country of the first leg's first segment
- **destinationCountry:** The destination country of the first leg's last segment
- **originIATA:** Origin IATA airport code
- **destinationIATA:** Destination IATA airport code
- **cabinClass:** Cabin class type, either ECONOMY, BUSINESS, PREMIUMECONOMY, FIRST
- **departureDate:** Departure date
- **returnDate:** Return date
- **departureTimeOfDay:** Departure time of day. Either 'EARLY_MORNING', 'MORNING', 'AFTERNOON', 'EVENING'. Early Morning (0000 to 0600), Morning (0600 to 1200), Afternoon (1200 to 1800), Evening (1800 to 2400)
- **returnTimeOfDay:** Return time of day. Either 'EARLY_MORNING', 'MORNING', 'AFTERNOON', 'EVENING'. Early Morning (0000 to 0600), Morning (0600 to 1200), Afternoon (1200 to 1800), Evening (1800 to 2400)
- **kind:** Trip type. Either 'RETURN', 'ONE_WAY' or 'MULTI_CITY'
- **marketingCarriers:** Marketing carrier code
- **stops:** Number of stops
- **route:** The first leg's origin city concatenated with the final leg's destination city.
- **pax:** Passenger count

(Queryable for data from 17 May 2020 onwards)

- **daysBeforeTravel:** Number of days between departure date and search date
- **travelMonth:** Month of departure date
- **dayOfWeek:** Day of departure date (1 represents Monday, 7 represents Sunday)
- **lengthOfTripInDays:** Number of days between return date and departure date
- **firstMarketingCarrier:** First marketing carrier code
- **travelType:** Travel type. Either 'INTERNATIONAL' or 'DOMESTIC'



## Supported Query Criteria 
-	Max number of `filter`s allowed in a query: 11
-	Max number of dimensions allowed in a `groupBy` query parameter: 3
-	Max date interval supported in a query: 30 days
-	Max number of queries allowed in a minute: 1
-	Partner's API key must be available in `API-Key` request header
-	Data available for querying dates from 1st October 2019 onwards.
