FROM nvcr.io/nvidia/pytorch:22.01-py3
LABEL maintainer="Melanie Segado <melanie.segado@gmail.com>"

ARG DEBIAN_FRONTEND=noninteractive
ENV NVIDIA_VISIBLE_DEVICES all \
    NVIDIA_DRIVER_CAPABILITIES compute, utility

WORKDIR /app
#COPY environment.yaml .

# Update package list and install essential packages
RUN apt-get update && apt-get install -y \
    wget bzip2 \
    git \
    curl \
    libgl1 \
    screen 
    


# Download and install Miniconda3
RUN wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O miniconda.sh && \
    bash miniconda.sh -b -p /opt/miniconda && \
    rm miniconda.sh

# Add Miniconda3 to the system PATH
ENV PATH="/opt/miniconda/bin:${PATH}"


RUN conda create -n torch_render python==3.8 -y && \
    echo ". activate torch_render" >> ~/.bashrc

RUN . activate torch_render && pip install -U torch matplotlib numpy pandas scipy && \
conda install ipykernel

    
CMD ["/bin/bash"]


