# Building for Arduino Microcontrollers

This section will guide you on converting your project to build for Arduino microcontrollers using the `fprime-arduino` package.

## Adding fprime-arduino

First, add the `fprime-arduino` package as a submodule into your project root.

```shell
# In led-blinker
git submodule add https://github.com/fprime-community/fprime-arduino.git
```

Add `fprime-arduino` as a library and change the default build toolchain to `teensy41` in `led-blinker/settings.ini` after the framework path.
```
library_locations: ./fprime-arduino
default_toolchain: teensy41
```
> If you would like to use a different board as your default toolchain, you may change `teensy41` to your desired board.

## Modifying F´ Configuration Files (Optional)

If you are building for a system with low memory (< 100KB RAM), this step is recommended.

Copy the default F´ configuration files into your project root.
```shell
cp -r fprime/config .
```

Reference the [`config`](../config/) files in this repository and modify your `config` files accordingly. Or, you may clone this repository and copy the entire `config` directory into your project.

Then redirect the configuration path in your `led-blinker/settings.ini` by adding the following line:
```
config_directory: ./config
```

## Test Deployment

Test the new teensy41 build by running:

```shell
fprime-util generate
fprime-util build
```

If you wish to test other Arduino builds, append the build name after `fprime-util generate` and `fprime-util build`. Tested boards are listed below (build name in parenthesis):
- Teensy 3.2 (teensy32)
- Teensy 4.0 (teensy40)
- Teensy 4.1 (teensy41)
- Adafruit Feather M0 (featherM0)
- Adafruit Feather RP2040 (featherrp2040rfm)
- SparkFun Thing Plus RP2040 (thingplusrp2040)
- ESP32 Dev Module (esp32)
- Raspberry Pi Pico W (rpipicow)

## Conclusion

Congratulations! You are now able to build an F´ deployment for Arduino microcontrollers! The next step is to create your LED Component.

> Note: You can no longer build for the native system as this is now an Arduino specific deployment.

### Next Step: [Component Design and Initial Implementation](./component-implementation-1.md).
