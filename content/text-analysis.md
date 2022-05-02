---
title: Text analysis
prev: network-analysis
---
NOTE:( Måske skal det skrives mindre teknisk?)

**Characterizing Words of the Speeches From Each Party**
<br />
The following section will attempt to discover words that characterize each of the political parties in the British Parliament using the transcripts described in the Data section (Insert ref to data). More specifically, the weighting scheme Term Frequency - Inverse Document Frequency (TF-IDF) will be used to find words/terms that describe the speeches conducted by each party. In the following analysis, only a subset of the parties has been chosen namely the Liberal Democrat, Conservative, Labour, Scottish National Party, UK Independence Party and the Green Party (WordClouds for all parliaments can be found here). The WordClouds are depicted as follows:

Liberal Democrat             |  Conservative
:-------------------------:|:-------------------------:
<img src="/images/wordcloud_Liberal Democrat.pdf" width="600" />  |  <img src="/images/wordcloud_Conservative.pdf" width="600" />

The WordClouds embeds a rich amount of information in a relatively dense illustration. Hence, it may be tedious to find descriptive words at first sight. However, diving deeper into the particular WordClouds does reveal insightful information regarding the parties. For instance, WordCloud associated with the Liberal Democrats emphasize words such as *School* and *Industry*, which aligns with the party's ideological identity as being in favour of liberal and social democracy. The WordCloud of the Conservative party is a bit more difficult to interpret due to the relatively high amount of non-informative words such as gentleman. However, the party has been known to be liberal and opposing an independent united Ireland, Scotland and Welsh, which could explain the presence of words such as *Industry*, *Ireland* and *Scotland*.

Labour             |  Scottish National Party
:-------------------------:|:-------------------------:
<img src="/images/wordcloud_Labour.pdf" width="600" /> | <img src="/images/wordcloud_Scottish_National_Party.pdf" width="600" />

Some of the political values associated with the Labour Party are also reflected. For instance, the presence of words such as *School* and *Pension*, which reflect their socialistic ideology. The Scottish National Party is also associated with quite some interesting terms in the above WordCloud. For instance, the word devolution is commonly used to address a greater level of self-government of the Scottish Parliament.

UK Independence Party             |  Green Pary
:-------------------------:|:-------------------------:
<img src="/images/wordcloud_UK Independence Party.pdf" width="600" /> | <img src="/images/wordcloud_Green Party.pdf" width="600" />

Furthermore, the UK Independence Party is frequently described as a relatively extreme right-wing populist party with an emphasis on lowering immigration, opposing Islam and being eurosceptic, which also can be seen by investigating the words in the WordCloud for instance *Border*, *Islam*, *Euro*. 
<br />
Lastly, the Green Party is known for its environmental ideology and its progressive approach toward animal rights, which is reflected by words in the WordCloud such as *Environment*, *Animal* and *Climate*.

Hence, the selected WordClouds demonstrate that the political parties are, in fact, addressing their proclaimed core values within the British Parliament. 

**Similarity Between Parties (TF-IDF & Cosine Similarity)**

The TF-IDF weighting scheme can also be utilized to find similar documents. Hence, it can be used to find similar and dissimilar parties with the usage of cosine similarity.(får teknisk??) The following illustration depicts the cosine similarity between speeches from each party. Note that a high value is associated with a high similarity:

<img src="/images/Party_similarity.pdf" width="600" /> 

Based on the similarity between speeches conducted in the parliament, it becomes evident that none of the parties is similar to the UK Independence Party with a similarity score approximately below 0.5 in a range from [0,1]. Furthermore, the Liberal Democrats are most similar to the Labour party, which is to be expected given that both parties are left-centred. Interestingly, both the Labour and Liberal Democrat Party demonstrate high similarity with the Conservative Party even though they often are interpreted as opposing parties. This could potentially be caused by the speeches following specific norms thereby making them similar due to conventional phrases.


**Temporal Analysis of the Topics Adressed in the British Parliament**
<br />
The purpose of the following analysis is to investigate how certain political topics have evovled throug time.
A graph that illustrates the number of occurrences of a specific topic through time was created as an attempt to investigate how frequent the British Parliament address different topics: 
{{< plotly obj="lexicalDispersionPlot" >}} 


After preprocessing the data, 17 topics were found. Using stemming, we counted the frequency of each topic during a given month and normalised this frequency according to the sum of the topic frequencies of that given month. Each point in the plot corresponds to a normalised topic frequency. 

{{< plotly obj="lineplots" >}}

> You can choose which topics you want to view in the plot by clicking on them

When comparing the plot to real world events, it can be seen - as expected - that the debate in parliament is influenced by those events. For instance, see the frequency of the two topics *pandem(ic)* and *test* begin to rise as the country begins to shut down due to Covid-19. 

This frequency is normalised across topics meaning that when one topic becomes more debated, other topics are going to be neglected. Continuing our Covid-19 example, we see *educ(ation)*, *defenc(e)*, *transport(ation)*, *crime* and *environ(ment)* take a steep dive in the graph. This gives insight into what topics are prioritised under which circumstances.

{{< plotly obj="heatmap" >}}

The heatmap shows the correlation coefficients between all topics. We see that *vaccin(e)*, *pandem(ic)* and *test* are strongly, positively correlated. But we can also see that *educ(ation)*, *defenc(e)*, *transport(ation)* and more are negatively correlated with *pandem(ic)*. This verifies what we saw earlier. Other trends also come to light now; *immigr(ation)*, *defenc(e)*, *welfar(e)*, *employ(ment)* and *crime* are all positively correlated suggesting that these topics tend to be discussed in the same months. *environ(ment)* is positively correlated with topics such as *transport* and *health*, and negatively correlated with *tax* and *welfar(e)*.

But more interestingly, we can through this data begin to see which topics are getting more important and which topics are not.

{{< plotly obj="ols" >}}

Here we see a general dedcrease in *tax* and an increase in *environ(ment)*. *defenc(e)* is also on the decrease, suggesting that the climate in and around Britain has been quite peaceful for some years (pre-Russian hostility). *educ(ation)* also gets lower and lower attention in parliament. This suggests either that schools are doing well and need less care from parliament or that education as a topic to be discussed is simply beginning to decline.  


