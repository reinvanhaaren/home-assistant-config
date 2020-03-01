# Rein van Haaren's Home Assistant configuration

![Project Maintenance][maintenance-badge]
[![GitHub Last Commit][last-commit-badge]][commits]
[![GitHub Activity][commits-badge]][commits]
[![License][license-badge]](LICENSE.md)
[![GitHub Stars][stars-badge]][stars]
[![GitHub Watchers][watchers-badge]][watchers]
[![GitHub Forks][forks-badge]][forks]

[![Home Assistant version][hass-version-badge]][hass-version]
[![Home Assistant Community Store version][hacs-version-badge]][hacs-version]

[![Buy me a coffee][buymeacoffee-badge]][buymeacoffee]

## Table of Contents

- [Welcome](#welcome)
- [General](#general)
  <!-- - [Docker](#docker) -->
- [Functionality worth mentioning](#Functionality-worth-mentioning)
- [Devices](#devices)
  <!-- - [Sensors](#sensors)
  - [Buttons](#buttons)
  - [Lights](#lights)
  - [Switches](#switches)
  - [Media Players](#media-players)
  - [Climate](#climate)
  - [Fans](#fans)
  - [Device Trackers](#device-trackers) -->
- [Hardware](#hardware)
  <!-- - [Machine](#machine)
  - [Connectivity](#connectivity) -->
- [Installed HACS modules](#installed-hacs-modules)
  <!-- - [Plugins](#plugins)
  - [Themes](#themes) -->
- [To-Do / Ideas](#to-do--ideas)
- [Wishlist](#wishlist)
- [Used resources](#used-resources)

## Welcome

Welcome to our smart home! Me and my roommate Bas live in our house in [Hilversum][google-maps-hilversum] ![The Netherlands][flag-nl]. We started automating our home in january 2020. We recieve new devices almost every week so our home automation is growing almost every day. While this configuration extends, I'll try to keep up with the documentation. Don't forget to 🌟 this repository so you will receive updates when new features or ideas are added.

## General

### Docker

I run Home Assistant in a Docker stack next to mosquitto, zigbee2mqtt and zigbee2mqttassistant. This makes it very easy to restart, upgrade and recreate containers without migrating config and data folders. The docker-compose.yaml is included with this repository, just like the (example) configuration files for mosquitto and zigbee2mqtt. In separate containers I run MariaDB for the recorder, nginx and certbot for the reverse proxy with SSL (Let's Encrypt) and portainer to manage the stacks, containers and images. The main operating system on my machine is Ubuntu 18.04.3 LTS with only Docker and Samba (for file sharing) installed.

### Home Assistant

I make use of the Home Assistant Community Store (HACS) to manage some third-party modules, [listed below](#installed-hacs-modules). For the frontend I use Bas Nijholt's [iOS Dark Mode Theme](https://github.com/basnijholt/lovelace-ios-dark-mode-theme) theme with HomeKit background 4.

## Functionality worth mentioning

### Washing machine

The usage of our washing machine is measured by a TP-Link HS110. When the washing machine is done (usage below 3 watts for more than 4 minutes) a push notification is sent to me and Bas. Besides the notification, I also soldered a nodemcu with relay board onto the start-button of the (dumb) washing machine. We can set the end time in Home Assistant and enable 'Auto-start'. The washing machine will automatically start (by close the relay for half a second) on the desired end time minus the average program duration of 1 hour and 45 minutes. When starting the washing machine the 'Auto-start' is turned off again.

### TV

We use a Tuya connected light bulb from LSC Connect (smart lighting from [Action](https://www.action.com/nl-nl/brand/lsc-smart-connect/)) to create a 'ambilight' on the white wall behind our TV. When te light in the living room is turned on, the light behind the TV is a nice purple. When you start Spotify, TuneIn Radio, Netflix or YouTube the light changes color to green or red. This works with the internal LG WEbOS-apps or with the Chromecast attached to the TV.

### Christmas Tree

We have a small christmas tree in the living room, just for fun. Why enjoy the lights in the tree in december only? There is a IKEA TRÅDFRI switch to turn the lights on and off.

## Devices

### Sensors

| Amount | Manufacturer | Description              | Type |
| ------ | ------------ | ------------------------ | ---- |
| 1x     | Xiaomi       | Aqara door sensor        | -    |
| 1x     | Xiaomi       | Aqara temperature sensor | -    |

### Lights

| Amount | Manufacturer      | Description                   | Type               |
| ------ | ----------------- | ----------------------------- | ------------------ |
| 5x     | IKEA              | TRÅDFRI LED bulb E26/E27      | LED1545G12         |
| 2x     | IKEA              | TRÅDFRI LED bulb E27 WW clear | LED1842G3          |
| 3x     | IKEA              | TRÅDFRI LED bulb E12/E14/E17  | LED1649C5          |
| 5x     | IKEA              | TRÅDFRI LED Spot GU10         | LED1650R5          |
| 1x     | IKEA              | TRÅDFRI driver 10 watt        | ICPSHC24-10EU-IL-1 |
| 1x     | LSC Smart Connect | Smart filament LED bulb       | Tuya connected     |
| 1x     | LSC Smart Connect | Smart multicolor LED bulb     | Tuya connected     |

### Switches

| Amount | Manufacturer | Description                                     | Type        |
| ------ | ------------ | ----------------------------------------------- | ----------- |
| 1x     | IKEA         | TRÅDFRI TRÅDFRI control outlet                  | E1603/E1702 |
| 1x     | TP-Link      | TRÅDFRI Wi-Fi smart plug with energy monitoring | HS110       |

### Buttons

| Amount | Manufacturer | Description                       | Type        |
| ------ | ------------ | --------------------------------- | ----------- |
| 3x     | IKEA         | TRÅDFRI ON/OFF switch with dimmer | E1743       |
| 1x     | IKEA         | TRÅDFRI remote control            | E1524/E1810 |
| 1x     | Xiaomi       | Aqara cube                        | -           |

### Media Players

| Amount | Manufacturer | Description                      | Type     |
| ------ | ------------ | -------------------------------- | -------- |
| 1x     | LG           | 4K LCD TV with WebOS integration | 43UJ670V |
| 1x     | Google       | Chromecast 3rd Generation        | -        |
| 1x     | Google       | Google Home Mini                 | -        |
| 1x     | Spotify      | API integration                  | -        |
| 1x     | Sony         | PlayStation 4, 500 GB disk       | -        |

### Climate

| Manufacturer | Description | Type    |
| ------------ | ----------- | ------- |
| Remeha       | Tzerra Plus | 28c CW4 |

### Fans

| Manufacturer | Description        | Type   |
| ------------ | ------------------ | ------ |
| Vasco        | Ventilation system | C400RF |

### Device trackers

| Manufacturer | Device   | Method                                   | Person |
| ------------ | -------- | ---------------------------------------- | ------ |
| Apple        | iPhone 8 | [Home Assistant Companion App][hass-app] | Rein   |
| Apple        | iPhone X | [Home Assistant Companion App][hass-app] | Bas    |

## Hardware

### Machine

| Manufacturer    | Description               |
| --------------- | ------------------------- |
| HP / Compaq     | 6300 Desktop PC           |
| Samsung         | 128 GB SSD 830 series     |
| Western Digital | 500 GB HDD Blue           |
| SK Hynix        | 2x 4GB RAM DDR3-1600      |
| Intel           | i5-3470 3.20GHz quad-core |

### Connectivity

- ZigBee CC2531 USB dongle with [Koenkk Z-Stack firmware](https://github.com/Koenkk/Z-Stack-firmware)
- IKEA TRÅDFRI Gateway (not used at this moment. All the TRÅDFRI-devices are directly connected to the CC2531)

## Installed HACS modules

### Plugins

- [Custom Header][hacs-custom-header] - 1.3.2
- [Mini Media Player][hacs-mini-media-player] - v1.6.0
- [slider-entity-row][hacs-slider-entity-row] - 11
- [mini-graph-card][hacs-mini-graph-card] - v0.9.3
- [vertical-stack-in-card][hacs-vertical-stack-in-card] - v0.2.1
- [fold-entity-row][hacs-fold-entity-row] - 14
- [button-card][hacs-button-card] - 3.1.1

### Themes

- [Google Dark Theme][hacs-google-dark-theme] - v1.2
- [iOS Dark Mode Theme][hacs-ios-dark-mode-theme] - 749a300

## To-Do / Ideas

- Google Assistant integration with Google Home Mini
- Card with recommendation about the weather when walking to/from work (do I need sunglasses and a t-shirt or gloves and a wool hat today)
- Delayed start for the washing machine by making use of a ESP8266 with relay board (soldered on the START-button)
- Push notifications when someone rings our doorbell (Comelit 2602)
- Integration with the [NS API](https://www.ns.nl/reisinformatie/ns-api) (Dutch Railway) with departure and arrival times, maintenance with diversions and travel planner
- Integration with the Pathé API and VUE API (Cinema's. Not public, by reverse engineering) with movie start times in near movie theaters (+ train recommendations to catch the movie in time)

## Wishlist

- iPad Mini e.g. in the living room to replace the thermostat
- Xiaomi Aqara motion sensors in the hallway
- Xiaomi Aqara door sensor in the mailbox for a You've Got Mail-push notification
- Sonoff Mini's behind the wall switches in the kitchen, bathroom, toilet, hallway and storage
- TP-Link HS110 for measuring the state of the ventilation
- TP-Link HS110 for the dishwasher
- LED strip in the living room to color the ceiling

## Used resources

To achieve this configuration I have gained inspiration from the following sources, but not limited to:

- [Bas Nijholt's Home Assistant Config](https://github.com/basnijholt/home-assistant-config)
- [Frenck's Home Assistant Config](https://github.com/frenck/home-assistant-config)
- [Zigbee2mqtt.io](https://www.zigbee2mqtt.io/)
- [Nginx and Let’s Encrypt with Docker in Less Than 5 Minutes](https://medium.com/@pentacent/nginx-and-lets-encrypt-with-docker-in-less-than-5-minutes-b4b8a60d3a71)

## Participation

I would love to share new ideas! Please contact me by e-mail or open a issue in this repository. You also can write new features or a bugfix according to the [code of conduct](CODE_OF_CONDUCT.md).

[maintenance-badge]: https://img.shields.io/maintenance/yes/2020
[last-commit]: https://github.com/reinvanhaaren/home-assistant-config/commits/master
[last-commit-badge]: https://badgen.net/github/last-commit/reinvanhaaren/home-assistant-config
[commits]: https://github.com/reinvanhaaren/home-assistant-config/commits/master
[commits-badge]: https://badgen.net/github/commits/reinvanhaaren/home-assistant-config
[license-badge]: https://badgen.net/github/license/reinvanhaaren/home-assistant-config
[stars]: https://github.com/reinvanhaaren/home-assistant-config/stargazers
[stars-badge]: https://badgen.net/github/stars/reinvanhaaren/home-assistant-config
[watchers]: https://github.com/reinvanhaaren/home-assistant-config/watchers
[watchers-badge]: https://badgen.net/github/watchers/reinvanhaaren/home-assistant-config
[forks]: https://github.com/reinvanhaaren/home-assistant-config/network/members
[forks-badge]: https://badgen.net/github/forks/reinvanhaaren/home-assistant-config
[hass-version]: https://www.home-assistant.io/blog/2020/02/26/release-106
[hass-version-badge]: https://img.shields.io/badge/Home%20Assistant-0.106.2-brightgreen.svg
[hacs-version]: https://github.com/hacs/integration/releases/tag/0.22.0
[hacs-version-badge]: https://img.shields.io/badge/Home%20Assistant%20Community%20Store-0.22.0-brightgreen.svg
[buymeacoffee]: https://www.buymeacoffee.com/reinvanhaaren
[buymeacoffee-badge]: https://www.buymeacoffee.com/assets/img/guidelines/download-assets-sm-2.svg
[flag-nl]: https://raw.githubusercontent.com/oxguy3/flags/master/mini/nl.png
[google-maps-hilversum]: https://goo.gl/maps/MGWwfvxenUMcvucM9
[hass-app]: https://apps.apple.com/nl/app/home-assistant/id1099568401
[hacs-custom-header]: https://github.com/maykar/custom-header
[hacs-fan-control-entity-row]: https://github.com/finity69x2/fan-control-entity-row
[hacs-mini-media-player]: https://github.com/kalkih/mini-media-player
[hacs-upcoming-media-card]: https://github.com/custom-cards/upcoming-media-card
[hacs-slider-entity-row]: https://github.com/thomasloven/lovelace-slider-entity-row
[hacs-mini-graph-card]: https://github.com/kalkih/mini-graph-card
[hacs-vertical-stack-in-card]: https://github.com/ofekashery/vertical-stack-in-card
[hacs-fold-entity-row]: https://github.com/thomasloven/lovelace-fold-entity-row
[hacs-button-card]: https://github.com/custom-cards/button-card
[hacs-google-dark-theme]: https://github.com/JuanMTech/google_dark_theme
[hacs-ios-dark-mode-theme]: https://github.com/basnijholt/lovelace-ios-dark-mode-theme
