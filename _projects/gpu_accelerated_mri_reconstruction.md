---
layout: page
title: GPU-Accelerated MRI Image Reconstruction
description: Real-time k-space-to-image reconstruction engine, migrated from legacy DSP processing to CUDA C++.
importance: 3
category: research
img: assets/img/mri_kspace_data.jpg
---

I worked on the reconstruction engine of a clinical MRI system - the server-side module that receives raw scanner data (k-space) over the network during a live exam and converts it into diagnostic images in real time. My focus was migrating the legacy DSP-based processing pipeline to CUDA C++ so reconstruction runs on GPU hardware, including embedded NVIDIA Jetson Xavier NX deployments.

![MRI k-space data and its Fourier-transform relationship to image space]({{ '/assets/img/mri_kspace_data.jpg' | relative_url }})

## System architecture

- The reconstruction engine runs as a network server on Ubuntu Linux. During a scan, the MRI spectrometer controller streams acquired k-space data to it over TCP/IP, along with a queue of processing commands describing how each acquisition must be handled.
- Processing is multithreaded: each receiver-coil channel is handled by its own worker thread with dedicated local memory, while a shared memory pool holds the multi-dimensional dataset (volumes, echoes, slices, views) across channels.
- Reconstruction is expressed as a command-queue pipeline - filtering, 1D/2D FFTs, phase correction, channel recombination, and image-domain post-processing are chained per pulse sequence.

## My contributions

- Re-engineered the k-space-to-image conversion stages for massively parallel GPU execution with CUDA C++, replacing sequential DSP-style loops with batched per-pixel and per-view kernels.
- Implemented and validated reconstruction paths for standard acquisition schemes, including partial-Fourier (homodyne) reconstruction, parallel-imaging (GRAPPA) reconstruction, and EPI reconstruction with phase correction.
- Integrated a Jetson Xavier NX-based reconstruction command server with the MRI spectrometer controller, enabling real-time processing and image rendering on embedded GPU hardware.
- Used a scanner-emulation test harness that replays recorded k-space data over the same network protocol as a live exam, allowing new algorithms to be debugged and verified end-to-end without scanner time.

## Technical challenges and impact

- Preserved numerical fidelity of the clinical pipeline while restructuring it for GPU parallelism - reconstructed images were validated against the legacy implementation.
- Managed GPU memory carefully to process large multi-channel, multi-slice datasets within the limits of an embedded Jetson module.
- Real-time constraint: data arrives continuously during acquisition, so per-view processing must keep pace with the scanner rather than run as an offline batch job.

**Tech:** CUDA C++, NVIDIA Jetson Xavier NX, Ubuntu Linux, TCP/IP socket programming, multithreading, FFT-based MRI reconstruction (GRAPPA, homodyne, EPI phase correction), Visual Studio.
