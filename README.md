This component creates a bluetooth bridge for an Ikea Idasen desk that uses a Linak controller with [ESPHome](https://esphome.io) and an [ESP32 device](https://esphome.io/devices/esp32.html).

![Home Assistant Desk Controller](ha-desk-controller.png)

The desk is controlled using the [cover integration](https://www.home-assistant.io/integrations/cover/) in Home assistant.

## Installation

Copy the `idasen_desk_controller` directory into your ESPHome `custom_components` directory (creating it if it does not exist).
For the first connection you will need to press the pairing button on the desk.

## Dependencies

This component requires an [ESP32 device](https://esphome.io/devices/esp32.html).

## Configuration


```yaml
idasen_desk_controller:
    # Desk controller bluetooth mac address
    # -----------
    # Required
    mac_address: "00:00:00:00:00:00"

cover:
  - platform: idasen_desk_controller
    name: "Desk"

sensor:
  - platform: idasen_desk_controller
    desk_height:
      # Height in cm
      name: "Desk Height"

binary_sensor:
  # Desk bluetooth connection
  - platform: idasen_desk_controller
    name: "Desk Connection"
    type: CONNECTION
  # Desk moving status
  - platform: idasen_desk_controller
    name: "Desk Moving"
    type: MOVING
```

## Troubleshooting

If you experience Wifi deconnexion, try to activate the [wifi fast connect](https://esphome.io/components/wifi.html) option.
```yaml
wifi:
  ssid: ...
  password: ...
  fast_connect: true
```


## References

* https://github.com/TheRealMazur/LinakDeskEsp32Controller
