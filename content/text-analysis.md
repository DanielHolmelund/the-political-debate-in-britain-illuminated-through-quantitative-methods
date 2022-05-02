---
title: Text analysis
prev: network-analysis
---

**Temporal Analysis of the Topics Adressed in the British Parliament**
<br />
The purpose of the following analysis is to investigate how certain political topics have evovled throug time.
A graph that illustrates the number of occurrences of a specific topic through time was created as an attempt to investigate how frequent the British Parliament address different topics: 
{{< plotly obj="lexicalDispersionPlot" >}} 

**Characterizing Words of the Speeches From Each Party**
<br />
The following section will attempt to discover words that characterize each of the political parties in the British Parliament using the transcripts described in the Data section (Insert ref to data). More specifically, the weighting scheme TF-IDF will be used to find words/terms that describe the speeches conducted by each party. In the following analysis, only a subset of the parties has been chosen namely the Liberal Democrat, Conservative, Labour, Scottish National Party, UK Independence Party and the Green Party (WordClouds for all parliaments can be found here). The WordClouds are depicted as follows:

Liberal Democrat             |  Conservative
:-------------------------:|:-------------------------:
<img src="/images/wordcloud_Liberal Democrat.pdf" width="600" />  |  <img src="/images/wordcloud_Conservative.pdf" width="600" />

The WordClouds embeds a rich amount of information in a relatively dense illustration. Hence, it may be tedious to find descriptive words at first sight. However, diving deeper into the particular WordClouds does reveal insightful information regarding the parties.   

Labour             |  Scottish National Party
:-------------------------:|:-------------------------:
<img src="/images/wordcloud_Labour.pdf" width="600" /> | <img src="/images/wordcloud_Scottish_National_Party.pdf" width="600" />

UK Independence Party             |  Green Pary
:-------------------------:|:-------------------------:
<img src="/images/wordcloud_UK Independence Party.pdf" width="600" /> | <img src="/images/wordcloud_Green Party.pdf" width="600" />




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


