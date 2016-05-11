Adam Watson
Lab 12

> You are missing part 2. 10/20

## Part 1

1) 
````R 
   > TriassicSynapsids <- downloadPBDB(Taxa=c("Synapsida"),StartInterval="Anisian",StopInterval="Rhaetian")
   > JurassicSynapsids <-downloadPBDB(Taxa=c("Synapsida"),StartInterval="Hettangian",StopInterval="Tithonian")
   > TriassicDiapsids <- downloadPBDB(Taxa=c("Diapsida"),StartInterval="Anisian",StopInterval="Rhaetian")
   > JurassicDiapsids <- downloadPBDB(Taxa=c("Diapsida"),StartInterval="Hettangian",StopInterval="Tithonian")
````

2) 
````R   
   > TDiapGenus <- cleanRank(TriassicDiapsids, "genus")
   > TSynGenus <- cleanRank(TriassicSynapsids, "genus")
   > TDiapLength <- length(unique(TDiapGenus[,"genus"]))
   [1] 389
   > TSynLength <- length(unique(TSynGenus[,"genus"]))
   [1] 116
````

3) 
````R
   > JSynGenus <- cleanRank(JurassicSynapsids, "genus")
   > JDiapGenus <- cleanRank(JurassicDiapsids, "genus")
   > DiapSurvivors<-intersect(TDiapGenus[,”genus”],unique(JDiapGenus[,"genus"]))
   > length(DiapSurvivors)
    [1] 33
   > DiapVictims<-setdiff(TDiapGenus[,"genus"],unique(JDiapGenus[,"genus"]))
   > Jlength(DiapVictims) 
    [1] 355
   > SynSurvivors<-intersect(TSynGenus[,"genus"],unique(JSynGenus[,"genus"]))
   > length(SynSurvivors)
    [1] 8
   > SynVictims<-setdiff(TSynGenus[,"genus"],unique(JSynGenus[,"genus"]))
   > length(SynVictims)
    [1] 108
````

4) 
````R
   > TDiapLength <- length(unique(TDiapGenus[,"genus"]))
   > TSynLength <- length(unique(TSynGenus[,"genus"]))
   > JSynLength <- length(unique(JSynGenus[,"genus"]))
   > JDiapLength <- length(unique(JDiapGenus[,"genus"]))
   > SynOdds<- (length(SynSurvivors)/(JSynLength+TSynLength)) / (length(SynVictims)/(TSynLength+JSynLength))
   > DiapOdds<- (length(DiapSurvivors)/(JDiapLength+TDiapLength)) / (length(DiapVictims)/(TDiapLength+JDiapLength))
   > OddsRatio <- DiapOdds/SynOdds
   [1] 1.25493
   > log(OddsRatio)
   [1] 0.2270795
````

5) 
````R
   > StandardError<-sqrt(1/length(DiapSurvivors) + 1/length(DiapVictims) + 1/length(SynSurvivors) + 1/length(SynVictims))
   > UpperLimit<-log(OddsRatio) + (StandardError*1.96)
   [1] 1.028955
   > LowerLimit<-log(OddsRatio) - (StandardError*1.96)
   [1] -0.5747958
````

Not significant


> copy pasting your R workflow is not an acceptable format for answering questions. 

Work-Flow


R version 3.2.4 (2016-03-10) -- "Very Secure Dishes"
Copyright (C) 2016 The R Foundation for Statistical Computing
Platform: x86_64-apple-darwin13.4.0 (64-bit)

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.

  Natural language support but running in an English locale

R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.

[R.app GUI 1.67 (7152) x86_64-apple-darwin13.4.0]

[History restored from /Users/patron/.Rapp.history]

