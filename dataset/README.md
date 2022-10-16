We used two datasets - *Bike Share Toronto Ridership Data*, and *Bike Share Toronto Station* Information Data.
The first dataset is the Bike Share Toronto Ridership Data (https://open.toronto.ca/dataset/bike-share-toronto-ridership-data/) which contains anonymized trip data. It includes:

| Field Name / Item / Column name | Description / Definition                                     | Comments / Examples                                          |
| ------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Trip Id                         | Object ID, unique integer                                    | Nominal value                                                |
| Trip Duration                   | Duration of a trip, in seconds                               |                                                              |
| Start Station Id                | Station_id of the station where the trip started (origin)    |                                                              |
| Start Time                      | Start time and date of a trip                                | mm/dd/yyyy hh:mm                                             |
| Start Station Name              | Name of the station where the trip started (origin)          |                                                              |
| End Station Id                  | Station_id of the station where the trip ended (destination) |                                                              |
| End Time                        | End time and date of a trip                                  | mm/dd/yyyy hh:mm                                             |
| End Station Name                | Name of the station where the trip ended (destination)       |                                                              |
| Bike Id                         | Bike_id of the bike                                          |                                                              |
| User Type                       | The type of user that took the trip                          | 'Annual Member' (annual pass holder) or 'Casual Member' (24 or 72 hour pass holders) |

We only use the monthly data of September 2022 which has 602817 entries dated from 09/01/2022 to 09/30/2022. Each entry represents a trip from start_station_id to end_station_id. We also removed 150 entries where end_station_id is NULL, resulting in 602667 valid entries in total.

The second dataset we compiled to locate each bike station is the station information data from Bike Share Toronto(https://tor.publicbikesystem.net/ube/gbfs/v1/en/station_information). After preprocessing, the dataset of our interest should only include the following fields:

| Field Name / Item / Column name | Description / Definition                   |
| ------------------------------- | ------------------------------------------ |
| station_id                      | Station's unique ID, string                |
| name                            | Station name, string                       |
| lat                             | Latitude, double                           |
| lon                             | Longitude, double                          |
| address                         | Address of the station, string             |
| Capacity                        | Bike rack capacity of the station, integer |

It is worth mentioning that the start station id and end station id from the ridership dataset are associated with the station_id in the stations dataset.

Please refer to the stations_dataset_preproc.ipynb/html file to go through the data preprocess. The generated maps including the basic distribution map of the shared bike terminals, hexagonal binning map, and the cluster map show that there are more bike terminals in downtown Toronto than in other areas of GTA.
