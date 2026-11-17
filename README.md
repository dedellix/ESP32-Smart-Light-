# ESP32 Embedded Security Project

## Overview

This project implements an ESP32-based smart lighting system using ESPHome. It combines physical hardware controls, environmental sensing, wireless connectivity, and a web interface.

The main objective is to build a functional embedded IoT device and investigate its security properties, potential vulnerabilities, and possible mitigations.

## Features

- Wireless connectivity through Wi-Fi.
- Web-based control of two LEDs (white and red).
- Independent brightness control for both LEDs.
- Physical push-button control.
- Temperature and humidity monitoring using a DHT11 sensor.
- Automatic red LED activation based on humidity thresholds.
- ESPHome Native API for device communication.
- OTA firmware updates.
- ESPHome Device Builder for device management and monitoring.

## Hardware

| Component | Configuration |
|---|---|
| Microcontroller | ESP32 DevKit V4 |
| Temperature and humidity sensor | DHT11 |
| White LED | GPIO 33 |
| Red LED | GPIO 32 |
| Push button | GPIO 27 |
| DHT11 data pin | GPIO 26 |
| LED control | PWM (LEDC) |

The LEDs are controlled independently, allowing brightness adjustment through the web interface.

## Software and Technologies

- ESPHome
- ESP32 / ESP-IDF
- Python
- ESPHome Device Builder
- Wi-Fi
- HTTP Web Server
- ESPHome Native API
- OTA updates

## Project Structure


## Installation

### 1. Install Python and ESPHome

Install ESPHome using pip:

```bash
python -m pip install esphome
```

Check the installation:

```bash
python -m esphome version
```

### 2. Configure credentials

Create a `secrets.yaml` file in the same directory as the ESPHome YAML configuration.


The configuration requires:

- Wi-Fi SSID and password
- Fallback access point password
- Native API encryption key
- OTA password
- Web interface username and password

**Important:** Never upload your actual `secrets.yaml` file or credentials to GitHub.

The configuration `secrets.yaml` should look like this:

```text
# Wi-Fi credentials
wifi_ssid: "YOUR_WIFI_SSID"
wifi_password: "YOUR_WIFI_PASSWORD"

# ESP32 fallback access point
fallback_ap_password: "YOUR_FALLBACK_AP_PASSWORD"

# ESPHome Native API encryption
api_encryption_key: "YOUR_BASE64_API_ENCRYPTION_KEY"

# OTA firmware updates
ota_password: "YOUR_OTA_PASSWORD"

# ESP32 web interface authentication
web_username: "YOUR_WEB_USERNAME"
web_password: "YOUR_WEB_PASSWORD"
```

Replace the fields inside the **double quotation mark** " " with your own credentials.

**Important reminder:** Never upload your actual `secrets.yaml` file or credentials to GitHub.

### 3. Validate the configuration

Go to the directory where the condiguration YAML file is.

```bash
python -m esphome config smartlight_a.yaml
```

### 4. Compile the firmware

```bash
python -m esphome compile smartlight_a.yaml
```

### 5. Upload through USB

Connect the ESP32 to your computer and identify its serial port.

```bash
python -m esphome upload smartlight_a.yaml --device <COM_PORT>
```

Replace `<COM_PORT>` with the appropriate port on your computer.


## ESPHome Device Builder

ESPHome Device Builder provides a graphical interface for managing ESPHome devices.

Install it:

To install ESPHome Device Builder, you can install via the executable in [ESPHome Installation Guide](https://esphome.io/install/). Follow the steps there to install it and launch it.

OR you can follow the command line approach:

```bash
python -m pip install esphome-device-builder
```

 To start it, you can 
```bash
esphome-device-builder PATH_TO_PROJECT
```
Open the interface in your browser:

```text
http://localhost:6052
```

Device Builder can be used to:

- Monitor device status.
- Access device logs.
- Manage ESPHome configurations.
- Compile and install firmware.
- Inspect device connectivity.

## Device Access and Monitoring

After the ESP32 connects to Wi-Fi, its IP address can be found in the ESPHome logs or the router's connected-device list.

you can connect to the web interface and control the Smart Light device via it, howver you should be in the same local network as the device.

The ESP32 hosts a web interface accessible through:

```text
http://ESP32_IP_ADDRESS
```

or you visit 

```text
http://http://esp32-smart-light.local/
```

Log in using the web interface credentials configured in `secrets.yaml`.

The interface provides access to:

- White LED control and brightness.
- Red LED control and brightness.
- Temperature readings.
- Humidity readings.

## Security Considerations


### Current security mechanisms


## Security Assessment

The next stage of the project investigates potential vulnerabilities using:

- Data Flow Diagrams (DFD).
- STRIDE threat modelling.
- Network traffic analysis.
- Service and port enumeration.
- Authentication and authorization testing.
- Firmware security assessment.
- Vulnerability analysis and mitigation recommendations.

All security testing is performed on the project device and within an authorized environment.
