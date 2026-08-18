# Deskbuddy

## Building

This repo directory (`Deskbuddy/`) is itself a valid Arduino sketch: `Deskbuddy.ino` matches the folder name, so `arduino-cli compile`/`upload` work directly from here. `arduino_secrets.h` lives in this repo too (gitignored, not tracked) for that to work.

There is a second, separate copy at `~/Documents/Arduino/DeskBuddy/DeskBuddy.ino` for the Arduino IDE GUI. It is NOT symlinked and does not sync automatically. After editing `Deskbuddy.ino` here, copy it over before building/flashing in Arduino IDE:

```
cp Deskbuddy.ino ~/Documents/Arduino/DeskBuddy/DeskBuddy.ino
```

That sketch folder has its own separate `arduino_secrets.h` copy too (gitignored, not tracked in this repo).
