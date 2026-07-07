# cursor_template

## プロジェクトを作る際
```text
git init

git submodule add https://github.com/yryo1005/cursor_template.git

mkdir orders
mkdir reports
```

## WSL環境を作るためのコマンド
```text
wsl --install -d Ubuntu-22.04

### 以下の内容を書き込み
username: user
passward: 20210401
###

sudo rm /etc/resolv.conf
sudo rm /etc/wsl.conf
mkdir /home/user/workspace

sudo nano /etc/wsl.conf
### 以下の内容を書き込み
[boot]
systemd=true
[network]
generateResolvConf=false
[interop]
enabled = true
appendWindowsPath = true
[automount]
enabled = true
mountFsTab = true
[user]
default = user
###

sudo nano /etc/resolv.conf
### 以下の内容を書き込み
nameserver 8.8.8.8
nameserver 8.8.4.4
###

wsl --shutdown

###
wsl --export Ubuntu-22.04 C:\Ubuntu-22.04.tar
mkdir C:\Ubumntu2204_Cursor_Plane
wsl --import Ubumntu2204_Cursor_Plane C:\Ubumntu2204_Cursor_Plane C:\Ubuntu-22.04.tar
wsl -d Ubumntu2204_Cursor_Plane

###
cd /home/user/
sudo apt update
sudo apt upgrade -y

# CUDA，CuDNN
wget https://developer.download.nvidia.com/compute/cuda/repos/wsl-ubuntu/x86_64/cuda-wsl-ubuntu.pin
sudo mv cuda-wsl-ubuntu.pin /etc/apt/preferences.d/cuda-repository-pin-600
wget https://developer.download.nvidia.com/compute/cuda/13.0.0/local_installers/cuda-repo-wsl-ubuntu-13-0-local_13.0.0-1_amd64.deb
sudo dpkg -i cuda-repo-wsl-ubuntu-13-0-local_13.0.0-1_amd64.deb
sudo cp /var/cuda-repo-wsl-ubuntu-13-0-local/cuda-*-keyring.gpg /usr/share/keyrings/
sudo apt-get update
sudo apt-get -y install cuda-toolkit-13-0
echo 'export PATH=/usr/local/cuda/bin:$PATH' >> ~/.bashrc
echo 'export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH' >> ~/.bashrc
echo 'export CUDA_HOME=/usr/local/cuda' >> ~/.bashrc
source ~/.bashrc
nvcc --version

wget https://developer.download.nvidia.com/compute/cudnn/9.23.2/local_installers/cudnn-local-repo-ubuntu2204-9.23.2_1.0-1_amd64.deb
sudo dpkg -i cudnn-local-repo-ubuntu2204-9.23.2_1.0-1_amd64.deb
sudo cp /var/cudnn-local-repo-ubuntu2204-9.23.2/cudnn-*-keyring.gpg /usr/share/keyrings/
sudo apt-get update
sudo apt-get -y install cudnn-cuda-13
CUDNN_SO=$(basename $(ls /usr/lib/x86_64-linux-gnu/libcudnn.so.9.*.* | head -n 1))
sudo ln -sf /usr/lib/x86_64-linux-gnu/${CUDNN_SO} /usr/local/cuda/lib64/libcudnn.so
sudo ln -sf /usr/lib/x86_64-linux-gnu/${CUDNN_SO} /usr/local/cuda/lib64/libcudnn.so.9
sudo ldconfig
sudo dpkg -l | grep cudnn

sudo apt install -y git build-essential curl wget unzip libgl1-mesa-glx libglib2.0-0 htop tmux

# UV
sudo apt install -y python3-dev
curl -LsSf https://astral.sh/uv/install.sh | sh
source $HOME/.local/bin/env

# TeX (インストール中に止まった場合，Enterキーを連打する)
sudo apt install -y texlive-full texlive-lang-japanese texlive-fonts-recommended texlive-fonts-extra texlive-latex-extra    
sudo kanji-config-updmap-sys haranoaji

sudo apt update
sudo apt upgrade -y

###

wsl --shutdown

###
wsl --export Ubumntu2204_Cursor_Plane C:\Ubumntu2204_Cursor_Plane.tar
```
