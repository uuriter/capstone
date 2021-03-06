# Introduction

Thailand is one of tourist favorite destinations.  The tourism industry contributes significantly to Thailand economic growth.  In 2016, the industry contributes to 17.7% of the nation's GDP.  **TAT** (Tourism Authority of Thailand) has a mission of promoting tourism in Thailand.  

**Amazing Thailand** is a successful tourist campaign issued by TAT.  Recently, TAT issued **Discover Thainess** tourist initiative as a supplement to the existing campaign.  The new campaign provides foreign visitors with Thai culture experience such as Thai fun, food, wellness, wisdom, and art.

<img src="https://cdn.pbrd.co/images/HEQvYG1.jpg" width="200"/>

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
