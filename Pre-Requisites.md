<h2>Prerequisites</h2>

Some things need to be setup in your config outside of this package.

I have detailed them here and provided example yaml code in `prerequisites.yaml`.

(please let me know if you come across anything I have forgotten so that I can update this readme).

----

__sensor.time__ is needed somewhere in your config

__sun2.__ This is a custom component (installable through HACS) that provides lots of solar information and creates `binary_sensor.above_horizon` which is used in the graphs.


However, if you prefer, you could easily provide your own `binary_sensor` using the core Sun component. The state of `sun.sun` is either `above_horizon` or `below_horizon`.

__Recorder.__ In order to show the irrigation times on the 'History' page you must have the `recorder` component installed. This is included in Home Assistant by default.

If you have configured `recorder` to _include_ entities you will need to include the eight sensors:


`irrigation_sensor_zone1_switch`, `irrigation_sensor_zone2_switch`... `irrigation_sensor_zone8_switch`


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
(This might be optional, I don't need to use it anymore but if your columns don't display in the right order
then look in `view_garden_version2.yaml`, there are some lines that need to be uncommented.)
- state-switch (https://github.com/thomasloven/lovelace-state-switch)
- time-picker-card (https://github.com/GeorgeSG/lovelace-time-picker-card)


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

__I use a theme called `dark_teal`__ (available here https://github.com/aFFekopp/dark_teal and via HACS) but it works with the default HA theme and should do with any other 'well behaved' theme as well.

__Weather sensors:__ See https://github.com/kloggy/HA-Irrigation-Version2/blob/master/Weather%20Sensors.md
