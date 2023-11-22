[![hacs_badge](https://img.shields.io/badge/HACS-Custom-orange.svg)](https://github.com/hacs/integration)  [![made-with-python](https://img.shields.io/badge/Made%20with-Python-1f425f.svg)](https://www.python.org/) [![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.me/cyberjunkynl/)


# NOTE: deprecated!
This integration is not maintained for Years, I suggest looking at this one:
https://github.com/YorkshireIoT/ha-google-fit

# Google Fit Sensor Component

Based on, with small fixes:

- <https://github.com/zewelor/ha_custom_components/tree/master/google_fit>
- <https://github.com/hemantkamalakar/haconfigs/tree/master/custom_components/google_fit>
- <https://github.com/vmanuel/hacs-google-fit>

Creates Google Fit sensors.
At the moment, the component provides following measurements:

- steps
- distance
- time
- calories
- weight
- height
- sleep
- heartrate

The sensors are designed to be flexible and allow customization to add new Google Fit dimensions with minimal effort with relative knowledge of Python and the Fitness Rest API.

# Installation

## HACS - Recommended
- Have [HACS](https://hacs.xyz) installed, this will allow you to easily update.
- Add `https://github.com/cyberjunky/home-assistant-google_fit` as a [custom repository](https://hacs.xyz/docs/navigation/repository) with Type: Integration
- Click Install under "Google Fit" integration.
- Restart Home-Assistant.

## Manual
- Copy directory `custom_components/google_fit` to your `<config dir>/custom_components` directory.
- Configure.
- Restart Home-Assistant.

## Example configuration.yaml

In order to add this component as is, add a new sensor:

```yaml
sensor:
  - platform: google_fit
    name: Google Fit
    client_id: your_client_id
    client_secret: your_client_secret
```

## Client ID and Client Secret

In order to generate your `client_id` and `client_secret`, see the prerequisites for the Google Calendar component:
<https://www.home-assistant.io/components/calendar.google/#prerequisites>
To make sensor work you have to enable the Fitness API in your project.
In oder to enable Fitness API open Google Cloud console: 
<https://console.cloud.google.com/apis/library/fitness.googleapis.com>
and enable API.

It is recommendable to store the `client_id` and `client_secret` as securely as possible. You can read about it on:
<https://www.home-assistant.io/docs/configuration/secrets/>

Example:

```yaml
  - platform: google_fit
    name: Bob
    client_id: !secret google_fit_client_id
    client_secret: !secret google_fit_client_secret
```

## FAQ

If you have issues authenticating or setup try this workaround first:

Set your HA timezone to (GMT+00:00) GMT (no daylight saving) then restart HA. You'll get a notification to Authenticate. Once the Auth with Google is complete, you can change your timezone back and restart.


## Debugging

Add the relevant lines below to the `configuration.yaml`:

```yaml
logger:
  default: info
  logs:
    custom_components.google_fit: debug
```
