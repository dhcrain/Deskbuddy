# Deskbuddy

## Arduino IDE sync

The Arduino IDE compiles from `~/Documents/Arduino/DeskBuddy/DeskBuddy.ino`, a separate copy from this repo's `desk_buddy_github.cpp`. They are NOT symlinked and do not sync automatically.

After editing `desk_buddy_github.cpp` here, copy it to the sketch file before building/flashing in Arduino IDE:

```
cp desk_buddy_github.cpp ~/Documents/Arduino/DeskBuddy/DeskBuddy.ino
```

`arduino_secrets.h` also has a separate copy in the sketch folder (gitignored, not tracked in this repo).
