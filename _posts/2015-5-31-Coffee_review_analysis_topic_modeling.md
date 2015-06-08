---
layout: post
title: Coffee drink trends from Amazon reviews
---

This time I analyzed 4,260,181 reviews of Amazon products from 1996-2014 in the "home & kitchen" category. As a big coffee fan myself, I was curious about which types of coffee are getting popular at home. I think one big trend in coffee is home brewing. Home brewing is usually cheaper and you can choose and make your own favorite coffee. During summer, you may want to make sharp cold brew coffee, and for after dinner you might want a double espresso or french press.

<img src="{{ '/assets/img/coffee_drinks.png' | prepend: site.baseurl }}">

### 1. Check the number of reviews mentioning types of coffee

First I checked the number of reviews from 2000-2013 by type of coffee. I filtered all Home & Kitchen category reviews with coffee related words. There were 294,539 reviews all together. Then I counted the number of reviews in each category. These category are a mix of methods of brewing and recipes of coffee (espresso drinks).
<img src="{{ '/assets/img/coffee_type_reviews.png' | prepend: site.baseurl }}" alt=“">

### 2. Sentiment analysis of coffee reviews

Here I tried to see if there are tendencies about positive and negative reviews in certain coffee types. TextBlob is a great start for quick sentiment analysis with Python. This package uses NLTK dictionaries and makes it easy to use with default settings. Sentiment analysis output gives us a polarity score -1 to 1 (most negative to most positive) for our corpus of amazon coffee related reviews.

I plotted average  polarity score and ratio (percentage of positive reviews) of each category. You can see very high average polarity from 'cappuccino', 'macchiato' and 'aeropress'. The reason for very low 'cold brew' scores may come from "cold coffee complaints” being mixed in to the 'cold brew' reviews.

<img src="{{ '/assets/img/sentiment_ave.png' | prepend: site.baseurl }}" alt=“">

In positive ratio plot, 'macciato', 'americano' and ‘cappuccino’ are the top 3.
<img src="{{ '/assets/img/sentiment_ratio.png' | prepend: site.baseurl }}" alt=“">

### 3. Word cloud plot

I think word clouds aren't new any more, but they're still very useful and a nice way of visualizing a summary of text data. The plot below is generated from 20,000 reviews mentioning "espresso". For home espresso category, 'machine', 'water', 'milk', 'make', 'great' are often used in reviews.

<img src="{{ '/assets/img/espresso_rev_1.png' | prepend: site.baseurl }}" alt=“">

#### Now I dig little deeper inside reviews. What are major topics in home espresso brewing? 

### 4. Topic modeling of home espresso reviews

<img src="{{ '/assets/img/topicmodel.png' | prepend: site.baseurl }}" alt=“">

Computationally pulling out the topics of a corpus is one of major tasks of Natural language processing (NLP). I used the NLTK dictionary and Gensim for topic modeling. Language processing requires feature extraction (vectorization, feature matrix) to perform further machine learning. Here I used term-frequency times inverse document-frequency (tf-idf) to vectorize and performed latent semantic indexing (LSI).

<img src="{{ '/assets/img/lsi.png' | prepend: site.baseurl }}" alt="">

### 5. Conclusion

The increase of amazon reviews suggests the strong trend of increased home brewing in multiple coffee types. High increases in espresso drinks from 2012-2013 are prominent. Some methods like 'siphon' seem to be still not that popular. Sentiment analysis suggested emergence of strong popularity in 'aeropress' and surprisingly high positive reviews in 'macchiato' and 'cappuccino'. Topic modeling pulled up reasonable (for me) topics about home espresso brewing: "Grinder", "Easy to make", "Water", "Milk frothing", "Size of machine". I also considered all of these topics before I bought my own espresso machine. I tried review clustering with K-means method before trying LSI, and it did not give me any reasonable clusters. On the other hand LSI method  pulled topics nicely. This is very impressive to me.

<img src="{{ '/assets/img/pupular_coffee.png' | prepend: site.baseurl }}" alt=“">

Now let's pause browsing and have a nice coffee!

<img src="{{ '/assets/img/review_ranking.png' | prepend: site.baseurl }}" alt=“">
