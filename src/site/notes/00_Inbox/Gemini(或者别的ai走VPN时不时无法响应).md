---
{"dg-publish":true,"permalink":"/00_Inbox/Gemini(或者别的ai走VPN时不时无法响应)/"}
---

# 在VPN的Rules修改配置
```c
dns:
  enable: true
  ipv6: false//不走ipv6
  listen: '127.0.0.1:5334'
  default-nameserver:
    - 223.5.5.5
    - 119.29.29.29
  proxy-server-nameserver:
    - 'https://223.5.5.5/dns-query'
    - 'https://doh.pub/dns-query'
  enhanced-mode: fake-ip
  fake-ip-range: 198.18.0.1/16
  use-hosts: false//不走用户主管ip
  use-system-hosts: false//同理
  fake-ip-filter:
    - '*.google.com'
    - '*.googleapis.com'
    - '*.gstatic.com'
    - '*.googleusercontent.com'
    - '*.msauth.net'
    - '*.msftauth.net'
    - '*.passport.com'
    - '*.sharepoint.com'
    - '*.xboxlive.com'
    - '*.market.xiaomi.com'
    - 'WORKGROUP'
    - '*.lan'
    - 'stun.*.*.*'
    - 'stun.*.*'
    - 'time.windows.com'
    - 'time.nist.gov'
    - 'time.apple.com'
    - 'time.asia.apple.com'
    - '*.ntp.org.cn'
    - '*.openwrt.pool.ntp.org'
    - 'time1.cloud.tencent.com'
    - 'time.ustc.edu.cn'
    - 'pool.ntp.org'
    - 'ntp.ubuntu.com'
  nameserver:
    - 'https://1.1.1.1/dns-query'
    - 'https://8.8.8.8/dns-query'
    - 'tls://1.1.1.1:853'
```
# 在proxy进行修改(同样是rules file)
```c
proxy-groups:
  - { name: Gemini, type: select, proxies: ['🇸🇬 新加坡1', '🇸🇬 新加坡2', '🇸🇬 新加坡3', '🇸🇬 新加坡4', '🇸🇬 新加坡5', '🇸🇬 新加坡6', '🇸🇬 新加坡7', '🇯🇵 日本1', '🇯🇵 日本2', '🇺🇸 美国1', '🇺🇸 美国2', BoostNet] }//插入新的proxy

  - { name: BoostNet, type: select, proxies: [自动选择, 故障转移, '🇸🇬 新加坡1', '🇸🇬 新加坡2', '🇸🇬 新加坡3', '🇸🇬 新加坡4', '🇸🇬 新加坡5', '🇸🇬 新加坡6', '🇸🇬 新加坡7', '🇯🇵 日本1', '🇯🇵 日本2', '🇺🇸 美国1', '🇺🇸 美国2', '🇭🇰 香港1', '🇭🇰 香港2', '🇭🇰 香港3', '🇭🇰 香港4', '🇭🇰 香港5', '🇭🇰 香港6', '🇭🇰 香港7', '🇭🇰 香港8', '🇭🇰 香港9', '🇭🇰 香港10', '🇭🇰 香港11', '🇭🇰 香港12', '🇭🇰 香港13', '🇭🇰 香港14', '🇭🇰 香港15', '🇭🇰 香港16'] }

```
# 在网页的QUIC关闭(快速加载协议)
chrome://flags/#enable-quic
egde自搜