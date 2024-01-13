# Setup

Necessities
```
sudo apt-get install git vim htop
```

Git
```
git config --global user.name "zxcvbnmditto"
git config --global user.email "chuhungclife@gmail.com"
ssh-keygen -t ed25519 -C "chuhungclife@gmail.com"
```

Miniconda

```
mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm -rf ~/miniconda3/miniconda.sh~/miniconda3/bin/conda init bash
~/miniconda3/bin/conda init bash
```
