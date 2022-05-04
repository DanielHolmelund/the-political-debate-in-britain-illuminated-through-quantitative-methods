---
title: Network analysis
prev: data-description
next: text-analysis
---

# **Network Analysis of the British Parliament Speeches**

The following section will attempt to analyse the political activity within the British Parliament by leveraging the results of the topic and text analysis of the speeches from the previous section combined with methods from the network science field. 

The first step in the analysis is to construct a network using the speech transcripts and associated metadata, which can be found in the [data section](http://localhost:1313/DanielHolmelund/the-political-debate-in-britain-illuminated-through-quantitative-methods/data-description/). One possible approach for constructed the network is to create a *bipartite* network with one partition being the members of the Parliament and the other partition being political topics discovered in the [text analysis section](http://localhost:1313/DanielHolmelund/the-political-debate-in-britain-illuminated-through-quantitative-methods/text-analysis/). Hence, constructing a network that tries to model the relationship between politicians and political topics based on their speeches conducted in the Parliament. Furthermore, to model the relationship within each partition, it is possible to project the initial bipartite graph into two distinct network as depicted in the following visualization:

<img src="/images/graph_construct.png" width="400" />

Thus, creating a network consisting of the members of the Parliament and a network consisting of the political topics. In the projected network with Parliament members, two members share a link/edge if they had a common political topic in the original bipartite network, also known as a common neighbour. Furthermore, the weight or strength of each edge corresponds to how many mutual neighbours the two members had in the original bipartite network. A more elaborate explanation of the technical details regarding the graph constructions can be found in the [explainer notebook](http://localhost:1313/DanielHolmelund/the-political-debate-in-britain-illuminated-through-quantitative-methods/explainer-notebook.html).

The following sections will focus on network modelling, community detection, and partition comparison.

#### **Network Modelling**

### **Bipartite Network**
<br />
As previously mentioned, the first step in the network modelling was to create a bipartite network. The relations between members of the Parliament and the chosen topics were determined by assessing which topics a given member mentions sufficiently frequent in their speeches. This was accomplished by simply counting the frequency distribution of topics for each Parliament member and using the standard deviation as a threshold for determining when a topic is mentioned sufficiently frequent. Hence, for each member of the Parliament, an edge is drawn from the member to a topic, if the frequency of the topic is more than one standard deviation away from the average topic frequency for that particular Parliament member. The described approach yields the following network:

(Insert image of bipartite network here)

(Comment on network)

(Write something about properties here)

### **Projected Networks**
<br />
Subsequently, the projected network consisting of the members of the Parliament was determined, using the previously described approach, to model the interaction between Parliament members. The projection yielded the following network:

(Insert image of projected network here)

(Comment on network)

(Write something about properties here)



#### **Community Detection**

(Insert size of community)

(Insert image of network with louvain community annotations)


#### **Partition Comparison**

(Insert histograms for each partition)

(Insert wordclouds for each partition)
