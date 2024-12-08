---
title: "sdkman安装"
linkTitle: "安装"
weight: 20
date: 2024-07-18
description: >
  安装sdkman
---

参考官方文档： https://sdkman.io/install

## 安装

在UNIX上安装SDKMAN是轻而易举的事。它可以轻松地在macOS、Linux和Windows（使用WSL）上设置。此外，它还兼容Bash和 zsh。

安装方式：

```bash
curl -s "https://get.sdkman.io" | bash
```

### Linux安装

这是在 linux mint 22下安装的输出日志：

```bash
......
                                                                 Now attempting installation...


Looking for a previous installation of SDKMAN...
Looking for unzip...
Looking for zip...
Looking for tar...
Looking for curl...
Looking for sed...
Installing SDKMAN scripts...
Create distribution directories...
Getting available candidates...
Prime platform file...
Prime the config file...
Installing script cli archive...
* Downloading...
######################################################################## 100.0%
* Checking archive integrity...
* Extracting archive...
* Copying archive contents...
* Cleaning up...

Installing script cli archive...
* Downloading...
######################################################################## 100.0%
* Checking archive integrity...
* Extracting archive...
* Copying archive contents...
* Cleaning up...

Set version to 5.18.2 ...
Set native version to 0.4.6 ...
Attempt update of interactive bash profile on regular UNIX...
Added sdkman init snippet to /home/sky/.bashrc
Attempt update of zsh profile...
Updated existing /home/sky/.zshrc



All done!
```

打开一个新的终端或在同一个shell中运行以下命令：

```bash
source "$HOME/.sdkman/bin/sdkman-init.sh"
```

验证一下：

```bash
sdk version
```

输出为:

```bash
SDKMAN!
script: 5.18.2
native: 0.4.6
```

### windows 安装

#### WSL

在尝试安装SDKMAN之前，先安装Windows Subsystem for Linux（WSL）。一个基本的工具集（bash，zip，unzip，curl）是必要的。大多数时候，它是开箱即用的。

> 备注：我现在不太喜欢使用 wsl，先不用。

#### Git Bash

> 备注：稍后尝试。

