__This is an example ONLY, for using SmartWeather__

DO NOT SIMPLY COPY THIS FILE AND INCLUDE IN YOUR CONFIG WITHOUT UNDERSTANDING IT!

I include this to help you use SmartWeather if you so chose to do.
This is __my__ SmartWeather config which uses five stations it may need some
changes to make it suitable for you. Or, it might work as it is.

I also use SmartWeather for Illuminance so that is here too but plays no part
in the irrigation package, I use it with my lights automations. There is also
a fallback Brightness sensor in here that I use when the SmartWeather stations
went offline. It is less useful if you use several stations as I now do but it
is left here for completeness.
You can use it it in your config if it is useful.

I will NOT be actively updating this file in the unlikely event that I make any
changes to it. I will endeavour to help setting it up if you have any specific
questions but remember that I am only offering this file as a guide to help you.

DO NOT SIMPLY COPY THIS FILE AND INCLUDE IN YOUR CONFIG WITHOUT UNDERSTANDING IT!

__smartweather.yaml__
```
#===================
#=== Input Booleans
#===================
input_boolean:
  #================================================
  #=== Indicate which stations to use for rainfall
  #================================================
  smartweather_rainfall_use_location_1:
  smartweather_rainfall_use_location_2:
  smartweather_rainfall_use_location_3:
  smartweather_rainfall_use_location_4:
  smartweather_rainfall_use_location_5:


#================
#=== Input Texts
#================
input_text:

  #=== Smartweather Location Codes
  smartweather_location_code1:
    min: 0
    max: 7
    initial: !secret smartweather_location_code_1

  smartweather_location_code2:
    min: 0
    max: 7
    initial: !secret smartweather_location_code_2

  smartweather_location_code3:
    min: 0
    max: 7
    initial: !secret smartweather_location_code_3

  smartweather_location_code4:
    min: 0
    max: 7
    initial: !secret smartweather_location_code_4

  smartweather_location_code5:
    min: 0
    max: 7
    initial: !secret smartweather_location_code_5


  #=== Smartweather Location Names
  smartweather_location_name1:
    min: 0
    max: 30
    initial: !secret smartweather_location_name_1

  smartweather_location_name2:
    min: 0
    max: 30
    initial: !secret smartweather_location_name_2

  smartweather_location_name3:
    min: 0
    max: 30
    initial: !secret smartweather_location_name_3

  smartweather_location_name4:
    min: 0
    max: 30
    initial: !secret smartweather_location_name_4

  smartweather_location_name5:
    min: 0
    max: 30
    initial: !secret smartweather_location_name_5


#============
#=== Sensors
#============
sensor:

  #====================================================
  #=== SmartWeather Sensors 
  #=== see - https://smartweather.weatherflow.com/map
  #===       for location of weather stations
  #===
  #=== Used to create sensors for
  #===   illuminance
  #===   rain today
  #===   rain yesterday
  #====================================================

  #=== Station 1 (see secrets.yaml)
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
      minutes: 86400

  #=== Station 2 (see secrets.yaml)
  - platform: rest
    resource: !secret smartweather_resource_2
    name: smartweather_2
    value_template: >
      {{ value_json.station_id }}
    json_attributes:
      - status
      - station_units
      - obs    
    scan_interval:
      minutes: 86400

  #=== Station 3 (see secrets.yaml)
  - platform: rest
    resource: !secret smartweather_resource_3
    name: smartweather_3
    value_template: >
      {{ value_json.station_id }}
    json_attributes:
      - status
      - station_units
      - obs    
    scan_interval:
      minutes: 86400

  #=== Station 4 (see secrets.yaml)
  - platform: rest
    resource: !secret smartweather_resource_4
    name: smartweather_4
    value_template: >
      {{ value_json.station_id }}
    json_attributes:
      - status
      - station_units
      - obs    
    scan_interval:
      minutes: 86400

  #=== Station 5 (see secrets.yaml)
  - platform: rest
    resource: !secret smartweather_resource_5
    name: smartweather_5
    value_template: >
      {{ value_json.station_id }}
    json_attributes:
      - status
      - station_units
      - obs    
    scan_interval:
      minutes: 86400


  #=== Average Smartweather Illuminance
  - platform: min_max
    type: mean
    name: Smartweather Average Illuminance
    entity_ids:
      - sensor.smartweather_1_illuminance
      - sensor.smartweather_2_illuminance
      - sensor.smartweather_3_illuminance
      - sensor.smartweather_4_illuminance
      - sensor.smartweather_5_illuminance


  #=== Average Smartweather Rain Today
  - platform: min_max
    type: mean
    name: Smartweather Average Rain today
    entity_ids:
      - sensor.smartweather_1_rain_today
      - sensor.smartweather_2_rain_today
      - sensor.smartweather_3_rain_today
      - sensor.smartweather_4_rain_today
      - sensor.smartweather_5_rain_today


  #=== Average Smartweather Rain Yesterday
  - platform: min_max
    type: mean
    name: Smartweather Average Rain yesterday
    entity_ids:
      - sensor.smartweather_1_rain_yesterday
      - sensor.smartweather_2_rain_yesterday
      - sensor.smartweather_3_rain_yesterday
      - sensor.smartweather_4_rain_yesterday
      - sensor.smartweather_5_rain_yesterday


  - platform: template
    sensors:
      #=============================
      #=== SmartWeather Illuminance 
      #=============================
      smartweather_1_illuminance:
        friendly_name: SmartWeather (id 1) Illuminance
        value_template: >
          {% set obs = state_attr('sensor.smartweather_1', 'obs') %}
          {% if obs is sequence and obs|length > 0 and obs[0].brightness is defined %}
            {{ obs[0].brightness }}
          {% else %}
            unknown
          {% endif %}
        unit_of_measurement: lux

      smartweather_2_illuminance:
        friendly_name: SmartWeather (id 2) Illuminance
        value_template: >
          {% set obs = state_attr('sensor.smartweather_2', 'obs') %}
          {% if obs is sequence and obs|length > 0 and obs[0].brightness is defined %}
            {{ obs[0].brightness }}
          {% else %}
            unknown
          {% endif %}
        unit_of_measurement: lux

      smartweather_3_illuminance:
        friendly_name: SmartWeather (id 3) Illuminance
        value_template: >
          {% set obs = state_attr('sensor.smartweather_3', 'obs') %}
          {% if obs is sequence and obs|length > 0 and obs[0].brightness is defined %}
            {{ obs[0].brightness }}
          {% else %}
            unknown
          {% endif %}
        unit_of_measurement: lux

      smartweather_4_illuminance:
        friendly_name: SmartWeather (id 4) Illuminance
        value_template: >
          {% set obs = state_attr('sensor.smartweather_4', 'obs') %}
          {% if obs is sequence and obs|length > 0 and obs[0].brightness is defined %}
            {{ obs[0].brightness }}
          {% else %}
            unknown
          {% endif %}
        unit_of_measurement: lux

      smartweather_5_illuminance:
        friendly_name: SmartWeather (id 5) Illuminance
        value_template: >
          {% set obs = state_attr('sensor.smartweather_5', 'obs') %}
          {% if obs is sequence and obs|length > 0 and obs[0].brightness is defined %}
            {{ obs[0].brightness }}
          {% else %}
            unknown
          {% endif %}
        unit_of_measurement: lux

      # #=== Average Smartweather Illuminance
      # smartweather_average_illuminance:
      #   friendly_name: SmartWeather Average Illuminance
      #   entity_id:
      #     - sensor.smartweather_2_illuminance
      #     - sensor.smartweather_3_illuminance
      #     - sensor.smartweather_5_illuminance
      #   value_template: >
      #     {% set entities = ['sensor.smartweather_2_illuminance',
      #                        'sensor.smartweather_3_illuminance',
      #                        'sensor.smartweather_5_illuminance'] %}
      #     {% set ns = namespace(count=0, value=0) %}
      #     {% for e in entities %}
      #       {% set s = states(e) %}
      #       {% if s != 'unknown' and
      #             s != 'unavailable' and
      #             s != '' %}
      #         {% set ns.count = ns.count + 1 %}
      #         {% set ns.value = ns.value + s | float %}
      #       {% endif %}
      #     {% endfor %}
      #     {% if ns.count == 0 %}
      #       'smartweather_unavailable'
      #     {% else %}
      #       {{ ns.value / ns.count }}
      #     {% endif %}
      #   unit_of_measurement: lux


      #========================================
      #=== Decode illuminance to a light level
      #========================================
      outside_light_level:
        friendly_name: Outside Light Level 
        value_template: >
          {% if states('sensor.current_light_level_sensor') == 'SmartWeather' %}
            {% set light_level = states('sensor.smartweather_average_illuminance') | int %}
          {% else %}
            {% set light_level = states('sensor.brightness') | int %}
          {% endif %}

          {% if light_level == 0 %} Dark
          {% elif light_level <= 1 %} Bright moonlight
          {% elif light_level <= 2 %} Night light
          {% elif light_level <= 10 %} Dimmed light
          {% elif light_level <= 50 %} 'Cosy' living room
          {% elif light_level <= 150 %} 'Normal' non-task light
          {% elif light_level <= 350 %} Working / reading
          {% elif light_level <= 700 %} Inside daylight
          {% elif light_level <= 2000 %} Maximum to avoid glare
          {% elif light_level <= 10000 %} Clear daylight
          {% elif light_level <= 120000 %} Direct sunlight
          {% else %} Too bright!
          {% endif %}
        icon_template: >
          {% if states('sensor.current_light_level_sensor') == 'SmartWeather' %}
            {% set light_level = states('sensor.smartweather_average_illuminance') | int %}
          {% else %}
            {% set light_level = states('sensor.brightness') | int %}
          {% endif %}

          {% if light_level == 0 %} mdi:brightness-1
          {% elif light_level <= 1 %} mdi:brightness-3
          {% elif light_level <= 2 %} mdi:candle
          {% elif light_level <= 10 %} mdi:brightness-4
          {% elif light_level <= 50 %} mdi:fireplace
          {% elif light_level <= 150 %} mdi:ceiling-light
          {% elif light_level <= 350 %} mdi:book-open-page-variant
          {% elif light_level <= 700 %} mdi:window-closed
          {% elif light_level <= 2000 %} mdi:weather-sunny
          {% elif light_level <= 10000 %} mdi:white-balance-sunny
          {% elif light_level <= 120000 %} mdi:sunglasses
          {% else %} mdi:alert-octagram-outline
          {% endif %}         


      #============================
      #=== SmartWeather Rain Today 
      #============================
      smartweather_1_rain_today:
        friendly_name: SmartWeather (id 1) Rain Today
        value_template: >
          {% set obs = state_attr('sensor.smartweather_1', 'obs') %}
          {% if is_state('input_boolean.smartweather_rainfall_use_location_1', 'off') %}
            unknown
          {% elif obs is sequence and obs|length > 0 and obs[0].precip_accum_local_day is defined %}
            {{ obs[0].precip_accum_local_day }}
          {% else %}
            unknown
          {% endif %}
        unit_of_measurement: mm

      smartweather_2_rain_today:
        friendly_name: SmartWeather (id 2) Rain Today
        value_template: >
          {% set obs = state_attr('sensor.smartweather_2', 'obs') %}
          {% if is_state('input_boolean.smartweather_rainfall_use_location_2', 'off') %}
            unknown
          {% elif obs is sequence and obs|length > 0 and obs[0].precip_accum_local_day is defined %}
            {{ obs[0].precip_accum_local_day }}
          {% else %}
            unknown
          {% endif %}
        unit_of_measurement: mm

      smartweather_3_rain_today:
        friendly_name: SmartWeather (id 3) Rain Today
        value_template: >
          {% set obs = state_attr('sensor.smartweather_3', 'obs') %}
          {% if is_state('input_boolean.smartweather_rainfall_use_location_3', 'off') %}
            unknown
          {% elif obs is sequence and obs|length > 0 and obs[0].precip_accum_local_day is defined %}
            {{ obs[0].precip_accum_local_day }}
          {% else %}
            unknown
          {% endif %}
        unit_of_measurement: mm

      smartweather_4_rain_today:
        friendly_name: SmartWeather (id 4) Rain Today
        value_template: >
          {% set obs = state_attr('sensor.smartweather_4', 'obs') %}
          {% if is_state('input_boolean.smartweather_rainfall_use_location_4', 'off') %}
            unknown
          {% elif obs is sequence and obs|length > 0 and obs[0].precip_accum_local_day is defined %}
            {{ obs[0].precip_accum_local_day }}
          {% else %}
            unknown
          {% endif %}
        unit_of_measurement: mm

      smartweather_5_rain_today:
        friendly_name: SmartWeather (id 5) Rain Today
        value_template: >
          {% set obs = state_attr('sensor.smartweather_5', 'obs') %}
          {% if is_state('input_boolean.smartweather_rainfall_use_location_5', 'off') %}
            unknown
          {% elif obs is sequence and obs|length > 0 and obs[0].precip_accum_local_day is defined %}
            {{ obs[0].precip_accum_local_day }}
          {% else %}
            unknown
          {% endif %}
        unit_of_measurement: mm

      # #=== Average Smartweather Rain
      # smartweather_average_rain_today:
      #   friendly_name: SmartWeather Average Rain Today
      #   entity_id:
      #     - sensor.smartweather_2_rain_today
      #     - sensor.smartweather_3_rain_today
      #     - sensor.smartweather_5_rain_today
      #   value_template: >
      #     {% set entities = ['sensor.smartweather_2_rain_today',
      #                        'sensor.smartweather_3_rain_today',
      #                        'sensor.smartweather_5_rain_today'] %}
      #     {% set ns = namespace(count=0, value=0) %}
      #     {% for e in entities %}
      #       {% set s = states(e) %}
      #       {% if s != 'unknown' and
      #             s != 'unavailable' and
      #             s != '' %}
      #         {% set ns.count = ns.count + 1 %}
      #         {% set ns.value = ns.value + s | float %}
      #       {% endif %}
      #     {% endfor %}
      #     {% if ns.count == 0 %}
      #       'unavailable'
      #     {% else %}
      #       {{ (ns.value / ns.count) | round(1) }}
      #     {% endif %}
      #   unit_of_measurement: mm

      #================================
      #=== SmartWeather Rain Yesterday 
      #================================
      smartweather_1_rain_yesterday:
        friendly_name: SmartWeather (id 1) Rain Yesterday
        value_template: >
          {% set obs = state_attr('sensor.smartweather_1', 'obs') %}
          {% if is_state('input_boolean.smartweather_rainfall_use_location_1', 'off') %}
            unknown
          {% elif obs is sequence and obs|length > 0 and obs[0].precip_accum_local_yesterday is defined %}
            {{ obs[0].precip_accum_local_yesterday }}
          {% else %}
            unknown
          {% endif %}
        unit_of_measurement: mm

      smartweather_2_rain_yesterday:
        friendly_name: SmartWeather (id 2) Rain Yesterday
        value_template: >
          {% set obs = state_attr('sensor.smartweather_2', 'obs') %}
          {% if is_state('input_boolean.smartweather_rainfall_use_location_2', 'off') %}
            unknown
          {% elif obs is sequence and obs|length > 0 and obs[0].precip_accum_local_yesterday is defined %}
            {{ obs[0].precip_accum_local_yesterday }}
          {% else %}
            unknown
          {% endif %}
        unit_of_measurement: mm

      smartweather_3_rain_yesterday:
        friendly_name: SmartWeather (id 3) Rain Yesterday
        value_template: >
          {% set obs = state_attr('sensor.smartweather_3', 'obs') %}
          {% if is_state('input_boolean.smartweather_rainfall_use_location_3', 'off') %}
            unknown
          {% elif obs is sequence and obs|length > 0 and obs[0].precip_accum_local_yesterday is defined %}
            {{ obs[0].precip_accum_local_yesterday }}
          {% else %}
            unknown
          {% endif %}
        unit_of_measurement: mm

      smartweather_4_rain_yesterday:
        friendly_name: SmartWeather (id 4) Rain Yesterday
        value_template: >
          {% set obs = state_attr('sensor.smartweather_4', 'obs') %}
          {% if is_state('input_boolean.smartweather_rainfall_use_location_4', 'off') %}
            unknown
          {% elif obs is sequence and obs|length > 0 and obs[0].precip_accum_local_yesterday is defined %}
            {{ obs[0].precip_accum_local_yesterday }}
          {% else %}
            unknown
          {% endif %}
        unit_of_measurement: mm

      smartweather_5_rain_yesterday:
        friendly_name: SmartWeather (id 5) Rain Yesterday
        value_template: >
          {% set obs = state_attr('sensor.smartweather_5', 'obs') %}
          {% if is_state('input_boolean.smartweather_rainfall_use_location_5', 'off') %}
            unknown
          {% elif obs is sequence and obs|length > 0 and obs[0].precip_accum_local_yesterday is defined %}
            {{ obs[0].precip_accum_local_yesterday }}
          {% else %}
            unknown
          {% endif %}
        unit_of_measurement: mm

      # #=== Average SmartWeather Rain Yesterday
      # smartweather_average_rain_yesterday:
      #   friendly_name: SmartWeather Average Rain Yesterday
      #   entity_id:
      #     - sensor.smartweather_2_rain_yesterday
      #     - sensor.smartweather_3_rain_yesterday
      #     - sensor.smartweather_5_rain_yesterday
      #   value_template: >
      #     {% set entities = ['sensor.smartweather_2_rain_yesterday',
      #                        'sensor.smartweather_3_rain_yesterday',
      #                        'sensor.smartweather_5_rain_yesterday'] %}
      #     {% set ns = namespace(count=0, value=0) %}
      #     {% for e in entities %}
      #       {% set s = states(e) %}
      #       {% if s != 'unknown' %}
      #         {% set ns.count = ns.count + 1 %}
      #         {% set ns.value = ns.value + s | float %}
      #       {% endif %}
      #     {% endfor %}
      #     {% if ns.count == 0 %}
      #       'unavailable'
      #     {% else %}
      #       {{ (ns.value / ns.count) | round(1) }}
      #     {% endif %}
      #   unit_of_measurement: mm


#================
#=== Automations
#================
automation:

  #=====================================================
  #=== Set up timing of sensor updates for Smartweather
  #=== When HA starts or sun elevation goes above -6
  #=====================================================
  - alias: SmartWeather Set Up Sensors
    trigger:
      - platform: homeassistant
        event: start

      - platform: numeric_state
        entity_id: sensor.elevation
        above: -6
        
    action:
      - service: script.turn_off
        entity_id: 
          - script.loop_smartweather_set_sensor_interval
          - script.smartweather_set_sensor_interval
      
      - delay: '00:00:01'

      - service: script.smartweather_set_sensor_interval


#============
#=== Scripts
#============
script:
  #================================================================= 
  #=== Set interval for the SmartWeather sensors
  #===
  #=== If using SmartWeather
  #===     When sun elevation >= -6
  #===       If SmartWeather brightness <= 5000, set 1 minute
  #===       Else if SmartWeather brightness <= 7500, set 15 minutes
  #===       Else if SmartWeather brightness > 7500, set 30 minutes
  #===     Else set 18 hours
  #===
  #=== If using Brightness 
  #===     When sun elevation >= -6
  #===       If Brightness <= 25, set 1 minute
  #===       Else if Brightness <= 30, set 15 minutes
  #===       Else if Brightness > 30, set 30 minutes
  #===     Else set 18 hours
  #=== 
  #==================================================================
  smartweather_set_sensor_interval:
    sequence:

      #=== Wait for script.loop_smartweather_set_sensor_interval to stop
      - service: homeassistant.turn_off
        entity_id: script.loop_smartweather_set_sensor_interval

      - wait_template: >
          {{ is_state('script.loop_smartweather_set_sensor_interval', 'off') }}

      - service: script.loop_smartweather_set_sensor_interval
        data_template:
          interval: >
            {% if states('sensor.elevation') | float >= -6 and 
                  states('sensor.current_light_level_sensor') == 'SmartWeather' %}
              {% if states('sensor.smartweather_average_illuminance') | int <= 5000 %}
                00:01:00
              {% elif states('sensor.smartweather_average_illuminance') | int <= 7500 %}
                00:15:00
              {% else %}
                00:30:00
              {% endif %}
            {% elif states('sensor.elevation') | float >= -6 and 
                    states('sensor.current_light_level_sensor') == 'Brightness' %}
              {% if states('sensor.brightness') | int <= 25 %}
                00:01:00
              {% elif states('sensor.brightness') | int <= 30 %}
                00:15:00
              {% else %}
                00:30:00
              {% endif %}
            {% else %}
              18:00:00
            {% endif %}


  #========================================================================
  #=== Update the sensor and loop the script that sets the sensor interval
  #===
  #=== Passed
  #===  interval - time to wait between sensor updates
  #========================================================================
  loop_smartweather_set_sensor_interval:
    description: Smartweather Loop The Sensor Interval Script
    fields: 
      interval:
        description: Time to wait between sensor updates
        example: 00:01:00

    sequence:
      #=== Update sensor
      - service: homeassistant.update_entity
        entity_id: sensor.smartweather_1

      #=== Update sensor
      - service: homeassistant.update_entity
        entity_id: sensor.smartweather_2

      #=== Update sensor
      - service: homeassistant.update_entity
        entity_id: sensor.smartweather_3

      #=== Update sensor
      - service: homeassistant.update_entity
        entity_id: sensor.smartweather_4

      #=== Update sensor
      - service: homeassistant.update_entity
        entity_id: sensor.smartweather_5

      #=== Wait the desired time
      - delay: "{{ interval }}"

      #=== Start the process again
      - service: script.smartweather_set_sensor_interval
```


