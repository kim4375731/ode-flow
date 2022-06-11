# ode-flow
This is term project for AI618 course Generative models and unsupervised learning. 

We strongly recommend to run this code in a docker environment we provide. The instruction for this is as following:

## Instruction to setup a docker environment
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

docker sudo USER

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
