---
layout: page
title: "Bachelor's Thesis: Cubic Drone"
description: Bachelor's Thesis · 04/2021 – 04/2022
img: assets/img/projects/hust-logo.jpg
importance: 4
category: Work
---

**Where:** Department of Applied Mechanics, Hanoi University of Science and Technology (HUST) — supervised by Dr. Thai Phuong Thao

**Cubic Drone.** In my bachelor's thesis, I designed a quadcopter whose four arms fold down into a cube when it rests and open flat to fly. The arm angles can also change during flight, so the drone can adapt its shape to its surroundings, for example to fly through a narrow gap. I designed the drone and its folding linkage, derived its equations of motion and built a PID controller for attitude and height, all simulated in MATLAB. The work was published at ASIAN MMS 2021 (Springer):

<div class="publications">
{% bibliography --group_by none %}
</div>

## How the drone folds and flies

Follow the drone from its folding mechanism to a controlled climb: how one servo per arm folds it into a cube, why tilted arms cost thrust, and how it holds its height with its arms folded.

<iframe class="cubic-frame" src="{{ '/assets/hust/cubic-drone.html' | relative_url }}" title="Animation of the Cubic Drone folding, its four-bar linkage, thrust and height control" loading="lazy"></iframe>

<p class="small text-muted">The geometry, mass and motor limits come from the thesis. The drone itself was not built, so all motion here is simulated.</p>

<figure class="cubic-cad">
  <img src="{{ '/assets/img/projects/cubic-drone-cad.jpg' | relative_url }}" alt="CAD model of the Cubic Drone, opened flat and folded into a cube, with a cut through the four-bar linkage" loading="lazy">
  <figcaption>The CAD model in Siemens NX: opened flat, folded into a cube, and a cut through one arm's linkage.</figcaption>
</figure>

**MATLAB simulations from the thesis:**

<div class="hust-videos">
  <figure>
    <video src="{{ '/assets/video/hust/cubic-climb-folded.mp4' | relative_url }}" poster="{{ '/assets/video/hust/cubic-climb-folded.jpg' | relative_url }}" controls muted loop playsinline preload="none"></video>
    <figcaption>PID height control: climbing to 16 m with the arms at 45°, 30°, 45° and 30°.</figcaption>
  </figure>
  <figure>
    <video src="{{ '/assets/video/hust/cubic-open-loop.mp4' | relative_url }}" poster="{{ '/assets/video/hust/cubic-open-loop.jpg' | relative_url }}" controls muted loop playsinline preload="none"></video>
    <figcaption>Open-loop control: setting the four motor speeds and four arm angles by hand.</figcaption>
  </figure>
</div>

## Fast planning in unknown environments

After the thesis, I worked with a student in our group on applying [FASTER](https://github.com/mit-acl/faster), MIT's planner for fast and safe flight through unknown environments, in ROS. Its pipeline builds a map from a depth camera, finds a global path with Jump Point Search, splits the free space along that path into convex regions, and optimizes a smooth local trajectory inside them. We tested it on a ground robot with an Intel RealSense depth camera in Gazebo, in forest, office and maze worlds.

**Could FASTER fly the Cubic Drone?** FASTER was built for multirotors, and with its arms held at one angle the Cubic Drone is a quadcopter, so in principle yes. The animation below is a concept simulation of that idea. The drone's size and thrust come from the thesis; the world, and the flight itself, are simulated.

<iframe class="faster-frame" src="{{ '/assets/hust/faster.html' | relative_url }}" title="Concept animation of the FASTER planner flying the Cubic Drone through an unknown environment" loading="lazy"></iframe>

<style>
  .faster-frame { display: block; width: 100%; height: 1100px; border: 0; margin: 0.5rem 0 1rem; background: transparent; }
  .cubic-frame { display: block; width: 100%; height: 1100px; border: 0; margin: 0.5rem 0 1rem; background: transparent; }
  .cubic-cad { margin: 0.5rem auto 1.5rem; max-width: 640px; }
  .cubic-cad img { width: 100%; border-radius: 8px; background: #fff; }
  .cubic-cad figcaption, .hust-videos figcaption { font-size: 0.85rem; color: var(--global-text-color-light); margin-top: 0.3rem; }
  .hust-videos { display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 1rem; margin: 0.5rem 0 1.5rem; }
  .hust-videos figure { margin: 0; }
  .hust-videos video { width: 100%; aspect-ratio: 16 / 9; object-fit: cover; border-radius: 8px; background: #0b0d10; }
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
