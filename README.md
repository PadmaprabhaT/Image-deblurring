# Deblurring Motion-Blur Images using Multi-Scale GAN with Hybrid Attention Residual Network

## Overview

Motion blur caused by camera shake or object movement significantly degrades image quality and makes it difficult to recover important visual information. This project proposes a **Multi-Scale Generative Adversarial Network (GAN)** enhanced with **Hybrid Attention Residual (HAR) blocks** for restoring sharp images from motion-blurred inputs.

Unlike conventional GAN-based deblurring methods, the proposed architecture combines **multi-scale feature extraction, channel attention, spatial attention, switchable normalization, and depthwise separable convolutions** to improve image restoration quality while reducing computational complexity.

---

## Features

- Multi-scale feature extraction using parallel convolutions (1×1, 3×3, 5×5, 7×7)
- Hybrid Attention Residual Blocks
  - Channel Attention
  - Spatial Attention
- Switchable Normalization
- Depthwise Separable CNN backbone
- PatchGAN Discriminator
- WGAN-GP adversarial training
- VGG19 Perceptual Loss
- L1 Reconstruction Loss
- Lightweight architecture with faster convergence

---

## System Architecture

```
Blurred Image
      │
      ▼
Multi-Scale Feature Extraction
      │
      ▼
Downsampling
      │
      ▼
Hybrid Attention Residual Blocks
      │
      ▼
Depthwise Separable CNN
      │
      ▼
Upsampling
      │
      ▼
Generated Sharp Image
      │
      ▼
PatchGAN Discriminator
      │
      ▼
Loss Computation
```

---

## Proposed Generator

The generator consists of

- Multi-scale feature extraction module
- Downsampling blocks
- 9 Hybrid Attention Residual (HAR) Blocks
- Depthwise Separable CNN
- Upsampling blocks
- Final image reconstruction layer

The HAR block integrates

- Residual learning
- Channel Attention
- Spatial Attention
- Switchable Normalization

to preserve fine textures while improving training stability.

---

## Loss Function

The model is trained using a combination of

- **WGAN-GP Adversarial Loss**
- **VGG19 Perceptual Loss**
- **L1 Reconstruction Loss**

This combination encourages

- sharper textures
- structural consistency
- realistic image generation
- stable GAN training

---

## Datasets

The model is trained and evaluated using multiple benchmark datasets.

| Dataset | Purpose |
|----------|---------|
| GoPro | Training & Testing |
| REDS | Testing |
| HIDE | Testing |
| RealBlur-J | Testing |

---

## Evaluation Metrics

Performance is evaluated using

- PSNR (Peak Signal-to-Noise Ratio)
- SSIM (Structural Similarity Index)

---

## Experimental Results

| Dataset | PSNR (dB) | SSIM |
|----------|-----------|-------|
| GoPro | **26.13** | **0.8296** |
| HIDE | 25.91 | 0.8193 |
| RealBlur-J | 24.26 | 0.7482 |
| REDS | 22.55 | 0.5707 |

---

## Novel Contributions

Compared to existing DeblurGAN architectures, this work introduces

- Hybrid Attention (Channel + Spatial)
- Switchable Normalization
- Depthwise Separable Convolutions
- Improved architecture stability
- Faster convergence with only **60 training epochs**
- Competitive image restoration quality with reduced computational cost

---

## Tech Stack

- Python
- PyTorch
- TorchVision
- OpenCV
- NumPy
- Matplotlib

---

## Project Structure

```
Image-Deblurring-Using-GAN/
│
├── dataset/
├── models/
│   ├── generator.py
│   ├── discriminator.py
│   └── attention.py
│
├── training/
│   ├── train.py
│   ├── test.py
│   └── utils.py
│
├── notebooks/
│   └── Image_Deblurring.ipynb
│
├── results/
├── images/
├── saved_models/
├── requirements.txt
├── README.md
└── LICENSE
```

## Applications

- Autonomous Vehicles
- Smartphone Photography
- Drone Imaging
- Satellite Imaging

---

## Authors

**Padmaprabha T**

**Poovitha S**

Department of Computer Science and Engineering

Mepco Schlenk Engineering College

---

## Acknowledgements

This work was inspired by recent advances in GAN-based image restoration, including DeblurGAN, DeblurGAN-v2, MIMO-UNet, and attention-based image deblurring networks.
