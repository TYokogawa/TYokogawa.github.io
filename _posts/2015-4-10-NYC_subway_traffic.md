---
layout: post
title: MTA New York Subway Traffic analysis
---

## Which station is best for flyer distribution in NYC subway station?

This is my first project in Metis. [MTA data][5] of turnstile counts are available.
The aim of this project is creating proposal and presentaion for hypothetical client who want to bring  women technology professionals to their event.
![alt text][4]

## Our team work flow:

####1.Get data: [MTA subway turnstile data][5] , April 04, 2015

####2.[Process-analyze data][6]: total traffic, traffic density(traffic per turnstile), commuter index(peak rush hours - nonpeak hours) 

####3.[Visualize analysis][3]: d3-js

####4.[Presentation][2]: we used slides.com

We calculated traffic density of people (population per turnstiles), and created original indicator,
**Commuter Index = (morning peak + evening peak) - (morning non-peak + evening non-peak).**
Then we used the product of these parameters to choose Top5 MTA station for flyer distribution.  

<iframe src="{{'/assets//html_plots/slides-deck.html' | prepend: site.baseurl }}" width="800" height="600" frameborder="0"></iframe>

Check out [python codes][1] for this process. 

















[1]: http://github.com/TYokogawa/NYC_subway_traffic_analysis
[2]: /html_plots/slides-deck.html
[3]: http://voodoolabs.github.io/Benson-Project/index.html
[4]: http://i.dailymail.co.uk/i/pix/2011/08/29/article-2031173-0D9EF3F000000578-112_964x724.jpg
[5]: http://web.mta.info/developers/turnstile.html
[6]: http://github.com/TYokogawa/NYC_subway_traffic_analysis
