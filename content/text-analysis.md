---
title: Text analysis
prev: data-description
next: network-analysis
---
**Analysing Speeches From Each Party**
<br />
The following section will attempt to analyse the speeches conducted by each political party by finding descriptive and informative words from the transcripts. Initially, all the transcripts in the corpus were grouped by political party resulting in 47 documents corresponding to each party. The approach of the analysis stems from a simple idea, counting. More specifically, to discover descriptive words associated with the 47 documents, the frequency of occurence for each term will be computed, also refered to as term-frequency. Thereby, constructing a term-document matrix which essentially is a table where each row corresponds to a document, each column corresponds to a term, and the value corresponds to the term-frequency. An example of a term-document matrix could be as follows:

|  | Education | Health | Finance | Minister |
|---|---|---|---|---|
| doc 1 | 7 | 3 | 0 | 15 |
| doc 2 | 0 | 2 | 9 | 13 |
| doc 3 | 1 | 9| 3 | 16 |

The underlying assumption of the counting approach is that a word's frequency can be seen as a proxy measure of the document's content. For example, in document three one of the most frequent terms is *Health*, and thereby we assume that it is reasonable to say that the topic of the document is related to health. Before computing the term frequencies it is important to remove common stop-words, otherwise, the stopwords will be associated with disproportional importance in terms of descriptiveness due to their frequent usage. However, the removal of stopwords is usually not enough. A typical shortcoming associated with term frequency is that it does not take into account that some terms are in general more frequent in the corpus. Consequently, a greater emphasis will be attributed to domain-specific common words than unique words. For instance, in the example presented above, the term *Minister* is associated with a high frequency across all documents in the corpus, however, it appears to be uninformative in terms of providing insights into the contents of the individual documents. Thus, the natural extension to overcome the described shortcoming of the counting approach is to weight the term-frequencies with the inverse of the document frequency (IDF):

$$IDF(t) = log(\frac{Total\ number\ of\ documents}{Number\ of\ documents\ with\ term\ t})$$

which entails that unique words should be associated with a greater importance. Combining the term-frequency with the inverse document frequency yields TF-IDF:

$$TFIDF(t)=TF(t) \cdot IDF(t)$$

Thus, TF-IDF assumes that a term's importance is proportional to how frequent the word occurs in a given document, and weighted with the inverse of how frequent the term occurs in the corpus. Thereby, compensating for common frequent words and attributing a greater emphasis on unique words. The following table demonstrates the term-document matrix weighted with the TF-IDF scheme:

|  | Education | Health | Finance | Minister |
|---|---|---|---|---|
| doc 1 | 1.2 | 0.001 | 0 | 0.006 |
| doc 2 | 0 | 0.0008 | 1.58 | 0.005 |
| doc 3 | 0.17 |0.003 | 0.52 | 0.006 |

Notice how the term *minister* is now associated with low importance for every document in the corpus in contrary to previously. In the following, the TFIDF weighting scheme will be used to find important terms that describe the speeches conducted by each party. The analysis will be limited to a subset of the parties, namely the Liberal Democrat, Conservative, Labour, Scottish National Party, UK Independence Party and the Green Party. However, the IDF is still computed on the entire corpus. Instead of presenting all the TF-IDF weighted words as presented in the above term-document matrix, a common visualization method is the usage of WordClouds. A WordCloud usually consist of a subset of the words present in a document, and the size of the words is proportional with the TF-IDF weight. The WordClouds of the selected political parties are depicted as follows:

Liberal Democrat             |  Conservative
:-------------------------:|:-------------------------:
<img src="/images/wordcloudLiberal Democrat.png" width="600" />  |  <img src="/images/wordcloudConservative.png" width="600" />

The WordClouds embeds a rich amount of information in a relatively dense illustration. Hence, it may be tedious to find descriptive words at first sight. However, diving deeper into the particular WordClouds does reveal insightful information regarding the parties. For instance, WordCloud associated with the Liberal Democrats emphasize words such as *School* and *Industry*, which aligns with the party's ideological identity as being in favour of a liberal and social democracy. The WordCloud of the Conservative party is a bit more difficult to interpret due to the relatively high amount of non-informative words such as gentleman. However, the party has been known to be liberal and opposing an independent united Ireland, Scotland and Welsh, which could explain the presence of words such as *Industry*, *Ireland* and *Scotland*.

Labour             |  Scottish National Party
:-------------------------:|:-------------------------:
<img src="/images/wordcloudLabour.png" width="600" /> | <img src="/images/wordcloudScottish_National_Party.png" width="600" />

