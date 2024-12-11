# Biodiversity Intactness Index Maricopa County

### **Title:** Urbanization and Biodiversity Loss: Analyzing the Impact on Phoenix, AZ (2017-2020)

#### **About:**
This repository aims to analyze the impact of urbanization on biodiversity loss in Phoenix, AZ, from 2017 to 2020. Through data analysis and visualization, we aim to identify areas where biodiversity intactness has been most significantly affected. In this repository you will find a data folder containing the shapfile for Phoenix Subdivision, a README containing everything you need to know about the repository, a .gitignore showing which objects git is not tracking, and a .ipynb notebook containing my analysis of BII chnage in the Poenix Subdivision.

#### **Repository Structure:**
```
BII_Maricopa_County
│   README.md
│   maricopa_biodiversity.ipynb    
│   .gitignore
|
└───data
    │   tl_2022_04_cousub.cpg
    │   tl_2022_04_cousub.dbf
    |   tl_2022_04_cousub.prj
    |   tl_2022_04_cousub.shp
    |   tl_2022_04_cousub.shp.ea.iso.xml
    |   tl_2022_04_cousub.shp.iso.xml
    |   tl_2022_04_cousub.shx
```

#### **Data & Access:**
The data used in this analysis includes the io-biodiversity collection from the Microsoft Planetary Computer STAC catalog as well as a shapefile for Phoenix Subdivision from the Census.gov website. The shapefile used for this notebook is in the data folder.

The Biodiversity Intactness Index (BII) is a measure of how much of a region's natural biodiversity remains intact despite human pressures. It estimates the average abundance of native species in a given area compared to their abundance in undisturbed conditions. The BII is calculated using data on plants, fungi, and animals from ecological studies conducted worldwide. This Biodiversity data was pulled directly through an API and steps are as follows:

```
# We use the Client function from the pystac_client package to access the catalog:
catalog = Client.open(
    "https://planetarycomputer.microsoft.com/api/stac/v1",
    modifier=planetary_computer.sign_inplace,
)

# Get collections and print their names
collections = list(catalog.get_collections())  # Turn generator into list

print('Number of collections:', len(collections))

print("Collections IDs (first 10):")
for i in range(10):
    print('-', collections[i].id)

# Select io-biodiversity
io_collection = catalog.get_child('io-biodiversity')
io_collection

# Time range and bounding box used
time_range = "2017-01-01/2020-01-01"

# NCEAS bounding box (as a GeoJSON)
bbox = { 
    "type": "Polygon", 
        "coordinates": [
     [
        [-112.826843, 32.974108], 
        [-112.826843, 33.863574],
        [-111.184387, 33.863574], 
        [-111.184387, 32.974108], 
        [-112.826843, 32.974108] 
    ] 
],
}

# Catalog search
search = catalog.search(
    collections = ['io-biodiversity'],
    intersects = bbox,
    datetime = time_range)
search

# Retrieve search items, you should have 4
items = search.item_collection()
len(items)
```
#### **References:**

Phoenix Subdivision Shapefile: U.S. Census Bureau. (2024). Cartographic boundary files - shapefile (Version 2024). Census.gov.Retrieved from https://www.census.gov/geographies/mapping-files/time-series/geo/carto-boundary-file.html

Biodiversity Intactness Index (BII) Time Series: Impact Observatory & Vizzuality. (2024). Biodiversity intactness index (BII) time series (Version 1). Microsoft Planetary Computer STAC catalog. Retrieved from https://planetarycomputer.microsoft.com/api/stac/v1/collections/io-biodiversity

University of California, Santa Barbara. (2024). MEDS EDS 220 course. Retrieved from https://meds-eds-220.github.io/MEDS-eds-220-course/
