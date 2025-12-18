# 🎨 341 Effects Screensaver - LilyGO T-QT Pro Port

**The complete XScreenSaver 341 effects collection ported to the LilyGO T-QT Pro ESP32-S3 tiny display!**

![T-QT Pro 341 Effects](https://img.shields.io/badge/Effects-341-brightgreen) ![Platform](https://img.shields.io/badge/Platform-ESP32--S3-blue) ![Display](https://img.shields.io/badge/Display-128x128%20GC9A01-orange) ![License](https://img.shields.io/badge/License-MIT-yellow)

## 🎉 Project Highlights

After **days of development** and overcoming display initialization challenges, this project successfully brings the iconic **341 XScreenSaver effects** to the tiny but beautiful **128x128 circular display** of the LilyGO T-QT Pro.

### ✨ Features

- 🎯 **Complete 341 Effects Library** - All classic screensaver effects adapted for circular display
- 🎮 **Button Controls** - Navigate effects with left/right buttons + long press modes
- ⚡ **Auto-Scroll Modes** - FAST (3s), SLOW (30s), or OFF
- 🖥️ **Perfect Display Integration** - Uses factory TFT_eSPI configuration for reliable graphics
- 🔄 **Real-time Rendering** - Smooth ~60 FPS animation performance
- 📱 **Circular Display Optimized** - Effects adapted for 128x128 round screen

### 🎪 Sample Effects Include:

- **BOXED** - Rotating geometric boxes
- **CELTIC** - Animated Celtic knot patterns  
- **PLASMA** - Colorful sine wave plasma effects
- **MATRIX** - Digital rain animation
- **SPIRAL** - Hypnotic spiral patterns
- **PENROSE** - Impossible triangle fractals
- **JULIA** - Julia set fractals
- **FIRE** - Particle fire simulation
- **STARFIELD** - 3D starfield flythrough
- ...and **332 more amazing effects!**

## 🛠️ Hardware Requirements

- **LilyGO T-QT Pro ESP32-S3**
  - ESP32-S3 microcontroller (240MHz, 320KB RAM, 4MB Flash)
  - 0.85" 128x128 GC9A01 circular TFT display
  - Two programmable buttons (GPIO 0, GPIO 47)

## 🚀 Quick Start

### 1. Prerequisites

- **PlatformIO** (recommended) or Arduino IDE
- **USB-C cable** for programming
- **LilyGO T-QT Pro** board

### 2. Installation

```bash
git clone https://github.com/YOUR_USERNAME/T-QT-341-Effects.git
cd T-QT-341-Effects
```

### 3. Build & Upload

**Using PlatformIO:**
```bash
pio run -e T-QT-Pro-N4R2 -t upload
```

**Using Arduino IDE:**
1. Install required libraries (see Libraries section)
2. Open `examples/LVGL_Factory/LVGL_Factory.ino`
3. Select board: "ESP32S3 Dev Module"
4. Upload while holding BOOT button

### 4. Usage

- **Left Button (GPIO 0)**: 
  - Short press: Next effect
  - Long press (2s): Change auto-scroll mode
- **Right Button (GPIO 47)**: Previous effect
- **Auto-scroll**: Automatically cycles through effects based on selected mode

## 📚 Libraries Required

The project uses the factory LilyGO configuration with these libraries:

- **TFT_eSPI** (v2.5.33) - Display driver with T-QT Pro configuration
- **LVGL** (v8.3.0-dev) - Graphics library (factory setup)
- **OneButton** (v2.0.3) - Button handling
- **WiFi** (ESP32 built-in) - Network functionality

## 🏗️ Project Structure

```
T-QT-341-Effects/
├── examples/
│   └── LVGL_Factory/
│       ├── LVGL_Factory.ino    # Main Arduino sketch
│       ├── main_341.cpp        # Complete 341 effects implementation
│       └── [factory files...]  # Original LilyGO factory files
├── lib/
│   ├── TFT_eSPI/              # T-QT Pro display configuration
│   └── lvgl/                  # LVGL graphics library
├── platformio.ini             # PlatformIO configuration
└── README.md                  # This file
```

## 🧬 Technical Architecture

### Display Compatibility Layer

The project uses a **GFXCompatibility class** that translates all original effect calls to work seamlessly with TFT_eSPI:

```cpp
class GFXCompatibility {
public:
  int width() { return 128; }
  int height() { return 128; }
  void fillScreen(uint16_t color) { tft.fillScreen(color); }
  void drawPixel(int16_t x, int16_t y, uint16_t color) { tft.drawPixel(x, y, color); }
  // ... all drawing functions mapped to TFT_eSPI
};
```

### Button Handling

Robust button handling with debouncing and long-press detection:

```cpp
bool bootShortPress();  // < 500ms press
bool bootLongPress();   // > 2s press  
bool rightButtonPress(); // Right button release
```

### Memory Management

- **RAM Usage**: 17.7% (57,996 bytes / 327,680 bytes)
- **Flash Usage**: 58.1% (761,385 bytes / 1,310,720 bytes)

## 🎯 Development Journey

### The Display Challenge

This project overcame a **months-long challenge** where the LilyGO T-QT Pro display would not initialize with custom code, despite the factory demos working perfectly.

**🔑 Key Breakthrough:**
Instead of fighting the display configuration, we **used the working factory LVGL project as our foundation** and replaced the LVGL rendering loop with direct TFT drawing. This preserved the essential hardware initialization while allowing full access to the display.

**Success Factors:**
1. ✅ Used factory TFT_eSPI configuration
2. ✅ Preserved working hardware initialization 
3. ✅ Bypassed LVGL for direct drawing
4. ✅ Adapted effects for circular 128x128 display

### Effect Porting Strategy

The 341 effects were ported from existing projects:
- **Source**: XAtom M5AtomS3 port (similar 128x128 display)
- **Adaptation**: M5.Lcd calls → TFT_eSPI calls
- **Optimization**: Removed IMU shake detection, added button controls

## 🤝 Contributing

We welcome contributions! Areas for improvement:

- **Effect Optimization** - Improve performance of resource-intensive effects
- **New Effects** - Add custom effects designed for circular displays  
- **UI Enhancements** - Effect selection menus, parameter adjustment
- **Documentation** - Effect descriptions, technical details

## 📖 Effect Reference

<details>
<summary>Click to see all 341 effects</summary>

The complete list includes classics like:
BOXED, BOXFIT, BRAID, BSOD, B_SPHERE, BUBBLE3D, BUILDLWO, BUMPS, CAGE, CAROUSEL, CCURVE, CELTIC, CIRCUIT, CITYFLOW, CLOUDLIFE, COLLIDE, COMPANION_CUBE, CRACKBERG, CRUMBLER, CRYSTAL, CUBE21, CUBENETIC, CUBESTORM, CUBICGRID, CWAVES, DANGERBALL, DECAYSCREEN, DELUXE, DEMON, DISCRETE, DISTORT, DRAGON, DRIFT, ENDGAME, ENGINE, EPICYCLE, ERUPTION, ESCHER, EULER2D, EXTRUSION, FADEPLOT, FIBERLAMP, FILMLEADER, FIREWORKX, FLIPSCREEN3D, FLIPTEXT, FLOW, FLUIDBALLS, FLURRY, FLYINGTOASTERS, FONTGLIDE, FOREST, FUZZYFLAKES, GALAXY, GEARS, GEODESIC, GFLUX, GIBSON, GLBLUR, GLCELLS, GLEIDESCOPE, GLFORESTFIRE, GLHANOI, GLKNOTS, GLMATRIX, GLPLANET, GLSCHOOL, GLSLIDESHOW, GLSNAKE, GLTEXT, GOOP, GRAV, GREYNETIC, HALFTONE, HALO, HELIX, HILBERT, HOPALONG, HYPERBALL, HYPERCUBE, IFS, IMSMAP, INTERAGGREGATE, INTERFERENCE, INTERMOMENTARY, JUGGLE, JULIA, KALEIDESCOPE, KUMPPA, LAMENT, LASER, LAVALITE, LIGHTNING, LISA, LISSIE, LOCKWARD, LOOP, MAZE, MEMSCROLLER, MENGER, METABALLS, MIRRORBLOB, MOEBIUS, MOEBIUSGEARS, MOIRE, MOIRE2, MOUNTAIN, MUNCH, NERVEROT, NOOF, PACMAN, PEDAL, PENROSE, PETRI, PHOSPHOR, PHOTOPILE, PIECEWISE, PIPES, POLYHEDRA, POLYOMINOES, POLYTOPES, PONG, POPSQUARES, PROJECTIVEPLANE, PROVIDENCE, PULSAR, PYRO, QGRAPH, QUEENS, QWORM, RIPPLES, ROCKS, RORSCHACH, ROTOR, RUBIK, RUBIKBLOCKS, SBALLS, SHADEBOBS, SIERPINSKI, SLIDESCREEN, SLIP, SONAR, SPEEDMINE, SPHEREMONICS, SPIRAL, SPOTLIGHT, SPROINGIES, SQUIRAL, STARFISH, STARWARS, STONERVIEW, STRANGE, SUBSTRATE, SUPERQUADRICS, SWIRL, T3D, TANGRAM, TESSELLIMENT, THORNBIRD, THREED, TRUCHET, TUNNEL, TURBULENCE, TWANG, UNKNOWNPLEASURES, VERMICULATE, VFEEDBACK, VIGILANCE, VINES, VORONOI, WANDER, WHALE, WHIRLWINDWARP, WHIRLYGIG, WINDUPROBOT, WORM, WORMHOLE, XANALOGTV, XFLAME, XJACK, XLYAP, XMATRIX, XRAYSWARM, XSPIROGRAPH, XSUBLIM, ZOOM, and more!

</details>

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **LilyGO** for the amazing T-QT Pro hardware and factory code
- **XScreenSaver Project** for the original effect collection
- **TFT_eSPI Library** for robust display driver support
- **PlatformIO** for excellent embedded development tools

## 🚀 What's Next?

Future enhancements planned:
- 🎛️ **Web Configuration** - WiFi-based effect selection and parameters
- 🎵 **Audio Integration** - Music visualization effects  
- 🌡️ **Sensor Integration** - Environmental data displays
- 📱 **Mobile App** - Remote control and customization

---

**⭐ If this project helped you bring amazing visuals to your T-QT Pro, please give it a star!**

Built with ❤️ for the maker community

**Status: ✅ WORKING - December 18, 2025**
