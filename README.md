<h1 align="center">A Garden Irrigation System for Home Assistant (Version2)</h1>

It is __important__ to understand that I am only using GitHub literally as a repository. What that means is I just copy my code from my PC to here so that it can be shared. There is no formal version control here other than that inherent in the Github editing history.

One day maybe I'll delve further into how GitHub works but for now I'm afraid that is the situation.

Furthermore, this is not quite a '*pick-it-up-and-drop-it-in*' solution. It nearly is but there are a few idiosyncracities. Be prepared to try it out and spend a short time setting it up.

<h2>Background</h2>

__IMPORTANT__ - This is only a *__preview__* of Version 2 and it will have changes made to it. Please bear that in mind if you decide to use it in any way and be sure to read ALL of this page.

__IMPORTANT__ - Please note that as it stands this assumes using `yaml` mode for Lovelace.

-----

I wrote this package mainly because Version 1 of my irrigation package worked so well for me that the 'chief gardener' in this house (my wife!) decided she would really like to expand it from four zones to eight so as to include the flower beds as well as the lawn.

Whilst I believe that version 1 could easily cope with this by the careful use of copy and paste I decided to do a complete rewrite.

One reason for this decision was that version 1 had been one of the first things I did with HA and I always thought that there were things I could have done better.

Also, being early 2020 many of us found ourselves with too much time on our hands due to the Corona virus so it seemed like a perfect project to pass some of the time.

All that time was not necessarily a good thing though as this project has ended up growing organically day by day rather than through good design. Furthermore as I learnt new techniques in Lovelace this became as much a project about the user interface as it did about the irrigation.

I am by no means a Javascript or CSS programmer so as I learn more, I may well go back at some point and rewrite (improve?) some sections. 

Version 1 was designed around a Sonoff 4ch but for version 2, I will use an 8 relay board controlled with an ESP32.
This in itself should make little difference as ultimately all the package does is turn switches on and off.

This package has been designed with two scheduled cycles per day with each cycle having up to 8 zones. The number of zones can be configured from the UI and like version 1, if more zones are needed some of the 'globals' need to be replicated.

Both scheduled cycles can be set to run at any time on any day(s) of the week.

A manual cycle is also provided.

The watering times can be automatically adjusted based on rainfall and temperature and whilst I think these have been improved in this version, like version 1 this is quite experimental. It is different to version 1 in that both the rainfall and temperature adjustments can be turned on or off independently of each other and for each cycle.

Almost everything can be set from the UI including the friendly names of cycles and zones. Tap/click on most fields to change them in a pop-up (but remember that if you have several browser tabs open the pop-ups may appear on a different tab!). 

__Note -__ Extensive use is made of `!include` to avoid code repetion. The files here are in the folder structure you need to replicate but you can easily change the code if it suits you to have your own folder structure.


<h2>Prerequisites</h2>

There are some [prerequisites](https://github.com/kloggy/HA-Irrigation-Version2/blob/master/prerequisites.md) to setting this up. 

--------------

__Disclaimer__ - This has __NOT__ been extensivley tested. In fact as of now it has only been used on my desk! Treat this as a preview but feel free of course to use, adapt or change it in any way you see fit. But if you do find errors I'd be interested to know so I can look at it although no promises can be made regarding how or when I will get to fix anything. Likewise if you come up with any improvements also please tell me!


<img src="https://github.com/kloggy/HA-Irrigation-Version2/blob/master/screenshots/screenshot-v2.png">
