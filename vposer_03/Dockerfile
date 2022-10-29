FROM chacorp/vposer:0.2
# ARG DEBIAN_FRONTEND=noninteractive
# # docker build -t chacorp/vposer:0.3 ./docker
# # docker run -it --rm chacorp/vposer:0.3 /bin/bash
##################################################################
# NVDIFFRAST
RUN apt-get update
RUN apt-get install -y \
    libblkid-dev \
    e2fslibs-dev \
    libaudit-dev \
    libhdf5-dev \
    libboost-all-dev

# ### Build OpenPose
# RUN git clone https://github.com/CMU-Perceptual-Computing-Lab/openpose.git
# RUN cd openpose && git submodule update --init --recursive --remote

# ### Our patch for OpenPose
# RUN git apply /source/RVH_Mesh_Registration/assets/openpose.patch
# ### this often falls into error 
# ### -> do it manually by copy-and-paste to openpose
# ### -> you need to open (assets/openpose.patch) file to do so.

ADD openpose /tmp/openpose
RUN export PATH=/usr/local/cuda-11.4/bin:$PATH
RUN export LD_LIBRARY_PATH=/usr/local/cuda-11.4/lib64:$LD_LIBRARY_PATH
RUN cd /tmp/openpose && cmake -DBUILD_PYTHON=ON -DUSE_CUDNN=OFF && make -j 16
RUN cd /tmp/openpose/python/openpose && make install
RUN cp /usr/local/python/openpose/pyopenpose.cpython-38-x86_64-linux-gnu.so /opt/conda/lib/python3.8/
RUN ln -s /opt/conda/lib/python3.8/pyopenpose.cpython-38-x86_64-linux-gnu.so /opt/conda/lib/python3.8/pyopenpose
