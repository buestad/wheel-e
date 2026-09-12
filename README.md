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
* Configure as a onewheel (Use tutorials for onewheels, not bikes. IMU and Motor calibation is required before installing/enabeling Wheel-E!)
* Put the bike on a stable surfce, wheel off the groung before installing/enabling Wheel-E.
* Configure parameters under ReFloat Cfg -> Bike.
* Disable the foot sensors by setting ADC Switch voltage to 0v (ReFloat Cfg -> Spec -> ADC1&2 Switch voltage: `0.0v`)
* Make sure that the built in ADC app is not enabled. (App Cfg -> General -> App to Use: `No App` or `UART`)
* To be safe, start with low motor current setting! (Motor Cfg -> General -> Current -> Motor Current Max)

## Full code documentation
[Wheel-E code modifications](doc/wheel-e_mods.md) This document describes the code changes made to ReFloat to implement the Wheel-E functionality. It includes explanations of the new state machine logic, parameter handling, and UI changes.

[ReFloat README](ReFloat_README.md) This is the original README for the ReFloat project, which provides an overview of the base code that Wheel-E is built upon. It includes setup instructions, functionality summaries, and documentation links for ReFloat itself.

## Project status
As of 13.09.2026: Code tested handheld on a VESCed Onewheel Pint by author. Tested to some extent on mini-bikes by other users. More testing and tuning needed.

Join the project discussion on Discord: [Vescify / Projects / Wheel-E](https://discord.com/channels/846794200308908065/1494378063352561704)