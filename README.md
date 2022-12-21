# MSR-mqtt_templates
MQTT templates for Multi-hub Reactor.

# Installation
Download the desired yaml files or bundled zip archives and save them in the reactor/config/mqtt_templates folder (no need to exctract the zip files), **restart Reactor**.

To update an existing template just do the same procedure.
If the template has breaking changes like capabilities removed, simply delete the entity from Reactors Entities page and restart Reactor to recreate the entity.

# Configuration
To add an entity using the downloaded template please refer to https://reactor.toggledbits.com/docs/MQTTController/#easy-device-configuration-using-existing-template and supply the `topic:` and template name (listed below) in the `uses_template:` key.

All *zigbee2mqtt_** templates have an optional key named `prefix:` that you can add and supply a value for if your Zigbee2MQTT prefix is not the default *zigbee2mqtt*.

### Zigbee2MQTT settings
mqtt_device.online requires `availability: true` *(default = false)* and `legacy_availability_payload: true` *(default = true)* in your Zigbee2MQTT configuration.

# Templates
| Template name | Description | Capabilities | Additional info | Bundled in |
| --- | --- | --- | --- | --- |
| `tasmota_sensor_lyw` | Tasmota template for Xiaomi Digital Display BLE Temperature and Humidity sensor [LYWSD03MMC](https://tasmota.github.io/docs/Bluetooth_ESP32/#supported-devices) | ***_temperature_sensor_***, humidity_sensor, battery_power | x_mqtt_device.poll[^3] | - |
| `zigbee2mqtt_tradfri_control_outlet` | Zigbee2MQTT template for [IKEA TRADFRI control outlet](https://www.zigbee2mqtt.io/devices/E1603_E1702_E1708.html#ikea-e1603%252Fe1702%252Fe1708) | ***_power_switch_***, value_sensor, string_sensor, toggle | - | zigbee2mqtt_ikea_tradfri.zip |
| `zigbee2mqtt_tradfri_light_bulb` | Zigbee2MQTT template for [IKEA TRADFRI LED bulb E26/E27 806 lumen, dimmable, warm white](https://www.zigbee2mqtt.io/devices/LED1836G9.html#ikea-led1836g9) | ***_power_switch_***, dimming, light_effect, value_sensor, string_sensor, toggle | light_effect.start[^1] light.effect.current[^2] | zigbee2mqtt_ikea_tradfri.zip |
| `zigbee2mqtt_tradfri_light_bulb_ws` | Zigbee2MQTT template for [IKEA TRADFRI bulb E12/E14/E17 WS 450/470/440 lumen, dimmable, white spectrum, opal white](https://www.zigbee2mqtt.io/devices/LED1903C5_LED1835C6.html#ikea-led1903c5%252Fled1835c6) | ***_power_switch_***, dimming, color_temperature, light_effect, value_sensor, string_sensor, toggle | light_effect.start[^1] light.effect.current[^2] | zigbee2mqtt_ikea_tradfri.zip |
| `zigbee2mqtt_tuya_smart_plug_pm` | Zigbee2MQTT template for [TuYa Smart plug (with power monitoring)](https://www.zigbee2mqtt.io/devices/TS011F_plug_1.html) | ***_power_switch_***, power_sensor, current_sensor, energy_sensor, voltage_sensor, value_sensor, string_sensor, toggle | - | - |
| `zigbee2mqtt_aqara_mini_switch` | Zigbee2MQTT template for [Xiaomi Aqara wireless switch](https://www.zigbee2mqtt.io/devices/WXKG11LM.html#xiaomi-wxkg11lm) | ***_button_***, battery_power, temperature_sensor, value_sensor | x_mqtt_device.poll[^3] | zigbee2mqtt_xiaomi_aqara.zip |
| `zigbee2mqtt_aqara_occupancy_illuminance` | Zigbee2MQTT template for [Aqara human body movement and illuminance sensor](https://www.zigbee2mqtt.io/devices/RTCGQ11LM.html#xiaomi-rtcgq11lm) | ***_motion_sensor_***, light_sensor, battery_power, voltage_sensor, temperature_sensor, value_sensor | x_mqtt_device.poll[^3] | zigbee2mqtt_xiaomi_aqara.zip |
| `zigbee2mqtt_aqara_illuminance_occupancy` | Zigbee2MQTT template for [Aqara human body movement and illuminance sensor](https://www.zigbee2mqtt.io/devices/RTCGQ11LM.html#xiaomi-rtcgq11lm) | ***_light_sensor_***, motion_sensor, battery_power, voltage_sensor, temperature_sensor, value_sensor | Same as the above but with illuminance as primary attribute. | zigbee2mqtt_xiaomi_aqara.zip |
| `zigbee2mqtt_aqara_temperature_humidity` | Zigbee2MQTT template for [Xiaomi Aqara temperature, humidity and pressure sensor](https://www.zigbee2mqtt.io/devices/WSDCGQ11LM.html) | ***_temperature_sensor_***, humidity_sensor, battery_power, voltage_sensor, value_sensor | x_mqtt_device.poll[^3] | zigbee2mqtt_xiaomi_aqara.zip |
| `zigbee2mqtt_aqara_humidity_temperature` | Zigbee2MQTT template for [Xiaomi Aqara temperature, humidity and pressure sensor](https://www.zigbee2mqtt.io/devices/WSDCGQ11LM.html) | ***_humidity_sensor_***, temperature_sensor, battery_power, voltage_sensor, value_sensor | Same as the above but with humidity as primary attribute. | zigbee2mqtt_xiaomi_aqara.zip |

[^1]: Possible values for light_effect.start are: *`blink`, `breathe`, `okay`, `channel_change`, `finish_effect`, `stop_effect`*. 
[^2]: light_effect.current is not readable from device.
[^3]: It's not possible to poll battery powered devices.

# Support
Support is provided by @Crille through [Smart Home Community](https://smarthome.community/)
