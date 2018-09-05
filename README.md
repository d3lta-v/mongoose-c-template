# Mongoose OS Hello World Template in C

## Overview

This is an empty Mongoose OS Hello World template written in C for the ESP8266.
The contents of this repository is optimised for Visual Studio Code on a Mac.
Pull requests are welcome for PC compatibility.

This repository is based upon the original [Mongoose OS empty template](https://github.com/mongoose-os-apps/empty)

## Basic setup
Make sure that you have cloned the [Mongoose OS Git repository](https://github.com/cesanta/mongoose-os)
to your computer to allow IntelliSense to detect the headers. The repository
should be placed in `${workspaceFolder}/../mongoose-os`.

For optimal experience, install the Mongoose OS IDE extension in Visual Studio
Code to configure the default serial port without having to manually set
environment variables.

## Basic tasks
All of the typical tasks you would do with Mongoose OS is packaged in
`tasks.json`. The tasks can be invoked with the Tasks > Run Build Task item
or the keyboard. The tasks available are as follows:

### `build`
Builds the current source code and generates the firmware file needed
for flashing. **IMPORTANT**: The firmware generated is meant for devices
with a 1MByte flash only. Please change `mos.yml`'s `build_vars` option to
specify your device's flash size.

### `flash`
Flashes the current connected devices as specified by the `MOS_PORT`
environment variable or through Visual Studio Code if you have the Mongoose OS
IDE extension installed.

### `console`
Displays the console of the currently connected device in the terminal.

## Modifications
This template can be modified to suit different Mongoose OS C applications,
such as building for different platforms or altering the flash size for an
ESP8266 with a different flash memory capacity (e.g. 4MByte instead of 1MByte).

### Changing the flash size
By default, this template uses 1MByte as the default flash size and overrides
Mongoose OS's 4MByte. To change the flash size:

1. Modify `mos.yml` `build_vars` to change the size of the built firmware
2. Modify `tasks.json` under the `flash` label and change the `--esp-flash-params`. Defaults to QIO, 8Mbyte, 40MHz flash

### Changing the chip type
By default, this templates assumes that you are building for the ESP8266.
To change the chipset you're building for:

1. Modify `tasks.json` under the `build` label arguments and change the `--arch` argument to any supported chip type
2. Modify `tasks.json` under the `flash` label arguments and change the `--esp-flash-params` argument to parameters that your chip type supports

## Caveats

### Mongoose OS IDE extension reliance
This template relies on the Mongoose OS IDE extension for Visual Studio Code,
which is not very well supported. 

### Limited IntelliSense
IntelliSense has been set to "Tag Parser" mode as using it in Default mode
results in warnings of missing header files, namely `mgos_mongoose.h` and other
header files that are only present during build time on the remote Docker image
