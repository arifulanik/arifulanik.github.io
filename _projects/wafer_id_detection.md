---
layout: page
title: Wafer ID Detection
description: CNN-based recognition of semi-font wafer IDs from machine-vision images.
importance: 5
category: research
img: assets/img/Wafer Id detection_Softwarer.jpg.png
---

Developed a computer-vision pipeline that detects and reads semi-font wafer IDs - alphanumeric identifiers laser-etched or dot-peened onto wafers for manufacturing traceability. It uses real-time machine-vision capture and CNN-based character recognition for low-contrast, noisy, irregular markings.

![Wafer ID detection software]({{ '/assets/img/Wafer Id detection_Softwarer.jpg.png' | relative_url }})

![Original semi-font wafer ID]({{ '/assets/img/Wafer Id detection_Wafer.jpg' | relative_url }})

## Development process

- Evaluated published and competitor approaches, then replaced an insufficiently accurate rule-based detector with a CNN-based recognition framework.
- Collected real ground-truth data by ordering wafers with printed IDs, first capturing samples with a Lucam camera and then with a high-speed Basler camera.
- Built a configurable preprocessing pipeline with contrast stretching, median and Gaussian blur, denoising, binary/adaptive thresholding, dot connection, dilation, and character-size controls.
- Added a desktop UI for test-image upload, filter tuning, live result validation, and model-training iteration.

## Technical challenges and impact

- Addressed limited representative training data with purpose-printed wafer samples instead of synthetic character data.
- Made preprocessing tunable per wafer type and imaging condition to improve low-contrast, dot-matrix character recognition.
- Delivered consistent recognition on real semi-font markings where the original rule-based approach could not meet accuracy requirements.

**Tech:** Basler and Lucam cameras, computer vision preprocessing, CNN character recognition, desktop GUI.
