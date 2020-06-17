# Metadata for problem set 4
This is the hourly precipitation data from the U.S. This data was obtained from https://data.nodc.noaa.gov/cgi-bin/iso?id=gov.noaa.ncdc:C00313
| Column Name | Description |
| ------- | ------- |
| STATION	| Unique identification number identifying each station |
| STATION_NAME |	Name identifying each station (can be a city or airport name) |
| ELEVATION	| The elevation(meters) above mean sea level during the time of recording |
| LATITUDE	| The latitude during the time of recording, for geographic location |
| LONGITUDE	| The longitude during the time of recording, for geographic location |
| DATE	| The year (4 digits), month (2 digits), and (day of the month) followed by a space then the hour (two digit) followed by a colon (:) followed by a This is the year of the record (4 digits), followed by month (2 digits), followed by a minute (two digits) of the time the data was recorded. |
| HPCP | The amount of precipitation (mm) recorded at the station for the hour ending at the time specified for DATE above. |	
| Measurement Flag	| Indicates if/when the accumulation is recorded (used for dates prior to 1984) |
| Quality Flag | Used to identify those sites that are deficient in the manner different shields are employed (used since January 1996). |


# How I would normalize
I would have two tables in order to normalize the data. 

My first table would be for the geographic location of the station. In this table I would include these columns: 'STATION', 'DATE', 'STATION_NAME', 'ELEVATION', 'LATITUDE', and 'LONGITUDE'. My primary key would be 'LATITUDE', 'LONGITUDE', AND 'DATE' in order to get an exact location and time of when the reading took place. 

The second one would be about the actual measurements taking place for the amount of precipitation. In this table I would include these columns: 'STATION', ''DATE', 'HPCP', 'Measurment Flag', and 'Quality Flag', and the primary key from table one (this will act as the foreign key between the two tables). The primary key for table two would be a composition of the 'STATION' and the 'DATE'. The reason why I chose both of them is because a station can not be recorded twice at the same time (you cant be two places at the same time thinking). If I just did 'Station' then there would be repeats for every time the station is recorded and if I just did 'Date' then it could have repeats if (by some chance) two stations were recorded at the exact same time. All of the other columns are more likely to have repeats.

# The data types for each column
Column | Type
--- | ---
STATION | CHAR string (6 digits)
STATION_NAME | VARCHAR string (max 200 characters)
ELEVATION | VARCHAR string (max 10 characters)
LATITUDE | VARCHAR string (max 10 characters)
LONGITUDE | VARCHAR string (max 10 characters)
DATE | DATETIME 
HPCP | VARCHAR string (max 10 charcters)
Measurement Flag: VARCHAR string (max 10 characters)
Quality Flag | VARCHAR string (max 10 characters)
