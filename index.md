# Nathan Walker's Digital Portfolio

---
<p>Hello, thank you for taking the time to investigate my portfolio! My name is Nathan Walker, and I am a Geography and Economics student at University of Wisconsin - Eau Claire.  <p>

![FormalPic](https://user-images.githubusercontent.com/80425389/111332499-d9331f80-863f-11eb-8706-030325e15cb2.jpg =250x250)

I am very passionate about the role of geography in human society today, and how space affects the every day lives of Americans and the surrounding environment. This may be demographic differences, urban planning, environmental conservation, or any other way we can improve the lives of citizens through policy and economics.  I pride myself on learning new techniques quickly and would like to develop an arsenal of skills to approach different problems. This may be working with Python or R to script and run statistical tests, using GIS software to visualize and create striking maps, or running analysis in Eviews.
  
## Map Projects
### Time Series Analysis
![Bay_Area_Time_Series](https://user-images.githubusercontent.com/80425389/110703101-f8056200-81b8-11eb-994c-15cb275478e1.jpg)
---
### Raster Interpolation
![Chesapeake_Bay](https://user-images.githubusercontent.com/80425389/110703102-f89df880-81b8-11eb-96e5-65a01d57188e.jpg)
---
### Cluster Analysis
![Crashes](https://user-images.githubusercontent.com/80425389/110703103-f89df880-81b8-11eb-9eb7-757eea63c650.jpg)
---
### Divy Bikes in Chicago Popularity Tessellation
![Divy_Bike_Map](https://user-images.githubusercontent.com/80425389/110703105-f9368f00-81b8-11eb-9967-875f7b21dfc7.jpg)
---
### R Data Preparation then QGIS Visualization
```
library(tigris)
library(sf)
library(readr)
library(dplyr)
library(here)
library(haffutils)
library(e1071)
install.packages("here")
## retrieve geometry for tracts
dane.tracts <- tracts(state = "55", county = "025")

## retrieve tabular data from web source
df <- read_csv("https://gitlab.com/mhaffner/data/-/raw/master/dane-data.csv")

## create several new columns
## column for z-scores for 2011 foreclosures
df$z11 <- (df$FRCLS_11 - mean(df$FRCLS_11)) / sd_pop(df$FRCLS_11)

## column for z-scores for 2012 foreclosures
df$z12  <- (df$FRCLS_12 - mean(df$FRCLS_12)) / sd_pop(df$FRCLS_12)

## column for change in number of foreclosures from 2011 to 2012
df$change <- df$FRCLS_12 - df$FRCLS_11

## column for z-scores for change in foreclosures from 2011 to 2012
df$zchange <- (df$change - mean(df$change)) / sd_pop(df$change)

## merge data
dane.data <- merge(dane.tracts, df, by = "GEOID")

## write data as a shapefile
st_write(dane.data, "C:/Users/supah/Documents/GEOG370/data/danedata.shp", delete_layer = TRUE)

#histogram of 2011 z-scores
hist(df$z11, col = "Lavender", main = "Histogram of 2011 Foreclosure Z-scores", xlab = "2011 Foreclosure Z-scores")
skewness(df$z11)
kurtosis(df$z11)

#histogram of 2012 z-scores
hist(df$z12, col = "darkseagreen2", main = "Histogram of 2012 Foreclosure Z-scores", xlab = "2012 Foreclosure Z-scores")
skewness(df$z12)
kurtosis(df$z12)

#histogram of change, along with some summarative statistics
hist(df$zchange, col = "darkslategray4", main = "Histogram of Change in Z-scores from 2011-2012", xlab = "Change in Z-score")
skewness(df$zchange)
kurtosis(df$zchange)
qnorm(.10, lower.tail = FALSE)
sd_pop(df$FRCLS_12)
mean(df$FRCLS_12)
```
![ForeclosureMap2](https://user-images.githubusercontent.com/80425389/111321310-cfa4ba00-8635-11eb-83ba-b592613c8814.png)
---
## Adobe Illustrator Maps  
![Africa_Coffee_Map1024_1](https://user-images.githubusercontent.com/80425389/111325821-10063700-863a-11eb-9b23-5ee749dee4f3.jpg)
---
## Research Papers  
### Hobbit or “Kiwi:” Lord of the Rings Tourism, Sustainability, and National Identity
[Tourism_Hobbit_Or_Kiwi.pdf](https://github.com/natewalk22/portfoliobasis/files/6119067/Tourism_Hobbit_Or_Kiwi.pdf)  
### Vietnam National Instagram Content Analysis
[Vietnam_Instagram_Analysis.pdf](https://github.com/natewalk22/portfoliobasis/files/6119068/Vietnam_Instagram_Analysis.pdf)

