---
title: Data description
prev: "/"
next: network-analysis
---

# **What is the data - and where does is come from?**

The transcripts from the British parliament is freely avaliable and published by the britsh government to the public. This project however made use a precollected dataset spanning a period approximately six years. From 05-01-2015 to 01-03-2021. This dataset was made avaliable in relation to a multilingial analysis of different parliamentary debates, with the main focus being the debate around COVID. The raw data can be downloaded here: [Parliamentary debates](https://www.clarin.si/repository/xmlui/handle/11356/1432)

Since the data itself is fragmented, the first step is to collect and represent the data in a meaningful datastructure that allows for further analysis. For this project all data is collected in a single Pandas dataframe.

The raw data is spread over six subfolder, one for each year. In these folders there are two files for each day. One that contains the transcripts themself and another file that contains the corresponding metadata. Each of these files have a ID column that allows to match the rows of the two data files.

The dataset is consisting of 552.103 datapoints, where each of these datapoints should be understood as a MP's speech in either of the houses. Each of these transcripts have after some prefiltering 14 attributed describing the speech. Some highlighted attributed are: 

* Date
* House
* Term
* Speaker name
* Speaker party
* Speaker role
* Speaker gender

# **Characteristics of data**

<img src="/images/num_speeches.png" width="1000" />

From this plot, it is apparent that the number of addresses each MP makes follows a power law. Prominent politicians are required to be more active in the houses. 

<img src="/images/top_speakers.png" width="1000" />

This is especially apparent in the following figure that the top ten speakers consist of 2 speakers of the house, 2 prime ministers and the rest being ministers. There is also an effect of some politicians being London based, meaning they have easier access to the Parliament than compared to Scottish politicians.

<img src="/images/house_speeches.png" width="1400" />

There is a clear distinction in the activity of the two houses. A hypothesis of why is that the house of common is elected each term and the primary goal of this house is to debate political topics and propose new laws. The lords are appointed and their primary goals are shaping laws and challenging the work of the government.  

<img src="/images/gender.png" width="1400" />

Based exclusively on the number of adresses it seems that the activities in the houses still are highly male dominated.

# **The ten characteristics of big data**

After this initial analysis of the data and its structure some of the ten characteristics of big data becomes apparent. In this section some of the most relevant characteristics are explored and used to highlight important distinctive features of the dataset.

* **Dirty:** As previously shown the data contained a "dirty" feature, the "Party_status". This highlight that the dataset is susceptible to being dirty since the data originally is manually collected by the stenographer that afterwards is archived. 
* **Always-on:** Since the British government makes this data publicly available, this project could be updated with the latest debates in the houses. However,  the newer data foundation will have another data structure, so new preprocessing code will have to be delveloped to encompass this. 
* **Incomplete:** As with most datasets, the metadata can always be expanded. In this case, the relation to the topic or bill is missing. Also if the speaker is pro or against the proposed bill. 



# **Sentiment Analysis**

For the basis of the sentiment analysis of the speeches in parliament, a dictionary-based sentiment analysis was applied. Here a predefined dictionary with happiness scores associated with the 10222 most commonly used words in the English dictionary is used to explore if sentiment analysis can highlight any underlying structures of the British parliament. The average happiness score for each day was found by using the following formula:

$$h_{avg}(T)=\sum_{i=1}^{N}h_{avg}(w_i)p_i$$

where

$$p_i = \frac{f_i}{\sum_{j=1}^{N}f_j}$$

is the corresponding normalized frequency and f_i is the frequency of the i'th word w_i.

More information about this method can be found [here](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0026752).

Sentiment analysis is an interesting topic that can illuminate how discourses evolve and show how different groups feel about certain topics. Therefore, the following section compares the two major parties and how their sentiment changes over time.

<img src="/images/happiness_scores.png" width="1400" />

As seen from the above figure, solely looking at the average happiness scores does not yield any information about sentiment around certain political topics that dominate over a longer period, like Brexit or COVID. This can to a high degree be attributed to the very formal setting and language used in these political addresses. Many of the words that constitute this formal language have a neutral happiness score and draw the average towards the neutral happiness score of 5. However, even in this formal setting that pr definition discusses serious topics the average happiness score is 5.51 for the Labour party and 5.55 for the Conservative party. This can be viewed in relation to the [Pollyanna hypothesis](https://en.wikipedia.org/wiki/Pollyanna_principle), namely that we as people tend to make use of a more positive language.


# **Wordshifts**

From the previous section, it is clear that the sentiment from the British parliament with a high temporal resolution does not yield any great insights. However, if we were to dive into certain dates for important events and compare the sentiment with the previous few days, would that yield any information about the sentiment in British politics?

For this, the date of the first COVID lockdown in Great Britain is investigated.

Labour            |  Conservative
:-------------------------:|:-------------------------:
<img src="/images/wordshift_labour.png" width="600" />  |  <img src="/images/wordshift_con.png" width="600" />

Here it is seen that both parties are slightly down in happiness scores compared with the 14 days before it is referenced against. But what is interesting is perhaps not the score itself, but the change in word frequency that their wordshifts uncovers. 

For negative words that emerge more than the usual, bill is at the top for both parties. This is a natural finding as legislators are proposing and discussing bills that can relieve the situation. Another series of negative words that are up are words describing the consequences of the pandemic, like "death", "emergency", "distancing", "crisis" etc.  

The positive words (right side of the figure) tell how the politicians for the respective parties address this time of crisis and how they wish to inspire hope and unity in the population. 

None of these findings might be truly surprising, since most of us understand the context around the COVID handling from a personal experience. However, this highlights the strengths of wordshifts that can illuminate landmark events and how these events affect the language.

