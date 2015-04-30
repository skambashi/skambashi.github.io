---
layout: article
title: Interning at PlaceIQ
modified:
categories: blog
excerpt:
tags: []
image:
  feature: blog_interning_at_placeiq_feature.gif
  teaser: blog_interning_at_placeiq_teaser.png
  thumb:
date: 2015-04-27T19:37:31-04:00
comments: true
---
Wow.

I can't believe it's already been four months since I arrived in New York City.

Now that I've lived here, I'm beginning to understand why this place attracts so many people.

There is a feeling of urgency everywhere. The kind that you get when scratching a lottery ticket. Almost as if the faster you scratch, the more likely you are to win.

The tall skyscrapers, the bright lights, and the busy streets all have an air of excitement about them. You can't help but feel that there's an opportunity at every corner, and that feeling hasn't faded since I stepped out of the airplane.

![Manhattan]({{ site.url }}/images/blog_interning_at_placeiq_1.jpg)

Back when I was looking for an internship in the fall, I had a bias against any tech company that wasn't in the valley (or at the very least, near it). Sure, I still applied to a lot of places that weren't on the west coast, but it was more as a backup in case I didn't get into any of the companies I wanted. Honestly, I have to say that I was blessed by the gem that I found here in New York. [PlaceIQ](http://www.placeiq.com/){:target="_blank"} was an awesome company to work for.

{% include toc.html %}

# PlaceIQ

So what is PlaceIQ?

In the words of Duncan McCall (the CEO):

_"We set out to build a location-intelligence company that would provide an unparalleled understanding of consumers in this new, digitally driven world. Our dynamic team is on a mission to provide solutions that power a new model of consumer behavior."_

...

What does that mean!?

At first glance, it's hard to grasp the value of that statement. Initially, even I didn't fully understand what PlaceIQ did, or why it was valuable.

To put it plainly, PlaceIQ is a location based analytics company that builds an understanding of how people behave in the physical world, by leveraging all the digital data that's available today.

And oh boy, is there a lot of it.

## Big Data

![Data everywhere]({{ site.url }}/images/blog_interning_at_placeiq_2.jpg)

