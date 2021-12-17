---
layout: post
title: The battle of electricity versus fossil fuels
subtitle: Discover the analysis 
thumbnail-img: /assets/img/gas-vs-electric.png
---

In the past few years, the topic of global warming has become central in public debate, raising political, social and economical questions. Among the many facets of this problem, a stake that gets the interest of many is transportation, of goods and people. Naturally, technology is allegedly coming to the rescue, with companies designing new cars running on electricity. Whether or not this is a solution to our problems is beyond the scope of what we will see, but let’s assume it is, what exactly does the general public think of this new generation of vehicles, that seems to have gotten so much hype in the last decade? Did the general opinion change, and if so why? 

![electric_combustion](/assets/img/gas-vs-electric.png)


To answer these questions, we studied a subset of a dataset named [Quotebank](https://dlab.epfl.ch/people/west/pub/Vaucher-Spitz-Catasta-West_WSDM-21.pdf), which is an open corpus of 178 million quotations attributed to their respective speakers, mostly american ones, extracted from 162 million news articles (almost entirely in English) published between 2008 and 2020. Although these quotes do not gather information about the “common folk”, we know people take interest and value the opinion of influential figures[^1], therefore the sentiment conveyed in these quotes approached how people view these different options. This dataset will allow us to gather information about what people have thought about the topic of electric cars versus thermic cars in a ten-year span. We study the evolution of the mindset of people about electric cars against thermic cars, from 2015 up until now.

 
[^1]:  https://www.tandfonline.com/doi/full/10.1080/21670811.2018.1423625 

One of the first milestones of electric car development was this event:

{: .box-note}
**U.S. Department of Energy :** "President Obama Announces $2.4 Billion in Funding to Support Next Generation Electric Vehicles", _March 19, 2009_

After taking this decision, which was partly in reaction to the price of the gallon of oil averaging 4$, President Obama set the goal for the U.S. to be the first country to reach one million electric vehicles by 2015. This illustrates a growing will to find and use alternatives to combustion engines, yet that innovation needs quite a starting boost, especially in this case in a country that is well known for its relish of "conventional" internal combustion engine vehicles[^2] . But maybe the cliché of the big American truck[^3] has a ground truth somewhere...

[^2] : https://www.youtube.com/watch?v=2Uneti_gkIw
[^3] : https://www.youtube.com/watch?v=5XcW4nxqDmw


## How is everyone feeling? 

To try and measure the evolution of the opinion on electric cars and thermal cars, a first-order approximation is to compare two leaders in the domain: Tesla and Chevrolet. Chevrolet as it is one of the most successful and best-selling car brands in the world[^4], especially in the US, and in average mid-range car prices, similar to Tesla.

[^4]: https://www.goodcarbadcar.net/chevrolet-us-sales-figures/

This is where our quotes dataset comes into play. The big advantage of words is that they convey emotions. Therefore from the quotes, we can build a first overview of what image each company has had in the past years by assessing the average sentiment in the quotes. After selecting a sample of quotes that share characteristic keywords (e.g. brand names, car models) and checking the uniqueness of each quote, we proceed to a Sentiment Analysis, via a lexicon-based algorithm called Valence Aware Dictionary sEntiment Reasoning (VADER). In a nutshell, this algorithm associates values to words depending on their meaning and the emotion they convey and uses them to compute a score that corresponds to the overall "positiveness" of the sentence. The analysis is also backed up by a similar method, text2emotion, which analyses the emotion of the sentence, and BERT, a sentiment analysis Deep Neural Network.

We have data spanning 5 years in total, between January 2015 and April 2020, so why not take advantage of it ? We look at both the number of quotes over time and the average sentiment score, with its corresponding standard deviation, of our quotes talking about Chevrolet and Tesla. The goal is to see if in this 5-year timespan the public opinion changed regarding either of these companies.

{% include general_chevrolet.html %}

A piece of information that jumps to our eye in the chart above is how the number of quotes varies. The average sentiment per month is overall around 0.5, and is mostly very stable except when the number of quotes is low. The third plot shows us the standard deviation also per month. Contrary to what one would expect, it oscillates a lot. **SO WHAT**

Before processing the quotes for Tesla, it is important to note that the quotes coming from its esteemed founder, Elon Musk, account for 24% of the selected quotes. Nonetheless, we decided his contribution was worth keeping, despite his bias in favor of Telsa, as we are looking at how what influential figures are saying.

{% include general_tesla.html %}

Now for Tesla, we notice the low count of quotes in early 2016 and late 2016/early 2017, which leads us to think that this is actually inherent to the Quotebank dataset. A striking difference is the average score that we observe over the years, being much lower for Tesla quotes. This can be due to several factors: the quality of the analysis and of the methods that might have more trouble analysing either one of the datasets, as well as global controversies around Tesla due to its novelty and practices. We finally notice that the standard deviation is much more stable in Tesla's quotes compared to Chevrolet's. **SO WHAT ?***

**EXPLAIN WHY THE RESULTS ARE NOT FOLICHON**

## Topic Analysis
After this basic overview of the general sentiment on each brand over the years, let us come back to our main concern: how are people's opinion on a brand influenced by events linked to said brand? This analysis requires selecting appropriate events and discussing them in a pertinent timeframe.
 
At first, the step of event selection was naively done by hand, reading through the history of each brand, and evaluating which events seemed like milestones and would easily show up in the quotes. However, this method can not lead to the most accurate results. Indeed, despite the rather huge size of the quotebanks dataset, it doesn't contain complete information about any event about any topic happening in the world. This implies that the event that we manually selected might be missing.
 
Another approach that is more tailored to the data at disposal is topic detection. With its barbaric name, the "Latent Dirichlet Allocation" (LDA) algorithm identifies which words in a batch of quotes are the most likely to accurately represent the topics covered by these quotes. 
 
### Words and Company Profile
A first iteration taking all the quotes into account for each brand revealed some predominant words. The wordclouds representing the words selected for topic analysis over the years are presented below: 

![image](/assets/tesla_cloud.png) | ![image](/assets/chevy_cloud.png)
- | -
Cloud of Words from Tesla quotes | Cloud of words from Chevrolet quotes

 In the case of Chevrolet, it is first worth noticing the word **"good"** is central. This could explain the higher VADER score presented earlier, as it constitutes a **general bias term**. Other central terms are **"race"**, **”track”** and **”teams”**, which picture Chevrolet as a brand invested in car racing (e.g. NASCAR). Several car models are identified as well. From this analysis, we can put the image of Chevrolet into words : a brand oriented towards racing and with a friendly facade (“good” and “weekend”).

On the other hand, Tesla seems more linked to business (‘people’, company’, ‘production’, ‘stock’, etc) and innovation (‘think’, ‘electric”, ‘autopilot’ etc). The lexicon is more varied compared to Chevrolet, less one-sided. 

The quotes validate what we could have expected: these two companies are not playing the same game. Chevrolet is a well-established corporation, manufacturing well-known models and taking part in classic championships. On the other hand, we understand Tesla has a lot to prove to deserve its place in the car industry. Despite this, the company is more focused on innovation and research and advertises these efforts.

### Name now one man
Now that we have a global picture of the topics related to each brand, the analysis is pushed further by reducing the batches of quotes taken into account, grouping them by year and month. This step allows one to have a more precise view on which topics characterise the companies through time. Some words are frequent and appear uniformly throughout the months and constitute a kind of background noise. On the opposite, some specific terms appear punctually in the timeline, thus indicating a special event occurred. The following events have been detected thanks to LDA :
 
**Tesla**
- February 2015: Elon Musk's 'insane' call: Tesla worth $700 billion. Same market cap of Apple at that time
- June to October 2015: Hype around the production of the Model X and start of the production
- January 2016: Australia's first Tesla Powerwall has been installed
- January 2017:  the massive Gigafactory battery production plant started mass-producing battery cells
- November - December 2019:  Reveal of the Cybertruck

**Chevrolet**
- December 2018-January 2019 : New Silverado model
- November 2016: MVP baseball player Zobrist wins a Camaro
- February 2018: The Camaro ZL1 was introduced in the Monster Energy NASCAR Cup Series. On February 18, 2018, Austin Dillon won the Daytona 500 in the ZL1's debut.
- April 2020: Team Carlin participates in the IndyCar iRacing Challenge with Chevrolet
We can now select some events and analyse the evolution of the sentiment of people towards the event and the company in time.


## What are they talking about? 

We present 4 events of interest, corresponding to 4 car releases or reveals. Since the number of quotes is lower in 2016 and 2017, no event in this period is selected. To check the evolution of the general sentiment, these events are studied in a 60 days timeframe.

### Chevrolet
For Chevrolet, we selected the release of the sixth-generation Camaro which took place in April 2018 and the release of the 2019 model of the Silverado. We took these two marketed models because we want to try to make a comparison with Tesla models and therefore not race cars. 

#### The 6th Edition Chevrolet Camaro

{% include chevrolet_camaro.html %}
For this first event, we can notice that the average of the feelings during the event is higher than before or after. However, we notice that its variance is greater than the period before and also that there is a greater gap between the mean and the median during the event. This could be interpreted as perhaps feelings were more mixed during the event. 

#### The Chevrolet Silverado

{% include chevrolet_silverado.html %}
The release of the Silverado in 2019 has different results. With increasing median sentiment, we could assume the release was welcomed by the general public. 

### Tesla 

For Tesla, we chose two fairly separated events. The first is the release of the Model X in September 2015 and the second is the CyberTruck presentation in November 2019.

### The Tesla Model X

{% include tesla_model_x.html %}
We notice that the average is lower than for Chevrolet in general. The boxplots are narrower, but the maximums and minimums are far apart. There is no significant difference between the three periods. 

## The Cybertruck 

{% include tesla_cyber.html %}

For the CyberTruck reveal, once again, the boxplots are narrower and the average remains more constant. 

**TO CHANGE**
Compared to Chevrolet we can see several things. The first is that the mean and median for Tesla are still very close. The boxplots are narrower and we see much fewer differences between the different periods, but above all the average is always lower than for Chevrolet. Tesla is still a very young car brand and is starting to establish itself in the automotive world. Elon Musk. As we have seen, he also plays an important role in Tesla's image. Due to lack of quote, we did not reduce the number of days per period, which we think would be more interesting to analyze the feelings, especially with Elon Musk who often makes the news for only a very small period of time. 


## Who is doing the talking ? 
Now, this is all fine and dandy, but during our initial topic analysis, something stood out that deserves attention: Who exactly is doing the talking? Are the people talking about Tesla the same ones that talk about Chevrolet? Where does everyone that's speaking come from? Tesla being a highly up and coming company with a mindset of innovation, we might have very different classes of people talking about it compared to a 100-year-old company like Chevrolet. To accomplish this, a great resource we can take advantage of is the information contained by the "occupation" field in the "wiki data" dumps (datasets fetched from Wikipedia's database). Indeed, we have the speakers who uttered the quotes, and therefore, with a little bit of digging, we can find their occupation(s). So we will focus on two events related to Tesla and two events related to Chevrolet. 

