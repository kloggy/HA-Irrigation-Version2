__Weather Sensors__

All weather sensors can be defined by the user.

There are five sensors used in this system

1. Current Temperature
2. Forecast High Temperature Today
3. Total Rainfall so far today: This is notoriously hard to get good data for unless you have a weather station of your own.
I use Smartweather to reasonably good effect but I know it is not available in all regions.
4. Actual Rainfall yesterday

The fifth sensor needs to return any text string describing the weather outlook (or anything else you want!).

I have written some default sensors (see below) into the system but they are easily changed from the settings page.

I have set the default sensors to SmartWeather and DarkSky this is because I use SmartWeather and whilst I am currently investigating a more generic and widely available alternative for rainfall data, so far I don't have one. Darksky I chose, simply because it is easy and until recently was fairly ubiquitous.
I think it is self explanatory but if this causes any questions in future I will update this page with advice

-----
__A Note On Weather Sensors__

__Dark Sky__ recently became unavailable to new users and will do so for everyone in 2021 as Apple have recently bought it.

(For those coming from an earlier version, you no longer have to make any code changes that were caused by my non-standard DarkSky sensor names)


__Smart Weather__ is available as a custom component (https://github.com/briis/smartweather) but I simply use REST sensors to receive the data.


For SmartWeather, look [here](https://smartweather.weatherflow.com/map) and see if there are any stations near you. I use five stations local to me and then using a series of sensors take the average. Rainfall data is notoriously hard to collect unless you have your own weather station so I have to leave it up to you to decide how to measure it for you locality. This is probably the part of the stystem  that will need the most attention to customise for you. Or of course you can simply just choose not to use it.

If there are local stations for you then note the station number(s) and then create a REST sensor for each station.

You'll also need to register for an `api_key`.

Of course there is *no requirement* to use Smartweather for rainfall data but if you use something else you will need to change the Lovelace to fit and also the code that collects rainfall measurements.

There are some pointers for setting SmartWeather up [here](https://github.com/kloggy/HA-Irrigation-Version2/blob/master/smartweather_example.md).

