# Installation

Most of the requirements of this project are exactly the same as [maskrcnn-benchmark](https://github.com/facebookresearch/maskrcnn-benchmark). If you have any environment problems, check their [issues page](https://github.com/facebookresearch/maskrcnn-benchmark/issues) first.

## Requirements

- Linux (tested on Ubuntu 22.04)
- Python 3.12.12
- PyTorch 2.7.0+cu128
- CUDA 12.8 (V12.8.93)
- NVIDIA GPU with ≥ 24 GB memory (tested on RTX 5090)

## Step-by-step Installation

```bash
# 1. Create conda environment
conda create --name tpdnet python=3.12 -y
conda activate tpdnet

# 2. Install PyTorch 2.7.0 with CUDA 12.8
pip install torch==2.7.0 torchvision==0.22.0 torchaudio==2.7.0 --index-url https://download.pytorch.org/whl/cu128

# 3. Install all dependencies (including pycocotools)
pip install -r requirements.txt

# 4. Build TPD-Net
python setup.py build develop
```

## Compatibility with Older PyTorch

This codebase is also compatible with PyTorch 1.6–2.x. For older setups, follow [IETrans INSTALL.md](https://github.com/waxnkw/IETrans-SGG.pytorch/blob/master/INSTALL.md).
