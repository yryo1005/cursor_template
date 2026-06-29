# cursor_template

## プロジェクトを作る際
```text
git init
git submodule add https://github.com/yryo1005/cursor_template.git
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
sudo apt install -y git build-essential curl wget unzip libgl1-mesa-glx libglib2.0-0 htop tmux

# UV
sudo apt install -y python3-dev
curl -LsSf https://astral.sh/uv/install.sh | sh
source $HOME/.local/bin/env

# TeX (インストール中に止まった場合，Enterキーを連打する)
sudo apt install -y texlive-full texlive-lang-japanese texlive-fonts-recommended texlive-fonts-extra texlive-latex-extra    
sudo kanji-config-updmap-sys haranoaji
```
