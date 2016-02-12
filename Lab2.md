Adam Watson
Lab 2

> Awesome job! A little more detail behind your answers to Section IV would have been best, but still good job. Final grade is 19.3/20

## Part 1

1)	I identified about three different species using morphological characteristics. 

+ Species 1 contains samples (24,25,7,12). 
+ Species 2 (1,2,4,6,7,8,9,10,11,17,20,21). 
+ Species 3 (3,5,13,14,15,16,18,19,22,23). 

> Good job!

2)	The morphological features I used were the general shape of the shell. Specifically, how it spirals and the shape of the whorls on the exterior of the shell. Beyond that, I used stratigraphic position to group like species. Lastly, I used shell dimensions, taking into consideration sexual dimorphism.

3)	It is hard to say whether or not ontogenetic change can be seen as I can’t determine if there are any juveniles present in the sample. 

> -0.5 points. The correct answer was the spacing of chambers, but I would have accepted any reasonable hypothesis.

4)	Sexual dimorphism is a factor and was evaluated by looking at the side profile of each species. The males have wider shells than the females.


## Part 2
1)	names(plethodon) function gives [1] "land"    "links"   "species" "site"    "outline"

2)	Each object is a list. 

> I meant each object of plethodon, but that's okay.

3)	

````R
> dim(plethodon[[1]])
>[1] 12  2 40
````

## Part 2.1
	 
1)	First I made a new <strike>list</strike> array of integers from the landmark data 

````R
Land <- hummingbirds[["land"]]
````

2)	 Then I used the procrustes fuction on Land, 

````R
ProcrustusHum <- gpagen(Land) 
````

3)	Finally ran a PCA

````R
> plotTangentSpace(ProcrustusHum[["coords"]],warpgrids=FALSE,verbos=FALSE)   
````

4)	There one species of hummingbirds.

Part 3
1)	Fangs longer than six inches.
2)	Sulfurous odor.
3)	Adorable eyelashes. 
4)	C, D, and E, have a sulfurous odor. 
5)	D does not have a laser death ray.
6)	Adorable eyelashes are a synapomorphy.
7)	Species A  is a monophyletic group, B and C are a paraphyletic group and D and E a monophyletic group.
8)	No, because it would be paraphyletic
9)	
+ 	Species A,B, C are Paraphyletic.
+ 	Species C,D, E are Monophyletic. 
+	  Species C,D are <strike>Polyphyletic</strike> paraphyletic 
+	  Species A,B are <strike>Paraphyletic</strike> monophyletic
+ 	Species A,D, E are <strike>Monophyletic</strike> polyphyletic

> - 0.75 points

Part 4
1)	Assuming Species D and E, species D is an example of peramorphosis and species E an example of paedomorphosis. 
2)	Gryphaea gigantea (E)
3)	Paedomorphosis 


