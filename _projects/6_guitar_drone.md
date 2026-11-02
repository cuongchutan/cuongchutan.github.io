---
layout: page
title: Autonomous Guitar-Filming Drone
description: Personal Project · 06/2024 – present
teaser: "A drone that films me playing guitar on my trips, with camera moves timed to the music."
img: assets/img/projects/guitar-drone.jpg
importance: 2
category: Personal
---

**Status:** In progress. The drone works in simulation; next, I am building my own physical drone.

**Motivation.** I love playing guitar on my trips, but rarely have someone with the skill and the time to travel with me and film it. While I play, both hands and my eyes stay on the guitar, so I cannot fly a drone myself. I want a drone that films me on its own, timed to the rhythm or cued by other parts of my body, and that moves artistically around me and the guitar instead of hovering in one place.

**What I did.**

- Built a MuJoCo simulation in which a drone films a humanoid playing a guitar cover of "10,000 Hours".
- The drone listens to the song, finds its beats, bars and phrases, and plans one camera move per phrase.
- A flight controller flies the moves in gusty wind, while a gimbal keeps the face or the guitar in frame.

**Next.** Build the drone, track the beat live from a microphone, detect me with a pose tracker, and add hands-free cues such as head or foot gestures to steer the shots.

## How the drone films the song

The song plays once through the first four steps, in time with the animation; the last step is the full demo of the flight.

<iframe scrolling="no" class="guitar-frame" src="{{ '/assets/guitar/guitar-drone.html' | relative_url }}" title="Animation of a drone filming a guitarist, with camera moves timed to the song" loading="lazy" allow="autoplay"></iframe>

<p class="small text-muted">Simulated in MuJoCo with a Unitree G1 humanoid and a Skydio X2 drone.</p>

<style>
  .post article p, .post article li { text-align: justify; hyphens: auto; }
  .guitar-frame { display: block; width: 100%; height: 1200px; border: 0; margin: 0.5rem 0 1rem; background: transparent; }
</style>

<script>
  window.addEventListener("message", function (e) {
    if (!e.data || e.data.thesisFrame !== "guitar") return;
    document.querySelectorAll(".guitar-frame").forEach(function (f) {
      f.style.height = e.data.h + "px";
    });
  });
</script>

**Stack:** Python · MuJoCo physics simulator · librosa audio analysis
