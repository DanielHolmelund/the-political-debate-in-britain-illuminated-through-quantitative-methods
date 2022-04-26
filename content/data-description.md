---
title: Data description
prev: "/"
next: network-analysis
---

# What is the data - and where does is come from?

> Collection of data

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


<img src="/images/num_speeches.pdf" width="200" />

![](/images/dtu-logo.png)
<img src="/images/dtu-logo.png" width="200" />

Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia curae; Suspendisse eu tellus ut erat porttitor luctus. Vivamus aliquam auctor massa, in auctor orci. Ut quis enim ut lorem consectetur blandit dictum eu mauris.