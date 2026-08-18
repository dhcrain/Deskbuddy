# Deskbuddy
Deskbuddy is a compact ESP32-based smart desk companion built around a touchscreen display. The project combines 3D printing, simple hardware, and software to turn a raw ESP32 screen into a practical mini dashboard for your workspace. It is designed to be easy to set up and easy to personalize.

## Compiling and uploading with arduino-cli

If you prefer the command line over Arduino IDE, you can build and flash Deskbuddy with [`arduino-cli`](https://arduino.github.io/arduino-cli/).

### 1. Install arduino-cli

```
brew install arduino-cli
```

### 2. Install the ESP32 core and required libraries

```
arduino-cli core install esp32:esp32
arduino-cli lib install "TFT_eSPI" "ArduinoJson" "XPT2046_Touchscreen"
```

### 3. Configure TFT_eSPI

Same as the Arduino IDE setup: edit `User_Setup.h` inside the installed `TFT_eSPI` library folder (typically `~/Documents/Arduino/libraries/TFT_eSPI/User_Setup.h`) so the driver and pin settings match your display. See `SETUP_GUIDE.md` for details.

Also make sure `arduino_secrets.h` exists (in whichever folder you compile from) with your WiFi credentials — see `arduino_secrets.h.example`.

### 4. Compile and upload

This repo folder (`Deskbuddy/`) is itself a valid sketch (`Deskbuddy.ino` matches the folder name), so you can build straight from it. There are two workflows depending on where you want the compiled sketch to live:

**Workflow A: compile directly from this repo**

```
arduino-cli compile --fqbn esp32:esp32:esp32 .
```

**Workflow B: sync to the Arduino sketchbook first** (needed if you also want to open the sketch in the Arduino IDE GUI)

```
cp Deskbuddy.ino ~/Documents/Arduino/DeskBuddy/DeskBuddy.ino
arduino-cli compile --fqbn esp32:esp32:esp32 ~/Documents/Arduino/DeskBuddy
```

Swap `esp32:esp32:esp32` (generic "ESP32 Dev Module") for a more specific FQBN if your board has one, e.g. run `arduino-cli board listall esp32` to see options.

### 5. Find the device port

Plug in the board over USB, then run:

```
arduino-cli board list
```

Look for the ESP32's serial port (e.g. `/dev/cu.usbserial-XXXX` on macOS, `/dev/ttyUSB0` on Linux, `COM3` on Windows).

### 6. Upload

```
arduino-cli upload -p <PORT> --fqbn esp32:esp32:esp32 .
```

(or the `~/Documents/Arduino/DeskBuddy` path if using Workflow B). If upload doesn't start automatically, hold the **BOOT** button on the board while it connects.

### 7. Monitor serial output (optional)

```
arduino-cli monitor -p <PORT> -c baudrate=115200
```

Useful for confirming WiFi connection and finding the device's local IP for the web interface.
