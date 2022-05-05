---
title: Summary
prev: network-analysis

---

Before the analysis was conducted, four research question was raised. The following section will summaries the findings related to each of the research questions.

# How can the political activity at the British Parliament be modelled as a network?
One approach to model the political activity using the transcripts is to initially create a bipartite network between members of the Parliament and Topics which they care about. Subsequently, to model the relationship between Parliament members, one can project the bipartite graph. The results of the network analysis yield that the described approach is a possible solution for how to model political activity using networks. However, an issue with the approach is that the relationships between Parliament members only rely on the topics they have in common. Hence, it could be discussed whether or not the usage of topics as a proxy measure for political activity is justifiable, and if a different measure would have been better.

# What insights can be obtained from using a network science approach?

The insights obtained have mainly demonstrated that a parlament member tend to more frequently address similar topics such as *EU* and *Legislation* or *Health* and *Pandemic*.

# What insights can be obtained from using traditional text-mining methods such as TF-IDF?

The text analysis of the transcripts demonstrated that political parties tend to address topics in the Parliament, which align with their core values. Similarities based on the transcripts from each party also demonstrated that centered and left-centered party are associated with high similarity, and right-wing populist parties have low similarity with other parties. 

The temporal text analysis demonstrated that topics addressed in the Parliament vary with time and are typically triggered by urgent events happening in the UK and around the world, such as the covid pandemic. Furthermore, the analysis also implicitly reveal the Parliament's interest in different topics. For instance, the environment has experienced an increase in attention, while the interest in defence has been descreasing. As a further investigation, it could be interesting to investigate if their is a correlation between the topic addressed in the Parliament and the topics, which the public believe to be of most importance.

It was demonstrated that sentiment as a raw metric does not yield any great insight into the tone of the political debate, or reflect if big events, that require extra political attention, have occurred. This is due to the general formal language in these political debates being performed and the dictionary-based method that was demonstrated can't detect these small fluctuations in language. 

Wordshifts were demonstrated to be a more useful metric in this context that can reveal word-based fluctuations over a small time period. With wordshifts, both major events were illuminated and the politician's word was used around these topics. 

# How can text-mining and network science approaches be combined to provide a holistic understanding of potential political communities and the topics discussed within a community?

Using approaches from the network science field, it was possible to discover communities of members within the British Parliament. Furthermore, using TF-IDF, it was possible to discover important words associated with each community. Hence, by combining the methods from the two fields, it was possible to find communities in the network and subsequently try to understand the topics associated with the community. 
