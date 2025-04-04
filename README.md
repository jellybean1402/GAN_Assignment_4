# GANs in Medical Imaging: Evaluating WGAN, LSGAN, and WGAN-GP on ChestMNIST  

## Author: Ramitha Vimala  

## Introduction  
Generative Adversarial Networks (GANs) have significantly impacted deep learning, especially in **image synthesis, data augmentation, and unsupervised learning**. GANs consist of two competing networks:  
- **Generator**: Creates synthetic images.  
- **Discriminator**: Differentiates real images from generated ones.  

In medical imaging, GANs help overcome **data scarcity, privacy concerns, and model generalization** challenges. They generate **high-quality synthetic medical images**, improving training datasets and aiding rare disease diagnosis.  

This study evaluates **WGAN, LSGAN, and WGAN-GP** on the **ChestMNIST** dataset to assess their performance in medical image generation.  

---

## Dataset: ChestMNIST  
ChestMNIST is a subset of **MedMNIST**, designed for medical image analysis.  
- Derived from **ChestX-ray14**, a large-scale X-ray dataset.  
- **28×28 grayscale** images for binary classification (**Normal vs. Abnormal**).  
- **48,000 training**, **3,000 test**, and **6,000 validation** images.  

---

## GAN Architectures  

### 1. Least Squares GAN (LSGAN)  
**LSGAN** improves training stability by replacing the **binary cross-entropy loss** with a **least squares loss**.  
- Reduces **mode collapse** and improves **gradient flow**.  
- Ensures that even well-classified samples contribute to training.  

**Performance:**  
- **Inception Score (IS):** 1.9261  
- **Fréchet Inception Distance (FID):** 16.5826  
- **Challenges:** Lower IS suggests generated images may **lack diversity**.  

### 2. Wasserstein GAN (WGAN)  
**WGAN** addresses GAN instability by replacing **Jensen-Shannon divergence** with the **Wasserstein distance (Earth Mover’s Distance)**.  
- Uses a **Critic instead of a Discriminator** for stable optimization.  
- Requires **weight clipping** to enforce Lipschitz continuity.  

**Performance:**  
- **Inception Score (IS):** 1.5324  
- **Fréchet Inception Distance (FID):** 15.6708  
- **Challenges:** High instability and possible **mode collapse**.  

### 3. Wasserstein GAN with Gradient Penalty (WGAN-GP)  
**WGAN-GP** improves WGAN by **replacing weight clipping** with a **gradient penalty**, ensuring smoother gradients and better training stability.  

**Performance:**  
- **Inception Score (IS):** **1.9554**  
- **Fréchet Inception Distance (FID):** **4.5178**  
- **Best Performance**: Most realistic and diverse generated images.  

---

## Comparison of GAN Architectures  

| GAN Model | Inception Score (IS) | FID Score | Stability | Mode Collapse |  
|-----------|-----------------|----------|------------|---------------|  
| **LSGAN**  | 1.9261          | 16.5826  | Moderate   | Possible     |  
| **WGAN**   | 1.5324          | 15.6708  | Low        | High         |  
| **WGAN-GP** | **1.9554**      | **4.5178**  | **High**   | **Minimal**  |  

### Key Findings:  
- **WGAN-GP outperforms** LSGAN and WGAN in **image quality and training stability**.  
- **LSGAN reduces instability** but still struggles with **image diversity**.  
- **WGAN suffers from mode collapse** and requires careful tuning.  

---

## Conclusion  
For **medical image generation**, **WGAN-GP** is the most effective model, producing **realistic and diverse** ChestMNIST images with minimal mode collapse. Future work can explore **convolutional architectures, deeper networks, and improved loss functions** for better medical image synthesis.  

---
