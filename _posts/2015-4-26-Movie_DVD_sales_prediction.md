---
layout: post
title: Blu-ray/DVD movies sales prediction
---

### Which Blu-ray/DVD movie titles make the top sales in 2015? How many units will be sold? 

Last two weeks I worked on Blu-ray/DVD sales prediction  project. [Boxoffice data][1] of about 15000 titles were obtained from Boxoffice Mojo site using [Beautiful Soup][2] tool.
In this project, I am a datasicentist working for a consulting company. One day I was asked to predict best new movies whose related products sales would be highest among 2015. So I created Blu-ray/DVD sales prediciton algorithm which would reflect popularity and project movie related products sales.
<img src="{{ '/assets/img/movie_dvd.jpg' | prepend: site.baseurl }}">

### Overview of my project:

####1. Get boxoffice data by webscraping.

####2. Bluray-dvd sales data from [opusdata.com][3] (SQL).

####3. Cleaning, join, explore the data.

####4. Popularity holding Index(PHI). 

I have created popularity holding index(PHI), which caluculates the change of weekly gross per theater value between first 2 week average and 4th week value. If the opening viewers give positive feedbacks and spread words to others, the weekly gross per theater still should hold its high number in 4th week. 
<img src="{{ '/assets/img/PHI_definition.png' | prepend: site.baseurl }}" alt=“">


####5. Linear regression for modeling.

Two variable (total first 4 week domestic gross and PHI) linear regression model is:
<img src="{{ '/assets/img/Two_variable_linear_regression.png' | prepend: site.baseurl }}" alt=“">

Final model of multivariate linear regression is:
<img src="{{ '/assets/img/DVD_linear_model.png' | prepend: site.baseurl }}" alt=“">


From final model I predicted Top 4 sales Blu-ray/DVD movies currently in theaters (April 26th, 2015). 
<img src="{{ '/assets/img/2015_DVD_prediction.png' | prepend: site.baseurl }}" alt=“">


####6. matplotlib / d3 visualizaion ([mpld3][4]).


####7. Interactive slides ([slides.com][5]).


Want to see my presentation [slides][6]?


Interactive plot: PHI vs domestic total gross
<iframe src="{{'/assets/img/a5000_w4_PHI_TDGross.html' | prepend: site.baseurl }}" width="900" height="520" frameborder="0"></iframe>









[1]: http://www.boxofficemojo.com
[2]: http://www.crummy.com/software/BeautifulSoup/
[3]: http://opusdata.com/
[4]: http://mpld3.github.io/
[5]: http://slides.com/
[6]: http://slides.com/tohei/movie#/
