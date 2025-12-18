# 🚀 Firmware Releases - T-QT Pro 341 Effects

## 📦 Latest Release - v1.0 (December 18, 2024)

**✅ WORKING FIRMWARE - Complete 341 Effects Screensaver**

### 📂 Release Files

#### Main Firmware
- **`T-QT-Pro-341-Effects-v1.0.bin`** (761KB) - Complete 341 effects screensaver
  - All 341 XScreenSaver effects implemented
  - Button controls (left/right navigation + auto-scroll modes)
  - Optimized for 128x128 circular display
  - Memory usage: 58.1% Flash, 17.7% RAM

#### Support Files  
- **`bootloader.bin`** (15KB) - ESP32-S3 bootloader
- **`partitions.bin`** (3KB) - Partition table

### 🔧 Flash Instructions

#### Method 1: PlatformIO (Recommended)
```bash
# Clone repository
git clone https://github.com/YOUR_USERNAME/T-QT-341-Effects.git
cd T-QT-341-Effects

# Build and flash
pio run -e T-QT-Pro-N4R2 -t upload
```

#### Method 2: Pre-built Firmware (esptool)
```bash
# Download the firmware file T-QT-Pro-341-Effects-v1.0.bin

# Flash using esptool (hold BOOT button)
esptool.py --chip esp32s3 --port /dev/ttyACM0 --baud 460800 write_flash 0x10000 T-QT-Pro-341-Effects-v1.0.bin
```

#### Method 3: ESP32 Flash Download Tool (Windows)
1. Download **ESP32 Flash Download Tool** from Espressif
2. **Hold BOOT button** on T-QT Pro
3. Select firmware file and address **0x10000**
4. Click "START" to flash

### 🎮 Usage After Flashing

**Button Controls:**
- **Left Button (GPIO 0)**: 
  - Short press: Next effect
  - Long press (2s): Change auto-scroll mode  
- **Right Button (GPIO 47)**: Previous effect

**Auto-Scroll Modes:**
- **FAST**: 3 seconds per effect
- **SLOW**: 30 seconds per effect
- **OFF**: Manual control only

### ✅ Expected Behavior

**Startup Sequence:**
1. LilyGO logo appears briefly
2. Red border test pattern flashes
3. First screensaver effect begins

**Normal Operation:**
- Smooth animated effects cycling automatically or manually
- Instant response to button presses
- Serial output showing effect numbers (115200 baud)

### 📊 Technical Specifications

- **Target Hardware**: LilyGO T-QT Pro ESP32-S3
- **Display**: 128x128 GC9A01 circular TFT
- **Framework**: Arduino with TFT_eSPI
- **Performance**: ~60 FPS real-time rendering
- **Effects**: All 341 classic XScreenSaver effects

### 🔍 Troubleshooting

**Problem**: Upload fails
**Solution**: Make sure to **hold BOOT button** during upload

**Problem**: Blank screen after flash  
**Solution**: 
- Verify correct firmware file (761KB)
- Check USB cable quality
- Try power cycle (unplug/replug USB)

**Problem**: Display garbled
**Solution**: Reflash firmware, ensure T-QT Pro model compatibility

### 🛠️ Development Build

To build from source instead of using pre-built firmware:
```bash
git clone https://github.com/YOUR_USERNAME/T-QT-341-Effects.git
cd T-QT-341-Effects
pio run -e T-QT-Pro-N4R2
```

The compiled firmware will be at: `.pio/build/T-QT-Pro-N4R2/firmware.bin`

---

## 📈 Version History

### v1.0 (December 18, 2024) - Initial Release ✅
- Complete 341 effects implementation
- T-QT Pro display integration
- Button controls and auto-scroll
- Production-ready firmware
- **Size**: 761KB firmware
- **Status**: WORKING - Successfully tested

---

**⚠️ Important**: Only use firmware matching your exact T-QT Pro model. This firmware is specifically built for **T-QT Pro ESP32-S3** with **128x128 GC9A01 display**.

**🎯 Verified Working**: This firmware has been successfully tested and confirmed working on LilyGO T-QT Pro hardware as of December 18, 2024.