# Weather Card Extended

This is a modified version of the [*Lovelace animated weather card*](https://github.com/bramkragten/custom-ui/tree/master/weather-card). I have added support for more attributes and also for daily and hourly mode, meaning this card can be used as a standard Weather Card for all Weather Components, but will also work with the Dark Sky Weather Component in hourly mode.
The main purpose for building it, was to have a Card that could display the additional attributes I have included in my Custom Weather Component called WeatherFlow. So on top of the extra information that the *animated weather card* is already showing, you also get Todays Rain and Wind Speed in the Forecast.

![alt text](https://github.com/briis/home-assistant/blob/master/custom-lovelace/weather-card-extended/images/weather-card-extended-dark.png "Weather Card Extended Dark")![alt text](https://github.com/briis/home-assistant/blob/master/custom-lovelace/weather-card-extended/images/weather-card-extended-light.png "Weather Card Extended Light")

## Installation
1. Download the [weather-card-extended.js](https://raw.githubusercontent.com/briis/home-assistant/master/custom-lovelace/weather-card-extended/weather-card-extended.js) and [weather-card-editor-extended.js](https://raw.githubusercontent.com/briis/home-assistant/master/custom-lovelace/weather-card-extended/weather-card-editor-extended.js) to `/config/www/custom-lovelace/weather-card-extended/` (or any other folder in the `/config/www` directory.
2. Save the [amCharts icons](https://www.amcharts.com/free-animated-svg-weather-icons/) in `/config/www/custom-lovelace/weather-card-extended/icons/` (Or any directory under `/config/www`).

Add the following to resources in your lovelace config:

```  
resources:
  - type: module
    url: /customcards/custom-lovelace/weather-card-extended/weather-card-extended.js
```
## Configuration
And add a card with type `custom:weather-card-extended`:
```yaml
- type: custom:weather-card-extended
  entity: weather.YourWeatherEntity
  mode: daily or hourly (daily is default - Optional)
  name: Name of your Weather Entity (Optional)
```
As this is a fork of [bramkragten's](https://github.com/bramkragten) Weather Card, there is still a link in here to the hosted icons. But if you want to use your local hosted icons, then add the following: (Where icons points to a directory where the amChart Icons have been stored)
```yaml
- type: custom:weather-card-extended
  entity: weather.YourWeatherEntity
  mode: daily or hourly (daily is default - Optional)
  name: Name of your Weather Entity (Optional)
  icons: "/customcards/custom-lovelace/weather-card-extended/icons/"
```
And make sure the **sun** component has been enabled in your configuration.yaml
```yaml
#configuration.yaml entry
sun:
```

## Optional - Add to Custom Updater
This Card support the Custom Updater, so if you have this enabled on your system, add the following line to `configuration.yaml`:
```yaml
custom_updater:
  card_urls:
    - https://raw.githubusercontent.com/briis/home-assistant/master/custom_cards.json
```
