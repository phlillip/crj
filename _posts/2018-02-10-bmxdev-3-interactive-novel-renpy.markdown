---
layout: post
comments: true
title:  BMX Dev S1W3 - activity
tagline: Interactive novels with Ren'Py.
date:   2018-02-10 18:00:00 +0000
categories: module4
---

**Create an interactive novel using Ren'Py, loosely based on the game creation activity from Week 2. There must be at least three interactive moments within the novel.**

### Design

Using my previous game concept as a base, I chose to create a flow diagram to help me understand the necessary choices and content for my novel:

<figure>
	<img src="/media/2018-02-10/vaporwave__process-flow.jpg" />
	<figcaption>
		Flow diagram for vaporwave.
	</figcaption>
</figure>

The 3 main choices in the game are as follows:

1. Choose music to use with the app - this either ends the game immediately (bad ending) or allows you to carry on.
2. Choose which type of surfboard - this gives you two distinct story paths. The longboard is the only way to the good ending, whie the shortboard gives you two variations of the sad ending.

Shortboard path

1. Allow fan to take a selfie - sad ending.
2. Don;t allow fan to take a selfie - sad ending with additional sadness.

Longboard path

1. Don't save the animals - leads you to an OK ending.
2. Save the animals - leads you to the good ending.

### Implementation

I spent a couple of hours getting to grips with Ren'Py, playing with various settings and trying to incorporate as many features as I could into my story. Here is the screencast of the first version:

<video src="/media/2018-02-10/vaporwave_screencast--1.mp4" controls>
Sorry, your browser doesn't support embedded videos, 
but don't worry, you can <a href="/media/SMRT.mp4">download it</a>
and watch it with your favorite video player!
</video>

### Moving Forward

Obviously this was an exercise in getting to grips with the technology and the logic behind it all, however my script writing needs serious work. The script, together with the graphics and sound are base-level placeholders in this instance.

I will seek out further information regarding copyright; imagery can be created by myself, however the use of music downloaded free from the internet needs careful consideration.

