<h2>Prerequisites</h2>

Some things need to be setup in your config for this to work as planned.

Most of them are due to that fact that this package makes use of some functions that I have written that are not used only by the irrigation system.

I have detailed them here (please let me know if you come across anything I have forgotten so that I can update this readme).

----

__sensor.time__ is needed somewhere in your config

__Notifications.__ Functionality is included but it makes use of a subsystem that I wrote for use throughout my system. 
I use it in this case so that when I am away on holiday it tells me when irrigation starts and ends.
In order for you to be able to adapt this to your own use you will need to define two extra 'helpers' somewhere in your config:

`input_text.notifications_user1_name` and

`input_text.notifications_user2_name`

Mine are not in this package because they are part of my notification system.
The actual notifications are also handled outside the package so some changes will be needed to suit whatever notification methods you choose to use.

(@http_edo13 has posted how they use Telegram here: https://community.home-assistant.io/t/my-garden-irrigation/99686/404)

__The Lovelace interface__ makes use of many custom cards (all installable using HACS https://github.com/hacs):


- card-mod (https://github.com/thomasloven/lovelace-card-mod)
- browser_mod (https://github.com/thomasloven/hass-browser_mod)
- button-card (https://github.com/custom-cards/button-card)
- multiple-entity-row (https://github.com/benct/lovelace-multiple-entity-row)
- config-template-card (https://github.com/iantrich/config-template-card)
- stack-in-card (https://github.com/custom-cards/stack-in-card)
- mini-graph-card (https://github.com/kalkih/mini-graph-card)
- lovelace_gen (https://github.com/thomasloven/hass-lovelace_gen) 
- layout-card (https://github.com/thomasloven/lovelace-layout-card)
- state-switch (https://github.com/thomasloven/lovelace-state-switch)

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

If there are local stations for you then note the station number(s) and then create a REST sensor for each station like this,

```
  - platform: rest
    resource: !secret smartweather_resource_1
    name: smartweather_1
    value_template: >
      {{ value_json.station_id }}
    json_attributes:
      - status
      - station_units
      - obs    
    scan_interval:
      minutes: NUMBER OF SECONDS
```

You'll need to register for an `api_key`.
Don't make the `scan_interval` too low else it will hammer their servers and you might get blocked.

My secret looks like this:

```
smartweather_resource_1: http://swd.weatherflow.com/swd/rest/observations/station/STATION_NO?api_key=MY_KEY
```

Of course there is *no requirement* to use Smartweather for rainfall data but if you use something else you will need to change the Lovelace to fit and also the code that collects rainfall measurements.

There are some pointers for setting SmartWeather up [here](https://github.com/kloggy/HA-Irrigation-Version2/blob/master/smartweather_example.md).

__Dark Sky__: (DarkSky will I believe become unavailable in 2021 as Apple have recently bought it.)

The following minimal configuaration is needed:

```
sensor:
  - platform: darksky
    api_key: !secret darksky_api_key
    forecast:
      - 0
    monitored_conditions:
      - temperature_high           
      - minutely_summary 
```

There are also two small code changes needed.

Firstly,

In file `item_schedule_cycle_header.yaml` you will need to make a small change.
My sensor is called `sensor.dark_sky_current_minutely_summary`. This is due to a historic issue as I have two darksky sensors,
one which I use for forecast and one for current information hence the different names
(they both have a different scan_interval but apart from that I can’t remember now why I did that!!).

You must change the line:

From:

`label: "[[[ return 'Weather Outlook: ' + states['sensor.dark_sky_current_minutely_summary'].state.replace(',', ',<br>'); ]]]"`

to:

`label: "[[[ return 'Weather Outlook: ' + states['sensor.dark_sky_minutely_summary'].state.replace(',', ',<br>'); ]]]"`

*The schedule start time will not show if this is not correct.* (I have just seen the changes for the latest `button-card` v3.3.1 and I am not sure if this statement is still correct).

Secondly,

You need to edit one line in `section_settings_temperature.yaml` in order to show the temperature graph. 

In the `custom:mini-graph-card` find the line:

`        - entity: sensor.dark_sky_forecast_daytime_high_temperature_0d`

and change it to:

`        - entity: sensor.dark_sky_daytime_high_temperature_0d`


__The file `section_settings_general.yaml`__ needs `sensor.esphome_irrigation_controller_wifi_signal`.

*The settings page will not display correctly without it.* (I have just seen the changes for the latest `button-card` v3.3.1 and I am not sure if this statement is still correct).

If you do not have this sensor simply delete (or comment) this section of that file.

```
#=== Irigation controller WiFi signal strength
- !include
  - item_settings_line.yaml
  - entity: sensor.esphome_irrigation_controller_wifi_signal
    name: Irrigation Controller WiFi Signal Strength
    tap_action: none
```

