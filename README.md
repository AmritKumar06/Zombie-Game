# Zombie Arena

A simple top-down zombie shooter built with SFML.

## Overview

This project is a small C++ game where the player moves through an arena, shoots zombies, and survives waves. The main game logic is implemented in `ZombieArena.cpp`, with supporting classes for the player, zombies, bullets, and horde creation.

## Features

- Full-screen SFML window and camera view
- Player movement using WASD
- Mouse aiming and shooting with left click
- Reload mechanic with limited ammo
- Basic enemy AI with multiple zombie types
- Background tiling using a texture atlas
- Score and high score tracking

## Controls

- `W` / `A` / `S` / `D` — move player
- `Left mouse button` — shoot
- `R` — reload
- `Enter` — start game / resume / pause
- `Escape` — quit

## Build Requirements

- C++ compiler supporting C++11 or newer
- SFML (Graphics, Window, System)

## Build Instructions

From the project root, compile using the main file `ZombieArena.cpp`.

Example command for MinGW/GCC:

```sh
g++ ZombieArena.cpp -o ZombieArena -lsfml-graphics -lsfml-window -lsfml-system
```

If SFML is installed in a custom location, add include and library paths:

```sh
g++ ZombieArena.cpp -I/path/to/SFML/include -L/path/to/SFML/lib -o ZombieArena -lsfml-graphics -lsfml-window -lsfml-system
```

> Note: `ZombieArena.cpp` includes the other source files directly, so only this file needs to be compiled as the entry point.

## Run

1. Ensure the `graphics/` and `sound/` folders are present next to the executable.
2. Run the executable from the project root so asset paths resolve correctly.

## Project Structure

- `ZombieArena.cpp` — main game entry point and game loop
- `Player.cpp` — player movement, rotation, health, and spawn logic
- `Zombie.cpp` — zombie types, movement, health, and hit handling
- `Bullet.cpp` — bullet behavior, flight, and collision shape
- `CreateHorde.cpp` — zombie spawn logic and horde creation
- `graphics/` — sprite and texture assets
- `sound/` — sound effect files
- `Player_Reference.cpp`, `ZombieArena_Reference.cpp` — alternate/reference versions of classes and game loop

## Assets

The game expects the following asset folders:

- `graphics/background_sheet.png`
- `graphics/crosshair.png`
- `graphics/player.png`
- `graphics/bloater.png`
- `graphics/chaser.png`
- `graphics/crawler.png`
- `graphics/blood.png`
- various pickup and UI icons

Sound files are present in `sound/`, though the current main code does not explicitly load them.

## Notes / Known Issues

- `ZombieArena.cpp` currently creates a fixed arena of `500 x 500` tiles and spawns four zombies per level.
- The project uses raw pointers for zombie arrays and direct source-file includes. A future refactor could separate compilation units and use standard containers.
- Some reference files like `Player_Reference.cpp` and `ZombieArena_Reference.cpp` appear to be alternate drafts and are not required to build the main game.

## Suggested Improvements

- add sound playback support
- add menus and HUD display for health, ammo, and score
- improve zombie spawning and level progression
- replace raw pointer arrays with `std::vector`
- ensure all zombie state fields are reliably initialized
