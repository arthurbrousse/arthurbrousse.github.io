---
layout: post
title: The battle of electricity versus fossil fuels
subtitle: Discover the analysis 
---

Everyone not living in a cave for the whole twentieth century is a witness of global warming. Everyone knows that transportation of goods and of people is one of the causes of global warming, and is therefore a field with room for improvement. Naturally, technology is nowadays coming to the rescue, designing new cars that run on electricity, and not on conventional fuel. How efficient is this, and mostly, what effects does it have on people ? What does the population think of this new generation of vehicles, that seems to have gotten so much hype in the last decade ? 

To answer these questions, we have been provided with a dataset named [Quotebank](https://dlab.epfl.ch/people/west/pub/Vaucher-Spitz-Catasta-West_WSDM-21.pdf), which is _an open corpus of 178 million quotations attributed to the speakers who uttered them, extracted from 162 million English news articles published between 2008 and 2020._ This dataset will allow us to gather informations about what people have thought about the topic of electric cars versus thermic cars in a ten year span. We study the evolution of the mindset of people in the United States about electric cars versus thermic cars, from 2010 up until now. 

{: .box-note}
**U.S. Department of Energy :** "President Obama Announces $2.4 Billion in Funding to Support Next Generation Electric Vehicles", _March 19, 2009_

After taking this decision in 2009, partly in reaction to the price of the gallon of oil averaging 4$, president Obama set the goal for the U.S. to be the first country to have one million electric vehicles on the roads by 2015. This illustrates the fact that work needed to be done in the U.S. to make electric cars "look cool", in a country that is well known for its relish of "conventional" internal combustion engine vehicles. The cliché of the big American truck surely has a groundtruth somewhere...

## How things stand in the early 2010's :
Quelques commentaires, ou bien si on a vraiment rien, on parle seulement de l'état des choses général avant la sortie de la model 3, et pas à partir de 2010.

## What is the question 

Now, to try and measure the evolution of the opinion on electric cars and thermal cars we estimed that we could compare the two leaders in the domain: Tesla and Chevrolet. We chose Chevrolet as it is one of the most sold car overall and has a standard similar to Tesla, being quite mass market but not necessarily oriented towards low-cost vehicles. 

The big advantage of words, is that they convey much emotions therefore using these quotes, we can build an overview of what image each brand has by measuring their sentiment. This is done using Sentiment Analysis, via a lexicon-based algorithm called Valence Aware Dictionnary sEntiment Reasoning (VADER) which, in a nutshell, has values associated to words, more or less positive depending on their meaning, and uses them to compute a score that corresponds to the overall "positiveness" of the sentence. The analysis is also backed up, by a similar method that analyses the emotion of the sentence and BERT, a sentiment analysis Deep Neural Network.

![Overall Chevrolet Plot](/assets/chevrolet_general.html)

Now, a striking difference, is the average score that we observe over the years, being much lower for Tesla quotes. Now, this can be due to several factors: The quality of the analysis and of the methods that might have more trouble analysing either one of the datasets, global controversies around Tesla due to its novelty and practices.  
{% include /assets/chevrolet_general.html %} 


We have 

## What are they talking about ? 

Now, we have analysed the emotions, but another question of interest is, what exactly is everyone talking about during this time ? We can try to detect what the main subject is throughout the years, what is everyone talking about when reffering to Tesla or Chevrolet. We know that over the years, and especially for car companies which release new models frequently, what people are saying about their brand changes: A good car, and everyone is happy, a leaked scandal that reveals the company has been faking its CO2 emissions, now everyone's not so happy. 

Here are the main thing people are saying:



## What has happened and what changed ?

## Who is doing the talking ? 

Now, we have differences, but there might be an important variable, where do everyone that's speaking coming from ? Tesla being a highly up and coming company with a mindset of innovation, we might have very different classes of people talking about it compared to a more traditional company like Chevrolet. To accomplish this, a great ressource we can take advantage of if the imformation contained by the "occupation" field in the wikidata dumps. Indeed, we have the speakers who uttered the quotes, and therefore, with a little bit of digging we can find their occupation.


Now, clealy, we can see how different the public talking about Tesla is from the one talking about Chevrolet, which reveals an important component of the comparison between electric and thermic vehicles: The latter is much more engrained in the collective mindset, with a whole world built around it like race cars, whose name is thus associated to the cars people buy. While Tesla is gaining in popularity these last few years, it still is engrained in people's mind as a novel technology that has still to prove itself. 

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


