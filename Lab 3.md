Adam Watson
Lab 3

> 19/20

## Part 1

1)	There are 704 collections associated with this reference.

2)	2449 is the reference id number.

## Part 1.1
1)	It represents who named the species.

2)	
+ Class: Strophomenata
+ Order: Strophomenida
+ Family: Strophomenidae
+ Genus: Strophomena 
+ Species: Planumbona

3)	Data was collected in the United States and Canada. (Not country, county. Union County Ohio)

> -1 Points

4)	Data is from the Ordovician

5)	Data was found in the Liberty formation.

## Part 2
1)	The colors represent what the age of the stratigraphic record the fossil came from.

2)	The fossil in the Ypresian is only found in the United States, England, and Belgium.

3)	Cincinnati 

4)	The age range for Ambonychia is the Ordovician. 

## Part 2.1

1)	Parallel 

2)	Myalinidia 

## Part 3

1)	https://paleobiodb.org/data1.2/occs/strata.json?datainfo&rowcount&base_name=Ambonychia&strat=Lexington Limestone

2)	https://paleobiodb.org/data1.2/occs/list.csv?datainfo&rowcount&base_name=mammalia&interval=Paleocene,Oligocene

3)	https://paleobiodb.org/data1.2/taxa/opinions.csv?datainfo&rowcount&base_name=Testudines&rank=order&interval=Mesozoic,Mesozoic&op_type=all

4)	https://paleobiodb.org/data1.2/colls/list.csv?datainfo&rowcount&base_name=Aves, Marsupialia, Sirenia&cc=NOA,US

5)	<strike>https://paleobiodb.org/data1.2/occs/list.csv?datainfo&rowcount&base_name=Gastropoda, Ficus&taxon_reso=genus</strike>

> - 1 points. You needed to do Gastropoda:Ficus

## Part 4

1)	Vertiginidae 

> Not in the paleobiology database, but I'll let it slide.

2)	Early Cretaceous, ~Aptian

3)	Paleogene 

4)	Tiktaalik was located in the topics during the late Devonian (Age: Frasnian)

5)	The Namacalathus in Kotodzha and Raiga formations

## Part 5

1)	URL <- https://paleobiodb.org/data1.2/colls/list.csv?base_name=Mammut&interval=Pliocene and then Mammut<-read.csv(URL,row.names=1)	    

2)	Dim(Mammut) 39,12

3)	Collection. Coll

4)	Mammut, Mastodon, Pliocene 

5)	URL<-https://paleobiodb.org/data1.2/colls/list.csv?base_name=Mammut&interval=Miocene,Pleistocene  

6)	URL <- https://paleobiodb.org/data1.2/colls/list.csv?datainfo&rowcount&base_name=mammut&interval=Miocene ,Pleistocene &show=paleoloc

## Part 6

1) DownloadPBDB <- function(Taxon,Time) {
+ URL <- paste("https://paleobiodb.org/data1.2/occs/list.csv?base_name=",Taxon,"&interval=",Time, sep="")
+ GetMyData <-read.csv(URL)
+ print(GetMyData)
+ }

> Great job! Use `return( )` rather than `print( )`.

➢	DownloadPBDB("Abra","Cenozoic")