{% include piechart_occupation.html %}

Clearly, we can see how different the public talking about Tesla is from the one talking about Chevrolet, which reveals an important component of the comparison between electric and thermic vehicles: the latter is much more ingrained in the collective mindset, with a whole world built around it like race cars, whose name is thus associated to the cars people buy. While Tesla is gaining in popularity these last few years, it still is branded in people's minds as a novel technology that still needs to prove itself, which actually has been shown in recent surveys [^5]. This comforts our conclusions drawn from the topic analysis.

[^5]: https://www.jdpower.com/business/press-releases/2020-q1-mobility-confidence-index-study-fueled-surveymonkey-audience

We have an example of the power of large scale data and what it can tell us. It is quite known now, that people tend to accommodate their behavior and opinion to the ones of recognized or influential people. 
- Telsa, while still being quite a new company with mixed feelings about it, has an aura of innovation and novelty around it which might sound promising for its future.
- Chevrolet on the other hand, has the advantage of being associated with race cars and the sentiment of freedom and adrenalin. 

Interestingly enough we found in the end very few mentions of the environmental stakes that lie in this discussion. Once again there might be several factors underlying this, maybe because this got even more launched at the front of the stage with the worldwide halt caused by Coronavirus which gave everyone time to reflect on how much screwed we actually were. Do the mode of transportation we take have an impact on this fight? Most likely, but our analysis with Quotebank tells us that it is definitely not at the heart of what has been extracted. 

## An overview of the opinion

Thanks to the Quotebank dataset, we were able to extract much information
