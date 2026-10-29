---
layout: page
title: Long-term Human Motion Prediction
description: University Research Assistant · 11/2024 – 04/2025
img: assets/img/projects/fau-logo.jpg
importance: 3
category: Work
---

**Where:** Chair of Automatic Control (Lehrstuhl für Regelungstechnik), FAU Erlangen-Nürnberg — supervised by M.Sc. Philipp Santer

**Goal.** Predict long-term human motion trajectories so robots can move safely around people.

**What I did.**

- Developed an MDP-based model with social forces in Python.
- Extended the JS-MDP planner (Rudenko et al., ICRA 2018) with obstacle-aware action discretization, a goal-distance reward, goal deceleration and dynamic inertia.
- Tuned the model with Bayesian optimization (SMAC3).

**Results.** On the THÖR dataset, reduced the average displacement error by **up to 19% vs. the constant-velocity model** and **8% vs. JS-MDP**, and analyzed the accuracy–runtime trade-off for real-time use.

## From observation to prediction

Pick one of the example scenes from my report and follow it step by step: what the model observes, how it infers each person's goal and plans towards it, how its 4.8-second prediction compares with other models and with where people actually walked, and how the models do across the whole dataset.

<iframe class="mdp-frame" src="{{ '/assets/mdp/prediction.html' | relative_url }}" title="Animation of human motion prediction on the THÖR dataset" loading="lazy"></iframe>

<p class="small text-muted">The example scenes were re-run with my final code; the benchmark numbers are from the final report. Trajectory data: <a href="http://thor.oru.se/" target="_blank" rel="noopener">THÖR dataset</a>, Örebro University.</p>

<style>
  .post article p, .post article li { text-align: justify; hyphens: auto; }
  .mdp-frame { display: block; width: 100%; height: 1100px; border: 0; margin: 0.5rem 0 1rem; background: transparent; }
</style>

<script>
  window.addEventListener("message", function (e) {
    if (!e.data || e.data.thesisFrame !== "mdp") return;
    document.querySelectorAll(".mdp-frame").forEach(function (f) {
      f.style.height = e.data.h + "px";
    });
  });
</script>

**Stack:** Python · Markov decision processes · Social forces · SMAC3
