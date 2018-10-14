---
layout: post
comments: true
title:  Here comes a new challenger!
tagline: Assessing frameworks.
date:   2017-03-27 08:30:00 +0000
categories: module1
---

**Accessibility is key.**

Monday morning 8am, browsing [HackerNews](https://news.ycombinator.com/news) and I stumble aross the comments for this article: [Python For Android](https://news.ycombinator.com/item?id=13964561); most notably [this one](https://news.ycombinator.com/item?id=13964561) by Raphael Gaschignard [(username rtpg)](https://news.ycombinator.com/user?id=rtpg) and the response by [freakboy3742](https://news.ycombinator.com/user?id=freakboy3742):

- - - 
<figure>
	<img src="/media/2017-03-27/python-voc.png" />
	<figcaption>
		Exchange between rtpg and freakboy3742 on HackerNews.
	</figcaption>
</figure>

Transcription:

**rtpg:**

*This project(Kivy) doesn't use the native Android UI components, so it's a bit of a negative. You don't get any of the stuff like accessibility.
So I remember hearing that a difficulty with hooking Python to Android is that there's some sort of limit to the amount of Java methods you can access through the JNI, but I could never find a proper explanation of this.
If I just had a version of CPython compiled on Android, given Java's nature of running on a virtual machine, wouldn't it be possible to dynamically load arbitrary classes through the JNI and use the native Android stuff?
What are the primary difficulties to this, if you ignore performance?*
	
**freakboy3742:**

*The primary difficulty is that JNI is really limited on Android. It exists, but it's really slow, and there are some hard limits imposed at the kernel level.
An alternative approach is VOC [(http://pybee.org/voc)](http://pybee.org/voc) - this is compiler that takes Python code, and output Java bytecode. This means you can use the Android native UI components, because your Python code becomes indistinguishable from code written in Java. Combine with Briefcase [(http://pybee.org/briefcase)](http://pybee.org/briefcase), and you can get an Android app with one command; combine with Toga [(http://pybee.org/toga)](http://pybee.org/toga), and you can get a cross platform app using native system components.*

*If you want to see this in action, here's a video: [https://www.youtube.com/watch?v=RisCgSIWwLA](https://www.youtube.com/watch?v=RisCgSIWwLA])*

*(Full disclosure - I'm the primary author of these tools)*

---

At the moment a lot of this goes over my head. However having spent a week dealing with Kivy's styling, upon watching the video referenced by freakboy3742 I am excited that native components can be used with Python, thus increasing the accessibility for all users. I get the feeling from my early experience that Kivy is more suited to games which inevitably run in full screen mode and have custom controls, whereas utility apps such as PitchPal may benefit from the native GUI.

Further investigation is needed.



> The one argument for accessibility that doesn't get made nearly often enough is how extraordinarily better it makes some people's lives. How many opportunities do we have to dramatically improve people's lives just by doing our job a little better? - Steve Krug