__brightness.yaml__
```
#=================
#=== Sensors
#=================
sensor:

  - platform: template
    sensors:

      #================================================================
      #=== Brightness sensor
      #===   Estimates the current light level outside as a percentage
      #===   using sun elevation and the DarkSky cloud coverage.
      #=================================================================
      brightness:
        friendly_name: 'Brightness'
        value_template: >-
          {% set elevation = state_attr('sun.sun','elevation') | float %}
          {% set cloud_coverage = states('sensor.dark_sky_current_cloud_coverage') | float %}
          {% set cloud_factor = (1 - (0.75 * ( cloud_coverage / 100) ** 3 )) %}
          
          {# set this to official sun elevation for end of twighlight #}
          {% set min_elevation = -6 %}

          {# set this to the maximum noon sun elevation (lowest maximum here is 15 degrees) #}
          {% set max_elevation = 62 %}

          {% set adjusted_elevation = elevation - min_elevation %}
          {% set adjusted_elevation = [adjusted_elevation, 0] | max %}
          {% set adjusted_elevation = [adjusted_elevation, max_elevation - min_elevation] | min %}
          {% set adjusted_elevation = adjusted_elevation / (max_elevation - min_elevation) %}
          {% set adjusted_elevation = adjusted_elevation * 100 %}
          {% set brightness = adjusted_elevation * cloud_factor %}
          
          {{ brightness | round }}
        unit_of_measurement: '%'
        device_class: 'illuminance'
```
