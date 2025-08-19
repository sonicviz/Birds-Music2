# Babylon Birds WebGPU Flocking App

## Overview

Babylon Birds is an advanced, interactive 3D flocking simulation built with Babylon.js and WebGPU. It visualizes the behavior of bird flocks using GPU-accelerated compute shaders, allowing for real-time, large-scale simulations with rich controls and customization. The app is designed for both educational and creative exploration of flocking algorithms, offering a wide range of parameters, mesh types, and visual effects.


## Features (2025 Update)

- **3D Flocking Simulation:** Real-time rendering of hundreds, thousands, or even millions of birds (boids) in a 3D space—using spatial indexing and parallel compute shaders for performance—scaling up to millions with the right parameter combinations and modern hardware. (See Performance & Scalability below.)
- **Multiple Algorithms:** Switch between classic, BirdMusic, and hybrid flocking algorithms, each with unique behavioral presets and parameter ranges.
- **Customizable Parameters:** Fine-tune edge margin, speed, visual range, minimum distance, cohesion, alignment, separation, center attraction, and individual freedom.
- **Behavior Presets:** Instantly apply realistic presets for different bird species (starlings, geese, sparrows, etc.), or save your own custom presets—including color, lighting, and sky settings.
- **Range & Distance Presets:** Explore various flocking formations, from tight swarms to loose, natural groups.
- **Mesh & Material Selection:** Choose between triangle, pyramid, or Babylon Bird meshes, and switch between shader-based or PBR materials.
- **Lighting Controls:** Adjust two independent lights (position, intensity, color) and visualize their effect on the flock.
- **Sky & Environment:** Customize the sky gradient, intensity, and colors for immersive backgrounds.
- **Post-Processing Effects:** Apply blur and other effects for cinematic visuals (bloom and motion blur are available but may be disabled for compatibility).
- **Mouse Avoidance:** Enable birds to avoid the mouse pointer in 3D, with adjustable strength and radius.
- **Auto-Rotate & Camera Presets:** Rotate the camera automatically or select from multiple preset viewpoints (top, front, side, etc.).
- **Randomization:** Instantly randomize parameters, colors, lights, and sky for creative exploration.
- **User Presets:** Save, load, and delete your own parameter presets using localStorage. Presets now support custom colors, lighting, and sky.
- **Wing Animation Controls:** Adjust wing flap speed and amplitude for more dynamic and realistic bird movement.
- **Audio Panel & Soundscapes:** (BirdMusic style) Control ambient and musical soundscapes, including master, melody, synth, pad, wind, and whoosh volumes, reverb, and soundscape selection. Toggle audio and expand/collapse the audio panel.
- **Enhanced Custom Presets:** Presets can now include material color, light colors, and sky colors for a complete look-and-feel snapshot.
- **Responsive UI:** All controls update in real time, with value displays and tooltips for clarity. Control panel is docked to the right for better usability.

## Performance & Scalability

This simulation is designed to handle **hundreds of thousands to millions of boids** in real time, depending on your GPU and the chosen settings. The actual maximum number of boids is determined by:

- **Visual Range & Min Distance:** Lower values allow more boids by reducing neighbor search cost.
- **Preset Selection:** Some presets are optimized for high density, others for realism or loose formations.
- **Hardware:** Modern discrete GPUs (especially with large VRAM and strong compute) will support more boids.
- **Browser & Driver:** WebGPU support and driver quality can affect performance and limits.

**Tips for Maximum Boids:**
- Use presets like `tight_swarms_1` or `sandpipers` for highest density.
- Lower the `visualRange` and `minDistance` sliders for more boids.
- Reduce post-processing effects for better performance.
- If you see slowdowns or crashes, reduce boid count or increase `visualRange`/`minDistance`.

**Warning:** Pushing to millions of boids may crash your browser or GPU if your hardware is not sufficient. Always increase boid count gradually and monitor performance.

## Controls & UI

- **Parameter Sliders:** Adjust flocking, mesh, material, lighting, post-processing, and wing animation parameters via intuitive sliders and dropdowns.
- **Preset Selectors:** Quickly switch between built-in and user-defined presets for behavior and range/distance.
- **Randomize Buttons:** Randomize parameters, colors, lights, and sky for instant variety.
- **Camera Controls:** Use the zoom slider, preset dropdown, and auto-rotate toggle to explore the flock from any angle.
- **Mouse Controls:** Enable/disable mouse avoidance, adjust its strength/radius, and reset or randomize mouse settings.
- **Light & Sky Controls:** Change light positions/colors/intensity, toggle debug light visualization, and customize the sky gradient.
- **Material Controls:** Adjust color, metallic, roughness, ambient, and transparency properties for the birds.
- **Wing Animation:** Control wing flap speed and amplitude for more lifelike movement.
- **Audio Panel:** Expand/collapse the audio panel to control soundscape, master volume, and individual sound layers (melody, synth, pad, wind, whoosh, reverb).
- **Post-Processing:** Control blur intensity and reset effects as needed.
- **Boid Count:** Use the boid slider to set the number of birds in the simulation (up to hardware limits).

## Technical Details

- **Babylon.js + WebGPU:** Uses Babylon.js for rendering and WebGPU for compute shader acceleration, enabling massive parallelism and high performance.
- **Compute Shaders:** All flocking logic, spatial indexing, and boid updates are performed on the GPU using WGSL shaders.
- **Instanced Rendering:** Birds are rendered as instanced meshes for efficiency, with support for custom mesh types and materials.
- **Parameter Uniforms:** All simulation parameters are passed to shaders via uniform buffers, allowing real-time updates.
- **LocalStorage Presets:** User presets are stored in the browser for persistent customization, now including color and lighting.
- **Responsive Design:** The app adapts to window resizing and device capabilities. Control panel is fixed to the right for modern UX.

## Getting Started

1. **Install Dependencies:**
	- Run `npm install` to install required packages.
2. **Run the App:**
	- Use `npm run dev` (or your preferred Vite command) to start the development server.
	- Open `index.html` in your browser.
3. **Explore:**
	- Use the UI controls to experiment with flocking behaviors, mesh types, lighting, soundscapes, and more.
	- Save your favorite parameter sets as user presets.

## File Structure

- `src/main3d.ts` — Main entry point for the 3D flocking simulation, UI logic, and audio panel.
- `src/meshes/` — Mesh definitions for birds (triangle, pyramid, Babylon Bird).
- `src/shaders/3d/compute/` — WGSL compute shaders for boid logic, grid management, and more.
- `index.html` — Main HTML file with UI elements and canvas.
- `style.css` — App styling.
- `package.json`, `tsconfig.json`, `vite.config.js` — Project configuration files.

## Credits

- Built with [Babylon.js](https://www.babylonjs.com/) and [WebGPU](https://gpuweb.github.io/).
- Flocking algorithm inspired by Craig Reynolds and extended for BirdMusic behaviors.
- Meshes, shaders, and UI designed for creative and educational use.
- Based on the original project: [BoidsWebGPU on GitHub](https://github.com/jtsorlinis/BoidsWebGPU)

## License

This project is licensed under the MIT License.

---

For questions, suggestions, or contributions, please open an issue or pull request.
