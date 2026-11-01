---
layout: page
title: Multi-Robot Inspection Planner Comparison
description: Personal project · my own test bench and unknown-map experiment, beyond the IEEE RAS Summer School on Multi-Robot Systems (2025)
img: assets/img/projects/mrs-2025.jpg
importance: 1
category: Personal
---

**Where:** Personal project after the 2025 IEEE RAS Summer School on Multi-Robot Systems at the Czech Technical University in Prague, where my team ranked 4th of 42 in the real-world challenge.

**Goal.** Two drones must photograph every inspection point in a surface mine as fast as possible, without coming too close to the terrain or to each other. I wanted to know which planner gives the fastest safe mission on all three challenge maps, and what it costs when the drones do not know the map at all.

**What the summer school provided.** The task, the simulator, the scoring rules and a baseline pipeline in ROS:

- the drones share the inspection points (k-means);
- each drone's viewpoints are ordered into a tour (LKH);
- each leg is planned with A\*, RRT or RRT\* on a map known before takeoff;
- the paths are turned into trajectories with TOPPRA.

During the week, my team completed and tuned this pipeline for one competition run per map.

**What I added afterwards, on my own.**

- **A test bench instead of a single run.** I ran the team's pipeline without ROS on all three maps, repeatedly, and scored every run with the competition's checks: inspections, distance to the terrain, distance between the drones, and the speed limits. This turns "it worked in the competition" into a measured comparison.
- **A question the summer school did not ask: what if the map is unknown?** I implemented a simplified FASTER (Tordesillas et al., IROS 2019) in which the drones know only their viewpoints. A 360° LiDAR maps the mine in flight, the planner replans every 0.4 s, and the drone always keeps room to brake inside space it has already seen. A second run with the full map known measures what the missing map costs.
- **A new planner, Lazy Theta\*.** This any-angle version of A\* searches the same grid but is not bound to the grid's 45° steps.
- **Two problems found in the code.** The grid planners started and ended their paths at the nearest grid cell instead of the exact viewpoint, so the drones missed most inspections (only 1 of 6 on the small map); I fixed it. Our RRT\* never rewired its tree, because the rewiring radius (1 m) was shorter than its branches (3 m), so it behaved exactly like RRT; the comparison uses a 6 m radius.
- **The motion graphic below.** It is built from the actual outputs of these runs.

**Results.**

- Among the planners that know the map, Theta\* was the fastest on all three maps (59.4 s on the large map, all 28 points inspected) and computed 3–6× faster than A\*.
- FASTER, starting with no map, inspected every point on every map. It was the fastest on the large map (57.6 s), tied with Theta\* on the moderate map and 5% slower on the small one.
- Not knowing the map cost FASTER only 0.2 s on the large map: its 10 m LiDAR sees much farther than the drone needs to brake. Its lead comes from how it follows the path, not from planning without a map.
- Every method kept at least 1.5 m from the terrain and 2.5 m between the drones.

## How the drones plan the mission

Follow one mission from the task to the flight: how the inspection points are shared and ordered, how each planner replaces the straight legs with safe paths, how FASTER discovers the mine while flying, and how the four methods compare on every map.

<iframe scrolling="no" class="mrs-frame" src="{{ '/assets/mrs/inspection.html' | relative_url }}" title="Animation of two drones inspecting a surface mine, comparing the A*, Theta*, RRT* and FASTER planners" loading="lazy"></iframe>

<p class="small text-muted">The terrain, inspection points, paths, trajectories and scores are the real outputs of the pipeline runs; only the playback happens in the browser. FASTER is simplified: the original optimizes its trajectories with a mixed-integer solver, while here the drone follows the planned path under the same limits as the other methods.</p>

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

**Stack:** Python · ROS1 · MRS UAV System · Apptainer · TOPPRA · LKH
