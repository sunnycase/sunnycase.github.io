---
layout: post
title:  "修复 ASUS UPNP 无法启动的问题"
date:   2024-08-17 00:00:19 +0800
categories: 折腾 ASUS UPNP
---

## 问题

更新 merlin 固件后 upnp 无法使用，具体表现为找不到 IGD

```bash
upnpc -l
upnpc : miniupnpc library test client, version 2.2.3.
 (c) 2005-2021 Thomas Bernard.
Go to http://miniupnp.free.fr/ or https://miniupnp.tuxfamily.org/
for more information.
List of UPNP devices found on the network :
 desc: http://192.168.2.30:40000/device.xml
 st: upnp:rootdevice

UPnP device found. Is it an IGD ? : http://192.168.2.30:40000/
No valid UPNP Internet Gateway Device found.
```

## 原因

miniupnpd 获取到的外网地址如果是 private address 会认为无效并退出

## 解决办法

`ext_ip` 的值其实并不影响 UPNP 功能，创建  `/jffs/scripts/upnp.postconf`

```bash
#!/bin/sh
CONFIG=$1
echo "ext_ip=1.1.1.1" >> $CONFIG
```

重启即可。
