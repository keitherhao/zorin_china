# zorin_china

如何使用zorin OS，并且配置

官网安装教程

<https://help.zorin.com/docs/getting-started/install-zorin-os/>

## 从官网下载iso镜像

<https://zorin.com/os/download/>

## 制作系统盘

### 下载烧录工具

<https://etcher.balena.io/>

### 烧录到U盘

## 从U盘启动

## 安装Zorin

## 选择apt镜像源 推荐USTC

<https://mirrors.ustc.edu.cn/help/ubuntu.html>

```shell
tmp="`cat /etc/apt/sources.list | grep \"https://mirrors.ustc.edu.cn/debian\"`"
echo $tmp
if [ -z "$tmp" ];then
 sudo apt install apt-transport-https -y
 sudo cp /etc/apt/sources.list /etc/apt/sources.list.bk
 sudo sed -i 's|http://deb.debian.org|https://mirrors.ustc.edu.cn|g' /etc/apt/sources.list
 sudo sed -i 's|http://security.debian.org/debian-security|http://mirrors.ustc.edu.cn/debian-security|g' /etc/apt/sources.list
 sudo apt-get update
 sudo apt-get upgrade -y
fi
```

## 更新

```shell
sudo apt update && sudo apt full-upgrade -y
```

## 设置语言、输入法

语言支持->添加或删除语言->选择中文添加

重启电脑（需要重启才能选择智能拼音）

设置->键盘->输入源->中文（智能拼音）（可以配置各种输入模式，我推荐小鹤双拼）

## 安装必要软件

```shell
# apt app
sudo apt install -y git curl wget cmake vim
```

### warp

```shell
# warp
# https://pkg.cloudflareclient.com/#ubuntu
# Add cloudflare gpg key
curl -fsSL https://pkg.cloudflareclient.com/pubkey.gpg | sudo gpg --yes --dearmor --output /usr/share/keyrings/cloudflare-warp-archive-keyring.gpg
# Add this repo to your apt repositories
# echo "deb [arch=amd64 signed-by=/usr/share/keyrings/cloudflare-warp-archive-keyring.gpg] https://pkg.cloudflareclient.com/ $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/cloudflare-client.list
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/cloudflare-warp-archive-keyring.gpg] https://pkg.cloudflareclient.com/ jammy main" | sudo tee /etc/apt/sources.list.d/cloudflare-client.list
# Install
sudo apt-get update && sudo apt-get install -y cloudflare-warp
```

### edge

```shell
# edge
sudo apt install -y software-properties-common apt-transport-https wget
wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/edge stable main"
sudo apt install -y microsoft-edge-stable
```

### appimagelauncher

```shell
cd ~/Downloads
wget https://github.com/TheAssassin/AppImageLauncher/releases/download/continuous/appimagelauncher_2.2.0-gha111.d9d4c73+bionic_amd64.deb
sudo dpkg -i appimagelauncher_2.2.0-gha111.d9d4c73+bionic_amd64.deb
```

### 阿里云盘

<https://github.com/tickstep/aliyunpan>

```shell
sudo curl -fsSL http://file.tickstep.com/apt/pgp | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/tickstep-packages-archive-keyring.gpg > /dev/null && echo "deb [signed-by=/etc/apt/trusted.gpg.d/tickstep-packages-archive-keyring.gpg arch=amd64,arm64] http://file.tickstep.com/apt aliyunpan main" | sudo tee /etc/apt/sources.list.d/tickstep-aliyunpan.list > /dev/null && sudo apt-get update && sudo apt-get install -y aliyunpan
```

### oh my bash

```shell
[ ! -d ~/.oh-my-bash ] && \
bash -c "$(curl -fsSL https://raw.githubusercontent.com/ohmybash/oh-my-bash/master/tools/install.sh)"
```

### wechat

<https://archive.ubuntukylin.com/software/pool/partner/weixin_2.1.1_amd64.deb>

### qq

<https://im.qq.com/linuxqq/index.shtml>
