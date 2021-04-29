# Introduction 

## Why did we build Travel Insight (TI) API? 

Travel Insight (TI) Aggregation API is driven by our partners' need to connect to a significantly easier alternative to the traditional, ad-hoc approaches of data collection and data analysis.

## What is it? 

Travel Insight (TI) Aggregated API is a public API that enables subscribed partners to get an aggregated result of search and redirect data based on a set of queries. 

## Why Use it? 

### Instant Results 

There’s no additional data processing required, unlike with raw data files.

### Easy Accessibility 

It’s easy to use and simple to plug into your Power BI tools. 

## How does it work? 

For a given Origin and Destination itinerary, Travel Insight API parses previously searched itineraries across an array of specified dates. The service is highly customisable and offers unsurpassed search criteria, including filtering such as multiple lengths of stay, number of stops, day of week, departure/arrival time window, etc.

## Aggregation API provides two endpoints to submit analytics queries:
- **/searches:** runs analytical query on searches data

- **/exits:** runs analytical query on exits (redirects) data

You’ll find an in-depth explanation of both endpoints later in this document.
