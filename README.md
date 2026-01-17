# Football Animation VR Trailer

![Game Dev](https://img.shields.io/badge/Game-Development-orange?style=for-the-badge)
![Unity Project](https://img.shields.io/badge/Unity-Project-lightgrey?style=for-the-badge)
![CSharp](https://img.shields.io/badge/Language-C%23-blueviolet?style=for-the-badge&logo=csharp)

A Unity project for creating immersive VR trailer animations featuring Football and basketball gameplay moments. This project combines a complete Football game engine with custom cinematic animation systems to showcase sports action in virtual reality.

## Overview

This project serves as a promotional tool for VR sports games, featuring:
- **Football Trailer**: Dynamic kick sequences with goalkeeper reactions and smooth camera work
- **Basketball Trailer**: Throw animations with curved ball physics and cinematic zooms
- **VR-Optimized**: Built with Unity's XR modules for immersive experiences
- **Modular Design**: Reusable components for creating custom sports animations
---
![GitHub Repo stars](https://img.shields.io/github/stars/HTANV/Football-Animation?style=for-the-badge)
![GitHub forks](https://img.shields.io/github/forks/HTANV/Football-Animation?style=for-the-badge)
![GitHub watchers](https://img.shields.io/github/watchers/HTANV/Football-Animation?style=for-the-badge)
![GitHub last commit](https://img.shields.io/github/last-commit/HTANV/Football-Animation?style=for-the-badge)

## Features

### Football Trailer System
- Player kick animation with configurable timing
- Realistic ball physics with curved trajectories
- Goalkeeper reaction system (alert → catch sequence)
- Dynamic camera following (ball → goalkeeper)
- Audio integration for impact sounds

### Basketball Trailer System
- Player throw animation sequences
- Physics-based ball flight with height curves
- Smooth camera zooming and following
- Skybox and court environment setup

### Technical Features
- **Unity 2022.3.62f2** compatibility
- **VR Ready** with XR modules enabled
- **Timeline Integration** for complex animation sequences
- **GLTF Support** for 3D model importing
- **Modular Script Architecture** for easy customization
---
![Unity](https://img.shields.io/badge/Unity-2022.3.62f2-black?style=for-the-badge&logo=unity)
![Platform](https://img.shields.io/badge/Platform-Windows%2010%2F11-blue?style=for-the-badge)
![VR Ready](https://img.shields.io/badge/VR-Ready-success?style=for-the-badge)
![XR](https://img.shields.io/badge/XR-Enabled-purple?style=for-the-badge)

## Requirements

- **Unity Editor**: 2022.3.62f2 or compatible version
- **Platform**: Windows 10/11 (VR headset recommended)
- **VR Hardware**: Optional (Oculus, HTC Vive, etc.)
- **Storage**: ~2GB free space for project and assets

## Installation & Setup

1. **Clone/Download** this repository
2. **Open with Unity Hub**:
   - Launch Unity Hub
   - Add project
   - Ensure Unity 2022.3.62f2 is installed

3. **First Time Setup**:
   - Unity will automatically import assets and resolve dependencies
   - Wait for package installation to complete
   - Open any trailer scene to begin

4. **VR Setup** (Optional):
   - Connect VR headset
   - Enable XR in Project Settings → XR Plug-in Management
   - Select appropriate VR SDK

## Usage

### Running Trailer Scenes

1. **Football Trailer**:
   - Open `Assets/Scenes/Trailer.unity` or `Assets/Scenes/Trailer_V2.unity`
   - Press Play in Unity Editor
   - Press 'K' key to trigger kick animation
   - Camera will automatically follow ball and goalkeeper

2. **Basketball Trailer**:
   - Open `Assets/Scenes/Trailer_Basketball.unity`
   - Press Play to start automatic animation sequence
   - Watch the throw → flight → zoom sequence

3. **Main Game**:
   - Open `Assets/FootballGameEngine(Indie)/Scenes/MainScene.unity`
   - Full Football game with AI players and physics

### Customization

#### Trailer Scripts Overview

**TrailerPlayer.cs**
```csharp
public class TrailerPlayer : MonoBehaviour
{
    [Header("Kick Settings")]
    public KeyCode kickKey = KeyCode.K;
    public float kickDelay = 0.4f;
    public float onKickZoom = 60f;
}
```
- Handles player animations and kick triggering
- `kickKey`: Key to trigger kick (default: K)
- `kickDelay`: Timing delay before ball release
- `onKickZoom`: Camera zoom level during kick

**TrailerBall.cs**
```csharp
public class TrailerBall : MonoBehaviour
{
    [Header("Target Settings")]
    public Transform target;
    public float flightDuration = 1.5f;
    public float height = 2f;

    [Header("Curve Settings")]
    public AnimationCurve flightCurve = AnimationCurve.EaseInOut(0, 0, 1, 1);
}
```
- Controls ball flight physics
- `target`: Destination transform for ball
- `flightDuration`: Time to reach target
- `height`: Maximum arc height
- `flightCurve`: Animation curve for trajectory

**TrailerCamera.cs**
```csharp
public class TrailerCamera : MonoBehaviour
{
    [Header("Target Settings")]
    public Transform target;
    public Vector3 offset = new Vector3(0, 2f, -4f);

    [Header("Smooth Settings")]
    public float positionSmoothSpeed = 5f;
    public float lookSmoothSpeed = 8f;
}
```
- Smooth camera following and rotation
- `target`: Object to follow
- `offset`: Camera position relative to target
- `positionSmoothSpeed`: Movement interpolation speed
- `lookSmoothSpeed`: Rotation interpolation speed

**GoalkeeperTrailer.cs**
```csharp
public class GoalkeeperTrailer : MonoBehaviour
{
    [Header("Timing Settings")]
    public float catchDelay = 0.8f;
}
```
- Controls goalkeeper reaction timing
- `catchDelay`: Time before catch animation starts

**BasketballAnimationController.cs**
```csharp
public class BasketballAnimationController : MonoBehaviour
{
    public Animator animator;
    public TrailerCamera trailerCamera;
    public TrailerBall trailerBall;
    public float throwDelay = 0.5f;
}
```
- Manages basketball throw sequence
- `throwDelay`: Delay before ball release

## Project Structure

```
FootbalAnimation/
├── Assets/
│   ├── Basketball_court.glb              # Basketball court 3D model
│   ├── BasketBallTrailer/                # Basketball trailer assets
│   │   ├── BasketballAnimationController.cs
│   │   ├── X Bot@Dribble.fbx            # Character animations
│   │   ├── Materials/                   # Court materials
│   │   └── sky.mat                      # Environment skybox
│   ├── FootballGameEngine(Indie)/       # Complete Football game asset pack
│   │   ├── Scenes/                      # Main game scenes
│   │   ├── Scripts/                     # Game logic scripts
│   │   ├── Animations/                  # Character animations
│   │   ├── Credits.txt                  # Asset credits
│   │   └── Documentation/               # Game engine manual
│   ├── Scenes/                          # Trailer scenes
│   │   ├── Trailer.unity               # Football trailer
│   │   ├── Trailer_V2.unity            # Football trailer variant
│   │   └── Trailer_Basketball.unity    # Basketball trailer
│   └── Trailer/                         # Football trailer scripts
│       ├── TrailerBall.cs
│       ├── TrailerCamera.cs
│       ├── TrailerPlayer.cs
│       ├── GoalkeeperTrailer.cs
│       ├── FieldPlayer.controller       # Animation controllers
│       └── Golkeeper.controller
├── Packages/                            # Unity package dependencies
├── ProjectSettings/                     # Unity project configuration
└── README.md                           # This file
```

## Configuration

### Quality Settings
- **Anti Aliasing**: 4x Multi Sampling
- **Shadow Resolution**: Medium
- **Texture Quality**: Full Res
- **Anisotropic Filtering**: Enabled

## Assets & Credits

### Models & Animations
- Character models and animations from Football Game Engine
- Basketball court GLTF model
- Custom animation controllers for trailer sequences


## Development Notes

### Animation Workflow
1. **Setup Characters**: Attach Animator components with appropriate controllers
2. **Configure Scripts**: Assign references in Inspector (camera, ball, goalkeeper)
3. **Timeline Integration**: Use Unity's Timeline for complex sequences
4. **Testing**: Use Play mode to test timing and camera work

