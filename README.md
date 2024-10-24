# 简单的 Sing-Box DNS 过滤器

## 简介
一个简陋的 Sing-Box DNS 过滤器实现，个人使用。

## 引用过滤器

### AdGuard DNS 过滤器
AdGuard DNS 过滤器包含多个过滤器，主要包括：
- **AdGuard 基础过滤器**
- **社交媒体过滤器**
- **防跟踪保护过滤器**
- **移动广告过滤器**
- **EasyList 和 EasyPrivacy**

该过滤器经过简化，确保与 DNS 级别的广告拦截兼容。AdGuard DNS 服务器使用此过滤器有效拦截广告和跟踪器。  
[查看规则](https://github.com/AdguardTeam/AdGuardSDNSFilter)

### OISD 过滤器
OISD 阻止列表旨在防止设备连接到不必要或有害的域。其特点包括：
- **减少广告**
- **降低恶意软件风险**
- **提升隐私保护**

OISD 列表优先考虑功能性，适合在家庭、工作等场合使用，用户反馈普遍良好。  
[查看规则](https://oisd.nl)

## 使用方法
以下是配置示例：

```json
{
  "dns": {
    "servers": [
      {
        "tag": "dns_block",
        "address": "rcode://success"
      }
    ],
    "rules": [
      {
        "outbound": "dnsblock",
        "server": "dns_block"
      }
    ],
    "route": {
      "rule_set": [
        {
          "type": "remote",
          "tag": "geosite-cn",
          "format": "binary",
          "url": "https://github.com/MetaCubeX/meta-rules-dat/raw/refs/heads/sing/geo/geosite/cn.srs",
          "download_detour": "proxy"
        }
      ]
    }
  }
}
```
通过上述配置，您可以在 Sing-Box 中实现基本的 DNS 过滤功能，提升网络安全与隐私保护。
