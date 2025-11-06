# Bubble Column Tweaks

A Minecraft mod that allows you to customize bubble column speeds for both magma blocks and soul sand. Compatible with **Fabric** and **Quilt**.

## Description

In vanilla Minecraft, soul sand creates bubble columns that push entities upward, while magma blocks create bubble columns that pull entities downward. However, the downward pull of magma blocks is slower than the upward push of soul sand. This mod makes magma blocks pull entities down at the same speed that soul sand pushes them up (by default), and allows you to customize both speeds via configuration.

**Server-side only:** This mod works when installed only on the server - clients do not need to install it! (clients can install if you want this in single player)


## Supported Versions

- **Minecraft 1.21.6 - 1.21.10**

## Requirements

- Minecraft 1.21.6 - 1.21.10
- Fabric Loader 0.16.0+ or Quilt Loader (for Quilt)
- Fabric API (included in build)
- Java 21 or higher

## Installation

### For Fabric:
1. Install [Fabric Loader](https://fabricmc.net/use/) for Minecraft 1.21.6 - 1.21.10
2. Install [Fabric API](https://modrinth.com/mod/fabric-api)
3. Download the latest release of this mod from the [Releases](https://github.com/fuglong/BubbleColumnTweaks_Mod/releases) page
4. Place the downloaded `.jar` file into your `mods` folder
5. Launch Minecraft

### For Quilt:
1. Install [Quilt Loader](https://quiltmc.org/en/install/) for Minecraft 1.21.6 - 1.21.10
2. Install [Quilted Fabric API (QFAPI)](https://modrinth.com/mod/qsl) (provides Fabric API compatibility)
3. Download the latest release of this mod from the [Releases](https://github.com/fuglong/BubbleColumnTweaks_Mod/releases) page
4. Place the downloaded `.jar` file into your `mods` folder
5. Launch Minecraft

**Note:** This mod works on Quilt because Quilt can run Fabric mods directly through Quilted Fabric API. No code changes needed!

## Configuration

The mod creates a configuration file at `config/bubblecolumntweaks.json` on first run. You can edit this file to customize bubble column speeds.

### Config File Structure

```json
{
  "magmaSpeedCap": -0.8,
  "magmaAcceleration": -0.08,
  "soulSandSpeedCap": 0.8,
  "soulSandAcceleration": 0.08,
  "magmaSurfaceSpeedCap": -1.8,
  "magmaSurfaceAcceleration": -0.1,
  "soulSandSurfaceSpeedCap": 1.8,
  "soulSandSurfaceAcceleration": 0.1
}
```

### Configuration Options

#### Regular Bubble Column Effects
- `magmaSpeedCap`: Maximum downward speed for magma blocks (default: `-0.8`)
- `magmaAcceleration`: How fast entities accelerate downward in magma columns (default: `-0.08`)
- `soulSandSpeedCap`: Maximum upward speed for soul sand (default: `0.8`)
- `soulSandAcceleration`: How fast entities accelerate upward in soul sand columns (default: `0.08`)

#### Surface Effects (when entities reach the top)
- `magmaSurfaceSpeedCap`: Maximum downward speed at magma surface (default: `-1.8`)
- `magmaSurfaceAcceleration`: Downward acceleration at magma surface (default: `-0.1`)
- `soulSandSurfaceSpeedCap`: Maximum upward speed at soul sand surface (default: `1.8`)
- `soulSandSurfaceAcceleration`: Upward acceleration at soul sand surface (default: `0.1`)

### Vanilla Values (for reference)
- **Magma**: speedCap = `-0.3`, acceleration = `-0.03`
- **Soul Sand**: speedCap = `0.7`, acceleration = `0.06`

### How to Configure

1. Run your server/client once to generate the config file
2. Stop the server/client
3. Edit `config/bubblecolumntweaks.json` with your desired values
4. Restart - changes will take effect immediately

**Note:** Negative values pull downward, positive values push upward. Higher absolute values = faster movement.

## Building from Source

1. Clone the repository:
   ```bash
   git clone https://github.com/fuglong/BubbleColumnTweaks_Mod.git
   cd BubbleColumnTweaks_Mod
   ```

2. Build the mod:
   ```bash
   ./gradlew build
   ```

3. The built `.jar` file will be located in `build/libs/`

## Development

### Project Structure

```
BubbleColumnTweaks_Mod/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── net/fuglong/bubblecolumntweaks/
│   │   │       ├── BubbleColumnTweaksMod.java   # Main mod class
│   │   │       ├── BubbleColumnConfig.java      # Configuration system
│   │   │       └── mixin/
│   │   │           └── EntityMixin.java         # Mixin to modify bubble column behavior
│   │   └── resources/
│   │       ├── fabric.mod.json                  # Mod metadata
│   │       └── bubblecolumntweaks.mixins.json   # Mixin configuration
├── build.gradle                                  # Gradle build configuration
├── gradle.properties                             # Project properties
├── settings.gradle                               # Gradle settings
└── README.md                                     # This file
```

### Setting Up Development Environment

1. Install JDK 21 or higher
2. Install IntelliJ IDEA or another Java IDE
3. Import the project as a Gradle project
4. Run `./gradlew genSources` to generate Minecraft sources
5. Run `./gradlew runClient` to test the mod

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Issues

If you encounter any bugs or have suggestions, please open an issue on the [GitHub Issues](https://github.com/fuglong/BubbleColumnTweaks_Mod/issues) page.
