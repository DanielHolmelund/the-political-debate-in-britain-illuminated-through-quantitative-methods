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


<p float="left">
  <img src="/images/num_speeches.pdf" width="200" />
  <img src="/images/top_speakers.pdf" width="200" />
</p>

Solarized dark             |  Solarized Ocean
:-------------------------:|:-------------------------:
<img src="/images/num_speeches.pdf" width="300" /> |  <img src="/images/top_speakers.pdf" width="300" />

From this plot it is apparent that the number of addresses each MP makes follows a power law. Prominent politicians are required to be more active in the houses as seen from the top ten speaker that consist of 2 speakers of the house, 2 prime ministers and the rest being ministers. 

<img src="/images/house_speeches.pdf" width="500" />

There is a clear distinction in the activity of the two houses. A hypothesis of why is that the house of common is elected each term and the primary goal of this house is to debate political topics and propose new laws. The lords are appointed and their primary goals are shaping laws and challenging the work of the government.  

<img src="/images/gender.pdf" width="500" />

Based exclusively on the number of adresses it seems that the activities in the houses still are highly male dominated.

# **The ten characteristics of big data**

After this initial analysis of the data and its structure some of the ten characteristics of big data becomes apparent. In this section some of the most relevant characteristics are explored and used to highlight important distinctive features of the dataset.

* **Dirty:** As previously shown the data contained a "dirty" feature, the "Party_status". This highlight that the dataset is susceptible to being dirty since the data originally is manually collected by the stenographer that afterwards is archived. 
* **Always-on:** Since the British government makes this data publicly available, this project could be updated with the latest debates in the houses. However,  the newer data foundation will have another data structure, so new preprocessing code will have to be delveloped to encompass this. 
* **Incomplete:** As with most datasets, the metadata can always be expanded. In this case, the relation to the topic or bill is missing. Also if the speaker is pro or against the proposed bill. 



# ** For text sentiment analysis**

# **Sentiment Analysis**

For the basis of the sentiment analysis of the speeches in parliament, a dictionary-based sentiment analysis was applied. Here a predefined dictionary with happiness scores associated with the 10222 most commonly used words in the English dictionary is used to explore if sentiment analysis can highlight any underlying structures of the British parliament. The average happiness score for each day was found by using the following formula:

$$h_{avg}(T)=\sum_{i=1}^{N}h_{avg}(w_i)p_i$$
where $p_i = \frac{f_i}{\sum_{j=1}^{N}f_j}$ and $f_i$ is the frequency of the i'th word $w_i$.

For more information the method used can be found [here](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0026752).

Sentiment analysis is an interesting topic that can illuminate how discourses evolve and show how different groups feel about certain topics. Therefore, the following section compares the two major parties and how their sentiment changes over time.

<img src="/images/happiness_scores.pdf" width="500" />

As seen from the above figure, solely looking at the average happiness scores does not yield any information about sentiment around certain political topics that dominate over a longer period, like Brexit or COVID. This can to a high degree be attributed to the very formal setting and language used in these political addresses. Many of the words that constitute this formal language have a neutral happiness score and draw the average towards the neutral happiness score of 5. However, even in this formal setting that pr definition discusses serious topics the average happiness score is 5.51 for the Labour party and 5.55 for the Conservative party. This can be viewed in relation to the [Pollyanna hypothesis](https://en.wikipedia.org/wiki/Pollyanna_principle), namely that we as people tend to make use of a more positive language.


# **Wordshifts**

<p float="left">
  <img src="/images/wordshift_labour.pdf" width="400" />
  <img src="/images/wordshift_con.pdf" width="400" />
</p>

