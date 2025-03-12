#tag:latest
FROM pytorch/pytorch:2.6.0-cuda12.4-cudnn9-runtime

# 更新系统库，安装常用工具
RUN apt-get update && apt-get install -y \
    libgl1-mesa-glx libpci-dev curl nano psmisc zip git && \
    apt-get --fix-broken install -y

# 安装 Conda 依赖
RUN conda install -y \
    cairo=1.18.2 \
    certifi=2024.8.30 \
    contourpy=1.1.1 \
    cycler=0.12.1 \
    einops=0.8.0 \
    fontconfig=2.15.0 \
    fonttools=4.53.1 \
    freetype=2.12.1 \
    greenlet=3.0.3 \
    icu=75.1 \
    joblib=1.4.2 \
    kiwisolver=1.4.5 \
    lcms2=2.17 \
    libboost=1.84.0 \
    libboost-python=1.84.0 \
    libdeflate=1.23 \
    libffi=3.4.6 \
    libiconv=1.18 \
    libjpeg-turbo=3.0.0 \
    liblapack=3.9.0 \
    libpng=1.6.47 \
    libsqlite=3.49.1 \
    libtiff=4.7.0 \
    matplotlib-base=3.7.3 \
    openjpeg=2.5.3 \
    openssl=3.4.1 \
    packaging=24.2 \
    pillow=10.4.0 \
    pycairo=1.26.1 \
    pyparsing=3.1.4 \
    python=3.8.20 \
    python-dateutil=2.9.0 \
    pytz=2024.2 \
    reportlab=4.2.2 \
    scikit-learn=1.3.2 \
    scipy=1.7.1 \
    sqlalchemy=2.0.32 \
    threadpoolctl=3.5.0 \
    tk=8.6.13 \
    typing-extensions=4.12.2 \
    wheel=0.45.1 \
    xz=5.6.4 && \
    conda clean -afy

# 安装 pip 依赖
RUN pip install pip==24.0 && python -m pip install --upgrade setuptools && \
    pip install \
    opencv-python \
    tb-nightly \
    matplotlib \
    logger_tt \
    tabulate \
    tqdm \
    wheel \
    mccabe \
    scipy \
    openpyxl \
    antlr4-python3-runtime==4.8 \
    bitarray==3.1.0 \
    cffi==1.17.1 \
    charset-normalizer==3.4.1 \
    colorama==0.4.6 \
    cython==3.0.12 \
    deprecated==1.2.18 \
    fairseq==0.12.2 \
    filelock==3.16.1 \
    fsspec==2025.2.0 \
    hydra-core==1.0.7 \
    idna==3.10 \
    importlib-metadata==8.5.0 \
    jinja2==3.1.5 \
    llvmlite==0.40.1 \
    lxml==4.9.4 \
    markupsafe==2.1.5 \
    matchms==0.26.4 \
    mpmath==1.3.0 \
    networkx==3.1 \
    numba==0.57.1 \
    numpy==1.22.4 \
    omegaconf==2.0.5 \
    pickydict==0.4.0 \
    portalocker==3.0.0 \
    pubchempy==1.0.4 \
    pycparser==2.22 \
    pyteomics==4.7.5 \
    pyyaml==6.0.2 \
    rdkit==2023.9.4 \
    regex==2024.11.6 \
    requests==2.32.3 \
    sacrebleu==2.5.1 \
    sparsestack==0.4.1 \
    sympy==1.13.3 \
    urllib3==2.2.3 \
    wrapt==1.17.2 \
    zipp==3.20.2
RUN /opt/conda/bin/conda init bash
