**Platine**:

- 3 Taster
  - jeweils beide in einem Package parallel
  - jeweilige Testpoints gegenüber
- 3 V über Batterie
- Taster sind über kleine Kapazität entprellt

**ESP32 mit ESPhome**: 

- <https://esphome.io/components/esp32.html>
- ESPhome: fertige ESPfirmware als client für Home Assistant
- Firmware mit mit yaml konfiguriert, dann geflashed
- open collector lässt sich realisieren
- Board ID: `az-delivery-devkit-v4`

```
switch:
  - platform: gpio
    pin:
      number: GPIO21
      mode:
        output: true
        open_drain: true
    id: velux_auf
    name: "Velux AUF"
    on_turn_on:
      - delay: 300ms
      - switch.turn_off: velux_auf
```

**Alle Steps:**

1. Kabel an Platine: 3V, GND, D1, D2, D3
2. Mit ESP verbinden
3. ESP flashen
4. Spannungsversorgung per USB am ESP board
5. Kleines Gehäuse drucken