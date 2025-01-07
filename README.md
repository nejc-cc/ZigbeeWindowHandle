# ZigbeeWindowHandle
Ikea Parasoll turned into a smart window handle

# Prerequities
Well, I made this work on my Home Assistant instance with Zigbee2MQTT addon. I guess this could be done with pretty much any Zigbee gateway really, the only downside is that you need to be able to invert payload that you get from modified Ikea Parasoll sensor: open is now closed and vice-versa.

## You also need these:
- Ikea Parasoll sensor 
- AAA battery (Ikea rechargeable Ladda works just fine)
- microswitch with lever (random AliExpress link: https://www.aliexpress.com/item/1005007507457426.html)
- 6 x 6 x 4,3 mm microswitch (optional but highly recommended)
- transparent (PLA/PETG/ABS/ASA...) filament
- any other filament color that you want to use for outer body and top cover parts
- longer shaft (about 1 cm longer than original)
- longer screws (for this project original screws were 1 cm too short as well)

## Small change in devices.yaml
If you defined a friendly name for your window sensor, you should have no problem finding the correct sensor in the `zigbee2mqtt/devices.yaml` (if you're using default settings for addon, if not, you probably have a reason for that and are probably capable of finding the config file :P ).<br>
All you need to do now is to add a few lines below your friendly name.
It should look something like this:
```yaml
'<zigbee device id>':
  friendly_name: <friendly name>
  homeassistant:
    contact:
      payload_on: true
      payload_off: false
```
Because we used the NO (normally-open) contact of switch, we need to let HA know that the states are now inverted.
After restarting Zigbee2MQTT it should start showing the correct position.

## License
This project is licensed under the [Creative Commons Attribution-NonCommercial 4.0 International License](https://creativecommons.org/licenses/by-nc/4.0/).  
You are free to share and adapt the designs for non-commercial purposes with proper attribution.
[![License: CC BY-NC 4.0](https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc/4.0/)
