__This is an example for using SmartWeather__

Do not copy this without understanding it, it is an example to help you only!

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
  #=== [REPEAT THIS FOR EACH STATION]
  - platform: rest
    resource: !secret smartweather_resource_1
    name: smartweather_1
    value_template: >
      {{ value_json.station_id }}
    json_attributes:
      - status
      - station_units
      - obs    


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


  - platform: template
    sensors:
      #============================
      #=== SmartWeather Rain Today 
      #============================
      #=== [REPEAT THIS FOR EACH STATION]
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

