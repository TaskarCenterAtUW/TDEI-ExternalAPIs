# Consumer API - v1.0 - MVP 

## Security / Authentication:
- All applications will be required to obtain an API key to use the TDEI consumer API
- Authentication to be used is OAuth 2.0
- The requirements for getting an API key are to provide a contact name, a valid email address and sign / acknowledge a data use agreement. 

## General API Calls:
### Use Cases
- As an application, I wish to retrieve a list of TDEI Consumer API versions
- As an application, I wish to retrieve a list of agencies for which the TDEI has data

## Pathways Consumer API - v1.0:
### Use Cases
- As an application, I wish to retrieve the most current pathways files for an agency
  - Most current GTFS-static release, which includes the pathways.txt, stops.txt and levels.txt files will be returned
  - request will be identified by agency
  - user will be able to specify a minimum confidence level

### Specifications
- There will be one API path that will take agency_id, and an optional minimum confidence level
- A url/uri to zip file will be returned
- Confidence level of the data will be returned
- valid_from and valid_to dates are returned, if valid_to is null, indicates this is the latest data
- The file returned is a GTFS static file which includes GTFS-pathways data 

## Flex Consumer API - v1.0:
### Use Cases
- As an application, I want to retrieve the most current GTFS-Flex data  GTFS-Flexible Trips file for an agency
  - A zip file with GTFS-Flexible Trips files (location_groups.txt, locations.geojson, stop_times.txt) and GTFS-Booking Rules files will be returned
  - Return a GTFS static file which includes GTFS-Flex v2 data including files and fields from the FlexibleTrips and BookingRules extensions 
  - user will be able to specify a minimum confidence level

### Specifications
- There will be one API path that will take agency_id, and an optional minimum confidence level
- A url/uri to zip file will be returned
- Confidence level of the data will be returned
- valid_from and valid_to dates are returned, if valid_to is null, indicates this is the latest data
- The file returned is a GTFS static file which includes GTFS-Flex v2 data

## OSW Consumer API - v1.0:
### Use Cases
- As an application, I want to retrieve the most current OSW data by bounding box
  - OSW data within the bounding box will be returned
  - data will be returned as a g-zip'd geojson file
  - user will be able to specify a minimum confidence level

### Specifications
- There will be one API path that will take a bounding box, and an optional minimum confidence level
- A url/uri to gzip json file will be returned
- Confidence level of the data will be returned
- valid_from and valid_to dates are returned, if valid_to is null, indicates this is the latest data
