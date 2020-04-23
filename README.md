<h1 align="center">A Garden Irrigation System for Home Assistant (Version2)</h1>


<h2>Background</h2>

__IMPORTANT__ - This is only a *__preview__* of Version 2 and it will have changes made to it. Please bear that in mind if you decide to use it in any way and be sure to read ALL of this page.

__IMPORTANT__ - Please note that as it stands this assumes using `yaml` mode for Lovelace.

__NOTE: If you want this version to co-exist with version 1 then you will need to make a small change in *version 1*. In the file `garden_irrigation.yaml` search and replace all occurances of `script.irrigation_irrigate_a_zone` to `script.irrigate_a_zone` and also change the name of that script in the same file.__

-----

I wrote this package mainly because Version 1 of my irrigation package worked so well for me that the 'chief gardener' in this house (my wife!) decided she would really like to expand it from four zones to eight so as to include the flower beds as well as the lawn.

Whilst I believe that version 1 could easily cope with this by the careful use of copy and paste I decided to do a complete rewrite.

One reason for this decision was that version 1 had been one of the first things I did with HA and I always thought that there were things I could have done better.

Also, being early 2020 many of us found ourselves with too much time on our hands due to the Corona virus so it seemed like a perfect project to pass some of the time.

as All that time was not necessarily a good thing though as this project has ended up growing organically day by day rather than through good design. Furthermore as I learnt new techniques in Lovelace this became as much a project about the user interface as it did about the irrigation.

I am by no means a Javascript or CSS programmer so as I learn more, I may well go back at some point and rewrite some sections. 

Version 1 was designed around a Sonoff 4 Channel but for version 2, I will use an 8 relay board controlled with an ESP32.
This in itself should make little difference as ultimately all the package does is turn switches on and off.

This package has been designed with two scheduled cycles per day with each cycle having up to 8 zones. The number of zones can be configured from the UI and like version 1, if more zones are needed some of the 'globals' need to be replicated.

Both scheduled cycles can be set to run at any time on any day(s) of the week.

A manual cycle is also provided.

The watering times can be automatically adjusted based on rainfall and temperature and whilst I think these have been improved in this version, like version 1 this is quite experimental. It is different to version 1 in that both the rainfall and temperature adjustments can be turned on or off independently of each other.

Almost everything can be set from the UI including the friendly names of cycles and zones. Tap/click on most fields to change them in a pop-up but remember that if you have several browser tabs open the pop-ups may appear on a different tab!  

__Note -__ Extensive use is made of `!include` to avoid code repetion. The files here are in the folder structure you need to replicate but you can easily change the code if it suits you to have your own structure.


<h2>Prerequisites</h2>

__sensor.time__ is needed somewhere in your config

I have written in some __notification__ functionality. I use it so that when I am away on holiday it tells me when irrigation starts and ends. In order for this to be used you will need to have two extra 'helpers':

`input_text.notifications_user1_name` and
`input_text.notifications_user2_name`

Mine are elsewhere in my config because they are part of my notification system. The actual notifications are also handled outside the package so some changes will be needed to suit whatever notification methods you choose to use.


__The Lovelace interface__ makes use of many custom cards (all installable using HACS https://github.com/hacs):


- card-mod (https://github.com/thomasloven/lovelace-card-mod)
- browser_mod (https://github.com/thomasloven/hass-browser_mod)
- button-card (https://github.com/custom-cards/button-card)
- multiple-entity-row (https://github.com/benct/lovelace-multiple-entity-row)
- config-template-card (https://github.com/iantrich/config-template-card)
- stack-in-card (https://github.com/custom-cards/stack-in-card)
- mini-graph-card (https://github.com/kalkih/mini-graph-card)
- lovelace_gen (https://github.com/thomasloven/hass-lovelace_gen) 


I use the Google font Oswald. I may consider in future making the font an option so that the user can change it via the UI but that is very low on my priorites. In the meantime to use Oswald add the following lines to your Lovelace `resources` section:

```
#=== FONTS
- url: https://fonts.googleapis.com/css?family=Oswald
  type: css
```

I use a theme called `dark_teal` (available here https://github.com/aFFekopp/dark_teal and via HACS) but I *think* it should work with the default HA theme as well.


__Weather sensors:__ I use SmartWeather and DarkSky weather sensors to provide the data for duration adjustments.

Smart Weather is available as a custom component (https://github.com/briis/smartweather) but I simply use REST sensors to receive the data.
DarkSky will I believe become unavailable in 2021 as Apple have recently bought it.

------------

__Finally:__ As expected, I am getting some feedback suggesting that the initial setup of this package is not entirely straight forward. This relates mostly to getting the UI to display correctly. I will at some point try and collate all the issues and where possible include code to get around them or at the very least document how to avoid and work around them. In the meantime I will add here the feedback I receive (verbatim).

- the file `section_settings_general.yaml` needs `sensor.garden_irrigation_controller_wifi_signal` for the correct settings display
- the file `item_cycle_schedule_title` needs `sensor.dark_sky_current_minutely_summary` for show label, I used `sensor.dark_sky_hourly_summary`.
- in the “switch zone name” you have to insert the name with “switch”, for example “switch.valve1”

--------------

__Disclaimer__ - This has __NOT__ been extensivley tested. In fact as of now it has only been used on my desk! Treat this as a preview but feel free of course to use, adapt or change it in any way you see fit. But if you do find errors I'd be interested to know so I can look at it although no promises can be made regarding how or when I will get to fix anything. Likewise if you come up with any improvements also please tell me!
