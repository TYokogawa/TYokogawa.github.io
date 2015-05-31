---
layout: post
title: Coffee drinks trend from Amazon reviews
---

This time I analyzed Amazon products 4260181 reviews from 1996-2014 in "home & kitchen" category. As myself is a big coffee fan, I was curious about which type of coffee are getting popular at home. I think one of big trend in coffee is home brewing. Home brewing is usually cheaper and you can choose and make your own favorite coffee. During summer, you may want to make sharp cold brew coffee, and for after dinner you might want double espresso or french press.

<img src="{{ '/assets/img/coffee_drinks.png' | prepend: site.baseurl }}">

###1. Check number of review mentioning types of coffee

First I checked number of reviews from 2000-2013 separated by types of coffee. I filtered all Home & Kitchen category reviews with coffee related words. There were 294539 reviews all together. Then I counted number of reviews in each category. These category are mix of method of brewing and recipe of coffee (espresso drinks).
<img src="{{ '/assets/img/coffee_type_reviews.png' | prepend: site.baseurl }}" alt=“">

###2. Sentiment analysis of coffee reviews

Here I tired to see if there are tendencies about positive and negative reviews in certain coffee types. TextBlob is great start for quick sentiment analysis with Python. This package use NLTK dictionaries and make it easy to use in some default setting. Sentiment analysis output gives us polarity score -1 to 1 (most negative to most positive) from corpus(amazon coffee related reviews).
I plotted average  polarity score and ratio (percentage of positive reviews) of each category. You can see very high average polarity from 'cappuccino', 'macchiato' and 'aeropress'. The reason of very low 'cold brew' score may come from "cold coffee complains” have mixed in the 'cold brew' review.  
<img src="{{ '/assets/img/sentiment_ave.png' | prepend: site.baseurl }}" alt=“">

In positive ratio plot, 'macciato', 'americano' and ‘cappuccino’ are the top 3.
<img src="{{ '/assets/img/sentiment_ratio.png' | prepend: site.baseurl }}" alt=“">

###3. Word cloud plot

I think word cloud is not new any more, but still very useful and nice way of visualizing summary of text data. The plot below is generated from 20000 reviews mentioned about "espresso". For home espresso category, 'machine', 'water', 'milk', 'make', 'great' are often used in reviews.
<img src="{{ '/assets/img/espresso_rev_1.png' | prepend: site.baseurl }}" alt=“">

#### Now I dig little deeper inside reviews. What is major topics in home espresso brewing? 

###4. Topic modeling of home espresso reviews

<img src="{{ '/assets/img/topicmodel.png' | prepend: site.baseurl }}" alt=“">

Computationally pulling out the topics of corpus is one of major tasks of Natural language processing (NLP). I used NLTK dictionary and Gensim for topic modeling. Language processing requires feature extraction (vectorization, feature matrix) to perform further machine learning. Here I used term-frequency times inverse document-frequency (tf-idf) to vectorize and performed latent semantic indexing (LSI).
<img src="{{ '/assets/img/lsi.png' | prepend: site.baseurl }}" alt=“">

###5. Conclusion

The increase of amazon reviews suggests the strong trend of increased of home brewing in multiple coffee types. High increase of espresso drinks from 2012-2013 is eminent. Some method like 'siphon' seems still not that popular. Sentiment analysis suggested emergence of strong popularity in 'aeropress' and surprisingly high positive reviews in 'macchiato' and 'cappuccino'. Topic modeling pulled up reasonable (for me) topics about home espresso brewing: "Grinder", "Easy to make", "Water", "Milk frothing", "Size of machine". I also considered about all of these topics before I bought my own espresso machine. I tried review clustering with K-means method before trying LSI, and it did not give me any reasonable clusters. On the other hand LSI method  pulled topics nicely. This is very impressive for me.
<img src="{{ '/assets/img/pupular_coffee.png' | prepend: site.baseurl }}" alt=“">

Now let's pause browsing and have a nice coffee!
<img src="{{ '/assets/img/review_ranking.png' | prepend: site.baseurl }}" alt=“">