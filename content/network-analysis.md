---
title: Network analysis
prev: data-description
---

# **Network Analysis of the British Parliament Speeches**

The following section will attempt to analyse the political activity within the British Parliament by leveraging the results of the topic and text analysis of the speeches from the previous section combined with methods from the network science field. 

The first step in the analysis is to construct a network using the speech transcripts and associated metadata, which can be found in the [data section](http://localhost:1313/DanielHolmelund/the-political-debate-in-britain-illuminated-through-quantitative-methods/data-description/). One possible approach for construction of the network is to create a [*bipartite*](https://en.wikipedia.org/wiki/Bipartite_graph) network with one partition being the members of the Parliament and the other partition being political topics discovered in the [text analysis section](http://localhost:1313/DanielHolmelund/the-political-debate-in-britain-illuminated-through-quantitative-methods/text-analysis/). Hence, constructing a network that tries to model the relationship between politicians and political topics based on their speeches conducted in the Parliament. Furthermore, to model the relationship within each partition, it is possible to project the initial bipartite graph into two distinct network as depicted in the following visualization:

<img src="/images/graph_construct.png" width="400" />

Thus, creating a network consisting of the members of the Parliament and a network consisting of the political topics. In the projected network with Parliament members, two members share a link/edge if they had a common political topic in the original bipartite network, also known as a common neighbour. Furthermore, the weight or strength of each edge corresponds to how many mutual neighbours the two members had in the original bipartite network. A more elaborate explanation of the technical details regarding the graph constructions can be found in the [explainer notebook](http://localhost:1313/DanielHolmelund/the-political-debate-in-britain-illuminated-through-quantitative-methods/explainer-notebook.html).

The following sections will focus on network modelling, community detection, and partition comparison.

#### **Network Modelling**

### **Bipartite Network**
<br />
As previously mentioned, the first step in the network modelling was to create a bipartite network. The relations between members of the Parliament and the chosen topics were determined by assessing which topics a given member mentions sufficiently frequent in their speeches. This was accomplished by simply counting the frequency distribution of topics for each Parliament member and using the standard deviation as a threshold for determining when a topic is mentioned sufficiently frequent. Hence, for each member of the Parliament, an edge is drawn from the member to a topic, if the frequency of the topic is more than one standard deviation away from the average topic frequency for that particular Parliament member. The described approach yields the following network:

<img src="/images/BG.png" width="600" />

It can be seen that there are a few nodes that are not connected to anything. These are also known as singletons. This is because of how we assign edges. If a parliament member (pm) talks equally much about all topics, there will not be a topic of which he/she talks more about than all the other topics. Therefore, our code will not assign an edge to a topic. It is, however, possible for a pm to have more than one edge assigned to them. These nodes can be seen as "bridges" between topics in the network. These bridges will thereby connect topics which actually groups similar topics together in the network. We can for example see see *eu* and *legisl(ation)* are connected by multiple bridges and are therefore placed near each other in the network.
We can also see topics related to *health* by this measure include *test*, *pandem(ic)*, *vaccin(e)* and *educ(ation)*.

### **Projected Networks**
<br />
Subsequently, the projected network consisting of the members of the Parliament was determined, using the previously described approach, to model the interaction between Parliament members. The projection yielded the following members of the Parliament network:

<img src="/images/proj_mp.png" width="600" />

The annotations of each node are determined by using the edge weights in the original bipartite network and then annotating each Parliament member with the topic associated with the highest edge weight.

We see the same trends as we saw in the bipartite network: there tend to form groups/communities which contain similar topics. However, it is more visible from this plot which communities are formed. *defenc(e)* is closely related to *world*, *tax* to *pension* and *legisl(ation)*, and *eu* to *legisl(ation)* and *economi(cs)*. The plot also tells us something about pms and their neighbours. The closer the distance between two pms, the more topics of interest they share. This means that the labeled version of the plot tells us which politicians are similar to each other with regards to topic mentions (not opinions).

Naturally, all pms adress all the topics to some degree. Therefore, the thresholding when defining the network have a high impact on the structure of the network. However, as seen from the degree histrogram for the projected network, each node still have a very high average degree meaning that the network is associated with a high inter- or intra-connectedness.

<img src="/images/degree_hist.png" width="600" />

The average clustering coefficent for the projected graph is: 0.80. This coefficent can be seen as a probability that two random nodes in the network are linked to eachother ([source](http://networksciencebook.com/chapter/2#clustering)). This is seen from the network visualisation that consists of many local, tightly connected clusters with *bridges* of pms between them that connects them into a global node structure. Additional many links also span across the clusters, resulting in the high average clustering coefficent. 


(Comment on network)

(Write something about properties here)



#### **Community Detection**
In this section, we use the Louvain algorithm in order to find the best possible clusters in our network.

<img src="/images/comm_size.png" width="600" />

The size of each cluster can be seen in the barplot above. It shows us that there is not a cluster with a relatively small number of nodes. This means that the network is quite well connected because we do not see a smaller community than we do. The network can be seen below.

<img src="/images/louvain_proj_mp.png" width="600" />

It is again apparent that the communities are pretty well inter-connected, meaning that the communities are linked together with other communities very well. This can be seen in the middle of the network, where we have a mix of different communities. 

Interestingly, when comparing this plot with the previous network plot, it can be seen that some of the groups we discussed earlier have been clustered together by the Louvain algorithm. For instance, community 0 consists of, among others, *health*, *pandem(ic)*, *vaccin(e)*, and *test*. 


#### **Partition Comparison**
The following section will compare the communities detected by the Louvain algorithm with the communities created by using the edge weight between members of the Parliament and the political topics. To conduct the partition comparison, we will use the *normalized mutual information* between the two partitions. Normalized mutual information can be formalized as the following:

$$I_{n}(X;Y)=\frac{I(X;Y)}{\frac{1}{2}H(X)+\frac{1}{2}H(Y)}$$

where X and Y are the partitions being compared and H(.) is the [shanon entropy](https://en.wikipedia.org/wiki/Entropy_(information_theory)) e.g.:
$$H(Y)=-\sum_{x}p(y)log(p(y)))$$

Mutual information gives us an estimate of how much information one would gain regarding X if we know the variable Y. However, to be able to compare the mutual information score across different partitions which may have different sizes, the estimate has to be normalized. Furthermore, the shanon entropy H(X) is an estimate of information associated with the variable X. 

Given that the Louvain algorithm is stochastic to a certain degree, the detected communities may differ based on initialization. Hence, to calculate the normalized mutual information (NMI) between the Louvain partition and the topic partition with an uncertainty measure, the Louvain algorithm was executed a thousand times while determining the NMI in each repetition. The average NMI between the two partitions with a 95% confidence interval was:
$$I(Louvain\ partition,\ Topics\ partition) = 0.30 \pm 0.001$$


To assess whether or not the estimated normalized mutual information is significant, a randomization test will be conducted. The randomization is conducted by randomly shuffling the topic partition, and the normalized mutual information between the Louvain communities and the random partition is then computed. To achieve a measure of uncertainty, the described procedure is repeated a thousand times, which yields the following illustration:

(Insert randomization image here)

(Remember to adjust the text below with results from randomization test)
Thus, the partition comparison yields that there is some shared information between the topic partition and the detected communities of the Louvain algorithm. However, it also becomes evident that not all the information of one partition can be described using the other partition. Consequently, an investigation of the topics within the detected Louvain communities could be interesting to elucidate if any pattern emerges within the community members. One approach would simply be to compute the normalized topic frequency distribution within each community:

<img src="/images/comm_hist_0.png" width="800" />

The topic frequency distribution within community 0 demonstrates that the majority of members are associated with the topic *health*.

<img src="/images/comm_hist_1.png" width="800" />

Subsequently, the frequency distribution of community 1 is mainly dominated by the topic *legislation* followed by *EU*.

<img src="/images/comm_hist_2.png" width="800" />

The topic frequencies within community 2 are more various, with the most frequent topics being *world*, *education*, *tax*, *economy*, *defence* and *employment*.

<img src="/images/comm_hist_3.png" width="800" />

Lastly, the topic distribution of community 3 demonstrates that the members of the community are mainly associated with the topic *EU*.

Subsequently, TF-IDF can be used to generate WordClouds related to each detected community as previously done in the [text analysis section](http://localhost:1313/DanielHolmelund/the-political-debate-in-britain-illuminated-through-quantitative-methods/text-analysis/). One feasible approach for computing the TF-IDF is to group the speeches of the Parliament members, who are within the same community as a single document. Thereby, resulting in four documents, one for each community. Furthermore, the IDF is computed on the entire corpus to achieve reasonable estimates. Subsequently, the TF-IDF representations of the four documents are computed with the IDF estimate, which are computed on the entire corpus. The described approach yields the following WordClouds for each community:

Community 0             |  Community 1
:-------------------------:|:-------------------------:
<img src="/images/wordcloud_0.png" width="600" /> | <img src="/images/wordcloud_1.png" width="600" />



Community 2            |  Community 3
:-------------------------:|:-------------------------:
<img src="/images/wordcloud2.png" width="600" /> | <img src="/images/wordcloud3.png" width="600" />
