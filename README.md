

# Keymaps for the [Adafruit RP2040 USB Host](https://www.adafruit.com/product/5723)

These keymaps depend upon [my Adafruit RP2040 USB Host Branch]((https://github.com/whyaaronbailey/adafruit_rp2040_usbh), which was based on [https://github.com/sekigon-gonnoc/qmk_firmware/tree/keyboard/sekigon/keyboard_quantizer/mini-full/keyboards/sekigon/keyboard_quantizer/mini])  https://github.com/whyaaronbailey/adafruit_rp2040_usbh  [Sekigon's Keyboard Quantizer mini-full branch](https://github.com/sekigon-gonnoc/qmk_firmware/tree/keyboard/sekigon/keyboard_quantizer/mini-full/keyboards/sekigon/keyboard_quantizer/mini) and [GongYiLiao's branch supporting the Adafruit RP2040 with USB Host](https://github.com/GongYiLiao/qmk_AdaFruitRp2040USBH)

## Available keymaps
* Generic ANSI 104 layout under `keymaps/ansi`
* Generic Razer Tartarus V2 under `keymaps/tartarus`
* PACS specific Razer Tartarus V2 keymaps under `keymaps/tartarus_pacs`

## PACS Keymaps

These keymaps are specific to a particular environment, which includes:
* Epic Hyperspace
* Nuance Powerscribe 360
* Change Healthcare McKesson PACS
* GE Universal Viewer

Until I determine how to simulate buttons clicks of a Nuance Powerscribe SpeechMike, the 'dictate', 'next field', 'previous field' and 'delete functions' require the use of Autohotkey.  The code for a possible script is provided below.

```
#SingleInstance Force
#Persistent
Menu, Tray, Add
Menu, Tray, Add, Microsoft Edge, OpenEdge
Menu, Tray, Add, Google Chrome, OpenChrome
Menu, Tray, Add
Menu, Tray, Add, StatDx, OpenStatDx
Menu, Tray, Add, qGenda, OpenqGenda
Menu, Tray, Add, QuinSite, OpenQuinSite
	
OpenqGenda() { Run, https://www.qgenda.com/ }
OpenQuinSite() { Run, https://compass.quinsite.com/productivity/ }
OpenStatDx() { Run, https://my.StatDx.com }
OpenEdge() { Run, msedge.exe }
OpenChrome() { Run, chrome.exe }

F13::
activewin := WinExist("A")
WinActivate, PowerScribe 360 | Reporting
Send, {F4}
WinActivate, %activewin%
return

F14::
activewin := WinExist("A")
WinActivate, PowerScribe 360 | Reporting
Send, {tab}
WinActivate, %activewin%
return

F15::
activewin := WinExist("A")
WinActivate, PowerScribe 360 | Reporting
Send, {delete}
WinActivate, %activewin%
return

F16::
activewin := WinExist("A")
WinActivate, PowerScribe 360 | Reporting
Send, {F12}
WinActivate, %activewin%
return
```
## Key Assignments:
```
    * TARTARUS KEY LABEL            LAYOUT 0                    LAYOUT 1
    *        01                     ANNOTATION (Y)              HANG (H)
    *        02                     WL_SOFT (1)
    *        03                     WL_LUNG (5)
    *        04                     WL_SUBDURAL (8) (275 90)    WL_VASCULAR (7) 684 45)
    *        05                     ZOOM (Z)                    INTERZOOM (+Z)
    *        06                     OPENEPIC
    *        07                     WL_BONE (2)                 WL_HARDWARE (6)
    *        08                     SCROLL_UP
    *        09                     WL_BRAIN (3)                WL_STROKE (4)
    *        10                     ARROW (A)                   ELLIPSE (E)
    *        11                     COPYACC
    *        12                     FAST_UP
    *        13                     SCROLLDOWN
    *        14                     FAST_DOWN
    *        15                     MEASURE (M)                 ROI (+E)
    *        16                     OPENGE                      OPENMCKESSON
    *        17                     SPINE LABEL (C)
    *        18                     SPINE LABEL (T)
    *        19                     SPINE LABEL (L)/NAVIGATOR
    *        20                     DICTATE
    *        THUMB BUTTON           MO(1) / LAYER SWITCH
    *        DIRECTION PAD
    *           UP                  FAST_UP
    *           DOWN                FAST_DOWN
    *           LEFT                KC_MS_WH_UP
    *           RIGHT               KC_MS_WH_DOWN
    */
```

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
