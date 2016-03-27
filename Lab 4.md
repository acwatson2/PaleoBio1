## PresAdam Watson
## Lab 4

> As in President?

> 18.5/20

### Part 1
		1) 
		
		````R
		apply(PresencePBDB,1,sum)
		Miocene = 602, Early Jurassic = 169, Late Cretaceous = 375, Pennsylvanian = 133
    ````

		2) ````length(apply(PresencePBDB,1,sum))```` This returns 29.

		3) ````> PresencePBDB[,"Mytilus"]```` 
                          
    This returns the epochs:
		
		4) Because the epochs with no data come later in the Geologic history than samples from epochs that have records such as the Pridoli, which predates the Pennsylvanian.
		
### Part 2
		1)  
		````R
		VecMiocene <- PresencePBDB["Miocene",]
                        > VecPleistocene <- PresencePBDB["Pleistocene",]
                        > Results <- VecMiocene + VecPleistocene
                        > table(Results)
                        > Results
                               0   1   2 
                           287 106 510 	
                        > 510/(106+510) =.8279221
      ````
            	
    2) By turning it into a distance index or 1 - .8279221 = 0.17207792
		
		3) 
		````R
		> vegdist(PresencePBDB, method="jaccard", binary=FALSE, diag=FALSE, upper=FALSE,na.rm = FALSE) 
		    0.17207792
		````
		
		4) 
		````R
		> VecPleistocene <- PresencePBDB["Pleistocene",]
		    > VecPliocene <- PresencePBDB["Pliocene",]	 
		    > VecMiocene <- PresencePBDB["Miocene",]
		    > VecOligocene <- PresencePBDB["Oligocene",]
	    	> VecEocene <- PresencePBDB["Eocene",]
		    > VecPaleocene <- PresencePBDB["Eocene",]
		    > MyData <- rbind(VecPleistocene,VecPliocene,VecMiocene,VecOligocene,VecEocene,VecPaleocene) 		    
		    > Result <- vegdist(MyData, method="jaccard", binary=FALSE, diag=FALSE, upper=FALSE,na.rm = FALSE)
		    > Result 
		    >              VecPleistocene VecPliocene VecMiocene VecOligocene  VecEocene
                VecPliocene      0.12692967                                               
               VecMiocene       0.17207792  0.08496732                                   
              VecOligocene     0.26910299  0.18968386 0.16065574                        
               VecEocene        0.21870048  0.13397129 0.08585056   0.19063005           
             VecPaleocene     0.21870048  0.13397129 0.08585056   0.19063005 0.0000000
    ````
    
  > You didn't answer the question! -0.5 Points

	### Part 3
	
	1) ````> RandomEpochs <- rbind(PresencePBDB["Pliocene",],PresencePBDB["Oligocene",],PresencePBDB["Paleocene",],PresencePBDB["Early Cretaceous",],PresencePBDB["Late Jurassic",],PresencePBDB["Middle Jurassic",])````
	
	2) 
	````R
	Data3.1 <- vegdist(RandomEpochs, method="jaccard", binary=FALSE, diag=FALSE, upper=FALSE,na.rm = FALSE)
		      
		1              2                3                 4                 5
               2 0.1896839                                        
               3 0.3791469 0.4104235                              
               4 0.7462908 0.7480315 0.6400742                    
               5 0.8652695 0.8653846 0.7902622 0.4703947          
               6 0.8852459 0.8814103 0.7931689 0.4883721 0.2962963
	````
	
	3) One and six are the most dissimilar and the order of the gradient is 1,2 3, 4 5,6. 
	
	> But which is 1, 2, 3, 4, 5, and 6!? -0.25 Points
	
	4)
		5) An Asteroid hit the earth. 

	### Part 4 
		
	1) > Ordovician <- downloadPBDB(Taxa=c("Animalia"),StartInterval="Ordovician",StopInterval="Ordovician")
	2) > Ordovician <- cleanGenus(Ordovician)
 	3) > OrdoMatrix <-presenceMatrix(Ordovician,SampleDefinition="geoplate")
	   > OrdoMatrix <-cullMatrix(OrdoMatrix,minOccurrences=2,minDiversity=25)
	
	4) > OrdoDCA<-decorana(OrdoMatrix)
	   > plot(OrdoDCA,display="sites")
	   They do not relate to lat and longitude. I know based on the mean found for lat/lng vs geoplate. 
	   > tapply(Ordovician[,"paleolat"],Ordovician[,"geoplate"],mean)
	   > tapply(Ordovician[,"paleolng”],Ordovician[,"geoplate"],mean)

  > Kind of a disappointingly sparse answer. -0.75 Points
