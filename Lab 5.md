Adam Watson	
Lab 5

> 9.5/20

Will update this in the next days

> I'm sorry, but you've had over a month :(

## Part 1
1) 

````R
> length(which(BivalveAbundance["Miocene",] != 0)) 
[1] 634
````

2)

````R
> max(BivalveAbundance["Pliocene",])/length(which(BivalveAbundance["Pliocene",] != 0))
[1] 0.7546816
````

> -1 Points
		
3) 

````R
1-sum(BrachiopodAbundance["Late Ordovician",]/length(which(BrachiopodAbundance["Late
                             Ordovician",]>0)))^2
[1] 0.9438304
````

4) 

````R
> GetEntropy <-function(time){
		    + Data <- 1-(sum(BivalveAbundance[time,])/length(which(BivalveAbundance[time,]!=0))^2)*
		    + log((sum(BivalveAbundance[time,])/length(which(BivalveAbundance[time,]!=0))^2))
		    + print(Data)
		    + }
		    > GetEntropy(“Late Cretaceous”)
		    [1] 1.21729  Why is this not working?????
````

> -1 Points, Compare to this version.

````R
N <- sum(BivalveAbundance["Late Cretaceous",])
n <- BivalveAbundance["Late Cretaceous",]
n <- n[which(n!=0)]
-sum((n/N)*log(n/N))
````
		    
5) > GetEntropy(“Paleocene)
		    [1] 1.141343     Why is this not working???????

> -1 Points
	
6) > ~6%.  An asteroid hit the earth

> -0.25 Points

7) > ~7%. It is slightly better. With such a minimal change it dos not reflect change better than the other method. 

> -0.25 Points
	
## Part 2

1) 

````R
> specnumber(BivalveAbundance["Miocene",])
[1] 634
````

2) 
````R
> diversity(BrachiopodAbundance, index = "simpson", MARGIN = 1, base = exp(1)) ["Late Ordovician"]
Late Ordovician 
0.9784588
````

3) 

````R
> diversity(BivalveAbundance["Late Cretaceous”,],”shannon”, MARGIN = 1, base = exp(1))
[1] 5.086512

4) 
````R
> diversity(BivalveAbundance["Paleocene",], index = "shannon", MARGIN = 1, base = exp(1))
[1] 4.511063
````

## Part 3
	
> -8 Points	