### script.rpy

	# Declare characters used by this game.
	define k = Character('Kev', color="#c8ffc8")
	define d = Character('Doc Si', color="#c8c8ff")
	define f = Character('Fan', color="#ff0000")

	# This is a variable that is False unless the reader selects a longboard
	default longboard = False
	# False unless the reader stops the fan having a selfie
	default selfie = False

	# The game starts here.
	label start:

	    # Start by playing some music.
	    play music "chains.mp3" fadein 5.0

	    scene black
	    with fade

	    "It's 2047 and the seas are polluted."

	    scene bg pollution
	    with fade

	    "Deep-sea landfills created 30 years ago have ruptured and waste is being washed to shore \ \ \ d a y \ \ \ a f t e r \ \ \ d a y ..."

	    "The world’s coastlines are being destroyed."

	    show kev bw back
	    with pixellate

	    "Kev can no longer run his surf business or enjoy his favourite past-time."

	    k "There must be something I can do about this!"

	    
	    hide kev bw back
	    show doc white smile
	    with vpunch

	    d "There is! With your skills and my genius we can solve the problem!"

	    scene bg cave
	    with fade

	    show doc white smile
	    with vpunch

	    d "Through my work at \ \ \ T h e \ \ \ B r i t i s h \ \ \ S e a \ \ \ R e s e a r c h \ \ \ C e n t r e ..."

	    d "... I have developed a revolutionary technology that vapourises plastic and oils using certain vibrational frequencies found in \ \ \ v a p o r w a v e \ \ \ music..."

	    d "...I have created a voice-controlled app that can harness this technology using the vibration module found in a mobile phone!"

	    hide doc white smile
	    show kev bw back
	    with pixellate

	    k "Oh yeah, what's it called?"

	    hide kev bw back
	    show doc white smile
	    with vpunch

	    d "It's called “V A P O R W A V E”"

	    d "If you can build a custom surfboard that will mount a mobile phone..."

	    d "...then together we can clean the world's beaches!"

	    hide doc white smile
	    show kev bw back
	    with dissolve

	    # decision 1: die or continue game

	    menu:

	        "But first we need to pick the right music..."

	        "every breaking wave":
	            jump badending

	        "i \ \ \ b l e s s  \ \ \ t h e \ \ \ r a i n s":
	            play music "toto.mp3"

	            scene black
	            with fade

	            "... d o w n  \ \ \ i n  \ \ \ a f r i c a ..."
	            with fade

	    # story continues

	    hide kev bw back

	    scene bg cave
	    with fade
	    show doc white smile
	    with vpunch

	    d "Excellent! Let's begin!"

	    d "Now, here's a mobile phone with my \ \ \ v a p o r w a v e \ \ \ app installed, simply mount it to your surfboard and get cleaning!"

	    # NEW SCENE: Kev's workshop

	    scene bg pc
	    show kev bw back
	    with fade

	    "Hmmm, which board should I use, I've got a longboard and a shortboard"

	    menu:

	        "The question is, which board to make..."

	        "...a \ \ \ l o n g b o a r d \ \ \ dude...":
	            jump longboard

	        "A shortboard homie!":
	            jump shortboard

	    label shortboard:

	        scene bg silversurfer

	        play music "onlyoveryou.mp3"

	        "I grab my shortboard and my raddest wetsuit, it's lime green!"

	        "I can't wait to head to the beach and shred some waves, i'll look great and i'll be saving the day!"

	        "After clearing the beach using a number of power moves, Kev is approached as he heads back up the beach."

	        f "Wow it's really you! Can I get a selfie?"

	        menu:

	            "Sure go right ahead":
	                jump sadending

	            "Sorry I don't have time, I've got beaches to clean!":
	                $ selfie = True
	                jump sadending

	    label longboard:

	        $ longboard = True

	        "With my longboard I can turn the phone up to it's maximum power and still catch waves"

	        "Kev sweeps along the waves, cleaning everything in sight"

	        "He comes across a baby seal trapped in oil and tangled in plastic netting, it looks messy"

	        menu:

	            "s a v e \ \ \ t h e \ \ \ a n i m a l s":
	                jump goodending

	            "Chase the sun":
	                jump okending

	label badending:
	    stop music

	    "No Kev. U2 songs are never the answer."

	    play music "toolittletoolate.mp3" fadein 5.0
	    scene black
	    with dissolve

	    "The pollution builds up..."

	    "...the very air we breathe is now contaminated..."

	    scene bg death
	    with dissolve

	    "...if only we had b l e s s e d    t h e    r a i n s..."

	    "{b}Bad Ending{/b}."

	    return

	label goodending:
	    scene bg dolphin

	    "Kev plucks the seal from the sea and it sits in front of him on the board"

	    "Kev goes on to clean all the beaches and save trapped wildlife."

	    "Peace and tranquility is returned to the oceans."

	    "Kev returns to his peaceful life of surfing and teaching."

	    "{b}... g o o d \ \ \ e n d i n g ...{/b}"

	    return

	label okending:
	    play music "lonely.mp3"
	    scene bg surf

	    "Kev leaves the seal, worried it will slow him down too much."

	    "Kev goes on to clean all the beaches."

	    "Peace and tranquility is returned to the oceans."

	    "However, many animals have died in the pollution."

	    "The eco-balance is disturbed and many species become extinct with no food chain to support them."

	    "Kev returns to his peaceful life of surfing and teaching, but now on a strict globally enforced diet of insects."

	    "{b}ok ending{/b}."

	    return

	label sadending:
	    scene bg surf
	    play music "onemoreyear.mp3" fadein 5.0

	    "Kev goes on to clean all the beaches."

	    "Peace and tranquility is returned to the oceans."

	    "However, due to his superstar status he has influenced a generation of surfers."

	    if selfie:
	        show kev bw back
	        "...all of whom hate him for shunning their photo attempts. They throw rocks at him in the water."

	        k "...I bust my stick I shred so bad..."

	    "The beaches are crowded and Kev can no longer surf in peace. He lives out a quiet life of sadness."

	    "{b}sad ending{/b}."

	    return