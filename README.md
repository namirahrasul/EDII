# EDII: Efficient Diffusion based Image Inpainting

This repository contains code for the paper **Efficient diffusion based Image Inpainting**install mpi4py openmpi
python setup.py
--- using **ImageNet** and **CelebA-HQ** datasets.

## Requirements

- Linux
- NVIDIA GPU with CUDA
- Python 3.9
- Conda / Miniconda
- OpenMPI (for `mpi4py`)

---

## Setup

Create a Conda environment and build the package:

conda create -n p2wd python=3.9
conda activate p2wd
conda install mpi4py openmpi
python setup.py


## Pretrained Models

**AlexNet**

AlexNet weights are obtained via the provided script:
    alexnet_download.py

**DDPM Checkpoints (1M training steps)**

ImageNet:
- 64×64: https://drive.google.com/file/d/1OsL6UrYFUtmwBLcOdRViRcfTSdoIySjR
- 256×256: https://drive.google.com/file/d/1fX0mcIWPAz7fd7tIWcVxFuPf65bqCjj3

CelebA-HQ:
- 64×64: https://drive.google.com/file/d/1GWdEYCqcGd55Gqkli80Z_O_t9cKuJWWP
- 256×256: https://drive.google.com/file/d/16Hz_Fis2PPmq2RrFy9Kj9WkZoXdsc3K0

Checkpoints should be placed under:
    ddpm_ckpt/{imagenet,celeba}/

---

## Experiments

Inpainting experiments are launched via:
    ./inpaint.sh

All outputs (images, logs, intermediate results) are written to:
    experiments/



## Reproducibility

- Random seeds are fixed in the experiment scripts.
- Hyperparameters and checkpoint paths are defined in inpaint.sh.
- GPU memory requirements scale with image resolution (64×64 vs. 256×256).

