# Wheel-E - VESC Package
Wheel-E is a VESC Package for electric mini-bikes with a wheelie mode. The package is a fork of [ReFloat](https://github.com/lukash/refloat) used in self-balancing skateboards.

## Functionality summary
* A "THROTTLE" state used when riding on two wheels. Using ADC1 for throttle and ADC2 for brake.
* A "WHEELIE" state which is the same as "RUNNING" state on onewheels, but with a different angle setpoint.
    * This mode is triggered when the pitch value gets close to the angle setpoint, or the optional button is pressed.
    * It exits back to "THROTTLE" when pressing the brake, or or the optional button is pressed or released
* The IU displays a mini-bike and throttle/brake gauge instead of footpads.
* Configurable parameters for the angle setpoint, throttle/brake current, and state transition thresholds.

## Hardware requirements
* VESC with IMU and ADC inputs
* Motor with hall sensors
* Analog trottle
* Analog or digital brake
* _Optional: Button between TX and GND which can be used to enter and/or exit wheelie mode._
* _Optional: Button between RX and GND which can be used for cruise control._

## Configuration
* Configure as a onewheel (Use tutorials for onewheels, not bikes)
* Configure parameters under ReFloat Cfg -> Bike.
* Disable the foot sensors by setting ADC Switch voltage to 0v (ReFloat Cfg -> Spec -> ADC1&2 Switch voltage: `0.0v`)
* Make sure that the built in ADC app is not enabled. (App Cfg -> General -> App to Use: `No App` or `UART`)
* To be safe, start with low motor current setting! (Motor Cfg -> General -> Current -> Motor Current Max)

# Refloat 1.3

A full-featured self-balancing skateboard package.

## New in 1.3
This version reworks a lot of the core control mechanisms and adds Setpoint Smoothing to all Tilts. Due to this, boards will behave slightly differently and tunes might need adjusting.

Changelog highlights:
- Reworked internal timing for better vibration rejection and more consistent tune behavior across setups
- Setpoint Smoothing for all Tilts (ATR, Torque Tilt, Brake Tilt, Turn Tilt, Remote)
- Torque normalization via motor Flux Linkage (firmware 6.06+)
- New and more consistent Reverse Stop
- Fullscreen remote overlay in package UI
- ...and many more features and fixes

For more details, read the [1.3 release post](https://pev.dev/t/refloat-version-1-3/2995).

## Support the project
I invest a lot of time and energy into the development and testing of Refloat. If you would like to support the development, here's [a few options to do so](https://riddimrider.one/donate/).

## Installation
### Upgrading
Back up your package config just in case (either by **Backup Configs** on the Start page, or by saving the XML in **Refloat Cfg**).

Unless upgrading from 1.0, an automatic config restore will pop up, confirm it. If this fails, restore the manual backup.

### Fresh Installation
If doing a fresh board installation, you need to do the **motor** and **IMU** calibration and configuration. If you install the package before that, you need to disable the package before running the **motor** _calibration_ and re-enable it afterwards.

For a detailed guide, read the [Initial Board Setup guide on pev.dev](https://pev.dev/t/initial-board-setup-in-vesc-tool/2190).

On (legacy) firmware 6.02, the **Low and High Tiltback voltages** in the **Specs** tab of **Refloat Cfg** need to be set according to your battery specs.

## Disclaimer
**Use at your own risk!** Electric vehicles are inherently dangerous, authors of this package shall not be liable for any damage or harm caused by errors in the software. Not endorsed by the VESC project.

## Credits
Author: Lukáš Hrázký

Original Float package authors: Mitch Lustig, Dado Mista, Nico Aleman

## Downloads and Changelogs
[https://github.com/lukash/refloat/releases](https://github.com/lukash/refloat/releases)
