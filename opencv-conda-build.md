#### Build OpenCV with CUDA enabled and install in Conda env.
#### ToDo: Fix dependencies: 
https://developer.nvidia.com/nvidia-video-codec-sdk/download

Manual: https://www.youtube.com/watch?v=Mww1-1NufIo&t=407s 

#### 1. Edit builder script:
- Detect and specify correct ```CUDA_ARCH_BIN```. 8.7 for Jetson Orin NX 16GB
```shell
nvidia-smi --query-gpu=compute_cap --format=csv
```

#### 2. Specify conda env and edit some build parameters in ```opencv-conda-build.sh```:
```shell
export CUDA_ARCH_BIN=8.7
conda env create cv2 python==3.10
conda activate cv2
export CONDA_ENV_PATH=/home/`whoami`/anaconda3/envs/cv2
```

#### 3. Run cmake build install in Screen:
```shell
sudo apt install screen
screen
./opencv-conda-build.sh 4.10.0
# a+d to detach
# screen -ls to find your screen
# screen -dr <screen_num> to attache to running screen
```
