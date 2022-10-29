FROM nvcr.io/nvidia/pytorch:21.08-py3
ARG DEBIAN_FRONTEND=noninteractive
# docker build -t chacorp/vposer:0.2 .
# docker run -it --rm chacorp/vposer:0.2 /bin/bash
##################################################################
# NVDIFFRAST
RUN apt-get update && apt-get install -y --no-install-recommends \
    pkg-config \
    libglvnd0 \
    libgl1 \
    libglx0 \
    libegl1 \
    libgles2 \
    libglvnd-dev \
    libgl1-mesa-dev \
    libegl1-mesa-dev \
    libgles2-mesa-dev \
    freeglut3-dev \
    cmake \
    curl
# GLEW
ENV LD_LIBRARY_PATH /usr/lib64:$LD_LIBRARY_PATH
ENV NVIDIA_VISIBLE_DEVICES all
ENV NVIDIA_DRIVER_CAPABILITIES compute,utility,graphics
ENV PYOPENGL_PLATFORM egl
RUN pip install --upgrade pip
# RUN pip install ninja imageio imageio-ffmpeg
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1
RUN pip install imageio imageio-ffmpeg==0.4.4 pyspng==0.1.0
# Install sshd
RUN apt-get install -y -q openssh-server
RUN apt-get install -y -q libsqlite3-dev
RUN update-alternatives --install /usr/bin/python python $(which python3) 1
RUN pip install jupyterlab
###################################################################
### PYTORCH 3D
# RUN pip uninstall opencv-python opencv-python-headless
RUN pip install opencv-python==4.5.3.56 opencv-python-headless==4.5.3.56
RUN pip install "git+https://github.com/facebookresearch/pytorch3d.git@stable"
### Vposer
RUN pip install trimesh pyrender smplx[all] chumpy omegaconf loguru dotmap 
RUN pip install transforms3d==0.3.1
RUN git clone https://github.com/nghorbani/human_body_prior.git
RUN mv human_body_prior /tmp/
COPY V02_05 /tmp/human_body_prior/support_data/dowloads/
RUN cd /tmp/human_body_prior && python setup.py develop
###################################################################
### setup for vessl path
RUN ln -s /opt/conda/bin/jupyter /usr/local/bin/jupyter
RUN update-alternatives --install /usr/bin/conda conda $(which conda) 1
RUN update-alternatives --install /usr/bin/pip pip $(which pip) 1
### Ninja
RUN wget https://github.com/ninja-build/ninja/releases/download/v1.8.2/ninja-linux.zip && unzip ninja-linux.zip -d /usr/local/bin/
RUN update-alternatives --install /usr/bin/ninja ninja /usr/local/bin/ninja 1 --force
### ETC
RUN apt-get install -y tmux htop
RUN pip install nvitop
RUN update-alternatives --install /usr/bin/nvitop nvitop /opt/conda/bin/nvitop 1
RUN update-alternatives --install /usr/bin/nvcc nvcc /usr/local/cuda/bin/nvcc 1
### juptyer notebook
RUN pip install ipywidgets
