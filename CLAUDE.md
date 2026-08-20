# Deskbuddy

## Building

This repo directory (`Deskbuddy/`) is itself a valid Arduino sketch: `Deskbuddy.ino` matches the folder name, so `arduino-cli compile`/`upload` work directly from here. `arduino_secrets.h` lives in this repo too (gitignored, not tracked) for that to work.

Prefer syncing over WiFi with `arduino-cli` OTA rather than flashing over USB. Get the device's IP first (`arduino-cli board list --discovery-timeout 5s`, look for the `network` port), then:

```
arduino-cli compile --fqbn esp32:esp32:esp32 .
arduino-cli upload -p <IP> -l network --fqbn esp32:esp32:esp32 -F password=<OTA_PASSWORD> .
```

`OTA_PASSWORD` comes from `arduino_secrets.h`. If an upload fails partway with a broken pipe, just retry.

There is a second, separate copy at `~/Documents/Arduino/DeskBuddy/DeskBuddy.ino` for the Arduino IDE GUI, with its own separate `arduino_secrets.h` (gitignored, not tracked in this repo). It is NOT symlinked and does not sync automatically.
