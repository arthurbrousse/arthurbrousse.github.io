---
layout: post
title: Electric or thermic, what's the dynamic? 
subtitle: Discover the analysis 
thumbnail-img: /assets/img/gas-vs-electric.png
---

In the past few years, the topic of global warming has become central in public debate, raising political, social and economical questions. Among the many facets of this problem, a stake that gets the interest of many is transportation, of goods and people. Naturally, technology is allegedly coming to the rescue, with companies designing new cars running on electricity. Whether or not this is a solution to our problems is beyond the scope of what we will see, but let’s assume it is. What exactly does the general public think of this new generation of vehicles, that seems to have gotten so much hype in the last decade? Did the general opinion change depending on the different events that occurred around these two technologies, and if so why? 
{: text-justify; style="text-align: center;"}

![electric_combustion](/assets/img/gas-vs-electric.png)


To answer these questions, we studied a subset of a dataset named [Quotebank](https://dlab.epfl.ch/people/west/pub/Vaucher-Spitz-Catasta-West_WSDM-21.pdf), which is an open corpus of 178 million quotations attributed to their respective speakers, mostly American ones, extracted from 162 million news articles (almost entirely in English) published between 2008 and 2020. Although these quotes do not gather information about the “common folk”, we know people take interest and value the opinion of influential figures [^1], therefore the sentiment conveyed in these quotes approached how people view these different options. This dataset will allow us to gather information about what people have thought about the topic of electric cars versus thermic cars in the past few years. We study the evolution of the mindset of people about electric cars against thermic cars, from 2015 up until now.

 
[^1]:  [News in Social Media](https://www.tandfonline.com/doi/full/10.1080/21670811.2018.1423625) 

One of the first milestones of electric car development was this event:

{: .box-note}
**U.S. Department of Energy :** "President Obama Announces $2.4 Billion in Funding to Support Next-Generation Electric Vehicles", _March 19, 2009_

After taking this decision, which was partly in reaction to the price of the gallon of oil averaging 4$, President Obama set the goal for the U.S. to be the first country to reach one million electric vehicles by 2015. This illustrates a growing will to find and use alternatives to combustion engines, yet that innovation needs quite a starting boost. This is especially the case in a country that is well known for its relish of "conventional" internal combustion engine vehicles [^2]. But surely the cliché of the big American truck has a ground truth somewhere [^3]...

[^2]: [Old school - new school drag racing](https://www.youtube.com/watch?v=2Uneti_gkIw)

[^3]: [Talking about the cliché](https://www.youtube.com/watch?v=5XcW4nxqDmw)


## How is everyone feeling? 

To try and measure the evolution of the opinion on electric cars and thermic cars, a first-order approximation is to compare two leaders in the domain: Tesla and Chevrolet. Chevrolet as it is one of the most successful and best-selling car brands in the world[^4], especially in the US, and in average mid-range car prices, similar to Tesla. The latter was picked due to its status as the global leader in electric car manufacturing.

[^4]: [CHEVROLET SALES FIGURES – US MARKET](https://www.goodcarbadcar.net/chevrolet-us-sales-figures/)

This is where our quotes dataset comes into play. The big advantage of words is that they convey emotions. Therefore from the quotes, we can build a first overview of what image each company has had in the past years by assessing the average sentiment in the quotes. After selecting a sample of quotes that share characteristic keywords (e.g. brand names, car models) and checking the uniqueness of each quote, we proceed to a Sentiment Analysis, via a lexicon-based algorithm called Valence Aware Dictionary sEntiment Reasoning (VADER). In a nutshell, this algorithm associates values to words depending on their meaning and the emotion they convey and uses them to compute a score that corresponds to the overall "positiveness" of the sentence. The analysis is also backed up by a similar method, text2emotion, which analyses the emotion of the sentence, and BERT, a sentiment analysis Deep Neural Network.

We have data spanning 5 years in total, between January 2015 and April 2020, so why not take advantage of it? We examine the number of quotes every month and assess the average sentiment score, along with standard deviation. The goal is to see if, in these 5 years, the public opinion changed regarding either of these companies.

{% include general_chevrolet.html %}

A piece of information that jumps to our eye in the chart above is how the number of quotes varies. The average sentiment per month is overall around 0.5 and is mostly very stable except when the number of quotes is low. This first observation suggests the overall opinion regarding Chevrolet is rather positive. This is expected from the status this company has on the American car market. The third plot shows us the standard deviation also per month. Notice it oscillates a lot, implying that these results should not be taken at face value.


Before processing the quotes for Tesla, it is important to note that the quotes coming from its esteemed CEO, Elon Musk, account for 24% of the selected quotes. Nonetheless, we decided his contribution was worth keeping, despite his bias in favor of Telsa, as we are looking at what influential figures are saying.

{% include general_tesla.html %}

As already noticed in the sample of quotes about Chevrolet, there is not a lot of quotes in early 2016 and late 2016/early 2017. This leads us to think this flaw could be inherent to the Quotebank dataset. A striking difference is the average score, much lower in the case of Tesla. There are several factors to account for. First, on the technical side, we might reconsider the validity of the subset chosen for the analysis (number of quotes, themes tackled in the quotes) as well as the methods used, which could be more adapted to some datasets. On the qualitative side, there are global controversies around Tesla due to its novelty, disruptiveness, and mediatic presence of Elon Musk.

The standard deviation presented for Tesla being on average larger than the calculated means, there is no general trend in the results obtained. The sentiment calculated in quotes about Tesla fluctuates largely, which illustrates the controversial character of the company.


## Topic Analysis
After this basic overview of the general sentiment on each brand over the years, let us come back to our main concern: how are people's opinions on a company influenced by events linked to the said company? This analysis requires selecting appropriate events and discussing them in a pertinent timeframe.

Another approach that is more tailored to the data at disposal is topic detection. With its barbaric name, the "Latent Dirichlet Allocation" (LDA) algorithm identifies keywords;  which words in a batch of quotes are the most likely to accurately represent the topics covered by these quotes. 
 
### Words and Company Profile
A first iteration taking all the quotes into account for each company revealed some predominant words. The word clouds representing the words selected for topic analysis over the years are presented below: 

![image](/assets/tesla_cloud.png) | ![image](/assets/chevy_cloud.png)
- | -
Cloud of Words from Tesla quotes | Cloud of words from Chevrolet quotes

 In the case of Chevrolet, it is first worth noticing the word **"good"** is central. This could explain the higher VADER score presented earlier, as it constitutes a **general bias term**. Other central terms are **"race"**, **”track”** and **”teams”**, which picture Chevrolet as a company invested in car racing (e.g. NASCAR). Several car models are identified as well. From this analysis, we can put the image of Chevrolet into words: a sympathetic company (“good” and “weekend”) with a special liking for racing.

On the other hand, Tesla seems more linked to business (‘people’, company’, ‘production’, ‘stock’, etc.) and innovation (‘think’, ‘electric”, ‘autopilot’, etc.). The lexicon is more varied compared to Chevrolet, less one-sided. 

The quotes validate what we could have expected: these two companies are not playing the same game. Chevrolet is a well-established corporation, manufacturing well-known models and taking part in famous racing championships. On the other hand, we understand Tesla has a lot to prove to deserve its place in the car industry. Despite this, the company is more focused on innovation and research and advertises these efforts.

## Name now one man
Now that we have a global picture of the topics related to each company, the analysis is pushed further by reducing the batches of quotes taken into account, grouping them by year and month. This step allows one to have a more precise view on which topics characterise the companies through time. Some words are frequent and appear uniformly throughout the months, and constitute a kind of background noise. On the other hand, some specific terms appear punctually in the timeline, thus indicating a special event occurred. The following events have been detected thanks to LDA :
 
**Tesla**
- February 2015: Elon Musk's 'insane' call: Tesla worth $700 billion by 2025 (same market cap as Apple as of 2015).
- June to October 2015: Hype around the production of the Model X and start of the production.
- January 2016: Australia's first Tesla Powerwall has been installed.
- January 2017:  The massive Gigafactory battery production plant started mass-producing battery cells.
- November - December 2019:  Reveal of the Cybertruck.

**Chevrolet**
- December 2018-January 2019: New Silverado model.
- November 2016: MVP baseball player Zobrist wins a Camaro.
- December 2017: HSV releases a new model of modified Chevrolet Silverado.
- February 2018: The Camaro ZL1 was introduced in the Monster Energy NASCAR Cup Series. On February 18, 2018, Austin Dillon won the Daytona 500 in the ZL1's debut.
- April 2020: Team Carlin participates in the IndyCar iRacing Challenge with Chevrolet.

We can now select some events and analyse the evolution of the sentiment of people towards the event and the company in time.


## What are they talking about? 

We present 4 events of interest, corresponding to 4 car releases or reveals. Since the number of quotes is lower in 2016 and 2017, no event in this period is selected. To check the evolution of the general sentiment, these events are studied in a 60 days timeframe.

### Chevrolet
For Chevrolet, we selected the release of the Chevrolet Silverado, constructed in cooperation with Holden Special Vehicles, and its later iteration of the 2019 model. We took these two marketed models because we want to try to make a comparison with Tesla models, therefore not race cars. 

#### Chevrolet Silverado in collaboration with HSV

{% include chevrolet_hsv.html %}
For this first event, we can notice that the average of the feelings during the event is higher than before or after. The reduced span of the boxplot during the event suggests a general enthusiasm for the release. This enthusiasm is short-lived as the distribution come back to the initial state. The analysis of this event supports the claim that thermic cars are still very much appreciated despite the well-established knowledge of the implications of buying new, high fuel consumption (16l/100km), cars.

#### The Chevrolet Silverado

{% include chevrolet_silverado.html %}
The release of the Silverado in 2019 has slightly different results. However, we still witness an increase in median and shortening of the sentiment distribution, which again suggests that the release of this model was in majority welcomed by the interested public.

### Tesla 

For Tesla, we chose two fairly separated events. The first is the release of the Model X in September 2015 and the second is the CyberTruck presentation in November 2019.

#### The Tesla Model X

{% include tesla_model_x.html %}
We notice that the average is lower than for Chevrolet in general. The boxplots are narrower, but the maximums and minimums are far apart. There is no significant difference between the three periods. Thus, new releases of Tesla seem not to have any impact on the interested public's view on the company. This statement supports the claim that the general feeling on electric cars is still mixed. We need to analyse another event to verify that conclusion.

#### The Cybertruck 

{% include tesla_cyber.html %}

For the CyberTruck reveal, once again, the boxplots are narrower and the average remains quite constant overall, although there is a minor drop during the event. This drop could be related to the [failure of the window chock resistance test](https://www.youtube.com/watch?v=LMWwImDX3ks) during the reveal, which caused a drop by 6% in Tesla's stock value. 


## Who is doing the talking? 
Now, this is all fine and dandy, but during our initial topic analysis, something stood out that deserves attention: Who exactly is doing the talking? Are the people talking about Tesla the same ones that talk about Chevrolet? Where does everyone that's speaking come from? Tesla being a highly up and coming company with a mindset of innovation, we might have very different classes of people talking about it compared to a 100-year-old company like Chevrolet. To accomplish this, a great resource we can take advantage of is the information contained by the "occupation" field in the "wiki data" dumps (datasets fetched from Wikipedia's database). Indeed, we have the speakers who uttered the quotes, and therefore, with a little bit of digging, we can find their occupation(s).

{% include piechart_occupation.html %}

We can see how different the public talking about Tesla is from the one talking about Chevrolet, which reveals an important component of the comparison between electric and thermic vehicles: the latter is much more ingrained in the collective mindset, with a whole world built around it like race cars, whose name is thus associated to the cars people buy. While Tesla is gaining in popularity these last few years, it still is branded in people's minds as a novel technology that still needs to prove itself, which has been shown in recent surveys [^5]. This comforts our conclusions drawn from the topic analysis.

[^5]: [Reality check of public sentiment on electric cars](https://www.jdpower.com/business/press-releases/2020-q1-mobility-confidence-index-study-fueled-surveymonkey-audience)

## To wrap it up...
We have an example of the power of large scale data and what it can tell us. It is quite known now, that people tend to accommodate their behavior and opinion to the ones of recognized or influential people. 
- Telsa, while still being quite a new company with mixed feelings about it, has an aura of innovation and novelty around it which might sound promising for its future.
- Chevrolet on the other hand, has the advantage of being associated with race cars and the sentiment of freedom and adrenalin. 

Interestingly enough we found in the end very few mentions of the environmental stakes that lie in this discussion. Once again there might be several factors underlying this, maybe because this got even more launched at the front of the stage with the worldwide halt caused by Coronavirus which gave everyone time to reflect on how much screwed we were. Do the mode of transportation we take have an impact on this fight? Most likely, but our analysis with Quotebank tells us that it is definitely not at the heart of what has been extracted. 
