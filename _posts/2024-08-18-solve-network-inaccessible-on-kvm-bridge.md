---
layout: post
title:  "KVM 添加 bridge 后 guest 只能和 host 互访的解决办法"
date:   2024-08-17 00:25:29 +0800
categories: 折腾 KVM
---

## 修改 iptables

默认的 FORWARD policy 是 DROP，需要修改接受 from/to br0 的 packet

```bash
iptables -I FORWARD -i br0 -j ACCEPT
iptables -I FORWARD -o br0 -j ACCEPT
```
