# ode-flow
This is term project for AI618 course Generative models and unsupervised learning. 

We strongly recommend to run this code in a docker environment we provide. The instruction for this is as following:

## Instruction to setup a docker environment
- Prerequisites
    - Linux kernel >= 3.10 (GNU/Linux x86_64)
    - Nvidia driver >= 418.81.07
    - Docker >= 19.03
    - Nvidia GPU Architecture >= Kepler
- Repository setups
```
sudo apt-get update
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release

```
- Add Docker’s official GPG key
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```
- Set the stable repository
```
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
- Install Docker Engine
```
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```
- Add docker group (to use docker command without sudo)
```
# Create the docker group.
sudo groupadd docker

# Add your user to the docker group.
sudo usermod -aG docker $USER
sudo usermod -aG docker {other user}

# reboot or type below for activate new group
newgrp docker
```
- Docker test 
```
docker run hello-world
```
- Setup Nvidia Container Toolkit 
```
distribution=$(. /etc/os-release;echo $ID$VERSION_ID) \
   && curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add - \
   && curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
```
- Install nvidia-docker
```
sudo apt-get update
sudo apt-get install -y nvidia-docker2
```
- Restart docker daemon
```
sudo systemctl restart docker
```
- CUDA container test
```
sudo docker run --rm --gpus all nvidia/cuda:11.0-base nvidia-smi

# Results should be like this:
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 470.86       Driver Version: 470.86       CUDA Version: 11.4     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA RTX A6000    Off  | 00000000:0B:00.0 Off |                  Off |
| 30%   40C    P8    24W / 300W |     17MiB / 48685MiB |      0%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
|   1  NVIDIA RTX A6000    Off  | 00000000:0C:00.0 Off |                  Off |
| 30%   36C    P8    20W / 300W |      5MiB / 48685MiB |      0%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
+-----------------------------------------------------------------------------+
```


## Pull and run the latest docker image of AI618_Group7 project (ode-flow)
- Pull the image
```
docker pull []
```
- Run a container
```
docker run []
```
## Train
## Evaluate
## Plot the results with pre-computed results in npz files by the authors
