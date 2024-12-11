# Biodiversity Intactness Index Maricopa County
Changes in biodiversity in Phoenix, AZ Subdivision

###**Title:** Urbanization and Biodiversity Loss: Analyzing the Impact on Phoenix, AZ (2017-2020)

####**About:**
This repository aims to analyze the impact of urbanization on biodiversity loss in Phoenix, AZ, from 2017 to 2020. Through data analysis and visualization, we aim to identify areas where biodiversity intactness has been most significantly affected

**Repository Structure:**
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

**Data:**
The data used in this analysis includes the io-biodiversity collection from the Microsoft Planetary Computer STAC catalog as well as a shapefile for Phoenix Subdivision from the Census.gov website. The Biodiversity Intactness Index (BII) is a measure of how much of a region's natural biodiversity remains intact despite human pressures. It estimates the average abundance of native species in a given area compared to their abundance in undisturbed conditions. The BII is calculated using data on plants, fungi, and animals from ecological studies conducted worldwide. This Biodiversity data was pulled directly through an API. The shapefile is the only data in the data folder. 
 
**References:**

Phoenix Subdivision Shapefile: U.S. Census Bureau. (2024). Cartographic boundary files - shapefile (Version 2024). Census.gov.Retrieved from https://www.census.gov/geographies/mapping-files/time-series/geo/carto-boundary-file.html

Biodiversity Intactness Index (BII) Time Series: Impact Observatory & Vizzuality. (2024). Biodiversity intactness index (BII) time series (Version 1). Microsoft Planetary Computer STAC catalog. Retrieved from https://planetarycomputer.microsoft.com/api/stac/v1/collections/io-biodiversity
