---
layout: page
title: Cubic Drone Simulation
description: Bachelor's Thesis · 04/2021 – 04/2022
img: assets/img/projects/hust-logo.jpg
importance: 4
category: Work
---

**Where:** Department of Applied Mechanics, Hanoi University of Science and Technology (HUST) — supervised by Dr. Thai Phuong Thao

**Goal.** A quadcopter whose four arms fold down into a cube when it rests and open flat to fly. The arm angles can also change during flight, so the drone can adapt its shape to its surroundings, for example to fly through a narrow gap.

**What I did.**

- Designed the drone and its folding mechanism in Siemens NX: one servo per arm drives a four-bar linkage. A MATLAB search listed every set of link lengths that folds into the cube, and I chose the most compact one.
- Derived the drone's 12 equations of motion, with the four arm angles as extra inputs.
- Built an open-loop simulator and a PID controller for roll, pitch, yaw and height in MATLAB.
- Tested the FASTER planner (Tordesillas et al., IROS 2019) with the Cubic Drone, for fast flight through unknown environments.

**Results.**

- With a 1 kg design and four motors of 4.0 N, the drone can take off and can hover with its arms tilted up to 52°.
- The controller held the drone's attitude and height with its arms folded, for example while climbing 6 m with the arms at 45°, 30°, 45° and 30°.
- The work was published at ASIAN MMS 2021 (Springer):

<div class="publications">
{% bibliography --group_by none %}
</div>

## How the drone folds and flies

Follow the drone from its folding mechanism to a controlled climb: how one servo per arm folds it into a cube, why tilted arms cost thrust, and how it holds its height with its arms folded.

<iframe class="cubic-frame" src="{{ '/assets/hust/cubic-drone.html' | relative_url }}" title="Animation of the Cubic Drone folding, its four-bar linkage, thrust and height control" loading="lazy"></iframe>

<p class="small text-muted">The geometry, mass and motor limits come from the thesis. The drone itself was not built, so all motion here is simulated.</p>

<figure class="cubic-figure">
  <img src="{{ '/assets/img/projects/cubic-drone-cad.jpg' | relative_url }}" alt="CAD model of the Cubic Drone, opened flat and folded into a cube, with a cut through the four-bar linkage" loading="lazy">
  <figcaption>The CAD model in Siemens NX: opened flat, folded into a cube, and a cut through one arm's linkage.</figcaption>
</figure>

<figure class="cubic-figure wide">
  <video src="{{ '/assets/video/hust/cubic-climb-folded.mp4' | relative_url }}" poster="{{ '/assets/video/hust/cubic-climb-folded.jpg' | relative_url }}" controls muted loop playsinline preload="none"></video>
  <figcaption>The MATLAB simulation from the thesis: with its arms at 45°, 30°, 45° and 30°, the drone climbs from 10 m to 16 m and holds its attitude. The z axis points down, so heights read as negative numbers.</figcaption>
</figure>

## Further experiment: fast planning in unknown environments

After the thesis simulations, I tested FASTER, a planner from MIT for fast and safe flight through unknown environments, with the Cubic Drone. FASTER builds a map from a depth camera, searches a global path that may cross unknown space, and optimizes a fast trajectory together with a safe backup that stays inside space the camera has already seen. Follow one flight through a wall with a 0.7 m slot: what the drone senses, how it plans, how it decides when to fold its arms to fit through the slot, and how much time folding saves.

<iframe class="faster-frame" src="{{ '/assets/hust/faster.html' | relative_url }}" title="Animation of the FASTER planner flying the Cubic Drone through an unknown environment and folding its arms for a narrow slot" loading="lazy"></iframe>

<p class="small text-muted">The world is generated; the flights are re-simulated in the browser with the drone's size, mass and motor thrust from the thesis.</p>

<style>
  .post article p, .post article li { text-align: justify; hyphens: auto; }
  .faster-frame { display: block; width: 100%; height: 1100px; border: 0; margin: 0.5rem 0 1rem; background: transparent; }
  .cubic-frame { display: block; width: 100%; height: 1100px; border: 0; margin: 0.5rem 0 1rem; background: transparent; }
  .cubic-figure { margin: 0.5rem auto 1.5rem; max-width: 640px; }
  .cubic-figure.wide { max-width: none; }
  .cubic-figure img { width: 100%; border-radius: 8px; background: #fff; }
  .cubic-figure video { display: block; width: 100%; aspect-ratio: 1362 / 724; border-radius: 8px; background: #0b0d10; }
  .cubic-figure figcaption { font-size: 0.85rem; color: var(--global-text-color-light); margin-top: 0.3rem; text-align: justify; hyphens: auto; }
</style>

<script>
  window.addEventListener("message", function (e) {
    if (!e.data || (e.data.thesisFrame !== "cubic" && e.data.thesisFrame !== "faster")) return;
    document.querySelectorAll("." + e.data.thesisFrame + "-frame").forEach(function (f) {
      f.style.height = e.data.h + "px";
    });
  });
</script>

**Stack:** MATLAB · Siemens NX · ROS1 · Gazebo
