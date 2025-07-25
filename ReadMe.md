# ESPhome for Velux 3LI D13 (KLI Series)

This is an open source project for converting a Velux remote into a smart home compatible device. The remote is paired over a closed wireless protocol with a Velux roller shutter. The regular way to allow integration into Home Assistant is via the proprietary Velux KLF 200 bridge (150€ /$ even used).

This approach emulates a button press on the remote directly. The regular buttons are still working.

If you do not want to solder, take a look at this awesome approach with spring contacts by Chris Bue on Thingyverse: https://www.thingiverse.com/thing:6427196

## 1. Velux 3LI D13

<img src="docs/remote_front.jpg" alt="Velux 3LI D13 Remote" width="300"/>

The remote is using 3 buttons to control the shutter. It is powered by two 1.5 V batteries. 

<img src="docs/remote_open.jpg" alt="Remote with cables" width="300"/>

We can open the remote and connect 5 cables to handily available pcb test points on the back of the pcb. They connect to the following signals on the PCB:

- Black: for GND
- Red: for 3V
- Blue / Brown / Purple: To the µc pins of the 3 buttons.

The 3 buttons do usually switch the µc pin to gnd as soon as pressed.

# 2. ESPhome

I had a ESP32 dev board lying around since 2 years which seemed perfect for this project. 

<img src="docs/setup_breadboard.jpg" alt="Remote with cables" width="300"/>

See https://esphome.io/ for a guide on how to flash your device. See `smartvelux.yaml` for the configuration. Note: the yaml file does not include the wifi credentials, these are stored in a `secrets.yaml` file which needs to be created individually:

```yaml
wifi_ssid: "your wifi ssid (with quotes)"
wifi_password: "your wifi password (with quotes)"
```

# 3. Housing

The housing consists of 2 3d printed parts. Additional things needed:
- 2 mm damping foam rubber, or similar, or nothing (adjust spacing in this case)
- 4x M3 heat press insert
- 4x M3 countersunk head screws

<div style="display: flex; gap: 20px;">
    <img src="docs/finished_front.jpg" alt="Housing Front" width="300"/>
    <img src="docs/finished_back.jpg" alt="Housing Back" width="300"/>
</div>