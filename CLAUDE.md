# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a cyberpunk-style fluid simulation built with Three.js and WebGL shaders. The project consists of HTML files in the `public/` directory with embedded JavaScript that creates interactive fluid simulations with particle rendering.

## Architecture

### Core Components

1. **Fluid Class** (`public/1.html` and `public/2.html`)
   - Handles fluid dynamics simulation using WebGL shaders
   - Manages velocity fields, pressure calculations, and advection
   - Implements incompressible Navier-Stokes equations

2. **Paint Class** (`public/1.html` and `public/2.html`)
   - Renders visual representation of the fluid
   - Handles cyberpunk-style color mixing and effects
   - Manages particle rendering with bloom effects

### Shader Pipeline

The simulation uses multiple WebGL shaders for different stages:
- **Force Init Shader**: Initializes velocity fields with noise
- **Advection Shader**: Handles fluid advection
- **Divergence Shader**: Calculates velocity divergence
- **Pressure Shader**: Solves pressure equations iteratively
- **Force Update Shader**: Updates velocity based on pressure gradient
- **Paint Shaders**: Handle visual rendering with cyberpunk aesthetics

### Key Parameters

- `params.speed`: Controls simulation speed (1-10)
- `params.vortexStrength`: Controls vorticity strength (0.5-3.0)
- `params.colorIntensity`: Controls visual color intensity (0.5-3.0)
- `params.autoSpeed`: Controls automatic force injection frequency (10-100)

## Development Commands

Since this is a static HTML files project, there are no build commands. Simply:

1. **Run the simulation**: Open any HTML file in the `public/` directory in a web browser
2. **Development**: Use a local server for development (e.g., `python -m http.server`)
3. **Deployment**: GitHub Pages automatically deploys from the `public/` directory via GitHub Actions

## Controls

- Interactive sliders for real-time parameter adjustment
- Reset button to restart the simulation
- Image capture (S key or button) with PNG export
- Automatic periodic reset every 640 frames

## Technical Notes

- Uses Three.js from CDN (version 0.150.1)
- WebGL shaders implement fluid dynamics calculations
- Render targets are used for multi-pass rendering
- Canvas preserveDrawingBuffer is enabled for image capture