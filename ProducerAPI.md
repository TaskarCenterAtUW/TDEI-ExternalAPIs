# Producer API - v1.0 - MVP 

## Security / Authentication:
- All applications will be required to obtain an API key to use the TDEI producer API
- Authentication to be used is OAuth 2.0
- The requirements for getting an API key are to provide a contact name, a valid email address and sign / 
acknowledge a data use agreement. 
- API calls will also be protected by user authorization to manage data contributions 

## General API Calls:
### Use Cases
- As an application, I wish to retrieve a list of TDEI Producer API versions. (/tdei_producer)
- As an application, I wish to retrieve a list of agencies for which the TDEI has data (/tdei_producer/v1.0/agencies)
- As an application, I wish to retrieve a list of transit stations for which the TDEI has data (/tdei_producer/v1.0/stations)

## Pathways Producer API - v1.0:
### Use Cases
- As an agency or data contributor, I wish to upload a GTFS-pathways set of files for a station 
  - Provide a url to the zip file
    - Zip file will be a GTFS data file that contains the pathways files (pathways.txt, stop.txt, levels.txt) 
    and any other GTFS static files that are required to interpret the pathways files
   - Provide meta-data to fill in the data record and pathways meta-data tables
     - Data Record table
       - data_type (can get from path)
       - timestamp (assigned by TDEI)
       - uploaded_by/producer_id (map appID to the producer ID)
         - Need to consider whether this is done in Auth service or DM service
       - Pathways meta-data
         - data_record_id (assigned by TDEI)
         - transit_agency_id (need to be provided in API) 
           - get transit_agency_id from agencies list
         - valid_from (need to be provided in API)
         - valid_to (need to be provided in API, need to allow an indefinite option) 
         - versionid (assigned by TDEI)
         - blob_uri (assigned by TDEI
- As an agency or data contributor, I wish to update the valid_to date of a GTFS-pathways file
  - file will be identified by data_record_id which can be retrieved from the /gtfs_flex endpoint
- As an agency or data contributor, I wish to retrieve a list of gtfs pathways files 



### Specifications
- One path, following will be required
  - appID
  - url to zip file - assume this is a full on GTFS release with pathways data
  - transit_agency_id
  - valid_from
  - valid_to (need to figure out how to handle 'indefinite', I'm not a fan of leaving empty as that can be error prone)
  - NEED CALL TO SET END DATE...

## Flex Producer API - v1.0:
### Use Cases
- As an agency or data contributor, I wish to upload the latest GTFS-Flex files for an agency, GTFS release 
to include Flexible Trips and Booking rules files for an agency 
  - Provide a url to the zip file
- Provide meta-data - meta-data for flex is identical to pathways - see information above

### Specifications
- One path, following will be required
  - appID
  - url to zip file - assume this is a full on GTFS release with pathways data
  - transit_agency_id
  - valid_from
  - valid_to (need to figure out how to handle 'indefinite', I'm not a fan of leaving empty as that can be error prone)

## OSW Producer API - v1.0:
### Use Cases
- As an agency or data contributor, I wish to upload an updated OSW file with data for my agency 
  - File should be a gzip'd geojson file
  - uploader should specify agency_id and bounding box and a vaid_date
  - Provide meta-data to fill in the data record and pathways meta-data tables
    - Data Record table
      - data_type (can get from path)
      - timestamp (assigned by TDEI)
      - uploaded_by/producer_id (map appID to the producer ID)
        - Need to consider whether this is done in Auth service or DM service
     - OSW meta-data
       - data_record_id (assigned by TDEI)
       - agency_id (need to be provided in API) 
         - get agency_id from agencies list
       - valid_date (need to be provided in API) 
         - date this file is consider valid by the agency
       - versionid (assigned by TDEI)
       - blob_uri (assigned by TDEI

### Specifications
- One path, following will be required
  - appID
  - url to a gzip json file 
  - agency_id
  - valid_date

