# TDEI-ExternalAPIs
External APIs for the TDEI project.

This repository contains the external APIs for the Transportation Data Equity Initiative (TDEI) project. These APIs will allow application developers and data tenants to consume data from and publish data to the TDEI. The APIs support three data types: [OpenSidewalks](https://www.opensidewalks.com), [GTFS-Pathways](https://developers.google.com/transit/gtfs/reference) and [GTFS-Flex-v2[(https://github.com/MobilityData/gtfs-flex/blob/master/spec/reference.md).

The Consumer API is intended for application developers to use to retrieve data from the TDEI. The initial API - v1.0 / MVP - is straightforward supporting retrieval of OSW data by bounding box and and retrieval of GTFS data by agency. Applications must register and get an API key, called an appID in the TDEI API, to use the API. There are not restrictions on who can get an appID, simply that an application must have an appID to use the TDEI Consumer API. 

The Producer API is intended for data tenants, transportation agencies, and TDEI project partners to publish data to the TDEI. This API is in the process of being defined, but will be straightforward allowing tenants, agencies and partners to publish data files to TDEI. Use of the Producer API will be restricted to TDEI project partners.
