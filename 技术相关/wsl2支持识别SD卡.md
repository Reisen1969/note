---
title: wsl2设置sd卡
date: 2023-10-02 16:09:20
tags: wsl2
toc: true
---




[微软参考](https://learn.microsoft.com/zh-cn/windows/wsl/connect-usb0)


## 重新编译wsl内核
原版的wsl不带sd卡的驱动, 需要重新编译内核

仓库 https://github.com/microsoft/WSL2-Linux-Kernel.git

```
sudo apt install build-essential flex bison libssl-dev libelf-dev dwarves
make menuconfig KCONFIG_CONFIG=Microsoft/config-wsl
```

打开 Device Driver->USB support  Support for Host-side USB 和 USB Mass Storage support

```
make -j$(nproc) bzImage KCONFIG_CONFIG=Microsoft/config-wsl
```

编译出的文件是 arch/x86/boot/bzImage

然后更改 wsl2的配置文件 `.wslconfig`

加入以下
```
[wsl2]
kernel=C:\\kernel\\bzImage_sd
```



## windows
安装 USBIPD-WIN

https://github.com/dorssel/usbipd-win

## wsl

```
sudo apt install linux-tools-generic hwdata
sudo update-alternatives --install /usr/local/bin/usbip usbip /usr/lib/linux-tools/*-generic/usbip 20
```

## 使用方法

在windows下执行 
```
usbipd wsl list


BUSID  VID:PID    DEVICE                                                        STATE
1-9    8087:0029  英特尔(R) 无线 Bluetooth(R)                                   Not attached
1-10   0b05:19af  AURA LED Controller, USB 输入设备                             Not attached
1-11   14cd:1212  USB 大容量存储设备                                            Not attached
4-2    046a:c122  USB 输入设备                                                  Not attached
4-3    18f8:1286  USB 输入设备                                                  Not attached
```

找到sd卡的编号

然后执行

```
usbipd wsl attach --busid 1-11
```

然后就能在wsl2 里看到 sd卡了


