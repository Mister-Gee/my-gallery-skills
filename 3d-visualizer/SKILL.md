---
name: 3d-visualizer
description: Render an interactive 3D visualization of an object, scene, or concept. Supports geometric shapes, solar system, molecule structures, and fractals.
metadata:
  homepage: https://mister-gee.github.io/my-gallery-skills/3d-visualizer/
---

# 3D Visualizer

An interactive, real-time 3D scene viewer powered by Three.js. Users can rotate, zoom, and pan the scene directly in the chat.

## Prompts / Triggers
- "Show me a 3D cube"
- "Visualize a solar system in 3D"
- "Render a 3D molecule"
- "Show a 3D sphere"
- "Create a 3D fractal"
- "Show me a rotating torus"
- "Show me a 3D human model"
- "Render a robot in 3D"
- "Load this 3D model: [url]"
- "Visualize [any geometric shape] in 3D"

## Instructions

Call the `run_js` tool with the following exact parameters:
- data: A JSON string with the following fields:
  - scene: String. The type of 3D scene to render. One of: "solar-system", "molecule", "geometry", "fractal", "human", "robot", "model". Defaults to "geometry".
  - shape: String (optional). For "geometry" scene type. One of: "cube", "sphere", "torus", "cone", "cylinder", "octahedron", "dodecahedron", "icosahedron". Defaults to "cube".
  - modelUrl: String (optional). For "model" scene type. A publicly accessible CORS-enabled URL to a .glb or .gltf file to load and display.
  - title: String (optional). A display title for the scene.
  - description: String (optional). A short description of what is being visualized.
