
<h1 align="center">A Garden Irrigation System for Home Assistant</h1>

__Please note that I recommend some understanding of Home Assistant in general and of Lovelace in particular if you choose to try this out.__

# November 2022

I have been tinkering with this package over the last few months mainly to keep it up to date with changes in HA as well as some small cosmetic improvements and code clean-ups. I have uploaded new files.

PLEASE make sure you keep a backup copy just in case. Everything has been working for me over the summer!

Finally...
I had every intention of improving the documentation for this package but sadly I just don't have the time anymore. 

# UPDATED - July 2021 (requires HA version 2021.7)

__WARNING__ - As you will read below, I don't use GitHub properly. For this update I have literally deleted everything and re-uploaded it. Apologies in advance but I'm not sure how that might affect anyone who does use gitHub properly.



This update is mostly just to tidy up a few things. It it includes some very minor bug fixes and some cosmetic improvements. It adds a little more cosistency to the code and the Lovelace files especially have had a few more comments added to (hopefully) make them more readable for those who like to tinker.

### There is one new feature:

You can now set a Cycle Schedule to only run *today*.
To explain, I only use the morning schedule. Afternoon watering is done on an ad-hoc basis but if I will be out all day I would turn on the Afternoon schedue and then need to remember to turn it off when I got home. Now I can have it on just for one day.

This setting is found in the Start Time pop-up.

### Breaking Change

Please note that a lot of files have been renamed and the entire folder structure has been changed for the fronet end (Lovelace). This is to provide greater constency, remove redundancies and to generally tidy things up.

### Warning

I understand that Smartweather will soon be [removing public access to thier api](https://community.home-assistant.io/t/smartweather-get-local-weather-data-combined-with-ai-powered-forecast/105151/171 "removing public access to thier api"). The date this was supposed to be happening has passed but my api key still works. However, I no longer use Smartweather and it is possible that at some point I will remove it from this package. I will definitely not be making any more updates or changes to this part of the package.

### Optional things included for reference

*Notifications.* Because I have a centralised 'sub-system' that handles all my notifications it is beyond the scope of this project to provide a common solution that works for everyone but my example (`irrigation_notifications.yaml`) should put you on the right path.

*Using a remote control button.* I use this almost every day (instead of the afternoon schedule). Be aware that as written (`irrigation_remote_control.yaml`) it handles a four button remote control which also allows a different command if two buttons are pressed at the same time. Again, you will need to modify the files for own use case but that should be fairly self explanatory. My example also deals with consecutive button presses; queuing up the commands.

### Sources of reference (not checked by me for currency or accuracy!)

Apart from my instructions here, there are some 'real world' guides on how to set up and configure this package which were written by people who have done it. I will link to them here:

By @itajackass - [A guide for Italian people]( https://www.domoticadiy.it/2020/06/irrigazione-smart-my-garden-irrigation-home-assistant/) - perfectly readable using Google Translate and has been confirmed to work by another user.

By @bbogdanmircea - [Setup guide](https://github.com/bbogdanmircea/HA-Irrigation-Version2) - A fork of this project which uses more than the (original) default maximum eight zones and also includes a general setup guide. It contains some good information but I understand that at the time of writing this it is not complete.

### Important Notes 

Please understand that I am posting this project *purely as a way to share it* because people showed an interest in Version 1. It is *my personal solution* which I am more than happy for anyone to use in any way they see fit. I am prepared to help people get this working but only if you have shown that you have tried more than just copying the files. The prerequisites are documented and must be followed.

I am only using GitHub literally as a repository. What that means is I simply copy my code from my PC to here so that it can be shared. There is no formal version control here other than that inherent in the Github editing history.

One day maybe I'll delve further into how GitHub works but for now I'm afraid that is the situation.

# Installation

Installation shuld be fairly simple it is just a matter of creating a folder for the package and a folder for the front end (Lovelace).

__Folder Structure:__ There are two elements to this project, the functional code (automations, scripts etc.) and the Lovelace UI.

The folder named `lovelace` should be copied in its entirety into your config folder. If you already have a `lovelace` folder in your config folder then simply copy the folder `lovelace\garden_irrigation` and the file `lovelace\view_garden_version2.yaml` into it. This structure is not optional. There are a lot of references to absolute file locations so unless you edit the code to reflect changes you make, it will not work.

The folder named `Garden Irrigation` is the functional code. This folder should be put somehwere such that HA recognises that location as its location for packages.

### Prerequisites

There are some [prerequisites](https://github.com/kloggy/HA-Irrigation-Version2/blob/master/Pre-Requisites.md) to setting this up. PLEASE READ THEM. Any questions posted that look like they haven't been read may be ignored.


Please note that as it stands this assumes that you are using `yaml` mode for Lovelace because that is what I use.

--------------

<h2>Background</h2>

I wrote this package mainly because Version 1 of my irrigation package worked so well for me that the 'chief gardener' in this house (my wife!) decided she would really like to expand it from four zones to eight so as to include the flower beds as well as the lawn.

Whilst I believe that Version 1 could easily cope with this by the careful use of copy and paste I decided to do a complete rewrite.

One reason for this decision was that Version 1 had been one of the first things I did with HA and I always thought that there were things I could have done better. Furthermore, Lovelace appeared since then so there is scope to do much more with the user interface.

Also, being early 2020 many of us found ourselves with too much time on our hands due to the Corona virus so it seemed like a perfect project to pass some of the time.

As I was writing it I was also learning new techniques in Lovelace from the forum so this became as much a project about the user interface as it did about the irrigation.

But... I am by no means a Javascript or CSS programmer so there may well be things I (or you) can improve on at some point in the future. 

Version 1 was designed around a Sonoff 4ch but for Version 2 I will use an 8 relay board controlled with an ESP32.
This in itself should make little difference as ultimately all the package does is turn switches on and off.

This package has been designed with two scheduled cycles per day with each cycle having up to 16 zones and all zones can be scheduled to run on any day(s) of the week.

A manual cycle is also provided.

The watering times can be automatically adjusted based on rainfall and temperature and whilst I think this has been improved in Version 2, as in Version 1 this is quite experimental. It is different to (better than) Version 1 in that both the rainfall and temperature adjustments can be turned on or off independently of each other and separately for each cycle and the sensors can easily be configured to use any weather source you choose.

Almost everything can be set from the UI including the friendly names of cycles and zones. Tap/click on fields to change them in a pop-up (but remember that if you have several browser tabs open the pop-ups may appear on a different tab!). 

__Note -__ Extensive use is made of `!include` to avoid code repetition. You need to replicate the folder structure in order for it to work. You can change the lovelace code if it suits you to have your own folder structure but I can't help if you choose to do that.

As it stands you need a `lovelace` folder and of course the usual folder that your packages are in.

(See the following documentation for [packages](https://www.home-assistant.io/docs/configuration/packages/) and [Lovelace](https://www.home-assistant.io/lovelace/dashboards-and-views/)).

--------------

__Disclaimer__ - I have been using this package now for a few weeks and whilst I do not use all the features I am confident that it all works as it has now also been used by some other people. Feel free of course to use, adapt or change it in any way you see fit. But if you do find errors I'd be interested to know so I can look at it although no promises can be made regarding how or when I will get to fix anything.


Likewise if you come up with any improvements also please tell me!

![image](https://user-images.githubusercontent.com/38220016/126191072-7cecfe10-261d-418c-8d9a-ee688a4b70f6.png)


