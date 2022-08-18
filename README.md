# 使用clash玩赛马娘

---

参考链接

[赛马娘clash分流规则](https://nga.178.com/read.php?tid=26630825&page=1)

---

## 声明

本人萌新 写下此md仅做记录

若你通过此篇解决了问题，那就太好了

---

## 过程



* 1、setting->mixin->YAML->edit 

```
mixin:
  dns:
    enable: true
    enhanced-mode: fake-ip
    nameserver:
      - 223.5.5.5
      - 1.1.1.1
      - 8.8.8.8
      - 114.114.114.114
      - https://doh.dns.sb/dns-query
      - https://dns.adguard.com/dns-query
      - https://cdn-doh.ssnm.xyz/dns-query
      - 119.29.29.29
  tun:
    enable: true
    stack: gvisor
    dns-hijack:
      - 198.18.0.2:53
    auto-route: true
    auto-detect-interface: true
```



* 2、setting->profiles->parsers->edit    <font color="#dd0000">url与proxies需修改为自己的</font> 

```
parsers:
  - url: "你订阅的"
    yaml:
      prepend-rules:
        - DOMAIN,prd-storage-umamusume.akamaized.net,赛马
        - DOMAIN,prd-storage-app-umamusume.akamaized.net,赛马
        - DOMAIN,prd-storage-game-umamusume.akamaized.net,赛马
        - DOMAIN-SUFFIX,cygames.jp,赛马
        - DOMAIN-KEYWORD,umamusume,赛马
        - DOMAIN-SUFFIX,dmm-extension.com,DMM
        - DOMAIN-SUFFIX,dmm.com,DMM
        - DOMAIN-SUFFIX,dmm.co.jp,DMM
        - DOMAIN-SUFFIX,dmmgames.com,DMM
        - DOMAIN-SUFFIX,dmm.hk,DMM
      prepend-proxy-groups:
        - name: 赛马
          type: select
          proxies:
            - 你的节点1
            - 你的节点2
            - 你的节点3
```



* 3、general->Service Mode->manage  **安装之后小地球会变绿**

* 4、只需要打开**TUN Mode**就行了，Mixin和system proxy都保持关闭状态



进不去dmm先挂日本节点，进不去游戏(一直说通信error)换成其他节点，比如我的西班牙节点是可以的(但是很慢)
进入游戏之后再切换到日本节点或者一个效果比较好的节点

本人clash萌新，以上操作存在错误的话欢迎大家指正，为后面的萌新开开路

---

### 汉化安利

哔哩哔哩指路：[【赛马娘】DMM版赛马娘本地化插件（部分汉化、解锁帧数）](https://www.bilibili.com/video/BV1vT4y1m7pE?spm_id_from=333.880.my_history.page.click)

github仓库：**[ Trainers-Legend-G](https://github.com/MinamiChiwa/Trainers-Legend-G)**
