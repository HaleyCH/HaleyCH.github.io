title: 快速配置https，使用Certbot申请 Let's Encrypt SSL 证书并配置定时续期
author: HaleyCH
tags:
  - https
  - ssl证书
categories:
  - 博客搭建
cover_image: 'https://i.hluvmiku.tech/f/63b6e3cec65c09c012b31daa/'
abbrlink: 5ac49a40
date: 2023-01-05 22:37:00
---
![img_63b6e3cec65c09c012b31daa](https://i.hluvmiku.tech/f/63b6e3cec65c09c012b31daa/)
省流：`certbot`
# 前言

有了博客，不能没有SSL证书。
于是找了个免费的一键配置SSL的`certbot`。

# 使用方法

首先安装 `yum install certbot` 。

安装完后使用 `certbot` 申请有通配符的域名 SSL 证书：
`certbot certonly -d *.your.domain --manual --preferred-challenges dns --server https://acme-v02.api.letsencrypt.org/directory`
其中 `your.domain` 替换为你的域名。
按步骤完成申请。证书将存放在 `/etc/letsencrypt/live/your.domain` 下。

然后配置定时更新
```bash
crontab -e
0 */12 * * * certbot renew --quiet --renew-hook "/etc/init.d/nginx reload"
```

最后配置 `/etc/nginx/nginx`

```nginx
server {
  listen: 443 ssl;
  server_name: your.domain;
  /* location部分自行配置 */
  
  listen ssl;
  ssl_certificate /etc/letsencrypt/live/your.domain/fullchain.pem;
  ssl_certificate_key /etc/letsencrypt/live/your.domain/privkey.pem;
}
```

配置完成。

# 参考资料
 - [https://www.cnblogs.com/jacklondon/p/renew_ssl_certification_by_cerbot.html](https://www.cnblogs.com/jacklondon/p/renew_ssl_certification_by_cerbot.html)