According to an [article](http://www.sciencedaily.com/releases/2013/05/130522085217.htm){:target="_blank"} posted by ScienceDaily, 90% of the world's data was generated over the last two years, and that was back in 2013!

So where is all this data coming from?

Aside from all the media that we produce with our phones, tablets, laptops, and more recently our smartwatches. Nowadays, things like fridges, cars, and even our [clothes](http://www.liveathos.com/){:target="_blank"} are generating data.

## Location Based

I mentioned before that we are a location based company, and what better way to build an understanding of the physical world than using data pertaining to it?

At this point most smartphones keep track of their own movement among various locations. PlaceIQ's platform leverages this anonymized data to build consumer profiles based on where devices have been. In other words, location based data can enable a better understanding of certain demographics that frequent a grocery store, or the type the restaurants those phone owners prefer over others!

## Privacy

Of course, there's always the concern with privacy, and rightfully so. This kind of personal and granular data wasn't available until recently, so no one is fully aware of it's implications. Look at Facebook for example, they received a lot of [backlash](http://www.forbes.com/sites/dailymuse/2014/08/04/the-facebook-experiment-what-it-means-for-you/){:target="_blank"} for their experiments that they conducted with their users' newsfeeds.

But not to worry, we don't have access to any personal information about you. To be honest, just your data alone isn't really useful at all in understanding human behaviour.  It's only when you can analyze data at scale, that you begin to see interesting patterns and behaviours. 

# Data Science Intern

My work as an intern in the Data Science team at PlaceIQ was related to gleaning bits of insight from our data, similar to the examples above.

![Data science]({{ site.url }}/images/blog_interning_at_placeiq_3.jpg)

## Data Munging

A lot of what I did at PlaceIQ was related to cleaning data and staging it for later use.

It is an underappreciated labour, but the process of preparing the data (also referred to as data wrangling) is something that is necessary in order to even start analyzing it.

Real world data rarely comes in a neatly packaged box that you can instantly run a machine learning algorithm on. It's an inconsistent, noisy mess that requires time and experience in order to tame it into something meaningful.

![Data wrangling]({{ site.url }}/images/blog_interning_at_placeiq_4.jpg)

## Evaluating Datasets

I often helped in the evaluation of new datasets. Although the more statistically heavy analysis was carried out by the full time data scientists, it was still awesome to see the kinds of things they looked out for in a good dataset.

The majority of the analysis was actually pretty intuitive. An ideal high fidelity user would send a relevant number of requests from locations of interest. As such, we might consider the distribution of users and locations by the number of requests they generated, and only take the devices that are within a threshold number of standard deviations from the mean as a basic filter.

Simply put, if you only ever saw one request from a user, then it would be useless since you wouldn't be able to extrapolate very much from a single data point. On the other hand, if a user were to be sending a ridiculous number of requests, it would skew your data, and it could potentially be a sign of a bot.

The evaluation with regards to location was outside the scope of what I did, but it's also the most interesting part of analyzing a location based dataset. As such, I thought I'd quickly go over some of the things that I learned from the data scientists.

Often times, the latitude and longitude of a request isn't as accurate as we'd like it to be. Apps and networks that publish these requests frequently round or append arbitrary digits to a latitude and logitude, and in the case of competitors, sample or obfuscate their data. This sometimes results in hotspots where all nearby requests are simply grouped to that location, or we might end up seeing a uniform distribution of users and requests within the dataset.

PlaceIQ uses something called Darwin to weed out ineffective and fraudulent location data as explained above. In other words, it's a pipeline process that results in data-based natural selection. Darwin examines the data by looking at things such as hyperlocality, which assesses if data is consistent with natural human movement, and clusterability, which determines if clusters of data points are consistent with what you'd expect to see in normal human activity.

![Bad data]({{ site.url }}/images/blog_interning_at_placeiq_5.jpg)

## Ad-Hoc Work

Ad-Hoc work was mostly a lot of data manipulation. There were many jobs that I worked on related to client requests, but I won't go into detail since it's not that different from the work I did with data munging and evaluating datasets.

## Technology Used

At the beginning of my internship, the majority of the data munging jobs were run on Amazon's EMR (ElastMapReduce) and most of our data was stored on Amazon's S3 server.

Towards the end, we began to move all our pipelines and data to our own personal data centers. Once we migrated to the data centers, there wasn't a need to wait for a cluster to spin up, and the overhead of having to install Spark or Hadoop on each node was gone. On top of that, all our data was locally accessible through HDFS within the data center and this sped up our workflow by a significant amount. The data centers were always up, and regularly maintained which was awesome.

The jobs I wrote were mostly in Scala using the Spark framework, as well as a bit of Java for Hadoop as well. Occasionally I would work with Python or write a quick Bash script to help with my workflow. Our data pipelines are run by Azkaban, which I only really dabbled in for a little bit, to include a small data pipeline (written in Python).

For my last project, I messed around a bit with HBase and Apache Phoenix to do some basic queries on it, but didn't really have the time to go more in depth. 

# Conclusion

{% include image-caption.html url="/images/blog_interning_at_placeiq_6.jpg" description="The awesome data science team at work" %}

In conclusion, PlaceIQ is an exciting place to work at. Aside from all the cutting-edge technology you get to work with, and all the amazing things you get to do with the data, there are the weekly happy hours (and the monthly big one), poker nights, ping pong tourneys, rock climbing groups, quarterly team outings, and some of the best people you could ever work with.

Oh, and there's snacks. A lot of snacks.

Finally, I'd like to thank everyone from the Data Science team for being such awesome mentors and friends these past four months! I may not always show it, but I really enjoyed my time here.

------------------------------------------------------------------------------------------------------------------

_If you want to help build a location-intelligence company that provides an unparalleled understanding of consumers in this new, digitally driven world, PlaceIQ is [hiring](http://www.placeiq.com/about-us/careers/){:target="_blank"}._

