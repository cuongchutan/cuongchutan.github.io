---
layout: page
title: Multi-Drone Planner Comparison
description: Personal Project · 09/2025 – 10/2025
teaser: "Which planner flies two drones through a mine inspection fastest, even when they have no map?"
img: assets/img/projects/mrs-2025.jpg
importance: 1
category: Personal
---

**Where:** Personal project after the IEEE RAS Summer School on Multi-Robot Systems (CTU Prague, 2025), where my team ranked 4th of 42 in the real-world challenge.

**Goal.** Find the fastest safe way for two drones to inspect a surface mine, and measure what it costs when the drones do not know the map.

**What I did.**

- Built a test bench around our competition pipeline that runs every method on all three challenge maps and scores each mission with the competition's checks.
- Compared A\*, Theta\* and RRT\*, which plan on the known map, with a simplified FASTER that maps the mine with a LiDAR while flying.
- Found and fixed a grid-planner bug that made the drones miss most inspections, and an RRT\* setting that kept it from rewiring.

**Results.**

- All four methods inspected every point and kept the safety distances on every map.
- With the map known, Theta\* was the fastest (59.4 s on the large map) and computed 3–6× faster than A\*.
- FASTER, without a map, was the fastest on the large map (57.6 s); not knowing the map cost it only 0.2 s.

## How the methods compare

Pick a map and a method: see how the inspection points are shared, where the four methods' paths differ, how the drones fly, and how fast each method is.

<iframe scrolling="no" class="mrs-frame" src="{{ '/assets/mrs/inspection.html' | relative_url }}" title="Animation of two drones inspecting a surface mine, comparing the A*, Theta*, RRT* and FASTER planners" loading="lazy"></iframe>

<p class="small text-muted">The terrain, paths, trajectories and scores are the real outputs of the runs; only the playback happens in the browser.</p>

<style>
  .post article p, .post article li { text-align: justify; hyphens: auto; }
  .mrs-frame { display: block; width: 100%; height: 1150px; border: 0; margin: 0.5rem 0 1rem; background: transparent; }
</style>

<script>
  window.addEventListener("message", function (e) {
    if (!e.data || e.data.thesisFrame !== "mrs") return;
    document.querySelectorAll(".mrs-frame").forEach(function (f) {
      f.style.height = e.data.h + "px";
    });
  });
</script>

**Stack:** Python · ROS1 · MRS UAV System