> source("https://raw.githubusercontent.com/aazaff/paleobiologyDatabase.R/master/communityMatrix.R")
Loading required package: RCurl
Loading required package: bitops
Loading required package: rgdal
Loading required package: sp
rgdal: version: 1.0-4, (SVN revision 548)
 Geospatial Data Abstraction Library extensions to R successfully loaded
 Loaded GDAL runtime: GDAL 1.11.2, released 2015/02/10
 Path to GDAL shared files: /Library/Frameworks/R.framework/Versions/3.2/Resources/library/rgdal/gdal
 Loaded PROJ.4 runtime: Rel. 4.9.1, 04 March 2015, [PJ_VERSION: 491]
 Path to PROJ.4 shared files: /Library/Frameworks/R.framework/Versions/3.2/Resources/library/rgdal/proj
 Linking to sp version: 1.1-1 
> 
> Lopingian<-downloadPBDB("Brachiopoda","Lopingian","Lopingian")
> 
> PostPermian<-downloadPBDB("Brachiopoda","Triassic","Neogene")
> Lopingian<-cleanRank(Lopingian,"genus")
> 
> PostPermian<-cleanRank(PostPermian,"genus")
> TropicalOccs<-subset(Lopingian,Lopingian[,"paleolat"] >= -23.5 & Lopingian[,"paleolat"] <= 23.5)
> ExtraTropicalOccs<-subset(Lopingian,Lopingian[,"paleolat"] <= -23.5 | Lopingian[,"paleolat"] >= 23.5)
> TropicalGeneraOccs<-subset(TropicalOccs,TropicalOccs[,"genus"]%in%ExtraTropicalOccs[,"genus"]!=TRUE)
> ExtraTropicalGeneraOccs<-subset(ExtraTropicalOccs,ExtraTropicalOccs[,"genus"]%in%TropicalOccs[,"genus"]!=TRUE)
> TropicalGenera<-unique(TropicalGeneraOccs[,"genus"])
> ExtraGenera<-unique(ExtraTropicalGeneraOccs[,"genus"])
> 
> TropicalSurvivors<-intersect(TropicalGenera,unique(PostPermian[,"genus"]))
> TropicalVictims<-setdiff(TropicalGenera,unique(PostPermian[,"genus"]))
> ExtraSurvivors<-intersect(ExtraGenera,unique(PostPermian[,"genus"]))
> ExtraVictims<-setdiff(ExtraGenera,unique(PostPermian[,"genus"]))
> TropicalOdds<- (length(TropicalSurvivors)/length(TropicalGenera)) / (length(TropicalVictims)/length(TropicalGenera))
> ExtraOdds<- (length(ExtraSurvivors)/length(ExtraGenera)) / (length(ExtraVictims)/length(ExtraGenera))
> OddsRatio<- TropicalOdds / ExtraOdds
> OddsRatio
[1] 1.722222
> log(OddsRatio)
[1] 0.5436154
> StandardError<-sqrt(1/length(TropicalSurvivors) + 1/length(TropicalVictims) + 1/length(ExtraSurvivors) + 1/length(ExtraVictims))
> StandardError
[1] 0.4461437
> 
> UpperLimit<-log(OddsRatio) + (StandardError*1.96)
> UpperLimit
[1] 1.418057
> LowerLimit<-log(OddsRatio) - (StandardError*1.96)
> LowerLimit
[1] -0.3308262
> Synapsids <- downloadPBDB(Taxa=c("Synapsida"),StartInterval="Anisian",StopInterval="Rhaetian")
> Diapsids <- downloadPBDB(Taxa=c("Diapsida"),StartInterval="Anisian",StopInterval="Rhaetian")
> DiapGenus <- cleanRank(Diapsids, "genus")
> SynGenus <- cleanRank(Synapsids, "genus")
> length(unique(DiapGenus[,"genus"]))
[1] 389
> length(unique(SynGenus[,"genus"]))
[1] 116
> JurassicSynapsids <- downloadPBDB(Taxa=c("Synapsida"),StartInterval="Hettangian”,StopInterval=“Tithonian”)
+ 
> JurassicSynapsids <- downloadPBDB(Taxa=c("Synapsida"),StartInterval="Hettangian”,StopInterval=“Tithonian”)
+ 
> JurassicSynapsids <-downloadPBDB(Taxa=c("Synapsida"),StartInterval="Hettangian”,StopInterval=“Tithonian")
> JurassicDiapsids <-downloadPBDB(Taxa=c("Diapsida"),StartInterval="Hettangian",StopInterval="Tithonian")
> JDiapGenus <- cleanRank(JurassicDiapsids, "genus")
> JSynGenus <- cleanRank(Synapsids, "genus")
> TDiapGenus <- cleanRank(Diapsids, "genus")
> 
> TSynGenus <- cleanRank(Synapsids, "genus")
> DiapSurvivorintersect(TdiapGenus,unique(JdiapGenus[,"genus"]))
Error: could not find function "DiapSurvivorintersect"
> DiapSurvivor <- intersect(TdiapGenus,unique(JdiapGenus[,"genus"]))
Error in unique(JdiapGenus[, "genus"]) : object 'JdiapGenus' not found
> DiapSurvivor <- intersect(TdiapGenus,unique(JDiapGenus[,"genus"]))
Error in as.vector(x) : object 'TdiapGenus' not found
> DiapSurvivor <- intersect(TDiapGenus,unique(JDiapGenus[,"genus"]))
> head(DiapSurvivor)
character(0)
> DiapSurvivor
character(0)
> length(DiapSurvivor)
[1] 0
> SynSurvivor <- intersect(TSynGenus,unique(JSynGenus[,"genus"]))
> SynSurvivor
character(0)
> head(TSynGenus)
   occurrence_no record_type reid_no flags collection_no
1         149619         occ      NA    NA         13220
2         149837         occ      NA    NA         13266
4         149868         occ   24304    NA         13271
7         256438         occ      NA    NA         24877
8         256439         occ      NA    NA         24877
10        272315         occ      NA    NA         26092
                          identified_name identified_rank identified_no
1  Therioherpeton n. gen. cargnini n. sp.         species         95407
2  Adelobasileus n. gen. cromptoni n. sp.         species         53176
4                 Massetognathus teruggii         species         80894
7                      Ischigualastia sp.           genus         39029
8                         Exaeretodon sp.           genus         39200
10              Dinodontosaurus platiceps         species         39026
              difference           accepted_name accepted_rank accepted_no
1                        Therioherpeton cargnini       species       95407
2                        Adelobasileus cromptoni       species       53176
4  subjective synonym of Massetognathus pascuali       species       80893
7                                 Ischigualastia         genus       39029
8                                    Exaeretodon         genus       39200
10   species not entered         Dinodontosaurus         genus       39026
   early_interval late_interval max_ma min_ma reference_no        lng       lat
1         Carnian        Norian    237  208.5         4389  -53.79139 -29.70194
2          Norian                  228  208.5         3846 -101.16389  33.43389
4        Ladinian                  242  237.0        13754  -67.82056 -29.82306
7         Carnian                  237  228.0         6971  -68.90500 -31.10111
8         Carnian                  237  228.0         6971  -68.90500 -31.10111
10       Ladinian                  242  237.0         7234  -67.77972 -29.85055
   paleomodel paleolng paleolat geoplate   phylum        class        order
1      gp_mid    -9.00   -38.72      201 Chordata Osteichthyes Cotylosauria
2      gp_mid   -35.98    10.17      101 Chordata Osteichthyes Cotylosauria
4      gp_mid   -27.03   -33.78      291 Chordata Osteichthyes Cotylosauria
7      gp_mid   -27.45   -37.31      291 Chordata Osteichthyes Cotylosauria
8      gp_mid   -27.45   -37.31      291 Chordata Osteichthyes Cotylosauria
10     gp_mid   -35.55   -38.17      201 Chordata Osteichthyes Cotylosauria
             family           genus
1  Therioherpetidae  Therioherpeton
2                     Adelobasileus
4  Traversodontidae  Massetognathus
7   Stahleckeriidae  Ischigualastia
8  Traversodontidae     Exaeretodon
10  Stahleckeriidae Dinodontosaurus
> head(JSynGenus)
   occurrence_no record_type reid_no flags collection_no
1         149619         occ      NA    NA         13220
2         149837         occ      NA    NA         13266
4         149868         occ   24304    NA         13271
7         256438         occ      NA    NA         24877
8         256439         occ      NA    NA         24877
10        272315         occ      NA    NA         26092
                          identified_name identified_rank identified_no
1  Therioherpeton n. gen. cargnini n. sp.         species         95407
2  Adelobasileus n. gen. cromptoni n. sp.         species         53176
4                 Massetognathus teruggii         species         80894
7                      Ischigualastia sp.           genus         39029
8                         Exaeretodon sp.           genus         39200
10              Dinodontosaurus platiceps         species         39026
              difference           accepted_name accepted_rank accepted_no
1                        Therioherpeton cargnini       species       95407
2                        Adelobasileus cromptoni       species       53176
4  subjective synonym of Massetognathus pascuali       species       80893
7                                 Ischigualastia         genus       39029
8                                    Exaeretodon         genus       39200
10   species not entered         Dinodontosaurus         genus       39026
   early_interval late_interval max_ma min_ma reference_no        lng       lat
1         Carnian        Norian    237  208.5         4389  -53.79139 -29.70194
2          Norian                  228  208.5         3846 -101.16389  33.43389
4        Ladinian                  242  237.0        13754  -67.82056 -29.82306
7         Carnian                  237  228.0         6971  -68.90500 -31.10111
8         Carnian                  237  228.0         6971  -68.90500 -31.10111
10       Ladinian                  242  237.0         7234  -67.77972 -29.85055
   paleomodel paleolng paleolat geoplate   phylum        class        order
1      gp_mid    -9.00   -38.72      201 Chordata Osteichthyes Cotylosauria
2      gp_mid   -35.98    10.17      101 Chordata Osteichthyes Cotylosauria
4      gp_mid   -27.03   -33.78      291 Chordata Osteichthyes Cotylosauria
7      gp_mid   -27.45   -37.31      291 Chordata Osteichthyes Cotylosauria
8      gp_mid   -27.45   -37.31      291 Chordata Osteichthyes Cotylosauria
10     gp_mid   -35.55   -38.17      201 Chordata Osteichthyes Cotylosauria
             family           genus
1  Therioherpetidae  Therioherpeton
2                     Adelobasileus
4  Traversodontidae  Massetognathus
7   Stahleckeriidae  Ischigualastia
8  Traversodontidae     Exaeretodon
10  Stahleckeriidae Dinodontosaurus
> TDiapGenus <- cleanRank(TriassicDiapsids, "genus")
Error in subset(DataPBDB, DataPBDB[, Rank] != "") : 
  object 'TriassicDiapsids' not found
> TriassicSynapsids <- downloadPBDB(Taxa=c("Synapsida"),StartInterval="Anisian",StopInterval="Rhaetian")
>  JurassicSynapsids <- downloadPBDB(Taxa=c("Synapsida"),StartInterval="Hettangian”,StopInterval=“Tithonian”)
+ 
>  JurassicSynapsids <-downloadPBDB(Taxa=c("Synapsida"),StartInterval="Hettangian”,StopInterval=“Tithonian”)
+ 
>  JurassicSynapsids <-downloadPBDB(Taxa=c("Synapsida"),StartInterval="Hettangian”,StopInterval=“Tithonian”)
+ 
> JurassicSynapsids<-downloadPBDB(Taxa=c("Synapsida"),StartInterval="Hettangian”,StopInterval=“Tithonian")
> TriassicDiapsids <- downloadPBDB(Taxa=c("Diapsida"),StartInterval="Anisian",StopInterval="Rhaetian")
> JurassicDiapsids <- downloadPBDB(Taxa=c("Diapsida"),StartInterval="Hettangian",StopInterval="Tithonian")
> TDiapGenus <- cleanRank(TriassicDiapsids, "genus")
> TSynGenus <- cleanRank(JurassicSynapsids, "genus")
Error in `[.data.frame`(DataPBDB, , Rank) : undefined columns selected
> TSynGenus <- cleanRank(TriassicSynapsids, "genus")
> JDiapGenus <- cleanRank(JurassicDiapsids, "genus")
> JSynGenus <- cleanRank(JurassicSynapsids, "genus")
Error in `[.data.frame`(DataPBDB, , Rank) : undefined columns selected
> JSynGenus <- cleanRank(JurassicSynapsids, "genus")
Error in `[.data.frame`(DataPBDB, , Rank) : undefined columns selected
> JurassicSynapsids<-downloadPBDB(Taxa=c("Synapsida"),StartInterval="Hettangian”,StopInterval=“Tithonian")
> JSynGenus <- cleanRank(JurassicSynapsids, "genus")
Error in `[.data.frame`(DataPBDB, , Rank) : undefined columns selected
> head(JurassicSynapsids)
                                   X.html..head..title.400.Bad.Request..title...head.
1                                                      <body><h1>400 Bad Request</h1>
2                                                                                <ul>
3 <li>Unknown interval 'Hettangian”'; Unknown interval 'StopInterval=“Tithonian'</li>
4                                                                               </ul>
5                                                                      </body></html>
> length(unique(TDiapGenus[,"genus"]))
[1] 389
> JurassicSynapsids<-downloadPBDB(Taxa=c("Synapsida"),StartInterval="Jurassic”,StopInterval=“Jurassic")
> head(JurassicSynapsids)
                                X.html..head..title.400.Bad.Request..title...head.
1                                                   <body><h1>400 Bad Request</h1>
2                                                                             <ul>
3 <li>Unknown interval 'Jurassic”'; Unknown interval 'StopInterval=“Jurassic'</li>
4                                                                            </ul>
5                                                                   </body></html>
> length(unique(TSynGenus[,"genus"]))
[1] 116
> head(TSynGenus)
   occurrence_no record_type reid_no flags collection_no
1         149619         occ      NA    NA         13220
2         149837         occ      NA    NA         13266
4         149868         occ   24304    NA         13271
7         256438         occ      NA    NA         24877
8         256439         occ      NA    NA         24877
10        272315         occ      NA    NA         26092
                          identified_name identified_rank identified_no
1  Therioherpeton n. gen. cargnini n. sp.         species         95407
2  Adelobasileus n. gen. cromptoni n. sp.         species         53176
4                 Massetognathus teruggii         species         80894
7                      Ischigualastia sp.           genus         39029
8                         Exaeretodon sp.           genus         39200
10              Dinodontosaurus platiceps         species         39026
              difference           accepted_name accepted_rank accepted_no
1                        Therioherpeton cargnini       species       95407
2                        Adelobasileus cromptoni       species       53176
4  subjective synonym of Massetognathus pascuali       species       80893
7                                 Ischigualastia         genus       39029
8                                    Exaeretodon         genus       39200
10   species not entered         Dinodontosaurus         genus       39026
   early_interval late_interval max_ma min_ma reference_no        lng       lat
1         Carnian        Norian    237  208.5         4389  -53.79139 -29.70194
2          Norian                  228  208.5         3846 -101.16389  33.43389
4        Ladinian                  242  237.0        13754  -67.82056 -29.82306
7         Carnian                  237  228.0         6971  -68.90500 -31.10111
8         Carnian                  237  228.0         6971  -68.90500 -31.10111
10       Ladinian                  242  237.0         7234  -67.77972 -29.85055
   paleomodel paleolng paleolat geoplate   phylum        class        order
1      gp_mid    -9.00   -38.72      201 Chordata Osteichthyes Cotylosauria
2      gp_mid   -35.98    10.17      101 Chordata Osteichthyes Cotylosauria
4      gp_mid   -27.03   -33.78      291 Chordata Osteichthyes Cotylosauria
7      gp_mid   -27.45   -37.31      291 Chordata Osteichthyes Cotylosauria
8      gp_mid   -27.45   -37.31      291 Chordata Osteichthyes Cotylosauria
10     gp_mid   -35.55   -38.17      201 Chordata Osteichthyes Cotylosauria
             family           genus
1  Therioherpetidae  Therioherpeton
2                     Adelobasileus
4  Traversodontidae  Massetognathus
7   Stahleckeriidae  Ischigualastia
8  Traversodontidae     Exaeretodon
10  Stahleckeriidae Dinodontosaurus
> JurrasicSynapsids <-downloadPBDB(Taxa=c("Synapsida"),StartInterval="Hettangian",StopInterval="Tithonian")
> head(JurrasicSynapsids)
  occurrence_no record_type reid_no flags collection_no             identified_name
1        138845         occ      NA    NA         11805 Morganucodon oehleri n. sp.
2        161480         occ      NA    NA         14228           Megazostrodon sp.
3        220155         occ      NA    NA         22711             Mammalia indet.
4        220167         occ      NA    NA         22711                 Docodon sp.
5        220168         occ      NA    NA         22711     Multituberculata indet.
6        220233         occ      NA    NA         22729              Tritylodon sp.
  identified_rank identified_no difference        accepted_name accepted_rank
1         species        203398            Morganucodon oehleri       species
2           genus         39752                   Megazostrodon         genus
3           class         36651                        Mammalia         class
4           genus         39775                         Docodon         genus
5           order         39779                Multituberculata         order
6           genus         39217                      Tritylodon         genus
  accepted_no early_interval late_interval max_ma min_ma reference_no        lng
1      203398     Hettangian                201.3  199.3        43837  102.10732
2       39752     Hettangian    Sinemurian  201.3  190.8         6296   27.56667
3       36651   Kimmeridgian     Tithonian  157.3  145.0        15179 -109.20583
4       39775   Kimmeridgian     Tithonian  157.3  145.0        15179 -109.20583
5       39779   Kimmeridgian     Tithonian  157.3  145.0        15179 -109.20583
6       39217     Hettangian    Sinemurian  201.3  190.8         5940   21.51660
        lat paleomodel paleolng paleolat geoplate   phylum        class
1  25.17269     gp_mid   120.20    37.81      611 Chordata Osteichthyes
2 -28.90000     gp_mid    15.57   -42.97      701 Chordata Osteichthyes
3  40.42361     gp_mid   -43.56    27.91      101 Chordata     Mammalia
4  40.42361     gp_mid   -43.56    27.91      101 Chordata     Mammalia
5  40.42361     gp_mid   -43.56    27.91      101 Chordata     Mammalia
6 -31.91660     gp_mid     7.37   -43.87      701 Chordata Osteichthyes
             order          family         genus
1     Cotylosauria                  Morganucodon
2     Cotylosauria                 Megazostrodon
3                                               
4        Docodonta    Docodontidae       Docodon
5 Multituberculata                              
6     Cotylosauria Tritylodontidae    Tritylodon
> JurassicSynapsids <-downloadPBDB(Taxa=c("Synapsida"),StartInterval="Hettangian",StopInterval="Tithonian")
> JDiapGenus <- cleanRank(JurassicDiapsids, "genus")
> JSynGenus <- cleanRank(JurassicSynapsids, "genus")
> SynSurvivor <- intersect(TSynGenus,unique(JSynGenus[,"genus"]))
> Synsurvivor
Error: object 'Synsurvivor' not found
> Synsurvivor
Error: object 'Synsurvivor' not found
> SynSurvivor
character(0)
> 
