---
layout: page
title: Model-free 3D Object Reconstruction
description: Master's thesis · Carl Zeiss Group · 01/2026 – 10/2026
importance: 1
category: Work
---

**Where:** Carl Zeiss Group, Oberkochen, Germany — Master's thesis

**Problem.** Model-based pose tracking needs a 3D model of the object. For unknown, textureless industrial parts there is often no CAD model, and classic multi-view stereo struggles without texture.

**What I built.** An RGB-only pipeline that reconstructs meshes of unknown, textureless objects without CAD models, producing object models for model-free pose tracking.

- Designed a modular six-stage architecture with a GUI, documented in UML.
- Combined SAM3 segmentation, XFeat feature extraction with RoMa v2 matching, and monocular depth anchored to visual-hull constraints.
- Built an automated evaluation framework (CAD alignment, Chamfer distance / F-score, ADD-S, statistics, ablation studies) that exposed failure modes hidden by single metrics.

**Results.** Benchmarked on 38 objects from 5 public datasets against FoundationPose, COLMAP MVS and NeMO. On industrial objects, it was the most accurate method (**2.8 mm Chamfer distance**), registered **100% of views** and ran **32% faster than COLMAP**.

**Stack:** SAM3 · XFeat · RoMa v2 · Monocular depth · Visual hull · GUI · UML
