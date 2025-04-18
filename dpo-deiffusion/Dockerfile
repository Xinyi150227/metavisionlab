#tag:latest
FROM nvidia/cuda:11.7.1-cudnn8-runtime-ubuntu20.04

# 更新系统库，安装常用工具
RUN apt-get update && apt-get install -y \
    libgl1-mesa-glx libpci-dev curl nano psmisc zip git && \
    apt-get --fix-broken install -y

# 安装 Conda 依赖
RUN conda install -n dpo-diff -y \
    pytorch==2.0.0 \
    torchvision==0.15.0 \
    torchaudio==2.0.0 \
    pytorch-cuda=11.7 \
    -c pytorch \
    -c nvidia

# 安装 pip 依赖
RUN /opt/conda/envs/dpo-diff/bin/pip install \
    diffusers==0.24.0 \
    accelerate==0.24.1 \
    transformers==4.35.2 \
    matplotlib==3.7.3 \
    openai==1.3.0 \
    nltk==3.8.1 \
    gpustat==1.1.1 \
    sentence-transformers \
    --no-cache-dir

RUN conda install -n dpo-diff -y \
    cudatoolkit=11.7 \
    numpy==1.22.4 \
    pandas==1.5.3 \
    pillow==9.5.0 \
    tqdm==4.65.0
RUN /opt/conda/bin/conda init bash
