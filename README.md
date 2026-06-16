# FaceLock: Proactive Adversarial Protection Against Unauthorized Identity Manipulation

FaceLock is a proactive adversarial defense framework designed to safeguard facial privacy against unauthorized biometric text-to-image generative modifications. Instead of detecting manipulated images post-facto (reactive protection), FaceLock injects imperceptible, optimized adversarial perturbations into a clean user portrait before it is uploaded to public or untrusted platforms. 

When an attacker attempts to pass a FaceLock-protected portrait through state-of-the-art diffusion-based editing pipelines (such as Stable Diffusion or Peft/LoRA-driven face-swapping mechanics), the spatial and semantic encoding maps collapse. This results in severe geometric distortion and completely breaks downstream biometric identity tracking, keeping your physical profile secure.

## Key Features

- **Proactive In-Camera/Pre-Upload Defense:** Embeds bounded, clean adversarial noise maps ($\epsilon = 0.08$) that are mathematically powerful yet completely unnoticeable to human observers.
- **Cross-Model Disruption:** Disrupts latent representations across text-guided diffusion frameworks (e.g., corporate re-stylization, attribute addition, and deep modifications).
- **Multi-Tier Security Auditing Pipeline:** - Dual evaluation metrics capturing pixel-level structural integrity (**PSNR**).
  - Production-grade Biometric Verification checking embedded vectors using **ArcFace (InsightFace Ecosystem)** against a standard verification threshold ($\tau = 0.68$).
  - High-level automated Vision-Language Model (**VLM**) validation logs via Qwen2.5-VL and Gemini frameworks.
### System Performance Indicators
- **Perceptual Metric:** High Peak Signal-to-Noise Ratio (PSNR) preserving original image clarity.
- **Biometric Metric:** Cosine distance inflation past $\tau = 0.68$, causing verification mechanisms to declare identity verification failure on generated forgeries.

## Experimental Benchmarks & Use-Cases

The pipeline demonstrates deterministic identity protection across multiple targeted generation prompts:

1. **Contextual Stylization Attacks (`"barbie style"`)**
   - *Without Protection:* ArcFace Cosine Distance = **0.4120** *(Identity successfully stolen/verified)*
   - *With FaceLock Protection:* ArcFace Cosine Distance = **0.8431** *(Identity successfully destroyed/protected)*

2. **Facial Attribute Modification (`"make the person wear glasses"`)**
   - *Without Protection:* ArcFace Cosine Distance = **0.3245** *(Identity tracked cleanly)*
   - *With FaceLock Protection:* ArcFace Cosine Distance = **0.7918** *(Identity broken)*

## Project Structure

```text
├── image_processing.py      # Master testing script, visualization hooks, and metric engines
├── defend.py                # Core perturbation optimization engine (L_inf PGD step)
├── edit.py                  # Generative model attack simulator (Stable Diffusion diffusion loop)
├── requirements.txt         # Package dependency tree
└── README.md                # System documentation
