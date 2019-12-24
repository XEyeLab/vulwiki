# ARP欺骗嗅探漏洞

### 漏洞描述

由于内网服务器没有进行mac于ip地址绑定，可进行arp嗅探，获取内网流量，从中得到一些管理密码。

### 漏洞危害

- 网站服务器未隔离，攻击者可截获所有网络数据包进行数据分析获取管理员密码。

### 修复方案

- 进行ARP绑定防止ARP欺骗被嗅探攻击。