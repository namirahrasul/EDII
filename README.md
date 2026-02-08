# EDII: Efficient Diffusion-based Image Inpainting

Namirah Rasul, Iftikher Jaman Ifti, Yousuf Fuad al-Kasheb, Dr. Hasanul Kabir, Mohammad Bakhtiar Hasan

This repository contains the code and pretrained models for **Efficient Diffusion-based Image Inpainting (EDII)**, our method that accelerates diffusion-based image inpainting while maintaining high-quality reconstruction. EDII builds upon the **Minutes-to-Seconds (M2S)** framework by integrating **single-step DPM-Solver++ sampling** and **encoder feature reuse** to achieve roughly a 2× speedup over M2S without retraining.

---

## Abstract

Diffusion-based image inpainting produces high-quality results but suffers from slow inference due to iterative denoising. EDII addresses this by combining a **coarse-to-fine sampling (CFS) strategy** with two complementary optimizations: single-step DPM-Solver++ for faster sampling, and encoder feature reuse to eliminate redundant computations. Our approach achieves substantial inference speedup while maintaining competitive perceptual quality on **CelebA-HQ** and **ImageNet** benchmarks.

---

## Features

- Faster inference (~2× speedup over M2S)  
- High-fidelity inpainting on ImageNet and CelebA-HQ  
- No retraining required for pretrained diffusion models  
- Supports multiple resolutions: 64×64 and 256×256  

---

## Requirements

- Linux  
- NVIDIA GPU with CUDA  
- Python 3.9  
- Conda / Miniconda  
- OpenMPI (for `mpi4py`)  

---

## Installation

1. Clone the repository
2. Create and activate Conda environment(Python 3.9)
3. Install dependencies:
```
conda install mpi4py openmpi
python setup.py
```

## Data Preparation

We perform experiments on the following datasets:

- [**ImageNet**](https://www.image-net.org/download.php)
- [**CelebA-HQ**](https://www.kaggle.com/datasets/badasstechie/celebahq-resized-256x256)

### Masks

We use subset of the mask test sets from [RePaint](https://github.com/andreas128/RePaint), which include 6 types: Wide, Narrow, Half, Expand, Alternating Lines, and Super-Resolve 2× You can download these mask datasets from the Google Drive link they provided [Download Link](https://drive.google.com/uc?id=1Q_dxuyI41AAmSv9ti3780BwaJQqwvwMv).

Pretrained models and checkpoints are required for inference. Place them in the following directory structure:

```
ddpm_ckpt/
├── imagenet/
│   ├── 64x64.ckpt
│   └── 256x256.ckpt
└── celeba/
    ├── 64x64.ckpt
    └── 256x256.ckpt
```

---

### Pretrained Models

- **AlexNet**: downloaded via `alexnet_download.py`  
- **DDPM Checkpoints**:  

**ImageNet:**
- 64×64: [Download Link](https://drive.google.com/file/d/1OsL6UrYFUtmwBLcOdRViRcfTSdoIySjR)  
- 256×256: [Download Link](https://drive.google.com/file/d/1fX0mcIWPAz7fd7tIWcVxFuPf65bqCjj3)  

**CelebA-HQ:**
- 64×64: [Download Link](https://drive.google.com/file/d/1GWdEYCqcGd55Gqkli80Z_O_t9cKuJWWP)  
- 256×256: [Download Link](https://drive.google.com/file/d/16Hz_Fis2PPmq2RrFy9Kj9WkZoXdsc3K0)  

---

## Usage

### Inpainting Experiments

Run the inpainting pipeline:

```
./inpaint.sh
```

All outputs (images, logs, intermediate results) are written to the `experiments/` folder.

---

## Results

Illustrative examples of EDII inpainting:

- EDII achieves **roughly 2× faster inference** than M2S while maintaining competitive **LPIPS, SSIM, PSNR, and L1** metrics.  
- Supports a range of mask types for both ImageNet and CelebA-HQ datasets.  

See figures in `experiments/` for sample outputs.

---

## Acknowledgment

This work builds upon:  
- [M2S: Minutes to Seconds](https://github.com/linghuyuhangyuan/M2S)  
- [RePaint](https://github.com/andreas128/RePaint)  
- [P2-weighting / LWDM](https://github.com/jychoi118/P2-weighting)  
- [guided-diffusion](https://github.com/openai/guided-diffusion)  

---

## Contact

For questions or suggestions, contact: **n.rsl.136@gmail.com**

    

