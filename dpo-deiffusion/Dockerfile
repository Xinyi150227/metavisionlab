#tag:latest
# 使用 CUDA 11.7 官方基础镜像
FROM nvidia/cuda:11.7.1-cudnn8-runtime-ubuntu20.04

# 设置清华源加速
ENV PIP_INDEX_URL=https://pypi.tuna.tsinghua.edu.cn/simple
RUN sed -i 's/archive.ubuntu.com/mirrors.tuna.tsinghua.edu.cn/g' /etc/apt/sources.list

# 安装基础系统依赖
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y \
    wget \
    git \
    libgl1-mesa-glx \
    libglib2.0-0 \
    python3.8-dev \
    python3-distutils && \
    rm -rf /var/lib/apt/lists/*

# 安装 Miniconda（关键修复步骤）
RUN wget https://repo.anaconda.com/miniconda/Miniconda3-py38_4.12.0-Linux-x86_64.sh -O miniconda.sh && \
    bash miniconda.sh -b -p /opt/conda && \
    rm miniconda.sh

# 配置 conda 环境
ENV PATH=/opt/conda/bin:$PATH
RUN conda init bash && \
    conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/ && \
    conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/

# 创建专用环境（修复conda环境路径）
RUN conda create -n dpo-diff python=3.8 -y

# 安装 PyTorch 2.0.0 (CUDA 11.7)
RUN conda install -n dpo-diff -y \
    pytorch==2.0.0 \
    torchvision==0.15.0 \
    torchaudio==2.0.0 \
    pytorch-cuda=11.7 \
    -c pytorch \
    -c nvidia

# 安装核心 pip 依赖（使用绝对路径）
RUN /opt/conda/envs/dpo-diff/bin/pip install \
    diffusers==0.24.0 \
    accelerate==0.24.1 \
    transformers==4.35.2 \
    matplotlib==3.7.3 \
    openai==1.3.0 \
    nltk==3.8.1 \
    gpustat==1.1.1 \
    sentence-transformers

# 安装必要运行时库
RUN conda install -n dpo-diff -y \
    cudatoolkit=11.7 \
    numpy==1.22.4 \
    pandas==1.5.3 \
    pillow==9.5.0 \
    tqdm==4.65.0

# 清理缓存
RUN conda clean -afy

# 设置默认工作环境
WORKDIR /workspace
ENV PYTHONPATH=/workspace
SHELL ["/bin/bash", "-c"]
CMD ["/bin/bash"]
