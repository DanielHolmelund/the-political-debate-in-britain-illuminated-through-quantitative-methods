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

<img src="/images/BG.png" width="600" />

(Comment on network)

### **Projected Networks**
<br />
Subsequently, the projected network consisting of the members of the Parliament was determined, using the previously described approach, to model the interaction between Parliament members. The projection yielded the following members of the Parliament network:

<img src="/images/proj_mp.png" width="600" />

The annotations of each node are determined by using the edge weights in the original bipartite network and then annotating each Parliament member with the topic associated with the highest edge weight.

(Comment on network)

Naturally all PM's adresses all the topics to some degree. Therefore, the thresholding then defining the network have a high impact on the structure of the network. However, as seen from the degree histrogram for the projected network, each node still have a very high average degree. 

<img src="/images/degree_hist.png" width="600" />

The clustering coefficent for the projected graph is: 0.80. The clustering coefficent can be seen as a measurement for local link density in the network ([source](http://networksciencebook.com/chapter/2#clustering)). With a clustering coefficent of 0.80 it is implied that two neighbors of a certain node have 80 % chance of being connected. This is seen from the network visualisation that consists of many locally tightly connected clusters with *bridges* of PM's between them that connects them into a global structure. 

#### **Community Detection**
<img src="/images/comm_size.png" width="600" />
(Insert size of community)

<img src="/images/louvain_proj_mp.png" width="600" />
(Insert image of network with louvain community annotations)


#### **Partition Comparison**
The following section will compare the communities detected by the louvain algorithm with the communities created by using the edge weight between members of the Parliament and the political topics. To conduct the partition comparison, we will use the *normalized mutual information* between the two partitions. Normalized mutual information can be formalized as the following:

$$I_{n}(X;Y)=\frac{I(X;Y)}{\frac{1}{2}H(X)+\frac{1}{2}H(Y)}$$

where X and Y are the partitions being compared and H(.) is the shanon entropy e.g.:
$$H(Y)=-\sum_{x}p(y)log(p(y)))$$

Mutual information gives us an estimate of how much information one would gain regarding X if we know the variable Y. However, to be able to compare the mutual information score across different partitions which may have different sizes, the estimate has to be normalized. Furthermore, the shanon entropy H(X) is an estimate of information associated with the variable X. 

The calculation of normalized mutual information between the two partitions yielded:
$$I(Louvain\ partition,\ Topics\ partition) \approx 0.29$$

To determine that the estimated normalized mutual information is significant, a randomization test will be conducted. The randomization is conducted by randomly shuffling the topic partition, and the normalized mutual information between the Louvain communities and the random partition is then computed. To achieve a measure of uncertainty, the described procedure is repeated a thousand times, which yields the following illustration:

(Insert randomization image here)

Thus, the partition comparison yields that there is some shared information between the topic partition and the detected communities of the Louvain algorithm. However, it also becomes evident that not all the information of one partition can be described using the other partition. Consequently, an investigation of the topics within the detected Louvain communities could be interesting to elucidate if any pattern emerges within the community members. One approach would simply be to compute the topic distribution within each community:

<img src="/images/comm_hist_0.png" width="800" />
<img src="/images/comm_hist_1.png" width="800" />
<img src="/images/comm_hist_2.png" width="800" />
<img src="/images/comm_hist_3.png" width="800" />

(Insert histograms for each partition)

(Insert wordclouds for each partition)
