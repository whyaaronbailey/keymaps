

# Keymaps for the [Adafruit RP2040 USB Host](https://www.adafruit.com/product/5723)

These keymaps depend upon [my Adafruit RP2040 USB Host Branch]((https://github.com/whyaaronbailey/adafruit_rp2040_usbh), which was based on [https://github.com/sekigon-gonnoc/qmk_firmware/tree/keyboard/sekigon/keyboard_quantizer/mini-full/keyboards/sekigon/keyboard_quantizer/mini])  https://github.com/whyaaronbailey/adafruit_rp2040_usbh  [Sekigon's Keyboard Quantizer mini-full branch](https://github.com/sekigon-gonnoc/qmk_firmware/tree/keyboard/sekigon/keyboard_quantizer/mini-full/keyboards/sekigon/keyboard_quantizer/mini) and [GongYiLiao's branch supporting the Adafruit RP2040 with USB Host](https://github.com/GongYiLiao/qmk_AdaFruitRp2040USBH)

## Available keymaps
* Generic ANSI 104 layout under `keymaps/ansi`
* Generic Razer Tartarus V2 under `keymaps/tartarus`
* PACS specific Razer Tartarus V2 keymaps under `keymaps/tartarus_pacs`

## How to use this repository

After [setup your qmk envorinment](https://github.com/qmk/qmk_firmware/blob/master/docs/newbs_getting_started.md), install [my Adafruit RP2040 USB Host Branch]((https://github.com/whyaaronbailey/adafruit_rp2040_usbh) following the 
instructions provided there, and  clone this repository to `keyboards/converter/adafruit_rp2040_usbh`. This should overwrite the included keymaps.

```
git clone [https://github.com/whyaaronbailey/adafruitrp2040_usbh.git](https://github.com/whyaaronbailey/keymaps_adafruit_rp2040_usbh.git) _your_qmk_repo/keyboards/converter/adafruit_rp2040_usbh
cd _your_qmk_repo/keyboards/converter/adafruit_rp2040_usbh
cd ../../..
make converter/adafruit_rp2040_usbh:_your_choice:uf2 
```
where `_your_choice` can be `ansi` for generic 104-key ANSI keyboard and `tartarus` for the generic Razer Tartarus V2 and 'tartarus_pacs' for the PACS specific keymap for Razer Tartarus V2.

## TODO:
* Thie currently depends on an older fork of [Hathach's TinyUSB](https://github.com/hathach/tinyusb) prior to 2/23/24 commits. The older distribution is included here. Need to update to using current TinyHub commits.
