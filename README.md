# ode-flow
This is term project for AI618 course Generative models and unsupervised learning. 

We strongly recommend to run this code in the docker environment we provide. The instruction for this is as following:

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
docker pull kim4375731/agen_ai618:8
```
- Run a container
    - Designate your own path to connect your host environment's path with the container's path: [host-path]:[container-path]
    ex. /home/yongjae/sharehouse:/root/sharehouse
    - Designate your container name: [container-name]
    ex. agen_ai618_8
```
docker run -it --privileged -v [host-path]:[container-path] -v /etc/localtime:/etc/localtime:ro -v /dev/input:/dev/input:ro --gpus all --net=host --env="DISPLAY" --env="QT_X11_NO_MITSHM=1" --env XAUTHORITY=$XAUTH --env=NVIDIA_DRIVER_CAPABILITIES=compute,graphics,utility --shm-size=8G --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" --name [container_name] kim4375731/agen_ai618:8
```
An example command:
```
docker run -it --privileged -v /home/yongjae/sharehouse:/root/sharehouse -v /etc/localtime:/etc/localtime:ro -v /dev/input:/dev/input:ro --gpus all --net=host --env="DISPLAY" --env="QT_X11_NO_MITSHM=1" --env XAUTHORITY=$XAUTH --env=NVIDIA_DRIVER_CAPABILITIES=compute,graphics,utility --shm-size=8G --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" --name agen_ai618_8 kim4375731/agen_ai618:8
```
With the command above, you will start a container with the name of 'agen_ai618_8' of the docker image 'kim4375731/agen_ai618:8'

- To stop the container, at host CLI:
```
docker stop [container-name]
```
- To confirm the list of running containers:
```
docker ps
```
- To confirm the full list of containers including stopped ones:
```
docker ps -a
```
- To start a stopped container: 
```
docker start -i [container-name]
```
- To open a new CLI session of a container while running the container:
```
docker exec -it [container-name] bash
```

## Train
## Evaluate
## Plot the results with pre-computed results in npz files by the authors
