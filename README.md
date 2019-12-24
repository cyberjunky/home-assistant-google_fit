[![hacs_badge](https://img.shields.io/badge/HACS-Custom-orange.svg)](https://github.com/custom-components/hacs)  [![made-with-python](https://img.shields.io/badge/Made%20with-Python-1f425f.svg)](https://www.python.org/) [![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.me/cyberjunkynl/)

# Google Fit Sensor Component

Based on, with small fixes:

- <https://github.com/zewelor/ha_custom_components/tree/master/google_fit>
- <https://github.com/hemantkamalakar/haconfigs/tree/master/custom_components/google_fit>
- <https://github.com/vmanuel/hacs-google-fit>

Creates Google Fit sensors.
At the moment, provides following measurements:

- steps
- distance
- time
- calories
- weight
- height
- sleep
- heartrate

Sensor is designed to be flexible and allow customization to add New Google Fit dimensions with minimal effort with relative knowledge of Python and Fitness Rest API.

## HACS - Recommended
- Have [HACS](https://hacs.xyz) installed, this will allow you to easily update.
- Add `https://github.com/cyberjunky/home-assistant-google_fit` as a [custom repository](https://hacs.xyz/docs/navigation/repository) with Type: Integration
- Click Install under "Google Fit" integration.
- Restart Home-Assistant.

## Manual

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

In order to generate your client_id and client_secret, see the prerequisites for Google Calender component:
<https://www.home-assistant.io/components/calendar.google/#prerequisites>
To make sensor work you have to enable Fintness API in your project.
In oder to enable Fitness API open Google cloud console: 
<https://console.cloud.google.com/apis/library/fitness.googleapis.com>
and enable API.

It is recommendable to store client_id and client_secret as secret as possible. You can read about it on:
<https://www.home-assistant.io/docs/configuration/secrets/>

Example:

```yaml
  - platform: google_fit
    name: Bob
    client_id: !secret google_fit_client_id
    client_secret: !secret google_fit_client_secret
```
