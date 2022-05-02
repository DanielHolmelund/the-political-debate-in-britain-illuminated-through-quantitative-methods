---
title: Text analysis
prev: network-analysis
---

Lorem ipsum dolor sit amet, consectetur adipiscing elit. In nulla tellus, tempus sed lobortis quis, venenatis ac ante. Maecenas accumsan augue ultricies metus hendrerit, in ultrices urna fringilla. Suspendisse lobortis egestas magna, sit amet fermentum ligula tincidunt vitae. Suspendisse cursus non dui a vulputate. Cras vestibulum vulputate enim eu placerat. Ut scelerisque semper justo sit amet auctor. Aliquam sit amet iaculis tortor.

Should be an image here:
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
 