Some of the political values associated with the Labour Party are also reflected. For instance, the presence of words such as *School* and *Pension* aligns with their socialistic ideology. The Scottish National Party is also associated with quite some interesting terms in the above WordCloud. For instance, the word devolution, which is commonly used to address a greater level of self-government of the Scottish Parliament.

UK Independence Party             |  Green Pary
:-------------------------:|:-------------------------:
<img src="/images/wordcloudUK Independence Party.png" width="600" /> | <img src="/images/wordcloudGreen Party.png" width="600" />

Furthermore, the UK Independence Party is frequently described as a relatively extreme right-wing populist party with an emphasis on lowering immigration, opposing Islam and being eurosceptic, which also can be seen by investigating the words in the WordCloud for instance *Border*, *Islam*, *Eurocrat*. 
<br />
Lastly, the Green Party is known for its environmental ideology and its progressive approach toward animal rights, which is reflected by words in the WordCloud such as *Environment*, *Animal* and *Climate*.

>Hence, the selected WordClouds demonstrate that the political parties are, in fact, addressing their proclaimed core values within the British Parliament. 

**Similarity Between Parties (TF-IDF & Cosine Similarity)**

The TF-IDF weighting scheme can also be utilized to approximate similarity between documents. Once the weighted term-document matrix has been created different similarity measures can be used to compute similarity between documents. One of the most common similarity measures are cosine similarity, which can be calculated as follows:

$$cosine(\textbf{v},\textbf{w}) = \frac{\textbf{v} \cdot \textbf{w}}{|\textbf{v}||\textbf{w}|}$$

where **v** and **w** are the TF-IDF (vector) representation of document v and w. All the pairwise cosine similarities of all documents in the corpus can then be computed to achieve similarity measures between all documents. Thus, using the 47 documents for each party, the similarity between all parties can be approximated by determining the cosine similarity between the TF-IDF representations of the grouped speeches. The following illustration depicts the cosine similarity between speeches from each of the selected parties. Note that a high value is associated with a high similarity:

<img src="/images/Party_similarity.png" width="600" />

Based on the estimated similarity, it becomes evident that none of the parties are similar to the UK Independence Party with a similarity score approximately below 0.5 in a range from [0,1]. Furthermore, the Liberal Democrats are most similar to the Labour party, which is to be expected given that both parties are left-centred. Interestingly, both the Labour and Liberal Democrat Party demonstrate high similarity with the Conservative Party even though they often are interpreted as opposing parties. This could potentially be caused by the speeches following specific norms, and thereby making them similar due to usage of conventional phrases.


**Temporal Analysis of the Topics Adressed in the British Parliament**
<br />
The following part of the analysis will attempt to investigate how different political topics have evovled throug time. In order to conduct the analysis, we have chosen a few topics that was present in the above TF-IDF WordClouds. Furthermore, the list of topics have also been further extended with topics we have believed were of particular increasing interests such as *pandemic*. Hence, the final list of topics constitutes of the following 18 topics:
 ['education',
 'health',
 'eu',
 'immigration',
 'crime',
 'pandemic',
 'vaccine',
 'world',
 'environment',
 'economy',
 'legislation',
 'employment',
 'transport',
 'tax',
 'pension',
 'welfare',
 'defence',
 'test']


Initially, the topics' evolution will be illustrated using an altered version of a lexical dispersion plot focussing on how the frequencies have changed throughout the year 2020:

<img src="/images/LexicalDispersionPlot.png" width="600" />

The size of each marker in the illustration corresponds to how frequent a topic has been mentioned on the specific day. Hence, the visualization demonstrates that the frequency of some topics are somewhat constant while others are associated with a higher variance. For instance, the frequency of the topic *vaccine* appears to have had an increase during the end of 2020, while topics such *health* and *eu* are associated with a constant high frequency. 

Subsequently, the variation of frequencies will be investigated throughout the entire timeframe in the corpus (2015-2021). Furthermore, we decided to conduct stemming on the topics to ensure that different inflexions of the topics map to the same topic. Thus, we counted the frequency of each topic for a given month and normalised the frequency according to the sum of the topic frequencies of that given month. The frequencies are illustrated in the following illustration, where each point in the plot corresponds to a normalised topic frequency:

{{< plotly obj="lineplots" >}}

> You can choose which topics you want to view in the plot by clicking on them

When comparing the plot to real world events, it can be seen - as expected - that the debate in parliament is influenced by those events. For instance, see the frequency of the two topics *pandem(ic)* and *test* begin to rise as the country begins to shut down due to Covid-19. 

