---
layout: post
title: ACM Hackathon Experience
---

I was invited to participate in the ACM Hackathon hosted at UC Santa Cruz with my good friend Daniel.

I have only been to a Hackathon once before in my life and I never implemented any solution. My friend Daniel was also a first timer.

This hackathon lasts 12 hours instead of the usual 24, which means that I was extremely interested, as I do not want to waste a complete day stuck in a room.
Usually I don't like hackathons because nothing productive gets done after a good 8 hour work shift, and usually you end up miserable. Not a feeling that I like.

Im the type of dude that likes to wake up early, with a good cup of coffee and breakfast in the stomach before heading to do work.
The morning is the best time to work, as the mind is fresh and ready from a good nights of sleep.

The project that we embarked upon was to create an Amazon Alexa App which would take in queries for the nearest Metro bus coming to the user's location. 

During the Hackathon we were getting stuck on the Santa Cruz Metro bus functionality due to a bug in the Alexa SSML Parsing. 

We were running out of time. 

It was during this time that I decided to pivot away and implement a simple Metro Bus functionality not using SSML (which is a markup language specifically for Alexa to utter words in a special format).
I also decided that we should implement other simple functions such as Loop bus lookup, and a Dininghall is open function.
To win, I knew we had to have more than just one really good feature. I imagined that three decent features outweighed one really good feature.

So in addition to the current functionality, Daniel and I implemented a "Dininghalls open" checker, and a "Loop status" checker.

We were worried that the current implementation on slugroute.com did not have an API or a way of retrieving GPS data from Loop buses.

I snooped around in my view-page-source curiousness and eventually found that they indeed had an API endpoint.

http://bts.ucsc.edu:8081/location/get

Weirdly named. However, it gives the position of each Loop bus Lat/Long coordinates. We sectioned off parts of campus in which these coordinates could fall into, and outputted them back to the user. This gave a good situational awareness of where the current Loop buses resided on campus.

We also levereaged the google Places API to retrieve the currently Opened dininghalls.

With these three functionalities:
1. Nearest Santa Cruz Metro 
2. Loop Bus Status
3. Which Dininghalls are open 

We won 1st prize at HackACM! 🙌 @Devpost http://dvp.st/2oQdNvp

Overall it was a great experience, even though Daniel and I were suffering from common cold during our 12 hour session. I was surprised at how well we worked together and the pace at which we learned AWS Lambda as well as Alexa, having never encountered it before.
I would suggest anyone trying to learn AWS Lambda, to create an Amazon Alexa app as an introductory project.

