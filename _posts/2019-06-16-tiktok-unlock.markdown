---
layout: post
title: "TikTok 封区解锁"
date: 2019-06-16 22:05:00 +0800
categories: Ruleset
tags: TikTok Surge Rule
img: https://aligege-1259468288.file.myqcloud.com/img/2019-06-16-tiktok-unlock.gif
key: 2019-06-16-tiktok-unlock
themecolor: "#fff"
themetextcolor: "#000"
describe: 
---

> 通过 [**Surge 3 Pro**](https://nssurge.com) 的 URL Rewrite 和 MitM 来破解 TikTok 地区限制问题，让国内的用户也可以使用 TikTok（国际版抖音）。

<!--more-->

**注：**注意在添加此规则之前需要先确认 Surge 已经打开了 Rewrite 和 MitM 功能的开关。并确保已经安装及信任了 Surge 当前配置文件中的 CA 证书，详情请查看 [**相关方法**](http://t.cn/AiCtbSCz)。

最后再将下方内容中的规则添加到 Surge 的配置文件中即可。

```shell
[Rule]
DOMAIN-SUFFIX,musical.ly,PROXY
DOMAIN-SUFFIX,pstatp.com,PROXY
DOMAIN-SUFFIX,tiktokv.com,PROXY

[URL Rewrite]
(.*video_id=\w{32})(.*watermark=)(.*) $1 302
(?<=(carrier|account|sys)_region=)CN JP 307
(?<=\?video_id=\w{32})[^*]+ 302

[MITM]
hostname = api*.amemv.com, api*.musical.ly, aweme*.snssdk.com, api*.tiktokv.com
enable = true
```