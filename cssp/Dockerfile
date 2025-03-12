#tag:latest
FROM pytorch/pytorch:2.6.0-cuda12.4-cudnn9-runtime

RUN apt-get update && apt-get install -y libgl1-mesa-glx libpci-dev curl nano psmisc zip git && apt-get --fix-broken install -y

RUN conda install -y scikit-learn pandas flake8 yapf isort yacs future libgcc

RUN pip install pip==24.0 && python -m pip install --upgrade setuptools && \
    pip install opencv-python tb-nightly matplotlib logger_tt tabulate tqdm wheel mccabe scipy openpyxl
