# Installation and Environment Configuration Guide

# 1. Automated Quick-Start (Google Colab Runtime)
If you are running a verification sequence inside a Google Colab notebook environment, initialize your stack by copying and executing the setup block below:

# Clone the repository
git clone [https://github.com/taco-group/FaceLock.git](https://github.com/taco-group/FaceLock.git)
cd FaceLock

# Install explicit system dependencies
pip install numpy matplotlib pillow transformers==4.38.2 diffusers==0.27.2 huggingface-hub==0.23.0 peft==0.9.0 accelerate==0.27.2 insightface onnxruntime-gpu opencv-python lpips deepface scipy

# Local Environment

# 2. Python environment
conda create -n facelock python=3.10 -y
conda activate facelock

# Install PyTorch with CUDA support (Adjust toolkit matching your GPU architecture)
conda install pytorch torchvision pytorch-cuda=12.1 -c pytorch -c nvidia -y

# Clone repository and change directories
git clone [https://github.com/taco-group/FaceLock.git](https://github.com/taco-group/FaceLock.git)
cd FaceLock

# Install the requirement tree
pip install -r requirements.txt
