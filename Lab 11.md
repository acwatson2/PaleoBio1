Adam Watson
Lab 11

> 16/20

## Part 1
1) `> TriassicUnits <-` 

> ??? -1 Points

2) 

````R
> length(TriassicUnits[,"unit_id"])
      [1] 838
````

3) `> TriassicUnits[1:10,]` With the exception of two metamorphic units the first ten units are igneous. 

4) t_age  is the age relative to the top of the unit and b_age is the age relative to the bottom of the strat unit. 

5) Most units range through the Triassic with the exception of few units that appear at the end of the Triassic and range into the mid cretaceous. 

## Part 2
1) `> TriassicUnits <- read.csv("https://macrostrat.org/api/units?lith_class=sedimentary&interval_name=Triassic&format=csv")`

2) `> AgeRestriction <- subset(TriassicUnits,TriassicUnits[,"t_age"]>=201 & TriassicUnits[,"b_age"]<=252)`

3) 

````R
  > PaleoMesoZoic <- read.csv("https://macrostrat.org/api/units?
     interval_name=Mesozoic&Paleozoic&format=csv")
   > Ordovician <- subset(PaleoMesoZoic,PaleoMesoZoic[,"t_age"]>=444 &
     PaleoMesoZoic[,"t_age"]<=485)
   > Silurian <- subset(PaleoMesoZoic,PaleoMesoZoic[,"t_age"]>=419 & 
     PaleoMesoZoic[,"b_age"]<=444)
   > Devonian <- subset(PaleoMesoZoic,PaleoMesoZoic[,"t_age"]>=359 &
     PaleoMesoZoic[,"b_age"]<=419)
   > Carboniferous <- subset(PaleoMesoZoic,PaleoMesoZoic[,"t_age"]>=299 &
     PaleoMesoZoic[,"b_age"]<=359)
   > Permian <- subset(PaleoMesoZoic,PaleoMesoZoic[,"t_age"]>=252 &
     PaleoMesoZoic[,"b_age"]<=299)
   > Triassic <- subset(PaleoMesoZoic,PaleoMesoZoic[,"t_age"]>=201 &
     PaleoMesoZoic[,"b_age"]<=252)
   > Jurassic <- subset(PaleoMesoZoic,PaleoMesoZoic[,"t_age"]>=145 &
     PaleoMesoZoic[,"b_age"]<=201)
   > Cretaceous <- subset(PaleoMesoZoic,PaleoMesoZoic[,"t_age"]>=66 &
     PaleoMesoZoic[,"b_age"]<=145)
````

4) 

````R
   > MyFreq <- c(length(Ordovician[,"unit_id"]),length(Silurian[,"unit_id"]),length(Devonian[,"unit_id"]),length(Carboniferous[,"unit_id"]),length(Permian[,"unit_id"]),length(Triassic[,"unit_id"]),length(Jurassic[,"unit_id"]),length(Cretaceous[,"unit_id"]))
   > MyFreq
    [1] 2072 1255 2037 3031  937  587 1091 4851
````

5) 
````R
  > Maths <- MyFreq[-3]
   > sd(Maths)
    [1] 1383.06
   > mean(Maths)
    [1] 2182
   > (mean(Maths)-MyFreq[6])/sd(Maths)
    [1] 1.15324
````

6) No, it’s less than 2 standard deviations and not significant. 

7) 

> No answer, -1 Points

## Part 3
1) 

````R
   > URL<-"https://macrostrat.org/api/columns?format=geojson_bare&project_id=1"
   > GotURL<-getURL(URL)
   > NAMap<-readOGR(GotURL,"OGRGeoJSON",verbose=FALSE)
   > plot(NAMap)
````

2) 
````R
   > URL2<-"https://macrostrat.org/api/columns?format=geojson_bare&interval_name=Induan&Anisian&lith_class=sedimentary&project_id=1"
   > GotURL2<-getURL(URL2)
   > NAMap2<-readOGR(GotURL2,"OGRGeoJSON",verbose=FALSE)
   > plot(NAMap2,col="#B7197E",add=TRUE)
````

3) 
````R
   > DataPBDB<-downloadPBDB(Taxa=c("Animalia"),StartInterval="Induan",StopInterval="Anisian")
   > points(DataPBDB[,"lng"],DataPBDB[,"lat"])
````

4) 
````R
   > quartz(“Question 4”)
   > URLQuestion4 <-"https://macrostrat.org/api/columns?
format=geojson_bare&interval_name=Lopingian&lith_class=sedimentary&project_id=1"
   > GotURL4<-getURL(URLQuestion4)
   > NAMapQuest4<-readOGR(GotURL4,"OGRGeoJSON",verbose=FALSE)
   > plot(NAMap)
   > plot(NAMapQuest4,col="#FF4C4C",add=TRUE)
````

5) 

````R
   > DataPBDB2<-downloadPBDB(Taxa=c("Animalia"),StartInterval="Lopingian",StopInterval="Lopingian")
   > points(DataPBDB2[,"lng"],DataPBDB[,"lat"])
````

6) 

> -2 Points
