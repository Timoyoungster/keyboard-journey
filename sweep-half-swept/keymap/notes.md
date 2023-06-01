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

# COMPILE COMMAND
*(board needs to be connected and in boot mode for this
as the command flashes the firmware directly after compilation)*

For the left side:
```
qmk flash -bl uf2-split-left -e CONVERT_TO=elite_pi <qmk configurator json export>
```
For the right side:
```
qmk flash -bl uf2-split-right -e CONVERT_TO=elite_pi <qmk configurator json export>
```

# ELITE-PI - BOOT MODE
In order to get the elite-pi into boot mode it has to be unplugged.

Then the "BOOT" pad and the 4th pin from the top on the right have to be connected with a wire / paperclip or a similar item.

With those two connectors bridged, the USB-C cable has to be plugged in and can only be released when windows recognises the USB-device (when it shows up as a drive in the explorer).