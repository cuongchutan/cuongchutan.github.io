---
layout: about
title: About
permalink: /
subtitle: Robotics Software Engineer &#124; ROS2 &middot; C++ &middot; Python &middot; 3D Perception

profile:
  align: right
  image: prof_pic.jpg
  image_circular: true # crops the image to make it circular
  more_info: >
    <div class="contact-line"><i class="fa-solid fa-location-dot fa-fw"></i><span>Aalen, Germany</span></div>
    <div class="contact-line"><i class="fa-solid fa-language fa-fw"></i><span>Vietnamese (native)<br>English (C1)<br>German (B1)</span></div>
    <div class="contact-line"><i class="fa-solid fa-envelope fa-fw"></i><span><a href="mailto:cuongchutan@gmail.com">cuongchutan@gmail.com</a></span></div>

selected_papers: false # replaced by the Publication section below
social: true # includes social icons at the bottom of the page

announcements:
  enabled: false

latest_posts:
  enabled: false
---

<style>
  .profile .contact-line { display: flex; gap: 0.5rem; margin: 0.35rem 0; line-height: 1.5; }
  .profile .contact-line i { color: var(--global-theme-color); margin-top: 0.25rem; }
  .profile .contact-line a { word-break: break-all; }
  .about-summary { text-align: justify; hyphens: auto; }
  .edu-card { display: flex; gap: 1rem; padding: 1rem 1.25rem; margin-bottom: 1rem; border: 1px solid var(--global-divider-color); border-left: 4px solid var(--global-theme-color); border-radius: 0.5rem; }
  .edu-icon { font-size: 1.6rem; color: var(--global-theme-color); line-height: 1; padding-top: 0.2rem; }
  .edu-body { flex: 1; min-width: 0; }
  .edu-head { display: flex; flex-wrap: wrap; justify-content: space-between; gap: 0.25rem 1rem; }
  .edu-degree { font-weight: 600; font-size: 1.1rem; }
  .edu-date { color: var(--global-text-color-light); white-space: nowrap; }
  .edu-school { margin: 0.15rem 0 0.5rem; }
  .edu-tags { display: flex; flex-wrap: wrap; gap: 0.4rem; }
  .edu-tag { font-size: 0.85rem; padding: 0.1rem 0.6rem; border-radius: 1rem; border: 1px solid var(--global-theme-color); color: var(--global-theme-color); }
  @media (min-width: 576px) {
    .post-header { margin-right: 32%; }
    .post article > .profile { margin-top: -6.4rem; }
  }
  .edu-note { margin-top: 0.5rem; font-size: 0.9rem; color: var(--global-text-color-light); }
</style>

**Open to full-time, long-term positions in robotics software, 3D perception and robot manipulation — available to start as soon as possible.**

I aim to be a robotics software engineer with an M.Sc. in Computational Engineering (Elite Program) from FAU Erlangen-Nürnberg. I build perception and manipulation software that runs on real robots. 
In my master's thesis at **Carl Zeiss**, I developed a method that reconstructs 3D models of unknown, textureless objects from RGB images alone; on industrial objects it was the most accurate method benchmarked (2.8 mm Chamfer distance) and ran 32% faster than COLMAP. 
As a robotics software intern at **BMW Group**, I contributed to a dual-robot pick-and-place cell that handled two full bins (~40 parts) autonomously. 
Before that, I worked on human motion prediction for safe human-robot interaction at **FAU**, safety-critical ADAS software on automotive ECUs at **Bosch**, and LiDAR SLAM and drone design at **HUST**.
{: .about-summary}

<div style="clear: both"></div>

## Education

<div class="edu-card">
  <div class="edu-icon"><i class="fa-solid fa-graduation-cap"></i></div>
  <div class="edu-body">
    <div class="edu-head">
      <span class="edu-degree">M.Sc. Computational Engineering</span>
      <span class="edu-date"><i class="fa-regular fa-calendar"></i> 10/2023 – 11/2026</span>
    </div>
    <div class="edu-school">Friedrich-Alexander-Universität Erlangen-Nürnberg (FAU), Germany</div>
    <div class="edu-tags">
      <span class="edu-tag">Elite Program</span>
      <span class="edu-tag">GPA 1.6 (German scale)</span>
    </div>
    <div class="edu-note"><i class="fa-solid fa-users"></i> Member of the Bavarian Graduate School of Computational Engineering (BGCE), Elitenetzwerk Bayern</div>
  </div>
</div>

<div class="edu-card">
  <div class="edu-icon"><i class="fa-solid fa-graduation-cap"></i></div>
  <div class="edu-body">
    <div class="edu-head">
      <span class="edu-degree">B.Sc. Mechatronics Engineering</span>
      <span class="edu-date"><i class="fa-regular fa-calendar"></i> 09/2017 – 05/2022</span>
    </div>
    <div class="edu-school">Hanoi University of Science and Technology (HUST), Vietnam</div>
    <div class="edu-tags">
      <span class="edu-tag">Elite Program</span>
      <span class="edu-tag">GPA 3.31 / 4.0 (Very Good) = 1.7 (German scale)</span>
    </div>
  </div>
</div>

## Skills

<div markdown="1">

| Area                 | Advanced               | Intermediate / Basic     |
| -------------------- | ---------------------- | ------------------------ |
| Robotics             | ROS2, MoveIt2          | Isaac Sim, MuJoCo        |
| 3D Perception        | OpenCV, Open3D         | PyTorch, SAM3            |
| Programming          | Python, C, C++, MATLAB | JavaScript               |
| AI applications      | LangChain, Streamlit   | LLMs, OCR, RAG           |
| Software development | Git, Linux             | Docker                   |
| CAD / 3D software    | SolidWorks             | Siemens NX, CloudCompare |

</div>

## Publication

<div class="publications">
{% bibliography --group_by none %}
</div>
