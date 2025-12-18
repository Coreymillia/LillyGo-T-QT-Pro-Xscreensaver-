# 🛠️ Installation Guide - T-QT Pro 341 Effects

This guide will help you get the 341 Effects screensaver running on your LilyGO T-QT Pro.

## 📋 Prerequisites

### Hardware
- **LilyGO T-QT Pro ESP32-S3** board
- **USB-C cable** for programming and power
- **Computer** running Windows, macOS, or Linux

### Software
- **PlatformIO** (recommended) OR **Arduino IDE**
- **Git** (for cloning repository)

## 🚀 Method 1: PlatformIO (Recommended)

### Step 1: Install PlatformIO

**VS Code Extension:**
1. Install [Visual Studio Code](https://code.visualstudio.com/)
2. Install the **PlatformIO IDE** extension
3. Restart VS Code

**Or install PlatformIO Core:**
```bash
pip install platformio
```

### Step 2: Get the Code

```bash
git clone https://github.com/YOUR_USERNAME/T-QT-341-Effects.git
cd T-QT-341-Effects
```

### Step 3: Build and Upload

```bash
# Build the project
pio run -e T-QT-Pro-N4R2

# Upload to device (hold BOOT button when prompted)
pio run -e T-QT-Pro-N4R2 -t upload

# Monitor serial output
pio device monitor --port /dev/ttyACM0 --baud 115200
```

## 🔧 Method 2: Arduino IDE

### Step 1: Install Arduino IDE

Download from [arduino.cc](https://www.arduino.cc/en/software)

### Step 2: Install ESP32 Board Support

1. Open Arduino IDE
2. Go to **File → Preferences**
3. Add this URL to "Additional Board Manager URLs":
   ```
   https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
   ```
4. Go to **Tools → Board → Boards Manager**
5. Search for "ESP32" and install **esp32** by Espressif Systems

### Step 3: Install Required Libraries

Go to **Tools → Manage Libraries** and install:
- **TFT_eSPI** (v2.5.33)
- **LVGL** (v8.3.0)
- **OneButton** (v2.0.3)

### Step 4: Configure TFT_eSPI

1. Navigate to your Arduino libraries folder
2. Open `TFT_eSPI/User_Setup_Select.h`
3. Comment out the default setup line
4. Add: `#include <User_Setups/Setup206_LilyGo_T_QT.h>`

### Step 5: Upload Code

1. Open `examples/LVGL_Factory/LVGL_Factory.ino`
2. Select **Board**: "ESP32S3 Dev Module"
3. Select **Port**: Your T-QT Pro's port
4. **Hold BOOT button** while clicking Upload
5. Release BOOT button when upload starts

## 🔍 Troubleshooting

### Upload Issues

**Problem**: Upload fails or times out
**Solution**: 
- Make sure you **hold the BOOT button** during upload
- Try a different USB cable
- Check the correct port is selected
- Reset the device and try again

**Problem**: "Failed to connect to ESP32"
**Solution**:
```bash
# Check if device is detected
ls /dev/ttyACM* /dev/ttyUSB*

# Try with different baud rate
pio run -e T-QT-Pro-N4R2 -t upload --upload-port /dev/ttyACM0
```

### Display Issues

**Problem**: Blank screen but code runs
**Solution**:
- Verify TFT_eSPI configuration includes T-QT Pro setup
- Check that User_Setup206_LilyGo_T_QT.h is enabled
- Ensure backlight pin (GPIO 10) is configured

**Problem**: Garbled display
**Solution**:
- Check display resolution is set to 128x128
- Verify SPI pins match T-QT Pro configuration
- Reset device and reflash

### Memory Issues

**Problem**: Build fails with "not enough memory"
**Solution**:
- The full 341 effects use significant memory
- Consider reducing effect count if needed
- Ensure ESP32-S3 board with sufficient flash is selected

## 📊 Expected Results

### Serial Output
```
341 Effects T-QT Pro Port Starting...
TFT dimensions: 128x128
GFX dimensions: 128x128
Starting with mode 0
```

### Display Output
- **Startup**: Red border test pattern briefly
- **Effects**: Animated screensaver effects cycling every few seconds
- **Buttons**: Left/right buttons change effects immediately

### Performance Metrics
- **RAM Usage**: ~18% (58KB / 328KB)
- **Flash Usage**: ~58% (761KB / 1.3MB) 
- **Frame Rate**: ~60 FPS smooth animation

## 🎮 Usage Instructions

### Button Controls
- **Left Button (GPIO 0)**:
  - **Short Press**: Next effect
  - **Long Press (2s)**: Change auto-scroll mode (Fast/Slow/Off)
- **Right Button (GPIO 47)**: Previous effect

### Auto-Scroll Modes
- **FAST**: Changes effect every 3 seconds
- **SLOW**: Changes effect every 30 seconds  
- **OFF**: Manual control only

### Effect Navigation
The screensaver cycles through all 341 effects:
1. BOXED → 2. BOXFIT → 3. BRAID → ... → 341. ZOOM → 1. BOXED

## 🆘 Getting Help

If you encounter issues:

1. **Check Serial Monitor** - Most problems show error messages
2. **Verify Hardware** - Test with LilyGO factory demo first
3. **Update Libraries** - Ensure compatible versions are installed
4. **Reset Configuration** - Try with fresh Arduino/PlatformIO install

**Common Solutions:**
- Hold BOOT button during upload
- Use high-quality USB cable
- Select correct board (ESP32S3 Dev Module)
- Verify TFT_eSPI configuration

## ✅ Success Confirmation

You'll know it's working when you see:
- 🟢 **LilyGO startup logo** appears briefly
- 🟢 **Test pattern** (red border, blue fill) flashes
- 🟢 **Animated effects** start cycling automatically
- 🟢 **Button presses** change effects immediately
- 🟢 **Serial output** shows effect numbers and mode changes

Enjoy your **341 amazing screensaver effects** on the beautiful circular display! 🎨✨