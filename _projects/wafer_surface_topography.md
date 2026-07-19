---
layout: page
title: Wafer Surface Topography
description: White-light interferometry based wafer surface profiling with CUDA C++.
importance: 2
category: research
img: assets/img/Wafer Surface topography.png
---

At Frontier Semiconductor Metrology, I developed a high-precision, non-contact wafer surface profiling system based on White Light Interferometry (WLI). The system combines synchronized optomechanical acquisition with a GPU-accelerated reconstruction pipeline to create nanometer-resolution 3D wafer height maps for manufacturing metrology and quality control.

![Wafer surface topography measurement]({{ '/assets/img/Wafer Surface topography.png' | relative_url }})

## System architecture

- A Basler industrial camera captures a high-resolution image at each Z-position while a Thorlabs piezoelectric stage scans a 400 micrometer range in approximately 10 nanometer steps.
- The resulting X-Y-Z image stack records intensity variation through the scan depth. Peak fringe contrast at each pixel indicates the local wafer height.
- A custom CUDA C++ kernel processes the independent pixel signals in memory-efficient batches, finding the best-focus/coherence position and assembling the final height map.

## Technical challenges and impact

- Synchronized camera exposure and piezo-stage positioning so every frame maps to a known height.
- Built noise-robust peak detection for sensor noise, vibration, and multiple local intensity maxima.
- Used batched GPU processing to handle hundreds of high-resolution frames without exhausting GPU memory.

The system produces non-contact, sub-micron-to-nanometer-accurate 3D surface maps and substantially reduces scan-to-result time compared with a CPU pixel-by-pixel pipeline.

**Tech:** Basler industrial camera, Thorlabs piezo Z-stage, WLI optics, MFC C++, camera SDK, CUDA C++.
