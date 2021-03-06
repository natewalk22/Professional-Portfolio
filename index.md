# Nathan Walker's Digital Portfolio

## About
<p>Hello, thank you for taking the time to investigate my portfolio! My name is Nathan Walker, and I am a Geography and Economics student at University of Wisconsin - Eau Claire.  </p>  

![FormalPic_50](FormalPic_1_25.jpg)

<p>I am passionate about the role of data analysis in human society today, and how space and economics affect the every day lives of the everyday person. This may be demographic differences, urban planning, environmental conservation, fiscal policy, or any other way we can improve the lives of citizens through policy and analysis.  I pride myself on learning new techniques quickly and would like to develop an arsenal of skills to approach different problems. This may be working with Python or R to script and run statistical tests, using GIS software to visualize and create maps, or tackling economic issues and disparities.  
</p>
  
---
**Email**: walkernj9595@uwec.edu <br>
**LinkedIn**: https://www.linkedin.com/in/nathan-walker-bb22301bb/


---
  
# Projects
## Maps
### Time Series Analysis
![Bay_Area_Time_Series](Bay_Area_Time_Series.jpg)
---
### Raster Interpolation
![Chesapeake_Bay](Chesapeake_Bay.jpg)
---
### Cluster Analysis
![Crashes](Crashes.jpg)
---
### Divy Bikes in Chicago Popularity Tessellation
![Divy_Bike_Map](Divy_Bike_Map.jpg)
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
![ForeclosureMap2](ForeclosureMap2.png)
---
## Adobe Illustrator Maps  
![Africa_Coffee_Map1024_1](Africa_Coffee_Map1024_1.jpg)
---
## Research Papers  
### Hobbit or ???Kiwi:??? Lord of the Rings Tourism, Sustainability, and National Identity
[Tourism_Hobbit_Or_Kiwi.pdf](Tourism_Hobbit_Or_Kiwi.pdf)  
### Vietnam National Instagram Content Analysis
[Vietnam_Instagram_Analysis.pdf](Vietnam_Instagram_Analysis.pdf)
## Posters
![188_Final_Poster](188_Final_Poster.png)  
## Tutorials  
[GeodatabaseTutorial.pdf](GeodatabaseTutorial.pdf)

