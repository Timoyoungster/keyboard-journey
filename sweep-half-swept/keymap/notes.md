# VERY IMPORTANT!!!!
even though it has a TRS/TRRS jack, a TRRS cable is necessary for it to function

If it still doesn't work add the following to the config:
```c
#define SPLIT_USB_DETECT
#define SPLIT_USB_TIMEOUT 2500
```
or try:
```c
#define SPLIT_USB_DETECT
#define SPLIT_USB_TIMEOUT_POLL 10
#define SPLIT_WATCHDOG_ENABLE
#define SPLIT_WATCHDOG_TIMEOUT 3000
```

# KEYMAP SETUP

Make sure to use the LAYOUT_split_3x5 macro for defining the layers (not LAYOUT)

## RULES
SPLIT_KEYBOARD = yes *(to make split mode work)*
COMBO_ENABLE = yes *(to enable the combo feature)*
CONVERT_TO = elite_pi *(to compile for the elite pi controller)*

## CONFIG.H
don't forget to add "#define EE_HANDS" to set the handedness on the EEPROM

# COMPILE & FLASH FIRMWARE
*(board needs to be connected and in boot mode for this
as the command flashes the firmware directly after compilation)*

For the *left side*:
```
qmk flash -bl uf2-split-left
```
For the *right side*:
```
qmk flash -bl uf2-split-right
```

# ELITE-PI - BOOT MODE
In order to get the elite-pi into boot mode it has to be unplugged.

Then the "BOOT" pad and the 4th pin from the top on the right have to be connected with a wire / paperclip or a similar item.

With those two connectors bridged, the USB-C cable has to be plugged in and can only be released when windows recognises the USB-device (when it shows up as a drive in the explorer).

# PROBLEMS
- some weird bug that makes the mouse click unusable when escaping from arrow layer after having selected with shift and arrow keys or something like that; effect is that all mouse clicks deregister right after registering -> nothing can be clicked anymore
