---
layout: post
comments: true
title:  stagdo.info
tagline: Working without a framework
date:   2018-04-21 11:00:00 +0000
categories: module4
---

**An attempt to fully understand the technology**

When it came to merging my prototype bmx builder in with the rest of my app, I realised I didn't fully understand how the framework actually worked. My entire life I have avoided jQuery for the simple reason that I didn't want to be plugging libraries in without understanding the underlying technology, so I decided to hand-build a single page application (SPA) before going back to Framework7.

I found an excellent youtube video tutorial [[1]](#ref) by Curran Kelleher, demonstrating an iterative way to implement navigation for a SPA using AJAX. He provided all his code examples [[2]](#ref) to work through along the way so I fully understood what was going on.

From this, I then decided to apply my long-standing idea of a stag do management app - ideal when you are abroad and don't want to have to keep reloading pages - and built out a real test case to use for my upcoming stag do in April 2018.

<figure>
	<img src="/media/2018-04-21/stag-page.jpg" />
	<figcaption>
		A sample page of the stagdo app showing the AJAX menu which doesn't force a page reload.
	</figcaption>
</figure>

The result is https://karls.stagdo.info, a password protected, AJAX powered SPA powered by a JSON back-end! I have been waiting for years to be able to write a sentence like that and fully understand it *and* fully deserve to say it!

I intend to turn this into a paid service to compete with the (extremely overpriced!) competition - the likes of chillisauce and red seven leisure so I will need to build out a control panel for the organiser. I have started planning for this by dynamically creating the "stags" page from a JSON file which I can write to from the control panel:

```
{
   "stags": [{
         "name": "stag__name",
         "nickname": "stag__nickname",
         "number": "stag__number",
         "indie": "stag__indie-outfit",
         "football": "stag__football-outfit",
         "tshirt": "stag__tshirt-size",
         "balance": "stag__debt"
      }
   ]
}
```

<figure>
	<img src="/media/2018-04-21/stag-card.jpg" />
	<figcaption>
		A generated stag card (with sensitive data blurred out) and debt summary.
	</figcaption>
</figure>

This also calculates the total amount owed to the organiser - in practice I found it very handy for everyone in the group to see who were the bad payers and how much I was owed, it certainly pulled on a few heart strings and got the money rolling in. It also provides a handy telephone link so I could phone any of the stags easily - often the organiser is dealing with people they have never met so they wouldn't necessarily have all the phone numbers to hand.

My first X customers will be able to request a customisation feature which I will roll out to all future customers, to help me build up the necessary features. At first thought, I plan to provide a custom subdomain ```customer.stagdo.info``` for 1 year at a fixed price.

<span id="ref"></span>
**References**  
1. Kelleher, C. Navigation for Single Page Applications, *YouTube*, Retrieved March 08, 2018: https://youtu.be/xN9QxPtK2LM
2. Kelleher, C. Navigation for Single Page Applications, *GitHub*, Retrieved March 08, 2018: https://github.com/curran/screencasts/tree/gh-pages/navigation