This frequency is normalised across topics meaning that when one topic becomes more debated, other topics are going to be neglected. Continuing our Covid-19 example, we see *educ(ation)*, *defenc(e)*, *transport(ation)*, *crime* and *environ(ment)* take a steep dive in the graph. This gives insight into what topics are prioritised under which circumstances.

{{< plotly obj="heatmap" >}}

The heatmap shows the correlation coefficients between all topics. We see that *vaccin(e)*, *pandem(ic)* and *test* are strongly, positively correlated. But we can also see that *educ(ation)*, *defenc(e)*, *transport(ation)* and more are negatively correlated with *pandem(ic)*. This verifies what we saw earlier. Other trends also come to light now; *immigr(ation)*, *defenc(e)*, *welfar(e)*, *employ(ment)* and *crime* are all positively correlated suggesting that these topics tend to be discussed in the same months. *environ(ment)* is positively correlated with topics such as *transport* and *health*, and negatively correlated with *tax* and *welfar(e)*. The plot below shows the same trend.

{{< plotly obj="corrplot" >}}

However, now we can also see the year of which the points lie. *tax* seems to be talked less and less about, while *environ(ment)* seems to become more and more debated in parliament. This is shown in the plot below. The illustration depicts a scatter plot with a linear regression fitted across all points by minimizing the squared distance to the line from all of the points. This means that it is the linear line that best suits the data, and the direction of which it travels tells us a lot about what the overall trend looks like.

{{< plotly obj="ols" >}}

The illustration demostrates a general deacrease in *tax*, and an increase in *environ(ment)*. *defenc(e)* is also on the decrease, suggesting that the situation in and around Britain has been quite peaceful for some years (pre-Russian hostility). *educ(ation)* also gets lower and lower attention in parliament. This suggests either that schools are doing well and need less care from parliament or that education as a topic to be discussed is simply beginning to decline.  


# **Sentiment Analysis**
The following section will analyse the sentiment of the overall political discourse within the British Parliament from 2015 to 2021.

For the basis of the sentiment analysis of the speeches in parliament, a dictionary-based sentiment analysis was applied. Here a predefined dictionary with happiness scores associated with the 10222 most commonly used words in the English dictionary is used to explore if sentiment analysis can highlight any underlying structures of the British parliament. The average happiness score for each day was found by using the following formula:

$$h_{avg}(T)=\sum_{i=1}^{N}h_{avg}(w_i)p_i$$

where

$$p_i = \frac{f_i}{\sum_{j=1}^{N}f_j}$$

is the corresponding normalized frequency and f_i is the frequency of the i'th word w_i.

More information about this method can be found [here](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0026752).

Sentiment analysis is an interesting topic that can illuminate how discourses evolve and show how different groups feel about certain topics. Therefore, the following section compares the two major parties and how their sentiment changes over time.

<img src="/images/happiness_scores.png" width="1400" />

As seen from the above figure, solely looking at the average happiness scores does not yield any information about sentiment around certain political topics that dominate over a longer period, like Brexit or COVID. This can to a high degree be attributed to the very formal setting and language used in these political addresses. Many of the words that constitute this formal language have a neutral happiness score and draw the average towards the neutral happiness score of 5. However, even in this formal setting, that pr definition discusses serious topics, the average happiness score is 5.51 for the Labour party and 5.55 for the Conservative party. This can be viewed in relation to the [Pollyanna hypothesis](https://en.wikipedia.org/wiki/Pollyanna_principle), namely that we as people tend to make use of a more positive language.


# **Wordshifts**

From the previous section, it is clear that the sentiment from the British parliament with a high temporal resolution does not yield any great insights. However, if we were to dive into certain dates for important events and compare the sentiment with the previous few days, would that yield any information about the sentiment in British politics?

For this, the date of the first COVID lockdown in Great Britain is investigated.

Labour            |  Conservative
:-------------------------:|:-------------------------:
<img src="/images/wordshift_labour.png" width="600" />  |  <img src="/images/wordshift_con.png" width="600" />

Here it is seen that both parties are slightly down in terms of their happiness scores compared with the 14 days before used as a reference point. But what is interesting is perhaps not the score itself, but the change in word frequency that their wordshifts uncovers. 

For negative words that emerge more than the usual, bill is at the top for both parties. This is a natural finding as legislators are proposing and discussing bills that can relieve the situation. Another series of negative words that have increased are words describing the consequences of the pandemic, like "death", "emergency", "distancing", "crisis" etc.  

The positive words (right side of the figure) tell how the politicians for the respective parties address this time of crisis and how they wish to inspire hope and unity in the population. 

None of these findings might be truly surprising, since most of us understand the context around the COVID handling from a personal experience. However, this highlights the strengths of wordshifts that can illuminate landmark events and how these events affect the language.


