---
layout: page
title: Mobile Robot SLAM & Cubic Drone
description: University Research Assistant · 01/2020 – 04/2022
img: assets/img/projects/hust-logo.jpg
importance: 5
category: Work
---

**Where:** Department of Mechatronics and Department of Applied Mechanics, Hanoi University of Science and Technology (HUST) — supervised by Assoc. Prof. Nguyen Xuan Ha and Dr. Thai Phuong Thao

**Autonomous service mobile robot.** Implemented 2D LiDAR-based SLAM and navigation in ROS1 on a mobile robot. The project won the **1st prize in the HUST Student Research Competition (2020)**.

## How the robot finds its way

Follow the robot from its sensors to a safe drive: why one LiDAR is not enough, how it maps a room, how it plans paths on that map, and what happens when an obstacle is invisible to the LiDAR.

<iframe class="hust-frame" src="{{ '/assets/hust/navigation.html' | relative_url }}" title="Animation of the robot's sensor layers, mapping, navigation and safety layer" loading="lazy"></iframe>

<p class="small text-muted">The map is the real one the robot recorded in the AIR lab; the drives are re-simulated in the browser using the parameters from our ROS configuration.</p>

**The real thing.** Clips from our 2020 presentation:

<div class="hust-videos">
  <figure>
    <video src="{{ '/assets/video/hust/real-robot-box.mp4' | relative_url }}" poster="{{ '/assets/video/hust/real-robot-box.jpg' | relative_url }}" controls muted loop playsinline preload="none"></video>
    <figcaption>The real robot turns away from a box held above its LiDAR plane.</figcaption>
  </figure>
  <figure>
    <video src="{{ '/assets/video/hust/gazebo-navigation.mp4' | relative_url }}" poster="{{ '/assets/video/hust/gazebo-navigation.jpg' | relative_url }}" controls muted loop playsinline preload="none"></video>
    <figcaption>Navigation in a simulated home (Gazebo and RViz).</figcaption>
  </figure>
  <figure>
    <video src="{{ '/assets/video/hust/gazebo-sensor-layers.mp4' | relative_url }}" poster="{{ '/assets/video/hust/gazebo-sensor-layers.jpg' | relative_url }}" controls muted loop playsinline preload="none"></video>
    <figcaption>Mapping a simulated room with the LiDAR (Gazebo and RViz).</figcaption>
  </figure>
</div>

<style>
  .hust-frame { display: block; width: 100%; height: 1100px; border: 0; margin: 0.5rem 0 1rem; background: transparent; }
  .hust-videos { display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 1rem; margin: 0.5rem 0 1.5rem; }
  .hust-videos figure { margin: 0; }
  .hust-videos video { width: 100%; aspect-ratio: 16 / 10; object-fit: cover; border-radius: 8px; background: #0b0d10; }
  .hust-videos figcaption { font-size: 0.85rem; color: var(--global-text-color-light); margin-top: 0.3rem; }
</style>

<script>
  window.addEventListener("message", function (e) {
    if (!e.data || e.data.thesisFrame !== "hust") return;
    document.querySelectorAll(".hust-frame").forEach(function (f) {
      f.style.height = e.data.h + "px";
    });
  });
</script>

**Cubic Drone.** Designed a foldable quadcopter that can rotate its arms vertically, published at ASIAN MMS 2021 (Springer):

<div class="publications">
{% bibliography --group_by none %}
</div>

**Stack:** ROS1 · 2D LiDAR SLAM · Navigation · Drone design
