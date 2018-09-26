# Introduction

Thailand is one of tourist favorite destinations.  The tourism industry contributes significantly to Thailand economic growth.  In 2016, the industry contributes to 17.7% of the nation's GDP.  **TAT** (Tourism Authority of Thailand) has a mission of promoting tourism in Thailand.  

**Amazing Thailand** is a successful tourist campaign issued by TAT.  Recently, TAT issued **Discover Thainess** tourist initiative as a supplement to the existing campaign.  The new campaign provides foreign visitors with Thai culture experience such as Thai fun, food, wellness, wisdom, and art.

In this report, our hypothetical non-profit organization is trying to help TAT by proposing **Tour Detour** initiative.  The purpose is to gain more local tourists.  We target Thai people who rarely travel.  By encouraging them to start small, which is by taking a little detour from their usual route, they might be interested in visit a tourist attraction.  

# Data

The input of our script is a pair of coordinates.  It might an origin and a destination of a usual route such as from work to home.  The script will output the distances between those coordinates and a list of tourist attractions ordered by the detour distances.  A detour distance is a distance from the origin to the tourist attraction plus a distance from the tourist attraction to the destination.

The following image shows the usual route.

![](https://cdn.pbrd.co/images/HEMPiHQ.png)

The following image shows the detour to Jim Thompson House.

![](https://cdn.pbrd.co/images/HEMOxX7.png)

Location data is obtained from Foursquare API.  A Venue API parameter 'section' will be set to 'arts' to get a tourist attraction in an art category.  The distance between two locations is obtained from Google Distance Matrix API.  The API receives origin and destination in latitude and longitude.  It returns the distance and the travel duration.  The sample result from the API is as follows.

```
{
  "destination_addresses": [
    "50/5 Rama I Rd, Khwaeng Rong Muang, Khet Pathum Wan, Krung Thep Maha Nakhon 10330, Thailand"
  ],
  "origin_addresses": [
    "99/46-7 ซอยอนันตนาค กรุงเกษม Wat Thepsirin, Khet Pom Prap Sattru Phai, Krung Thep Maha Nakhon 10100, Thailand"
  ],
  "rows": [
    {
      "elements": [
        {
          "distance": {
            "text": "3.6 km",
            "value": 3592
          },
          "duration": {
            "text": "8 mins",
            "value": 450
          },
          "status": "OK"
        }
      ]
    }
  ],
  "status": "OK"
}
```

# Methodology

**FourSquare API** is used to obtain nearby venues of both origin and destination.
To find tourist attractions, we set the parameter **section** to arts and delete row that has categories of 'Theater' or 'Multiplex'.
The API returns data in JSON format which is transformed to Pandas DataFrame.

**Google Map Distance Matrix API** is used to find the usual route duration and a trip duration.
The usual route duration is the duration from the origin to the destination.
The trip duration is the duration from origin to a tourist attraction and from a tourist attraction to the destination.
A detour duration is the difference between these duration.
It is added to the DataFrame for data visualization.

**Folium library** and **IPyWidget** are used to interactively *explore* tourist attractions.
Folium library is used to display an interactive map.
IPyWidget is used to filter the DataFrame by the detour duration.
For example, as shown in the picture when the slider is set to 5, 
the map will show the venues with 0-5 minutes the detour duration.
If the slider is set to 10, 
the map will show the venues with 5-10 minutes the detour duration.

<img src="https://pasteboardfiles.s3.amazonaws.com/images/f3d7c29/8882f4cdef85c87e80346ac13c3f3e91.png?X-Amz-Expires=600&X-Amz-Date=20180926T005731Z&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAJZEXC3KKHVJLXFMA/20180926/us-east-1/s3/aws4_request&X-Amz-SignedHeaders=host&X-Amz-Signature=baec273bcd1aa4f6805be672b2904b9e6bd8d2e34c611def47b78b94a69a0d1d"
width="300" />
 
