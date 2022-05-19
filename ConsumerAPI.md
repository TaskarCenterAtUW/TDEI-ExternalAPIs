# Consumer API - v1.0 - MVP 

## Updates
### 5/16/2022
- Actually really removed station from flex (I apparently missed this last time)
- Updated flex to clarify that there is one call which will return a zip file with all flex data
- Removed questions, these have been updated now

### 5/12/2022
- Removed station and bounding box from pathways, removed station from flex to simplify, moved notes on those to the Future API doc
- Also removed stations call since there are now no retrievals based on station_id in this API

## Security / Authentication:
- All applications will be required to obtain an API key to use the TDEI consumer API
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

### Specifications
- There will be one API path that will take agency_id, url to zip file will be returned
- We should be returning the GTFS static file from the agency, believe that will include pathways data

## Flex Consumer API - v1.0:
### Use Cases
- As an application, I want to retrieve the most current GTFS-Flex data  GTFS-Flexible Trips file for an agency
  - A zip file with GTFS-Flexible Trips files (location_groups.txt, locations.geojson, stop_times.txt) and GTFS-Booking Rules files will be returned
  - Question is if these files are part of a GTFS release and if we should just return the release. For now I left pathways and flex separately assuming we will get flex and pathways data from separate sources, at least initially. 

### Specifications
- There will be one API path that will take agency_id, url to zip file will be returned

## OSW Consumer API - v1.0:
### Use Cases
- As an application, I want to retrieve the most current OSW data by bounding box
  - OSW data within the bounding box will be returned
  - data will be returned as a g-zip'd geojson file

### Specifications
- There will be one API path that will take a bounding box, url to gzip json file will be returned

