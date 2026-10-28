---
layout: page
title: Long-term Human Motion Prediction
description: University Research Assistant · FAU Erlangen-Nürnberg · 11/2024 – 04/2025
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

**Stack:** Python · Markov decision processes · Social forces · SMAC3
