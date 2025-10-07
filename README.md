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
```
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
1. PINAS Ilocos: https://spacedata.philsa.gov.ph/#DTQNX9
2. PINAS Aklan: https://spacedata.philsa.gov.ph/#R814CO
3. PINAS Davao: https://spacedata.philsa.gov.ph/#0KFK4G
4. PINAS Zamboanga: https://spacedata.philsa.gov.ph/#9BP768
5. PINAS Mindoro: https://spacedata.philsa.gov.ph/#0PX9ED
6. PINAS All: https://spacedata.philsa.gov.ph/#P1NAS