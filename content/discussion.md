---
title: Summary
prev: network-analysis

---
# **TLDR;**

Before the analysis was conducted, four research questions were raised:

>How can the political activity at the British Parliament be modelled as a network?

One approach to model the political activity using the transcripts is to initially create a bipartite network between members of the Parliament and Topics which they care about. Subsequently, to model the relationship between Parliament members, one can project the bipartite network into one partition. The results of the network analysis yield that the described approach is a possible solution for how to model political activity using networks. However, an issue with the approach is that the relationships between Parliament members only rely on the topics they have in common. Hence, it could be discussed whether or not the usage of topics as a proxy measure for political activity is justifiable, and if a different measure would have been better.

Furthermore, our way of defining edges in the bipartite graph could also be up for debate. The choice of threshold can be changed which might ultimately change all the subsequent results and conclusions. 

>What insights can be obtained from using a network science approach?

The insights obtained have mainly demonstrated that a Parlament member tend to frequently address similar topics such as *EU* and *Legislation* or *Health* and *Pandemic*.

>What insights can be obtained from using traditional text-mining methods such as TF-IDF?

The text analysis of the transcripts demonstrated that political parties tend to address topics in the Parliament, which align with their core values. Similarities based on the transcripts from each party also demonstrated that centered and left-centered parties are associated with high similarity, and that right-wing populist parties have low similarity with left-wing parties. 

The temporal text analysis demonstrated that topics addressed in the Parliament vary with time and are typically triggered by urgent events happening in the UK or around the world, such as the covid pandemic or the Brexit vote. Furthermore, the analysis also implicitly reveals the Parliament's interest in different topics. For instance, the environment has experienced an increase in attention, while the interest in defence has been descreasing. As a further investigation, it could be interesting to investigate if there is a correlation between the topic addressed in the Parliament and the topics which the public believe to be of most importance.

It was demonstrated that sentiment as a raw metric does not yield any great insight into the tone of the political debate, or reflect if big events, that require extra political attention, have occurred. This is due to the generally formal language in these political debates and the dictionary-based method that lacked the ability to detect these small fluctuations in language. 

Wordshifts were demonstrated to be a more useful metric in this context because they revealed word-based fluctuations over a small time period. With wordshifts, both major events were illuminated and the political discourse about these events.

>How can text-mining and network science approaches be combined to provide a holistic understanding of potential political communities and the topics discussed within a community?

Using approaches from the network science field, it was possible to discover communities of members within the British Parliament. Furthermore, using TF-IDF, it was possible to discover important words associated with each community. Hence, by combining the methods from the two fields, it was possible to find communities in the network and subsequently understand the topics associated with the communities.

 Overall this project was a:

<img src="/images/great-success-yes.gif" width="800" />