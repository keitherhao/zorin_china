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

## 更新

## 设置语言、输入法

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
sudo apt-get update && sudo apt-get install cloudflare-warp
```

### edge

```shell
# edge
sudo apt install -y software-properties-common apt-transport-https wget
wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/edge stable main"
sudo apt install -y microsoft-edge-stable
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
