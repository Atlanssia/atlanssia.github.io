---
title: Realtime Blackhole List
date: 2017-03-17 19:49:40
tags:
---

## 定义
RBL : Realtime Blackhole List
中国反垃圾邮件联盟目前提供黑名单服务分为4部分：CBL,CDL,CBL+,CBL-。另外中国互联网协会反垃圾邮件(信息)中心也提供了RBL服务

## 配置方法

| - | 地址         | 测试地址  | 返回状态码 |
|---|---|---|---|
| CBL | cbl.anti-spam.org.cn | 2.0.0.127.cbl.anti-spam.org.cn. |	127.0.8.2 |
| CDL |	cdl.anti-spam.org.cn |	0.0.0.240.cdl.anti-spam.org.cn.	| 127.0.8.4 |
| CBL+ |	cblplus.anti-spam.org.cn |	2.0.0.127.cblplus.anti-spam.org.cn. | 127.0.8.6 |
| CBL- |	cblless.anti-spam.org.cn |	2.0.0.127.cblless.anti-spam.org.cn.	| 127.0.8.5 |
| RBL | rbl.anti-spam.cn	| 1.1.168.192.rbl.anti-spam.cn	| 127.0.0.2 |

在Postfix2中配置`smtpd_recipient_restrictions`:

```
smtpd_recipient_restrictions = XXXXXXX
reject_rbl_client cbl.anti-spam.org.cn,
reject_rbl_client cdl.anti-spam.org.cn,
...
```

测试服务可以在 `reject_rbl_client` 前加上 `warning_if_reject`

## 其他常用RBL

| -	| 服务器地址	| 返回状态码| 
|---|---|---|
| SPAMHAUS SBL	| sbl.spamhaus.org	| 127.0.0.2 |
| SPAMHAUS XBL	| xbl.spamhaus.org	| 127.0.0.4-6 |
| SPAMHAUS SBL+ XBL	| sbl-xbl.spamhaus.org	| 127.0.0.2-6 |
| spamcop RBL	| bl.spamcop.net	| 127.0.0.2 |

其中spamhaus.org提供三种类型：XBL，SBL，ROKSO
- XBL（Exploits Block List）
- SBL（The Spamhaus Block List）
- ROKSO （TheRegister of Known Spam Operations）确定（有确切证据）的已知垃圾邮件发送者

另外还有（部分服务已下线，未验证）

```
ORDB-RBL-------------------------------relays.ordb.org
spamhaus-------------------------------sbl.spamhaus.org
spamcop--------------------------------bl.spamcop.net
Infinite-Monkeys-----------------------proxies.relays.monkeys.com
NJABL----------------------------------dnsbl.njabl.org
osirusoft.com--------------------------relays.osirusoft.com
MAPS-RBL-------------------------------blackholes.mail-abuse.org
MAPS-DUL-------------------------------dialups.mail-abuse.org
MAPS-RSS-------------------------------relays.mail-abuse.org
MAPS-RBL+------------------------------rbl-plus.mail-abuse.ja.net
Easynet-DNSBL--------------------------blackholes.easynet.nl
Easynet-Proxies------------------------proxies.blackholes.easynet.nl
Easynet-Dynablock----------------------dynablock.easynet.nl
OSIRUSOFT-SPEWS------------------------spews.relays.osirusoft.com
```
