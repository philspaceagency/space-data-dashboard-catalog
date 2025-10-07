# space-data-dashboard-catalog

### :pushpin: Jump to repository
1. [geoserver-docker](https://github.com/philspaceagency/geoserver-docker) - Add data to Geoserver
2. [space-data-dashboard-terriajs-docker](https://github.com/philspaceagency/space-data-dashboard-terriajs-docker) - Add data to Space Data Dashboard catalog

### :pushpin: How to add data to Space Data Dashboard
1. Clone this repository
```
cd ~/Projects
git clone git@github.com:philspaceagency/space-data-dashboard-catalog.git
```
2. Edit the catalog (catalog-index.json) to add data. For geoserver data, follow the following format.
```json
{
    "isGeoServer": "true",
    "type": "wmts",
    "name": "Land Surface Temperature (LST)",
    "url": "https://geoserver.philsa.gov.ph/geoserver/gwc/service/wmts?service=WMTS&acceptVersions=1.0.0&request=GetCapabilities",
    "layer": "space-data-dashboard:NCR_LST_COG",
    "opacity": 1,
    "legends": [
        {
        "title": "Land Surface Temperature (Celsius) ",
        "type": "continuous",
        "min": 20,
        "max": 36,
        "units": "°C",
        "items": [
            {
            "title": "20",
            "color": "#30123b"
            },
            {
            "title": "24",
            "color": "#28bceb"
            },
            {
            "title": "28",
            "color": "#a4fc3c"
            },
            {
            "title": "32",
            "color": "#fb7e21"
            },
            {
            "title": "36",
            "color": "#7a0403"
            }
        ]
        }
    ]
}

```
4. Save the catalog and push to repository.
```
git add .
git commit -m "add sample data"
git push -u origin main
```

### Adding PINAS Workshop data
1. Once added in Geoserver, create new json file for the PINAS workshop data e.g. ABCDEF.json.
2. Fill the empty json file with the definition of the data. Example shown below.
```json
{
    "catalog": [
        {
            "name":"PINAS Ilocos Participatory Mapping",
            "type":"group",
            "members":[
                {
                    "isGeoServer": "true",
                    "type": "wmts",
                    "name": "PINAS Ilocos Participatory Mapping Point",
                    "url": "https://geoserver.philsa.gov.ph/geoserver/gwc/service/wmts?service=WMTS&acceptVersions=1.0.0&request=GetCapabilities",
                    "layer": "pinas:pinas-ilocos-point",
                    "opacity": 1
                },
                {
                    "isGeoServer": "true",
                    "type": "wmts",
                    "name": "PINAS Ilocos Participatory Mapping Area",
                    "url": "https://geoserver.philsa.gov.ph/geoserver/gwc/service/wmts?service=WMTS&acceptVersions=1.0.0&request=GetCapabilities",
                    "layer": "pinas:pinas-ilocos-polygon",
                    "opacity": 1
                }
            ]
        }
    ],
    "corsDomains": [
      "localhost",
      "corsproxy.com",
      "geoserver.philsa.gov.ph",
      "raw.githubusercontent.com",
      "storage.googleapis.com",
      "ows.services.dea.ga.gov.au"
    ]
}
```

3. Save the catalog and push to repository.
```
git add .
git commit -m "add sample data"
git push -u origin main
```
4. Visit the Space Data Dashboard with PINAS data through the link following the filename of json e.g. https://spacedata.philsa.gov.ph/#ABCDEF

### :pushpin: List of PINAS Catalog
| Area | Code | Link |
| ----- | ----- | ----- |
| All | P1NAS | https://spacedata.philsa.gov.ph/#P1NAS |
| Ilocos | DTQNX9 | https://spacedata.philsa.gov.ph/#DTQNX9 |
| Aklan | R814CO | https://spacedata.philsa.gov.ph/#R814CO |
| Davao | 0KFK4G | https://spacedata.philsa.gov.ph/#0KFK4G |
| Zamboanga | 9BP768 | https://spacedata.philsa.gov.ph/#9BP768 |
| Mindoro | 0PX9ED | https://spacedata.philsa.gov.ph/#0PX9ED |

### :pushpin: Dataset List as of 07 October 2025
| Section | Dataset | Description | Number of Data |
| ----- | ----- | ----- | ----- |
| Climate | Land Surface Temperature (LST) | Land surface temparature of Manila. | 1 |
| Land Cover and Land Use | 2022 National Land Cover | Land cover classification map of the Philippines. | 1 |
| Flood Hazard | Various Flood Extent Map | Different flood extent shapefiles across the Philippines using different sensors. | 1 |
| Environment | Nitrogen Dioxide (NO2) | Monthly average NO2 from 2019 to 2023. This dataset is from TROPOMI instrument onboard Sentinel-5. | 58 |
| PINAS Workshop | Various dataset from PINAS workshops | Digital shapefile of participatory mapping conducted during PINAS workshops. Dataset can be viewed using dedicated links. | 6 |

### :pushpin: Missing Dataset
| Section | Dataset | Description | Issue |
| ----- | ----- | ----- | ----- |
| Environment | 2023 Mangrove Map | National mangrove map of the Philippines using satellite data and citizen science validation. | Current shapefile has geometry problems when uploaded to PostGIS. |