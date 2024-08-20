---
layout: post
title:  "Windows 映射 SMB 驱动器的常规配置"
date:   2021-10-11 22:22:39 +0800
categories: 折腾 SMB
---

基本的配置方法不用再赘述，这里记录一下可能遇到的几个问题。

## 不能在管理员权限的应用中找到映射的驱动器或者无法执行需要管理员权限的程序

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` 下创建一个名为
`EnableLinkedConnections` 的 `DWORD` = 1 即可。

## 打开文件时出现安全提示

`Internet 选项` -> `本地 Intranet` -> `站点` 中加入驱动器地址就可以了，例如 `file:///C:`。
