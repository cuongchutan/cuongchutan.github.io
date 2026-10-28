---
layout: page
title: Model-free 3D Object Reconstruction
description: Master's thesis · Carl Zeiss Group · 01/2026 – 10/2026
importance: 1
category: Work
---

**Where:** Carl Zeiss Group, Oberkochen, Germany — Master's thesis

**Goal.** Model-based pose tracking needs a 3D model of the object, but unknown, textureless industrial parts often come without a CAD model. My thesis develops an RGB-only method that reconstructs meshes of such objects without CAD models, so they can serve as object models for model-free pose tracking.

**Results.**

- Benchmarked on **38 objects from 5 public datasets** against FoundationPose, COLMAP MVS and NeMO.
- On industrial objects, it was the **most accurate method (2.8 mm Chamfer distance)**.
- Registered **100% of views** and ran **32% faster than COLMAP**.

## From video to 3D model

Three example runs, one for each way the camera and the object can move. Pick an object and watch it go from the input video through the reconstruction pipeline.

<iframe class="thesis-frame" data-view="pipeline" src="{{ '/assets/thesis/reconstruction.html?view=pipeline' | relative_url }}" title="Reconstruction pipeline animation" loading="lazy"></iframe>

## Outputs

The reconstructed meshes, their accuracy against the CAD model, and how well they match every input view. The car has no CAD model, so it is checked against the input views only.

<iframe class="thesis-frame" data-view="results" src="{{ '/assets/thesis/reconstruction.html?view=results' | relative_url }}" title="Reconstruction results animation" loading="lazy"></iframe>

<p class="small text-muted">These are single example runs; the benchmark figures above are averages over all objects. The object choice is shared between the two animations.</p>

> The thesis is under a confidentiality notice (Sperrvermerk) for two years, so the methodology is not published here. I am happy to talk about the work in an interview within those limits.

<style>
  .thesis-frame { display: block; width: 100%; height: 760px; border: 0; margin: 0.5rem 0 1rem; background: transparent; }
</style>

<script>
  window.addEventListener("message", function (e) {
    if (!e.data || !e.data.thesisFrame) return;
    document.querySelectorAll(".thesis-frame").forEach(function (f) {
      if (f.dataset.view === e.data.thesisFrame) f.style.height = e.data.h + "px";
    });
  });
</script>
