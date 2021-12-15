---
layout: post
title: The battle of electricity versus fossil fuels
subtitle: Discover the analysis 
---

Everyone not living in a cave for the whole twentieth century is a witness of global warming. Everyone knows that transportation of goods and of people is one of the causes of global warming, and is therefore a field with room for improvement. Naturally, technology is nowadays coming to the rescue, designing new cars that run on electricity, and not on conventional fuel. How efficient is this, and mostly, what effects does it have on people ? What does the population think of this new generation of vehicles, that seems to have gotten so much hype in the last decade ? 

To answer these questions, we have been provided with a dataset named [Quotebank](https://dlab.epfl.ch/people/west/pub/Vaucher-Spitz-Catasta-West_WSDM-21.pdf), which is _an open corpus of 178 million quotations attributed to the speakers who uttered them, extracted from 162 million English news articles published between 2008 and 2020._ This dataset will allow us to gather informations about what people have thought about the topic of electric cars versus thermic cars in a ten year span. We study the evolution of the mindset of people in the United States about electric cars versus thermic cars, from 2015 up until now. 

{: .box-note}
**U.S. Department of Energy :** "President Obama Announces $2.4 Billion in Funding to Support Next Generation Electric Vehicles", _March 19, 2009_

After taking this decision in 2009, partly in reaction to the price of the gallon of oil averaging 4$, president Obama set the goal for the U.S. to be the first country to have one million electric vehicles on the roads by 2015. This illustrates the fact that work needed to be done in the U.S. to make electric cars "look cool", in a country that is well known for its relish of "conventional" internal combustion engine vehicles. The cliché of the big American truck surely has a groundtruth somewhere...

## How things stand in the early 2010's :
Quelques commentaires, ou bien si on a vraiment rien, on parle seulement de l'état des choses général avant la sortie de la model 3, et pas à partir de 2010.

## What is the question 

Now, to try and measure the evolution of the opinion on electric cars and thermal cars we estimed that we could compare two leaders in the domain: Tesla and Chevrolet. We chose Chevrolet as it is one of the most succesful and best-selling car brands in the U.S. and has a standard similar to Tesla, being quite mass market but not necessarily oriented towards low-cost vehicles. 

The big advantage of words, is that they convey much emotions. Therefore from the quotes in the dataset, we can build a first overview of what image each brand has had in the past years by assessing the average sentiment in the quotes. After selecting a sample of quotes which share characteristic keywords (e.g. brand names, car models) and checking the uniqueness of each quote, we proceed to a Sentiment Analysis, via a lexicon-based algorithm called Valence Aware Dictionnary sEntiment Reasoning (VADER). In a nutshell, this algorithm associates values to words depending on their meaning and the emotion they convey, and uses them to compute a score that corresponds to the overall "positiveness" of the sentence. The analysis is also backed up, by a similar method that analyses the emotion **GIVE NAME** of the sentence and BERT, a sentiment analysis Deep Neural Network.

Maitenant que nous avons sélectionné les quotes qui parlent de Chevrolet et de Tesla, calculé les sentiments qui en ressortent, il est de temps d'analyser nos résultats. Pour se faire nous allons dans un premier temps montrer la moyenne des sentiments par mois ainsi que le notre de quotes entre Janvier 2015 et Décembre 2020.  

{% include general_chevrolet.html %}

On peut remarque que pour Chevrolet, le nombre de quotes varie mais surtout qu'en Janvier 2016, Novembre/Décembre 2016 et Janvier 2017 nous avons presque aucune quote. La moyenne des sentiments par mois et relativement élevée mais surtout très stable mis à part lorsque le nombre de quote est bas. Le troisième plot nous montre la standard déviation également par mois. Contrairement à ce qu'on aurait pû attendre, elle oscille beaucoup. 

{% include general_tesla.html %}

Maintenat pour Tesla, on voit qu'il y a aussi peut de quotes en début 2016 et fin 2016/début 2017. On pourrait penser que le dataset QuoteBank a peut être moins de données pour cette période. On remarque que contrairement à Chevrolet, le nombre de quotes augement considérablement après 2017. Nous avons aussi découvert que dans nos quotes selectionées, 24% sont des citations d'Elon Musk, le créateur de Tesla. Le score est en moyenne plus bas et beaucoup moins stable que celui de Chevrolet. On remarque finalement que la standard deviation est beaucoup plus stable dans les quotes de Tesla comparé à celle de Chevrolet.

Now, a striking difference, is the average score that we observe over the years, being much lower for Tesla quotes. Now, this can be due to several factors: The quality of the analysis and of the methods that might have more trouble analysing either one of the datasets, global controversies around Tesla due to its novelty and practices.  

## Topic Analysis

After this overview of the general sentiment on each brand over the years, let us come back to our main concern : how are people's views on the brand influenced by events linked to said brands ? This analysis requires to select appropriate events and discuss them on a pertinent timeframe.

At first, the step of event selection was done by hand, reading through the history of each brand and evalutating which events seemed like milestones and would easily show up in the quotes. However, this method can not lead to the most accurate results. Indeed, despite the rather huge size of the quotebanks dataset, it doesn't contain complete information about any event about any topic happening in the world. This implies that the event that we manuallly selected might be missing. 

Another approach which is more tailored to the data we have at disposal is topic detection. With its barabaric name, the "Latend Dirichlet Allocation" algorithm is able to identify which words in a batch of quotes are the most likely to accurately represent what topics these quotes cover. The brand names were ignored in this process, as they appeared in every quote in our batches due to our selection process as indicated above. 


### Words and Company Profile
A first iteration taking all the quotes into account for each brand revealed some predominant words. In the case of Chevrolet, the word **"good"** is central. This could explain the higher VADER score presented earlier and be a **general bias term**. Another central term is **"race"**. These two words are the two main representatives of this brand.

2 WORD CLOUDS TODO : 1 WITH WORDS, 1 WITHOUT

The same first iteration is applied to the quotes related to Tesla.  GIVE THE WORDS
2 WORD CLOUDS TODO : 1 WITH WORDS, 1 WITHOUT

DRAW CONCLUSION ON THE PROFILE OF THE COMPANIES

### Name now one man

Now we have an intuition of the topics related to each brand, the analysis is push further by reducing the batches of quotes, grouping them by year and month. This step, along with discarding the main words cited earlier, allowed to have a more precise view on which topics characterise the brands through time. Some words are frequent and appear uniformly throughout the months and constitute a kind of background noise. On the opposite, we can find specific terms which appear punctually in the timeline, thus indicating a special event occured. Topics detected are (GIVE DATES): 
- Tesla
  - Model X
  - Cybertruck
- Chevrolet
  -  New camaro model 
  -  New Silverado model (selected as keyword in the quote selection process)



## What are they talking about ? 

Now this is all fine and dandy, but during our intial topic analysis, something stood out that deserves attention: Who exactly is doing the talking ? Are the people talking about Tesla the same ones that talk about  where do everyone that's speaking coming from ? Tesla being a highly up and coming company with a mindset of innovation, we might have very different classes of people talking about it compared to a 100 year old company like Chevrolet. To accomplish this, a great ressource we can take advantage of if the information contained by the "occupation" field in the wikidata dumps. Indeed, we have the speakers who uttered the quotes, and therefore, with a little bit of digging we can find their occupation(s).


Maintenant que nous avons regardé en général, les sentiments qui ressortent des quotes, nous allons nous concentrer sur deux événements relié à Tesla et deux événements relié à Chevrolet. Pour se faire, nous avons fait du topic detection en regroupant les phrases par mois. Pour voir si une différence de sentiments avait lieu entre avant, pendant et après un événements nous avons décidé d'utiliser des boxplots. En effet, ils nous permettent de résumer et visualiser les distributions plus facilement. Pour la période nous avons décidé de prendre 20 jours pour chacune d'entre elles et pour celle pendant, avec la date de l'événement au centre. Vu que le nombre de quotes est plus bas en 2016 et en 2017 nous avons préféré selectionner des événements qui ne sont pas dans ces années.  

Here are the main thing people are saying:
## Chevrolet

Pour Chevrolet, nous avons sélectionnée la sortie de la sixème génération de la Camara qui a eu lieu en Avril 2018 et la sortie du modèle 2019 de la Silverado. Nous avons pris ces deux modèles commercialisé car nous voulons essayé de faire une comparaison avec des modèles Tesla et donc pas des voitures de courses. 

## The 6th Edition Chervrolet Camaro

{% include chevrolet_camaro.html %}
Pour ce premier événement, nous pouvons remarque que la moyenne des sentiments pendant l'événement est plus haute qu'avant ou après. On remarque cependant que sa variance est plus grande que la période avant et aussi qu'il y a un plus grand écart entre la moyenne et la médiane pendant l'événement. On pourrait interpreter cela avec le fait que peut être les sentiments étaient plus partagés durant l'événement. 
## The Chevrolet Silverado

{% include chevrolet_silverado.html %}
La sortie de la Silverado en 2019 a des résultats différents. En effet on voit que la médiance augmente entre les trois périodes. La boxplot pour la période d'après est plus petit et surtout plus haute que les deux autres. On peut donc dire à travers ces résultats que les retours par rapport à la sortie du modèle sont assez positifs. 

On remaque à travers ces deux événements que la moyenne reste proche des 0.5 et qu'on a plus de variation au niveau de la médiane ou de la taille des boxplots.
## Tesla 
Pour Tesla, nous avons choisi deux événements assez séparés. Le premier est la sortie du modèle X en Septembre 2015 et le deuxième est la présentation CyberTruck en Novembre 2019.
## The Tesla Model X

{% include tesla_model_x.html %}
On remaque que la moyenne est plus basse que pour Chevrolet en générale. Les boxplots sont plus étroits mais on des maximums et minimums très espacés. On ne constate pas de différence significante entre les trois périodes. 
## The Cybertruck 

{% include tesla_cyber.html %}

Pour le dévoilement du CyberTruck, une fois de plus, les boxplots sont plus étroits et il la moyenne reste plus constante. 

Comparé à Chevrolet on peut constater plusieurs choses. La première est que la moyenne et la médiane pour Tesla sont toujours très proches. Les boxplots sont plus étroits et nous voyons beaucoup moins de différences entre les différentes périodes mais surtout que la moyenne est toujours plus basse que pour Chevrolet. Tesla est encore une marque de voiture très jeune et commence à s'imposer dans le milieu automobiles. Elon Musk. comme nous avons pû le voir joue aussi un rôle important dans l'image de Tesla. A cause de manque de quote, nous n'avons pas pû réduire le nombre de jour par période, ce qui selon nous serait plus intéressant pour analyser les sentiments, surtout avec Elon Musk qui fait souvent les nouvelles pour seulement une très petite période de temps. 

## Who is doing the talking ? 

Now, we have differences, but there might be an important variable, where do everyone that's speaking coming from ? Tesla being a highly up and coming company with a mindset of innovation, we might have very different classes of people talking about it compared to a more traditional company like Chevrolet. To accomplish this, a great ressource we can take advantage of if the imformation contained by the "occupation" field in the wikidata dumps. Indeed, we have the speakers who uttered the quotes, and therefore, with a little bit of digging we can find their occupation.

{% include piechart_occupation.html %}

Now, clealy, we can see how different the public talking about Tesla is from the one talking about Chevrolet, which reveals an important component of the comparison between electric and thermic vehicles: The latter is much more engrained in the collective mindset, with a whole world built around it like race cars, whose name is thus associated to the cars people buy. While Tesla is gaining in popularity these last few years, it still is engrained in people's mind as a novel technology that has still to prove itself. 

We have an example of the power of large scale data and what it can tell us. It is quite known now, that people tend to accomodate their behavior and opinion to the ones of recognized or influential people. 
- Telsa, while still being quite a new company whith mixed feeling about it, has an aura of innovation and novelty around it which might sound promising for its future.
- Chevrolet on the other hand, has the advantage of being associated to race cars and the sentiment of freedom and adrenalin. 

Interestingly enough we found in the end very few mentions of the environmental stakes of that lies in this discussion. Once again there might be several factors underlying this, maybe because this got even more launched at the front of the stage with the worldwilde halt caused by Coronavirus which gave everyone time to reflect how much screwed we actually were. Do the mode of transportation we take have an impact in this fight ? Most likely, but our analysis with Quotebank tells us that it is defenitely not at the heart of what has been extracted. 

## An overview of the opinion

Thanks to the Quotebank dataset, we were able to extract much information

## The Tesla Model 3
Tesla was founded in July 2003 as Tesla Motors, the name being in honor of Nikola Tesla. Elon Musk became the largest shareholder of the company when he made an investment of 6.5 million USD in February 2004, and he has served as CEO of the company since 2008. Tesla had been producing the Model S since 2012, but the sales numbers of this car have never risen enough to play a significant role on the vehicles market in the US (aorund 200'000 units sold by the end of 2017). The Model 3 was marketed as being more affordable to more people than previous models by Tesla. 

_Des ptits graphs, des ptits plots..._

## Big fuss for Tesla, big numbers for conventional engines
If you care to venture a guess, try to find the most sold car in the United States in 2017, the year of the release of the Model 3. Well, the first three spots are taken by fueled-powered trucks by Ford, Chevrolet and GMC. Since everybody in the US is named Ford, we cannot conduct a relevant analysis with that name, so we focus ourselves on the second most sold car in 2017, the Chevrolet Silverado.

_Des ptits graphs, des ptits plots..._

## How things stand now
_Des ptits graphs, des ptits plots..._

## In a nutshell...
lé zaméricain y conduise dé gros voitur et muske il é maran mdr


