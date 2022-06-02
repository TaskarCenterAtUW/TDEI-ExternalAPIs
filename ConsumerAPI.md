# Consumer API - v1.0 - MVP 

## Security / Authentication:
- All applications will be required to obtain an API key to use the TDEI consumer API
- Authentication to be used is OAuth 2.0
- The requirements for getting an API key are to provide a contact name, a valid email address and sign / acknowledge a data use agreement. 

## General API Calls:
### Use Cases
- As an application, I wish to retrieve a list of TDEI Consumer API versions
- As an application, I wish to retrieve a list of agencies for which the TDEI has data
- As an application, I wish to retrieve a list of stations for which the TDEI has pathways data
- As an application, I wish to retrieve a list of versions of the pathways standard in which data is available
  (to include link to documentation)
- As an application, I wish to retrieve a list of versions of the flex standard in which data is available
  (to include link to documentation)
- As an application, I wish to retrieve a list of versions of the osw standard in which data is available
  (to include link to documentation)
- As an application, I wish to retrieve a list of flex data files available
- As an application, I wish to retrieve a list of pathways data files available

## Pathways Consumer API - v1.0:
### Use Cases
- As an application, I wish to retrieve the most current pathways file for a station
  - GTFS-static files including the pathways.txt, stops.txt and levels.txt files and any GTFS static
  files necessary to interpret the pathways files will be returned
  - request will be identified by station
  - application will be able to specify a minimum confidence level
  - application will be able to specify a version of the pathways standard that they can accept 
- As an application, I wish to retrieve a specific pathways file for a station
  - GTFS-static files including the pathways.txt, stops.txt and levels.txt files and any GTFS static
  files necessary to interpret the pathways files will be returned
  - application will provide file_id, file_id to be retrieved by using the list of pathways data files available call

### Specifications
- There will be one API path that will take station_id, and an optional minimum confidence level and an optional
  schema versions that the application wants and an optional valid_from / start date identifying the file the application
  wants (schema_version, station_id, valid_from is a key)
- A url/uri to zip file will be returned
- Confidence level of the data will be returned
- schema version will be returned
- valid_from and valid_to dates are returned, if valid_to is null, indicates this is the latest data
- The file returned is a GTFS static file which includes GTFS-pathways data and any GTFS static files which are needed
to interpret the pathways data. File will not be a full GTFS static release.
- For the mvp, the endpoint will accept a single version in the request 
- For the mvp the endpoint will return at most one file

## Flex Consumer API - v1.0:
### Use Cases
- As an application, I want to retrieve the most current GTFS-Flex data for an agency
  - A zip file with GTFS-Flex v2 data including FlexibleTrips files (location_groups.txt, locations.geojson, stop_times.txt) and GTFS-Booking Rules files will be returned
  - request will be identified by agency
  - application will be able to specify a minimum confidence level
  - application will be able to specify a version of the flex standard that they can accept  
- As an application, I wish to retrieve a specific flex file for a station
  - A zip file with GTFS-Flex v2 data including FlexibleTrips files (location_groups.txt, locations.geojson, stop_times.txt) and GTFS-Booking Rules files will be returned
  - application will provide file_id, file_id to be retrieved by using the list of flex data files available call

### Specifications
- There will be one API path that will take agency_id, and an optional minimum confidence level and an optional
  schema versions that the application wants and an optional valid_from / start date identifying the file the application
  wants (schema_version, agency_, valid_from is a key) 
- A url/uri to zip file will be returned
- Confidence level of the data will be returned
- schema version will be returned
- valid_from and valid_to dates are returned, if valid_to is null, indicates this is the latest data
- The file returned is a GTFS static file which includes GTFS-Flex v2 data and any GTFS static files which are needed
to interpret the flex data. File will not be a full GTFS static release.
- For the mvp, the endpoint will accept a single version in the request 
- For the mvp the endpoint will return at most one file

## OSW Consumer API - v1.0:
### Use Cases
- As an application, I want to retrieve the most current OSW data by bounding box
  - OSW data within the bounding box will be returned 
  - data will be returned as a gzip'd geojson file (multiple geojson files may be included in the gzip'd file)
  - user will be able to specify a minimum confidence level
  - application will be able to specify a version of the OSW standard that they can accept 

### Specifications
- There will be one API path that will take a bounding box, and an optional minimum confidence level
- A url/uri to gzip json file will be returned
- Confidence level of the data will be returned
- valid_from and valid_to dates are returned, if valid_to is null, indicates this is the latest data
