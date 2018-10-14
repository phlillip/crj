---
layout: post
comments: true
title:  Need more data
tagline: API's vs. website scraping
date:   2017-04-17 014:30:00 +0000
categories: module1
---

**An app designed for 1 man will only be downloaded once.**

Whilst rebuilding my appjam app for general release, I had to face the issue of mass usability. Due to the constraints of the appjam I had to limit my app prototype to static, prepopulated data, which would only work for one use case&mdash;in this case, one single Sunday League football team.

To make the app truly useful, it had to be able to be used by anybody that wanted to track their team's data. This left me with two options:

**1. Allow the user to input all the data themselves.**

This means typing in all the player names, all the opponents team names and all the competition names. The player names could theoretically come from the phone data; presumably the manager would have all his player's phone numbers saved in his phone. The other data could be aded on a game by game basis, or a list of league teams entered when the app is first used. Either way, this is work that must be done by the user.

**2. Use data that already exists to populate the app.**

All Sunday League footballers must be registered with the FA. All the league data is [available online](http://full-time.thefa.com/) so I contacted the FA to see if they had an API I could use to get access to the relevant data. I am still trying to navigate my way through their communication channels to get to the right person, but in case this ends in disappointment, there may be another way&mdash;web scraping.

I have used [beautifulsoup](https://www.crummy.com/software/BeautifulSoup/), which is a Python web scraping tool, to access the information directly from the HTML pages that the FA publish.

- - - 
<figure>
	<img src="/media/2017-04-17/beautifulsoup-webscraping.png" />
	<figcaption>
		Here you can see the results of the webscraping in the console. The function pulls the team names when given the correct webpage to scrape.
	</figcaption>
</figure>

---

I am already seeing a few issues with this; if the FA make any changes to their web markup, the scraping function will no longer work. I also need to figure out how to get the function to look at the correct webpage in the first place. It may be better to launch with manual data entry first, then spend some time investigating my options. This will at least result in a fully functioning app for anyone to use.

> War is ninety percent information. - Napoleon Bonaparte
