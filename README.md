# Everything Presence Lite

The Everything Presence Lite is a presence sensor for the smart home featuring mmWave for presence, light level illuminance sensor, and integrates directly with [Home Assistant](https://www.home-assistant.io/) through [ESPHome](https://esphome.io/).

If you'd like to buy the Everything Presence Lite, that is located [here](https://shop.everythingsmart.io/products/everything-presence-lite)

The official user guide for the Everything Presence Lite is located [here](https://docs.everythingsmart.io/s/products/doc/everything-presence-lite-epl-ZVnBzYzuX2)!

![Everything Presence One](static/images/everything-presence-lite-front-shot-no-cover.jpg)

---

## Hardware Variants

### Standard Everything Presence Lite (EPL)

The default family of configurations (`everything-presence-lite-ha*.yaml`) targets the original EPL hardware (ESP32 + LD2450/LD2410/etc).

### EPL C3 — ProductBakery (`epl-c3-productbakery.yaml`)

A community variant for custom hardware built around the **ESP32-C3-MINI** module.

**Hardware summary:**

| Component | Details |
|-----------|---------|
| MCU / Module | ESP32-C3-MINI |
| mmWave sensor | Hi-Link LD2450 (UART, 256 000 baud) |
| Ambient light | BH1750 (I²C) |
| LED strip | 3× SK6812 NeoPixel |

**Pin mapping:**

| Signal | GPIO |
|--------|------|
| LD2450 UART TX | GPIO21 |
| LD2450 UART RX | GPIO20 |
| BH1750 SDA | GPIO0 |
| BH1750 SCL | GPIO1 |
| SK6812 DIN | GPIO4 |
| SK6812 count | 3 |

**Flashing:**

1. Open `epl-c3-productbakery.yaml` in ESPHome.
2. Fill in your Wi-Fi credentials via `secrets.yaml` (same format as other EPL configs).
3. Compile and flash to your ESP32-C3-MINI board.

**Compatibility notes:**

- This variant does **not** require OTA via `http_request` and has no Bluetooth proxy enabled by default (the ESP32-C3 is single-core; enabling BLE proxy alongside heavy UART processing is not recommended).
- Existing standard EPL variants are completely unaffected by this addition.
