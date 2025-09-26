# Denoising Diffusion Probabilistic Model (DDPM) on CIFAR-10

This project implements a **Denoising Diffusion Probabilistic Model (DDPM)** for generative modeling on the **CIFAR-10 dataset**.  
The model learns to generate high-quality images by iteratively denoising Gaussian noise, conditioned on class labels.

---

## Project Overview

- **Dataset:** CIFAR-10 (32×32 color images across 10 classes).  
- **Preprocessing:**
  - Random horizontal flips and random cropping for data augmentation.  
  - Normalization to range [-1, 1].  

- **Model Core:**  
  - A **U-Net–based architecture** (`ContextUnet`) with residual convolutional blocks.  
  - **Time Embeddings:** Encodes diffusion step information.  
  - **Class Conditioning:** One-hot encoded class labels embedded and used to guide generation.  
  - **Dropout Context Mask:** Allows stochastic masking of conditioning during training for robustness.  

- **Diffusion Process:**  
  - **Forward Process:** Images are gradually noised across a fixed number of time steps.  
  - **Reverse Process:** The DDPM progressively removes noise to reconstruct data samples.  
  - **Noise Prediction Objective:** The model is trained to predict added noise at each step using MSE loss.  

---

## Key Components

- **ResidualConvBlock:** Convolutional layers with optional residual connections.  
- **UnetDown / UnetUp:** Encoder and decoder blocks for the U-Net backbone.  
- **ContextUnet:** Main architecture integrating noise/time embeddings and class conditioning.  
- **DDPM Class:**
  - Implements the full diffusion process.  
  - Training loss based on noise prediction.  
  - Sampling procedure to generate images from random noise.  

---

## Evaluation

- **PSNR (Peak Signal-to-Noise Ratio):** Used to assess reconstruction quality at various stages.  
- **Visualization Tools:**
  - Side-by-side comparisons of original, noisy, and reconstructed images.  
  - Progressive sampling outputs to visualize the denoising trajectory.  

