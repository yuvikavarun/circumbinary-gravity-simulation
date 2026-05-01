# P-Type Circumbinary Planet Simulation

A real-time, WebGL-powered physics playground where a terrestrial planet orbits two stars (a primary yellow star and a secondary red dwarf).

Instead of faking the orbits with fixed animations, I wanted to see what happens when you actually simulate the gravity and lighting. Here's a quick look at how it works under the hood.

## Tech Stack

![Three.js](https://img.shields.io/badge/threejs-black?style=for-the-badge&logo=three.js&logoColor=white)
![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E)
![WebGL](https://img.shields.io/badge/WebGL-990000?style=for-the-badge&logo=webgl&logoColor=white)
![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/css3-%231572B6.svg?style=for-the-badge&logo=css3&logoColor=white)

## The Physics

* **Live N-Body Gravity:** The simulation calculates the gravitational pull between all three bodies every frame using standard Newtonian physics ($F = G \frac{m_1 m_2}{r^2}$). It's a dynamically calculated, chaotic environment.

* **Symplectic Euler Integrator:** Standard math usually breaks orbital simulations over time (planets eventually crash or fly away). By chopping the frames into smaller sub-steps and calculating velocity first, the engine conserves the system's energy and keeps the orbits perfectly stable.

* **Galactic Helical Motion:** Solar systems aren't stationary; they orbit the galactic center. Toggling the "Galactic Orbit" applies a continuous velocity along the Y-axis, showing how the system actually corkscrews through space.

## The Planet

I used high-res Earth cartography to really show off how a planet's surface reacts to being lit by two different suns.

* **Normal Mapping:** This does the heavy lifting. It alters the surface normals so the yellow and red stars cast physically accurate, shifting shadows across the mountains and terrain as they orbit.

* **Atmosphere:** There's a slightly larger, independent mesh wrapped around the planet for clouds. It uses additive blending to simulate atmospheric dynamics without clipping into the ground.

## Rendering

* **Procedural Stars:** The star textures aren't loaded from images. They're generated procedurally at runtime using the HTML5 Canvas API, layering thousands of radial gradients to look like bubbling plasma.

* **True Dual Lighting:** There's no fake global lighting. High-intensity point lights are nested directly inside the stars, so you can watch the warm yellow and deep red lights physically blend on the planet's surface.

* **Tone Mapping:** I used ACESFilmic tone mapping to handle the massive dynamic range. It keeps the bright star cores from blowing out the colors while maintaining the pitch-black void of space.

---

Built by Yuvika Varun
