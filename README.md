# Raspberry Pi MQTT Monitor V2

[![GitHub release (latest by date)](https://img.shields.io/github/v/release/danmrossi/rpi-mqtt-monitor-v2)](https://github.com/danmrossi/rpi-mqtt-monitor-v2/releases)
[![GitHub repo size](https://img.shields.io/github/repo-size/danmrossi/rpi-mqtt-monitor-v2)](https://github.com/danmrossi/rpi-mqtt-monitor-v2)
[![GitHub issues](https://img.shields.io/github/issues/danmrossi/rpi-mqtt-monitor-v2)](https://github.com/danmrossi/rpi-mqtt-monitor-v2/issues)
[![GitHub closed issues](https://img.shields.io/github/issues-closed/danmrossi/rpi-mqtt-monitor-v2)](https://github.com/danmrossi/rpi-mqtt-monitor-v2/issues?q=is%3Aissue+is%3Aclosed)
[![GitHub language count](https://img.shields.io/github/languages/count/danmrossi/rpi-mqtt-monitor-v2)](https://github.com/danmrossi/rpi-mqtt-monitor-v2)
[![GitHub top language](https://img.shields.io/github/languages/top/danmrossi/rpi-mqtt-monitor-v2)](https://github.com/danmrossi/rpi-mqtt-monitor-v2)

<p align="center">
  <img src="./images/rpi-mqtt-monitor-2-min.png" alt="Raspberry Pi MQTT Monitor" />
</p>

The easiest way to track your Raspberry Pi or Ubuntu computer system health and performance in Home Assistant.

* Start monitoring your system in just a few minutes.
* Monitor: cpu load, cpu temperature, free space, used memory, swap usage, uptime, wifi signal quality, network IO, voltage, rpi power health, rpi5 fan speed, apt updates available on host, external sensors, hdd/ssd temperature and system clock speed.
* Remotely restart / shutdown your system and control your monitors.
* Automatic HASS configuration: Supports discovery messages, so no manual configuration in [Home Assistant](https://www.home-assistant.io/) configuration.yaml is needed.
* Automated installation and configuration: you can install it and schedule it with a service or cron with just one command from shell.
* Easy uninstallation, just run rpi-mqtt-monitor-v2 --uninstall
* Configurable: You can select what is monitored and how the message(s) is send (separately or as one csv message).
* Easy update: You can update the script by calling it with command line "rpi-mqtt-monitor-v2 --update" or via Home Assistant UI.
* Support multiple languages: English, German and Bulgarian

## Table of Contents

- [CLI arguments](#cli-arguments)
- [Installation](#installation)
  - [Automated](#automated)
  - [Automated installation preview](#automated-installation-preview)
  - [Manual](#manual)
  - [How to update](https://github.com/danmrossi/rpi-mqtt-monitor-v2/wiki/How-to-update)
- [Configuration](https://github.com/danmrossi/rpi-mqtt-monitor-v2/wiki/Configuration)
  - [External Sensors](https://github.com/danmrossi/rpi-mqtt-monitor-v2/wiki/External-Sensors)
- [Schedule Raspberry Pi MQTT Monitor execution as a service](https://github.com/danmrossi/rpi-mqtt-monitor-v2/wiki/Manual-Installation#schedule-raspberry-pi-mqtt-monitor-execution-as-a-service)
- [Schedule Raspberry Pi MQTT Monitor execution with a cron](https://github.com/danmrossi/rpi-mqtt-monitor-v2/wiki/Manual-Installation#schedule-raspberry-pi-mqtt-monitor-execution-with-a-cron)
- [Home Assistant Integration](#home-assistant-integration)
- [To Do](#to-do)
- [Feature request](#feature-request)


## Installation

### Automated

Run this command to use the automated installation:

```bash
bash <(curl -s https://raw.githubusercontent.com/danmrossi/rpi-mqtt-monitor-v2/master/remote_install.sh)
```

### Automated installation preview

[![asciicast](https://asciinema.org/a/726rhsITLusB88xL4VGPdU2sJ.svg)](https://asciinema.org/a/726rhsITLusB88xL4VGPdU2sJ)

Raspberry Pi MQTT monitor will be installed in the location where the installer is called, inside a folder named rpi-mqtt-monitor-v2.

The auto-installer needs the software below and will install it if its not found:

* git
* python (2 or 3)
* python-pip
* paho-mqtt (python module)
* requests (python module)

Only python is not automatically installed, the rest of the dependencies should be handled by the auto installation.
It will also help you configure the host and credentials for the mqtt server in config.py and create the service or cronjob configuration for you.
It is recommended to run the script as a service, this way you can use the restart, shutdown and display control buttons in Home Assistant.

### Manual
[moved to wiki](../../wiki/Manual-Installation)

## Uninstallation

To uninstall Raspberry Pi MQTT Monitor, run the following command:

```bash
rpi-mqtt-monitor-v2 --uninstall
```

## CLI arguments

```
usage: rpi-mqtt-monitor-v2 [-h] [-H] [-d] [-s] [-v] [-u] [-w] [--uninstall]

Monitor CPU Load, temperature, frequency, free space, etc., and publish the data to an MQTT server or Home Assistant API.

options:
  -h, --help       show this help message and exit
  -H, --hass_api   send readings via Home Assistant API (not via MQTT)
  -d, --display    display values on screen
  -s, --service    run script as a service, sleep interval is configurable in config.py
  -v, --version    display installed version and exit
  -u, --update     update script and config then exit
  -w, --hass_wake  display Home assistant wake on lan configuration
  --uninstall      uninstall rpi-mqtt-monitor-v2 and remove all related files

```

## Home Assistant Integration

If you are using discovery_messages, then this step is not required as a new MQTT device will be automatically created in Home Assistant and all you need to do is add it to a dashboard.

Use '''rpi-mqtt-monitor-v2 --hass_wake''' to display the configuration for Home Assistant wake on lan switch.

[moved to wiki](../../wiki/Home-Assistant-Integration-(outdated))

## To Do

- improve hass api integration

## Feature request

If you want to suggest a new feature or improvement don't hesitate to open an issue or pull request.
