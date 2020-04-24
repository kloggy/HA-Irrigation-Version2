<h2>Prerequisites</h2>

Some things need to be setup in your config for this to work as planned.

Most of them are due to that fact that this package makes use of some functions that I have written that are not used only by the irrigation system. I have detailed them here.

----

__sensor.time__ is needed somewhere in your config

__Notifications.__ Functionality is included but it makes use of a subsystem that I wrote for use throughout my system. 
I use it in this case so that when I am away on holiday it tells me when irrigation starts and ends.
In order for you to be able to adapt this to your own use you will need to define two extra 'helpers' somewhere in your config:

`input_text.notifications_user1_name` and

`input_text.notifications_user2_name`

Mine are not in this package because they are part of my notification system.
The actual notifications are also handled outside the package so some changes will be needed to suit whatever notification methods you choose to use.


__The Lovelace interface__ makes use of many custom cards (all installable using HACS https://github.com/hacs):


- card-mod (https://github.com/thomasloven/lovelace-card-mod)
- browser_mod (https://github.com/thomasloven/hass-browser_mod)
- button-card (https://github.com/custom-cards/button-card)
- multiple-entity-row (https://github.com/benct/lovelace-multiple-entity-row)
- config-template-card (https://github.com/iantrich/config-template-card)
- stack-in-card (https://github.com/custom-cards/stack-in-card)
- mini-graph-card (https://github.com/kalkih/mini-graph-card)
- lovelace_gen (https://github.com/thomasloven/hass-lovelace_gen) 

Don't forget to update your `resources` as per the instruction in HACS


__I use the Google font Oswald.__ I may consider in future making the font an option so that the user can change it via the UI but that is very low on my priorites.
In the meantime to use Oswald add the following lines to your Lovelace `resources` section:

```
#=== FONTS
- url: https://fonts.googleapis.com/css?family=Oswald
  type: css
```

__I use a theme called `dark_teal`__ (available here https://github.com/aFFekopp/dark_teal and via HACS) but I *think* it should work with the default HA theme as well.


__Weather sensors:__ I use SmartWeather and DarkSky weather sensors to provide the data for duration adjustments.

__Smart Weather__ is available as a custom component (https://github.com/briis/smartweather) but I simply use REST sensors to receive the data.
DarkSky will I believe become unavailable in 2021 as Apple have recently bought it.

Look [here](https://smartweather.weatherflow.com/map) and see if there are any stations near you.

If there are you need to note the station number and then create a REST sensor for each station like this,

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

Of course there is *no requirement* to use Smartweather but if you use something else you will need to change the Lovelace to fit and also the code that collects rainfall measurements.

__Dark Sky__: The darksky sensor must have `minutely_summary` as one of it's monitored conditions.
The file `item_schedule_cycle_header` makes use of it and it appears in one line but you will need to make a small change.
My sensor is called `sensor.dark_sky_current_minutely_summary`. This is due to a historic issue as I have two darksky sensors,
one which I use for forecast and one for current information hence the different names
(they both have a different scan_interval but apart from that I can’t remember now why I did that!!).

You must either change your sensor name to match mine or more likely, change the sensor to match yours.

From:

`label: "[[[ return 'Weather Outlook: ' + states['sensor.dark_sky_current_minutely_summary'].state.replace(',', ',<br>'); ]]]"`

to:

`label: "[[[ return 'Weather Outlook: ' + states['sensor.dark_sky_current_summary'].state.replace(',', ',<br>'); ]]]"`

*The schedule start time will not show if this is not correct*

__The file `section_settings_general.yaml`__ needs `sensor.esphome_irrigation_controller_wifi_signal`.

The settings page will not display correctly without it.
If you do not have this sensor simply delete (or comment) this section of that file.

```
#=== Irigation controller WiFi signal strength
- !include
  - item_settings_line.yaml
  - entity: sensor.esphome_irrigation_controller_wifi_signal
    name: Irrigation Controller WiFi Signal Strength
    tap_action: none
```

