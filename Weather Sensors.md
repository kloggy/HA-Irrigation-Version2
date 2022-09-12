__Weather Sensors__

All weather sensors can be defined by the user.

There are six user defined sensors used in this system

1. Current Temperature
2. Forecast High Temperature Today
3. Total Rainfall so far today
4. Actual Rainfall yesterday

All the above sensors have a default based on [OpenWeatherMap](https://www.home-assistant.io/integrations/openweathermap/) but can be changed in the settings page.

5. Raining Now (optional)
If you want to prevent irrigation when it is rainig 'now' you need to proviude a `binary_senor`.

6. Weather Outlook (optional)
In order to have the weather outlook displayed you need to provide a sensor called `sensor.irrigation_weather_outlook`. Its state is some text and it can have either an icon or a picture defined.

Here is an example of the Weather Outlook sensor (this is mine and it will **NOT** work for you, it is *just an example*),
```
  - platform: template
    sensors:

      #=== Irrigaton Weather Outlook
      #=== Creates a two line wether outlook with approprite icon 
      irrigation_weather_outlook:
        value_template: >
          {% set current_conditions = states(states('input_text.weather_sensor_forecast_conditions')) | title%}
          {% set current_conditions = current_conditions.replace('Partlycloudy', 'Partly Cloudy') %}

          {% set max_high_temp = states(states('input_text.weather_sensor_forecast_high_temperature')) | round(1) %}
          {% set will_rain_today = states(states('input_text.weather_sensor_will_it_rain_today')) %}
          {% set will_rain_tomorrow = states(states('input_text.weather_sensor_will_it_rain_tomorrow')) %}
          {% set total_rain_today = states(states('input_text.weather_sensor_forecast_total_rain_today')) %}
          {% set total_rain_tomorrow = states(states('input_text.weather_sensor_forecast_total_rain_tomorrow')) %}
          {% set chance_of_rain_today = states(states('input_text.weather_sensor_forecast_chance_of_rain_today')) %}
          {% set chance_of_rain_tomorrow = states(states('input_text.weather_sensor_forecast_chance_of_rain_tomorrow')) %}

          {% set rain_today = total_rain_today ~ 'mm / ' ~ chance_of_rain_today ~ '%' %}
          {% set rain_tomorrow = total_rain_tomorrow ~ 'mm / ' ~ chance_of_rain_tomorrow ~ '%' %}

          {% set outlook = 'Outlook: ' ~ current_conditions ~ ', High Temp ' ~ max_high_temp ~ '°C<br>' %}

          {% if will_rain_today == '1' and will_rain_tomorrow == '1' %}
            {% set outlook = outlook ~ 'Rain Today (' ~ rain_today ~ ') & Tomorrow (' ~ rain_tomorrow ~ ')' %}
          {% elif will_rain_today == '1' %}
            {% set outlook = outlook ~ 'Rain Today (' ~ rain_today ~ '), none tomorrow' %}
          {% elif will_rain_tomorrow == '1' %}
            {% set outlook = outlook ~ 'Rain Tomorrow (' ~ rain_tomorrow ~ ')' %}
          {% else %}
            {% set outlook = outlook ~ 'No rain forecast today or tomorrow.' %}
          {% endif %}

          {{ outlook }}
        entity_picture_template: >
          {% set current = state_attr('sensor.weather_api_current', 'current') %}
          {% set icon = current.condition.icon %}
          {% set icon = icon.split('/')[-1] %}
          {% set icon = icon.split('.')[0] %}
          {% set is_day = true if states('sensor.elevation') | int > 0 else false %}
          
          {% if is_day %}
            {{ '/local/icons/weather_icons/weather_api_day/' ~ icon ~ '.png' }}
          {% else %}
            {{ '/local/icons/weather_icons/weather_api_night/' ~ icon ~ '.png' }}
          {% endif %}
```

