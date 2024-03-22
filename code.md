



switch:
  - platform: gpio
    pin: GPIO2
    id: gpio_2
    name: "GPIO 2 Switch"
    restore_mode: ALWAYS_ON

  - platform: gpio
    pin: GPIO4
    id: gpio_4
    name: "GPIO 4 Switch"
    restore_mode: ALWAYS_ON

  - platform: template
    name: "Open Door"
    id: open_door  
    turn_on_action:
      - switch.turn_off: gpio_2
      - delay: 1s
      - switch.turn_on: gpio_2

  - platform: template
    name: "Close Door"
    id: close_door
    turn_on_action:
      - switch.turn_off: gpio_4
      - delay: 1s
      - switch.turn_on: gpio_4
