# Supported Device Types

COW supports automatic warranty management on a best effort basis for the following device manufacturers:

* Apple (pre-2022 models)
* Dell
* HP
* Lenovo
* Microsoft
* Toshiba, including devices listed as dynabook

Devices from other manufacturers, such as ASUS, Acer and Samsung, are still listed on the [Devices](../using-cow/navigation/devices/ "mention") page with their manufacturer, but COW does not look up their warranties.

## Detecting the manufacturer from a serial number

When no manufacturer is given, COW guesses it from the length of the serial number and marks the guess with `(Autodetect)`:

| Serial length       | Detected manufacturer |
| ------------------- | --------------------- |
| 7 characters        | Dell                  |
| 8 characters        | Lenovo                |
| 9 characters        | Toshiba               |
| 10 characters       | HP                    |
| 12 or 14 characters | Microsoft             |

A serial of any other length is left as `Unknown`. Apple serials are not detected this way.
