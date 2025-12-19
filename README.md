# MSR-mqtt_templates
MQTT templates for Multi-hub Reactor.

# Installation
Download the desired yaml files or bundled zip archives and save them in the reactor/config/mqtt_templates folder (no need to exctract the zip files), **restart Reactor**.

To update an existing template just do the same procedure.
MQTTController build 24050 and newer rebuilds the entity when a new template version is detected.

# Configuration
To add an entity using the downloaded template please refer to https://reactor.toggledbits.com/docs/MQTTController/#easy-device-configuration-using-existing-template and supply the `topic:` and template name (listed below) in the `uses_template:` key.

All *zigbee2mqtt_** templates have an optional key named `prefix:` that you can add and supply a value for if your Zigbee2MQTT prefix is not the default *zigbee2mqtt*.

### Zigbee2MQTT settings
mqtt_device.online requires `availability: true` *(default = false)* and `legacy_availability_payload: true` *(default = true)* in your Zigbee2MQTT configuration.

# Templates
| Template name | Description | Capabilities | Additional info | Bundled in |
| --- | --- | --- | --- | --- |
| `shelly_plug_s` | Template for [Shelly Plug S](https://www.shelly.cloud/en-se/products/product-overview/shelly-plug-s) | ***_power_switch_***, power_sensor, energy_sensor, temperature_sensor, binary_sensor | binary_sensor monitors device overtemperature | - |
| `tasmota_sensor_lyw` | Tasmota template for Xiaomi Digital Display BLE Temperature and Humidity sensor [LYWSD03MMC](https://tasmota.github.io/docs/Bluetooth_ESP32/#supported-devices) | ***_temperature_sensor_***, humidity_sensor, battery_power | x_mqtt_device.poll[^3] | - |
| `tasmota_sensor_lyw_h` | Tasmota template for Xiaomi Digital Display BLE Temperature and Humidity sensor [LYWSD03MMC](https://tasmota.github.io/docs/Bluetooth_ESP32/#supported-devices) | ***_humidity_sensor_***, temperature_sensor, battery_power | Same as the above but with humidity_sensor.value as primary attribute. | tasmota_sensor_lyw.yaml |
| `xiaofang_motion_light_sensor` | Custom template for [Xiaomi DaFang Hacks / XiaoFang 1S / Wyzecam V2 / Wyzecam Pan / Other T20 Devices](https://github.com/EliasKotlyar/Xiaomi-Dafang-Hacks) | ***_power_switch_***, motion_sensor, light_sensor, string_sensor | power_switch activates/deactivates the cameras motion sensor detection. Optional configuration key `prefix:` *(default = myhome)* light_sensor.value[^5] x_mqtt_device.online[^4]  | - |
| `zigbee2mqtt_aqara_mini_switch` | Zigbee2MQTT template for [Xiaomi Aqara wireless switch](https://www.zigbee2mqtt.io/devices/WXKG11LM.html#xiaomi-wxkg11lm) | ***_button_***, battery_power, temperature_sensor | x_mqtt_device.poll[^3] | zigbee2mqtt.zip |
| `zigbee2mqtt_aqara_occupancy_illuminance` | Zigbee2MQTT template for [Aqara human body movement and illuminance sensor](https://www.zigbee2mqtt.io/devices/RTCGQ11LM.html#xiaomi-rtcgq11lm) | ***_motion_sensor_***, light_sensor, battery_power, voltage_sensor, temperature_sensor | x_mqtt_device.poll[^3] | zigbee2mqtt.zip |
| `zigbee2mqtt_aqara_illuminance_occupancy` | Zigbee2MQTT template for [Aqara human body movement and illuminance sensor](https://www.zigbee2mqtt.io/devices/RTCGQ11LM.html#xiaomi-rtcgq11lm) | ***_light_sensor_***, motion_sensor, battery_power, voltage_sensor, temperature_sensor | Same as the above but with light_sensor.value as primary attribute. | zigbee2mqtt.zip |
| `zigbee2mqtt_aqara_temperature_humidity` | Zigbee2MQTT template for [Xiaomi Aqara temperature, humidity and pressure sensor](https://www.zigbee2mqtt.io/devices/WSDCGQ11LM.html) | ***_temperature_sensor_***, humidity_sensor, battery_power, voltage_sensor, value_sensor | x_mqtt_device.poll[^3] | zigbee2mqtt.zip |
| `zigbee2mqtt_aqara_humidity_temperature` | Zigbee2MQTT template for [Xiaomi Aqara temperature, humidity and pressure sensor](https://www.zigbee2mqtt.io/devices/WSDCGQ11LM.html) | ***_humidity_sensor_***, temperature_sensor, battery_power, voltage_sensor, value_sensor | Same as the above but with humidity_sensor.value as primary attribute. | zigbee2mqtt.zip |
| `zigbee2mqtt_generic_power_switch` | Zigbee2MQTT template for generic power_switch. | ***_power_switch_*** | - | zigbee2mqtt.zip |
| `zigbee2mqtt_generic_power_switch_pm` | Zigbee2MQTT template for generic power_switch with power moitoring. | ***_power_switch_***, power_sensor, current_sensor, energy_sensor, voltage_sensor | - | zigbee2mqtt.zip |
| `zigbee2mqtt_tradfri_light_bulb` | Zigbee2MQTT template for [IKEA TRADFRI LED bulb E26/E27 806 lumen, dimmable, warm white](https://www.zigbee2mqtt.io/devices/LED1836G9.html#ikea-led1836g9) | ***_power_switch_***, dimming, light_effect | light_effect.start[^1] light.effect.current[^2] | zigbee2mqtt.zip |
| `zigbee2mqtt_tradfri_light_bulb_d` | Zigbee2MQTT template for [IKEA TRADFRI LED bulb E26/E27 806 lumen, dimmable, warm white](https://www.zigbee2mqtt.io/devices/LED1836G9.html#ikea-led1836g9) | ***_dimming_***, power_switch, light_effect | Same as the above but with dimming.level as primary attribute. | zigbee2mqtt.zip |
| `zigbee2mqtt_tradfri_light_bulb_ws` | Zigbee2MQTT template for [IKEA TRADFRI bulb E12/E14/E17 WS 450/470/440 lumen, dimmable, white spectrum, opal white](https://www.zigbee2mqtt.io/devices/LED1903C5_LED1835C6.html#ikea-led1903c5%252Fled1835c6) | ***_power_switch_***, dimming, color_temperature, light_effect | light_effect.start[^1] light.effect.current[^2] | zigbee2mqtt.zip |
| `zigbee2mqtt_tradfri_light_bulb_ws_d` | Zigbee2MQTT template for [IKEA TRADFRI bulb E12/E14/E17 WS 450/470/440 lumen, dimmable, white spectrum, opal white](https://www.zigbee2mqtt.io/devices/LED1903C5_LED1835C6.html#ikea-led1903c5%252Fled1835c6) | ***_dimming_***, power_switch, color_temperature, light_effect | Same as the above but with dimming.level as primary attribute. | zigbee2mqtt.zip |
| `zigbee2mqtt_tuya_2_gang_switch` | Zigbee2MQTT template for [Tuya TS0002](https://www.zigbee2mqtt.io/devices/TS0002.html#tuya-ts0002) | ***_power_switch_*** | Requires: [endpoint] | zigbee2mqtt.zip |
| `zigbee2mqtt_tuya_door_sensor` | Zigbee2MQTT template for [Sonoff Contact sensor](https://www.zigbee2mqtt.io/devices/SNZB-04.html#sonoff-snzb-04) | ***_door_sensor_***, battery_power | x_mqtt_device.poll[^3] | zigbee2mqtt.zip |
| `zigbee2mqtt_tuya_leak_sensor` | Zigbee2MQTT template for [Aubess IH-K665](https://www.zigbee2mqtt.io/devices/IH-K665.html#aubess-ih-k665) | ***_leak_detector_***, battery_power | x_mqtt_device.poll[^3] | zigbee2mqtt.zip |
| `zigbee2mqtt_tuya_occupancy_illuminance` | Zigbee2MQTT template for [TuYa Luminance motion sensor](https://www.zigbee2mqtt.io/devices/ZG-204ZL.html#tuya-zg-204zl) | ***_motion_sensor_***, light_sensor, battery_power | x_mqtt_device.poll[^3] | zigbee2mqtt.zip |
| `zigbee2mqtt_tuya_illuminance_occupancy` | Zigbee2MQTT template for [TuYa Luminance motion sensor](https://www.zigbee2mqtt.io/devices/ZG-204ZL.html#tuya-zg-204zl) | ***_light_sensor_***, motion_sensor, battery_power | x_mqtt_device.poll[^3] | zigbee2mqtt.zip |

All Zigbee2MQTT devices supporting OTA firmware updates will have either "available", "updating" or "idle" in the `x_zigbee2mqtt_ota.value`

[^1]: Possible values for `light_effect.start` are: `blink`, `breathe`, `okay`, `channel_change`, `finish_effect`, `stop_effect`. 
[^2]: `light_effect.current` is not readable from device.
[^3]: It's not possible to poll battery powered devices, recomendeation is to publish `retained` messages from the client.
[^4]: DaFang Hacks doesn't publish any suitable topic for LWT. The `string_sensor.value` is the last published time from the camera, updates at the intervall set in the custom firmware `mqtt.conf` and can be used in a Dynamic Group with the `filter_expression: time() - entity.attribute_meta.string_sensor.value.last_modified > 300000` to catch a disconnected camera.
[^5]: `light_sensor.value` is a virtual, calculated by the camera, value - the higher value the darker environment.

# Support
Support is provided by @Crille through [Smart Home Community](https://smarthome.community/)
