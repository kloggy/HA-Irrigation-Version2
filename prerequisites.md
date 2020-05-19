<h2>Prerequisites</h2>

Some things need to be setup in your config for this to work as planned.

Most of them are due to that fact that this package makes use of some functions that I have written that are not used only by the irrigation system.

I have detailed them here and provided example yaml code in `prerequisites.yaml`.

(please let me know if you come across anything I have forgotten so that I can update this readme).

----

__sensor.time__ is needed somewhere in your config

__Notifications.__ Functionality is included but it makes use of a subsystem that I wrote for use throughout my system. 
I use it in this case so that when I am away on holiday it tells me when irrigation starts and ends.
In order for you to be able to adapt this to your own use you will need to define two extra 'helpers' somewhere in your config:

`input_text.notifications_user1_name` and `input_text.notifications_user2_name`

Mine are not in this package because they are part of my notification system.
The actual notifications are also handled outside the package so some changes will be needed to suit whatever notification methods you choose to use.

(@http_edo13 has posted how they use Telegram here: https://community.home-assistant.io/t/my-garden-irrigation/99686/404)

__The Lovelace interface__ makes use of many custom integrations/cards (all installable using HACS https://github.com/hacs):


- browser_mod (https://github.com/thomasloven/hass-browser_mod)
- lovelace_gen (https://github.com/thomasloven/hass-lovelace_gen)

--------

- card-mod (https://github.com/thomasloven/lovelace-card-mod)
- hui-element (https://github.com/thomasloven/lovelace-hui-element)
- button-card (https://github.com/custom-cards/button-card)
- config-template-card (https://github.com/iantrich/config-template-card)
- mini-graph-card (https://github.com/kalkih/mini-graph-card)
- layout-card (https://github.com/thomasloven/lovelace-layout-card)
- state-switch (https://github.com/thomasloven/lovelace-state-switch)
- time-picker-card (https://github.com/GeorgeSG/lovelace-time-picker-card)

Don't forget to update your `resources` as per the instruction in HACS


__I use the Google font family Oswald.__ I have allowed the user to change the font family name via the UI and currently it will be reflected in *some* of the UI. I am not sure how it will affect the layout if you change it but the option is there to play with if you want to.

In the meantime to use Oswald add the following lines to your Lovelace `resources` section:

```
#=== FONTS
- url: https://fonts.googleapis.com/css?family=Oswald
  type: css
```

__I use a theme called `dark_teal`__ (available here https://github.com/aFFekopp/dark_teal and via HACS) but it should work with the default HA theme (and any other 'well behaved' theme) as well.


__Weather sensors:__ I use SmartWeather and DarkSky weather sensors to provide the data for duration adjustments.

__Smart Weather__ is available as a custom component (https://github.com/briis/smartweather) but I simply use REST sensors to receive the data.


For SmartWeather, look [here](https://smartweather.weatherflow.com/map) and see if there are any stations near you. I use five stations local to me and then using a series of sensors take the average. Rainfall data is notoriously hard to collect unless you have your own weather station so I have to leave it up to you to decide how to measure it for you locality. This is probably the part of the stystem  that will need the most attention to customise for you. Or of course you can simply just choose not to use it.

If there are local stations for you then note the station number(s) and then create a REST sensor for each station.

You'll also need to register for an `api_key`.

Of course there is *no requirement* to use Smartweather for rainfall data but if you use something else you will need to change the Lovelace to fit and also the code that collects rainfall measurements.

There are some pointers for setting SmartWeather up [here](https://github.com/kloggy/HA-Irrigation-Version2/blob/master/smartweather_example.md).

__Dark Sky__:

DarkSky will I believe become unavailable in 2021 as Apple have recently bought it.

UPDATE: I have just been told that you can no longer get a *new* api code.

DarkSky is used for temperature data.

My sensor is called `sensor.dark_sky_current_minutely_summary`. This is due to a historic issue as I have two darksky sensors,
one which I use for forecast and one for current information hence the different names
(they both have a different scan_interval but apart from that I can’t remember now why I did that!!).

Because of that there are *some small code changes you need to make*.

1.  In file `lovelace/templates/garden/cycles/item_cycle_header.yaml` you will need to make a small change.

Change the line from:

`label: "[[[ return 'Weather Outlook: ' + states['sensor.dark_sky_current_minutely_summary'].state.replace(',', ',<br>'); ]]]"`

to:

`label: "[[[ return 'Weather Outlook: ' + states['sensor.dark_sky_minutely_summary'].state.replace(',', ',<br>'); ]]]"`

2. In the file `lovelace/templates/garden/settings/temperature/item_settings_temperature_graph.yaml` you need to edit _two_ lines in order to show the temperature graph. 

Change the line:

`  - entity: sensor.dark_sky_current_temperature`

to

`  - entity: sensor.dark_sky_temperature`

and change the line:

`        - entity: sensor.dark_sky_forecast_daytime_high_temperature_0d`

to:

`        - entity: sensor.dark_sky_daytime_high_temperature_0d`

3. In the file `package/garden_weather_temperature.yaml you need to edit _two_ lines.

Change the line:

`          {{ states('sensor.dark_sky_current_temperature') | float > states('input_number.irrigation_actual_high_temp_0') | float }}`

to:

`          {{ states('sensor.dark_sky_temperature') | float > states('input_number.irrigation_actual_high_temp_0') | float }}`

and change the line:

`            {{ states('sensor.dark_sky_current_temperature') }}`

to:

`            {{ states('sensor.dark_sky_temperature') }}`



