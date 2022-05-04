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

