# Setup

### GPU Driver
Use ubuntu-driver proprietary driver
Software & Updates -> Additional Drivers

This time I am using nvidia-driver-535
```
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 535.146.02             Driver Version: 535.146.02   CUDA Version: 12.2     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce GTX 1080 Ti     Off | 00000000:1D:00.0  On |                  N/A |
| 11%   52C    P8              21W / 280W |    538MiB / 11264MiB |     19%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
```

### Necessities
```
sudo apt-get install git vim htop ibus-chewing
```

### Git
```
git config --global user.name "zxcvbnmditto"
git config --global user.email "chuhungclife@gmail.com"
ssh-keygen -t ed25519 -C "chuhungclife@gmail.com"
```

### Miniconda
[Reference](https://docs.conda.io/projects/miniconda/en/latest/)
```
mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm -rf ~/miniconda3/miniconda.sh~/miniconda3/bin/conda init bash
~/miniconda3/bin/conda init bash
```

### Verify Pytorch using GPU
Now torch ships with cuda & cudnn binaries. No need to undergo the process of installing those from source

```
conda create --name torch-gpu-verify python=3.10
conda activate torch-gpu-verify
pip install numpy torch
```

```
import torch

# This should be true
torch.cuda.is_available()

# This should not be zero
torch.cuda.device_count()
```

### Docker
[Reference](https://docs.docker.com/desktop/install/ubuntu/)
[Docker Desktop deb](https://desktop.docker.com/linux/main/amd64/docker-desktop-4.26.1-amd64.deb?utm_source=docker&utm_medium=webreferral&utm_campaign=docs-driven-download-linux-amd64)
```
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

Docker Hub gpg key
This allows Docker Desktop to access the remote Docker Repository
```
gpg --generate-key
pass init <your_generated_gpg-id_public_key>
```