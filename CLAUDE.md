# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A self-contained 3D interactive experience built with vanilla JavaScript and Three.js. Two explorable environments (a hallway and a bedroom) with first-person navigation.

## Running the Project

Open `world.html` directly in a browser. No build step, package manager, or dependencies to install—Three.js is loaded via CDN.

## Architecture

Single HTML file (`world.html`) containing all code:

- **Renderer setup** (lines 33-41): WebGL with shadows, ACES tone mapping
- **Scene builders**: `buildHub()` (lines 101-185) and `buildBedroom()` (lines 188-360) construct the 3D environments
- **Character system**: `makeCharacter()` (lines 74-98) creates the player avatar
- **Input handling**: Arrow keys/WASD for movement, collision detection in `tick()` (lines 395-424)
- **Scene transitions**: `goTo()` (lines 372-392) handles fade between scenes
- **Atmosphere**: Dust particle animation, torch flicker effects

## Key Patterns

- `mat(color)` / `flat(color)`: Material helpers for Lambert/Basic materials
- `box(w, h, d, color)`: Creates shadow-casting box meshes
- `place(obj, x, y, z)` / `addTo(scene, obj)`: Positioning helpers
- Point lights with `userData.base` property animate with flicker effects
