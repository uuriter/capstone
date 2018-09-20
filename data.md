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
