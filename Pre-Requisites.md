<h2>Prerequisites</h2>

__sensor.time__ is needed somewhere in your config

```
#============
#=== Sensors
#============
sensor:
  #==================
  #=== Time and Date 
  #==================
  - platform: time_date
    display_options:
      - 'time'
      - 'date'
```

__sun2.__ This is a custom component (installable through HACS using the repository `https://github.com/pnbruckner/ha-sun2`) that provides lots of solar information and creates `binary_sensor.above_horizon` which is used in the graphs.


However, if you prefer, you could easily provide your own `binary_sensor` using the core Sun component. The state of `sun.sun` is either `above_horizon` or `below_horizon`.

__Recorder.__ In order to show the irrigation times on the 'History' page you must have the `recorder` component installed. This is included in Home Assistant by default.

There are many ways to include and exclude domains and entities in Recorder but you need to ensure that the following sensors are included:


`irrigation_sensor_zone1_switch`, `irrigation_sensor_zone2_switch`... `irrigation_sensor_zone16_switch`

Also there are *lot* of entities created by this package, many (most?) of which you can exclude from [Recorder](https://www.home-assistant.io/integrations/recorder/) in order to limit the DB size and processor time needed to record them.

for example to prevent the irrigation package input numbers from being recorded you can use this:
```
#=============
#=== Recorder
#=============
recorder:
  purge_keep_days: 3
  exclude:
    entity_globs:
      input_number.irrigation*
```
Be aware that this will only keep three days of any data.

__Notifications.__ Functionality is included but it makes use of a subsystem that I wrote for use throughout my system. 
I use it in this case so that when I am away on holiday it tells me when irrigation starts and ends.
In order for you to be able to adapt this to your own use you will need to define two extra 'helpers' somewhere in your config:

```
#================
#=== Input texts
#================
input_text:
  notifications_user1_name:
    min: 0
    max: 20

  notifications_user2_name:
    min: 0
    max: 20
```

Mine are not in this package because they are part of my notification system.
The actual notifications are also handled outside the package so some changes will be needed to suit whatever notification methods you choose to use.

(@http_edo13 has posted how they use Telegram here: https://community.home-assistant.io/t/my-garden-irrigation/99686/404)

__Custom integrations/cards__ (all installable using HACS https://github.com/hacs):

*Integrations (don't forget to follow the installation instructions for these!)*

- browser_mod (https://github.com/thomasloven/hass-browser_mod)
- lovelace_gen (https://github.com/thomasloven/hass-lovelace_gen)

--------

*Custom Cards*

- card-mod (https://github.com/thomasloven/lovelace-card-mod)
- hui-element (https://github.com/thomasloven/lovelace-hui-element)
- button-card (https://github.com/custom-cards/button-card)
- config-template-card (https://github.com/iantrich/config-template-card)
- mini-graph-card (https://github.com/kalkih/mini-graph-card)
- layout-card (https://github.com/thomasloven/lovelace-layout-card)
- state-switch (https://github.com/thomasloven/lovelace-state-switch)
- time-picker-card (https://github.com/GeorgeSG/lovelace-time-picker-card)


__Weather sensors:__ See https://github.com/kloggy/HA-Irrigation-Version2/blob/master/Weather%20Sensors.md

__Fonts__ You can change the font used via the UI. It defaults to whatever is used in your current theme but a condensed font will display better as there is a lot squeezed onto the screen.

I have had good success with Oswald and Dosis but you can experiment with any font you like.
To use these fonts add the following lines to your Lovelace `resources` section:

```
#=== FONTS
- url: https://fonts.googleapis.com/css?family=Oswald
  type: css
- url: https://fonts.googleapis.com/css?family=Dosis
  type: css
```

__Themes__

It is completely outside the scope of this project (see [Themes](https://www.home-assistant.io/integrations/frontend/) for more information) but to get the blurred background seen behind pop-ups in the screen shots here you need to add this to your current theme file:

```
  #=== blurring-background-behind-popup
  dialog-backdrop-filter: blur(5px)
  dialog-border-radius: 1em;
  dialog-box-shadow: 0em 0em 0.5em;
  iron-overlay-backdrop-opacity: 1
  iron-overlay-backdrop-background-color: rgba(0, 0, 0, 0.32)
  mdc-dialog-box-shadow: 0em 0em 0.5em
  mdc-shape-medium: 1em
```

If you use the default theme then you can create `my-theme.yaml` with all the above prefixed with:

```
my-theme:
```

and suffixed with:

``` 
  modes:
    light: 
      dummy-colour: rgb(255, 255, 255)

    dark:
      dummy-colour: rgb(255, 255, 255)
```
(`light` and `dark` modes need something so create dummy variables)

Then change your current theme to `my-theme`

