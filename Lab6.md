Adam Watson
Lab 6

> 20/20

## Part 1

	1) > dim(DataPBDB[1])-dim(MacroPBDB[1])
                 [1] 25153     0
	2) The data in macrostrat only contains samples of North America vs. the 
	       Paleobiology database.

## Part 2
	1) > OrderTable <- sort(specnumber(OrderMatrix))
	   > length(OrderTable)
	   [1] 157
	   > OrderTable[147:157]
             Harkless Fm       Forteau Fm     Parker Slate   Snowy Range Fm      Weymouth Fm      Langston Fm    Wheeler Shale Marjum Limestone       Stephen Fm       Kinzers Fm       Chancellor 
                      14               14               16               16               16               17               18               19               23               24               27
	   > Temp <- OrderTable[147:157]
	   > CandidateUnits <- names(Temp)
	  [1] "Harkless Fm"   "Forteau Fm"   "Parker Slate"   "Snowy Range Fm"   "Weymouth Fm"   "Langston Fm"   "Wheeler Shale"   "Marjum Limestone"   "Stephen Fm"    "Kinzers Fm"    "Chancellor"

	2) > GenusFrequencies <- sort(apply(GenusMatrix,2,sum))
	3) > barplot(table(GenusFrequencies))	
	4) Biological inequality
	5) > RareGenera <- GenusFrequencies[which(GenusFrequencies <= median(GenusFrequencies))]

## Part 3
	1) Temp was previously created in part 2 question 1 
	   > CandidateMatrix <- GenusMatrix[names(Temp),]
	2) > PercentShared 
           Harkless Fm       Forteau Fm     Parker Slate   Snowy Range Fm      Weymouth Fm      Langston Fm    Wheeler Shale Marjum Limestone       Stephen Fm       Kinzers Fm       Chancellor 
             0.4137931        0.5652174        0.2812500        0.1951220        0.6764706        0.1632653        0.2307692        0.3559322        0.3055556        0.2586207        0.5714286 
	   
	   The Harkless Fm, Forteau Fm, and the Chancellor are most likely to be Lagerstätten. They all share, save for the Harmless Fm, over 50 percent of species making them good
	   good candidates for Lagerstätten.

	3) The Chancellor group which is during the Cambrian. It is significant because of the explosion of life that occurred at this time and gives a good record of the beginnings of life. 
