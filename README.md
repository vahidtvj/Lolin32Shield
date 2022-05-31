# Lolin 32 Shield

A collection of useful stuff to have on a ESP32 dev board

## Whats on the board?

- A Micro SD card
- **DS1307**, `for time keeping`
- Battery Switch
- Battery Probe `(This is Builtin on Lolin d32 board)`
- Passive Buzzer, `when you want to annoy others!`
- QC3 capable USB port, `so you can have 12v`
- PWM controlled header, `in case you want to control sth high power (usable with QC)`
- A voltage booster, `cuz some modules just don't work with 3.3v`
- And Mosfets, `To shut everthing off`

![Schematic](./pics/schematic_dark.svg#gh-dark-mode-only)
![Schematic](./pics/schematic_light.svg#gh-light-mode-only)

## GPIO Wiring

|                         PIN                         | GPIO |
| :-------------------------------------------------: | :--: |
|                        SD_CS                        |  5   |
| <span style="text-decoration:overline">SD_EN</span> |  33  |
|                       BUZZER                        |  32  |
|                        VBAT                         |  35  |
|                      BOOST_EN                       |  27  |
|                       USB_DM                        |  17  |
|                       USB_DP                        |  16  |
|                       MOSFET                        |  4   |

### Some Notes

Due to availability, I had to use _DS1307_ RTC chip. **PCF8523T** is a much better alternative. DS1307 requires 5v to operate, so when powering from a lipo battery you have to enable the voltage booster.

SD card can be disabled using **SD_EN** PIN to save power. Don't forget to set it low before trying to read the card.

The USB_C port is there so you can connect a second power source (**Not connected to ESP**). This is useful when you have devices that draw more current and your laptop's usb ports can't supply enough power.
Also Quick Charge Enabled Adapters can be used to get higher voltages like 12v ( `voltage level is controlled by the ESP, checkout `[QC3Control](https://github.com/vahidtvj/QC3Control) ).

### Future Changes

- **PCF8523T** as a drop-in replacement for _DS1307_
- 3.3v Regulator for USB_C input (has to work with QC3 voltage levels)
- A RESET Button

## License

This project is licensed under the [MIT License](LICENSE)
