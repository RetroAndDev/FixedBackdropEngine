# FixedBackdropEngine

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20macOS%20%7C%20Linux-lightgrey.svg)]()
[![C++](https://img.shields.io/badge/C++-17-00599C.svg?logo=c%2B%2B)]()
[![Status](https://img.shields.io/badge/status-Work%20In%20Progress-yellow.svg)]()

> ⚠️⚠️⚠️ WARNING
> 
>  **This repository** is the fork of the main project and will be the most up-to-date as it this the lead developer's fork. The source code under it should not be used in production

<p>
  <i>Bringing back the golden age of survival horror, one pre-rendered background at a time.</i>
</p>

A specialized game engine designed for creating games with **pre-rendered backgrounds**, inspired by classic survival horror titles like Resident Evil (1996-2002) and other PlayStation 1 era games.

> ⚠️ **This repository is currently under active development in a private fork.** Public updates will be pushed periodically.

## 🎯 Project Goals

**Primary Objective:** Create a functional clone of **Resident Evil 1 (2002 GameCube Remake)** as a proof of concept and testing ground for the engine's capabilities.

**Long-term Vision:** Build the best game engine specifically tailored for fixed-camera, pre-rendered background games, with modern workflow improvements and innovative features.

---

## ✨ Key Features

### Core Engine Features

- **🎮 Pre-rendered Background System**
  - Optimized rendering pipeline for static backgrounds
  - Multi-layer depth management (foreground/middleground/background)
  - Camera calibration tools (pitch/yaw from screenshots)
  - Walkable zone editor with multi-floor support

- **🖼️ Innovative Asset Workflow**
  - Create backgrounds using **Minecraft** (with decoration mods)
  - Screenshot-based asset creation (no 3D modeling skills required!)
  - Integrated tools for geometry tracing and collision setup
  - Layer-based depth masking (character occlusion)

- **🌐 Cross-Platform Support**
  - Windows (x64)
  - macOS (Intel & Apple Silicon)
  - Linux
  - Future ports: Nintendo Wii U / Switch (via DevKitPro)

- **🎨 Modern Rendering**
  - OpenGL 3.3+ rendering backend
  - 3D character models with animations (via Assimp)
  - Efficient 2D/3D hybrid rendering
  - Dynamic lighting on characters over static backgrounds

- **🔊 Audio System**
  - 3D positional audio
  - Background music and ambient sounds
  - Cross-platform audio engine (miniaudio)

- **🌐 Dual-Screen Network Play** *(Innovative Feature)*
  - Asymmetric gameplay with two displays
  - Server/Client architecture for Steam Deck + PC combo
  - Network streaming of secondary display
  - Input forwarding from remote device
  - Support for Wii U GamePad-style experiences

### Development Tools

- **Scene Editor** - Visual editor for creating and editing game scenes
- **Walkable Zone Tracer** - Draw navigation meshes over pre-rendered backgrounds
- **Camera Calibrator** - Extract camera angles from screenshots
- **Collision Editor** - Place and configure collision volumes
- **Asset Packer** - Bundle and optimize game assets

---

## 🎬 The Vision: Minecraft-Based Background Creation

Traditional pre-rendered background games require skilled 3D artists. This engine innovates by enabling developers to:

1. **Build scenes in Minecraft** using decoration mods
2. **Take screenshots** from the desired camera angle
3. **Import into Scene Editor** and trace walkable zones
4. **Export layers in Krita** for depth-based character occlusion
5. **Configure collision** and triggers directly in the editor

This workflow dramatically lowers the barrier to entry for solo developers and small teams without dedicated 3D artists.

---

## 🏗️ Architecture

```
FixedBackdropEngine/
├── src/
│   ├── Engine/          # Core engine library (static/shared)
│   │   ├── Core/        # Application, Window, Input, Time
│   │   ├── Rendering/   # Renderer, Camera, Shaders, Textures
│   │   ├── Scene/       # Scene management, Entities, Components
│   │   ├── Physics/     # Collision, Navigation mesh
│   │   ├── Audio/       # Audio engine and sources
│   │   ├── Network/     # Server/Client for dual-screen
│   │   └── Assets/      # Asset management and loading
│   │
│   ├── Game/            # Game implementation (RE1 clone)
│   │   ├── main.cpp     # Main game executable
│   │   ├── main_client.cpp  # Lightweight client for second screen
│   │   └── Assets/      # Game-specific assets and scenes
│   │
│   ├── Tools/           # Development tools
│   │   ├── SceneEditor/
│   │   ├── AssetPacker/
│   │   └── CameraCalibrator/
│   │
│   └── ThirdParty/      # External libraries
│       ├── SDL/         # SDL3 (windowing, input)
│       ├── glm/         # OpenGL Mathematics
│       ├── assimp/      # 3D model loading
│       ├── json/        # Scene serialization
│       └── stb/         # Image loading
```

---

## 🔧 Technology Stack

| Component | Library | Purpose |
|-----------|---------|---------|
| **Windowing** | SDL3 | Cross-platform window management |
| **Rendering** | OpenGL 3.3+ | Graphics API |
| **Mathematics** | GLM | 3D math operations |
| **Models/Animations** | Assimp | 3D asset importing |
| **Audio** | miniaudio | Cross-platform audio |
| **Networking** | ENet | UDP reliable networking |
| **Serialization** | nlohmann/json | Scene and data storage |
| **Image Loading** | stb_image | Texture loading |

---

## 🚀 Building the Engine

### Prerequisites

- CMake 3.20+
- C++17 compatible compiler (MSVC, GCC, Clang)
- Git

### Quick Start

```bash
# Clone the repository
git clone https://github.com/yourusername/FixedBackdropEngine.git
cd FixedBackdropEngine

# Install dependencies (automatic)
./setup_dependencies.sh  # Linux/macOS
# or
.\setup_dependencies.ps1  # Windows PowerShell

# Build
mkdir Build && cd Build
cmake ..
cmake --build . --config Release

# Run the demo
cd src/Game
./FixedBackdropGame  # Linux/macOS
# or
FixedBackdropGame.exe  # Windows
```

### Build Options

```bash
cmake .. -DFBE_BUILD_TOOLS=OFF     # Disable editor tools
cmake .. -DFBE_BUILD_CLIENT=OFF    # Disable network client build
cmake .. -DFBE_BUILD_SHARED=ON     # Build engine as shared library
cmake .. -DCMAKE_BUILD_TYPE=Debug  # Debug build
```

---

## 🎮 Dual-Screen Network Architecture

The engine supports two operational modes for asymmetric gameplay:

### Mode 1: Powerful PC + Steam Deck
- **PC (Server)**: Runs the full game, renders main screen
- **Steam Deck (Client)**: Displays second screen, sends controller input

### Mode 2: Steam Deck + Lightweight PC
- **Steam Deck (Server)**: Runs the full game, renders second screen locally
- **PC (Client)**: Receives and displays main screen stream

This flexible architecture enables Wii U GamePad-style gameplay on modern hardware.

---

## 📚 Documentation

Full documentation is coming soon. For now, refer to:
- [Build Instructions](docs/BUILD.md) *(coming soon)*
- [Scene Format Specification](docs/SCENE_FORMAT.md) *(coming soon)*
- [Asset Pipeline Guide](docs/ASSET_PIPELINE.md) *(coming soon)*
- [Network Protocol](docs/NETWORK_PROTOCOL.md) *(coming soon)*

---

## 🛣️ Roadmap

### Phase 1: Core Engine (Current)
- [x] Project structure and build system
- [x] SDL3 integration and window management
- [ ] OpenGL renderer with shader pipeline
- [ ] Pre-rendered background display system
- [ ] 3D character rendering with Assimp
- [ ] Basic input handling

### Phase 2: Scene System
- [ ] Scene file format (JSON-based)
- [ ] Walkable zone navigation
- [ ] Collision detection system
- [ ] Camera angle switching
- [ ] Scene transition system

### Phase 3: Development Tools
- [ ] Scene Editor with ImGui
- [ ] Walkable zone tracer
- [ ] Camera calibration tool
- [ ] Asset packer

### Phase 4: Game Features
- [ ] Inventory system
- [ ] Door/transition mechanics
- [ ] Save/Load system
- [ ] Item interaction
- [ ] Enemy AI

### Phase 5: Resident Evil 1 Clone
- [ ] Mansion layout recreation
- [ ] Character models (Jill/Chris)
- [ ] Core gameplay loop
- [ ] Puzzle mechanics
- [ ] Combat system

### Phase 6: Network & Polish
- [ ] Dual-screen networking
- [ ] Audio system
- [ ] Performance optimization
- [ ] Console ports (Wii U/Switch)

---

## 🤝 Contributing

This project is currently in early development. Contributions, suggestions, and feedback are welcome once the core architecture stabilizes.

**Note:** Active development happens in a private fork. Public releases will be merged periodically.

---

## 📜 License

This project will be released under the MIT License. *(License file coming soon)*

**More detail(s) about Licensing will be revealed later**
***(don't worry, it will be free & open-souce)***

---

## 🙏 Acknowledgments

- Inspired by the classic Resident Evil series (Capcom)
- Built with SDL3, Assimp, GLM, and other amazing open-source libraries
- Special thanks to the retro gaming and game engine development communities

---

<p align="center">
  <i>Bringing back the golden age of survival horror, one pre-rendered background at a time.</i>
</p>
