---
layout: page
title: Hardware-Accelerated Auto Focus
description: Real-time focus optimization on NVIDIA Jetson Orin NX.
importance: 1
category: research
---

Designed a hardware-accelerated autofocus system for real-time image processing and focus optimization using NVIDIA Jetson Orin NX, CUDA C++, and a Basler camera.

- Synchronized camera acquisition with motor-controller Z-axis traversal for automated focus sweeps.
- Built a client-server architecture to receive autofocus commands from FSM's RAFT software and coordinate camera-motor operations.
- Optimized CUDA C++ kernels with edge-based sharpness metrics for low-latency focal-position determination.
