title: '[uWSGI] invalid request block size: 21573 (max 4096)...skip'
author: HaleyCH
tags:
  - Solved
  - uWSGI
  - Python
  - Flask
categories:
  - Common mistakes
abbrlink: 394285b4
cover: 'http://i.hluvmiku.tech/f/63b1446daf4452e2604c5b5e/'
cover-img: 'http://i.hluvmiku.tech/f/63b146570226d7a9075072ff/'
cover_image: 'http://i.hluvmiku.tech/f/63b1472baf4452e2604c5b62/'
date: 2022-12-15 13:09:00
---
# 问题描述
在使用 `uwsgi --socket 0.0.0.0:5000 --wsgi-file app.py --callable app --processes 1 --threads 1 --stats 127.0.0.1:5001` 部署`i.hluvmiku.tech`后，访问该网页发现出现__502 Bad Gateway__。

同时可以看到后端显示`invalid request block size: 21573 (max 4096)...skip`。
# 解决方案
在查阅[这篇文章](https://stackoverflow.com/questions/15878176/uwsgi-invalid-request-block-size)后，我得到了解决方案，即：__将`--socket 0.0.0.0:5000` 改为 `--http 0.0.0.0:5000`即可__。
>I aslo ran into same issue while following some tutorial. The problem was that I set the option socket = 0.0.0.0:8000 instead of http = 0.0.0.0:8000. socket option intended to be used with some third-party router (nginx for instance), while when http option is set uwsgi can accept incoming HTTP requests and route them by itself.

# 问题分析
http和http-socket的区别在于，如果我们想直接将uwsgi用作服务器（例如Apache和nginx那样）直接暴露在公网那么就使用http；

如果有单独的服务器（例如Apache或者nginx），由服务器将请求转发给uwsgi处理，并且使用http协议，那么此时使用http-socket。

- http: 自己会产生一个http进程(可以认为与nginx同一层)负责路由http请求给worker, http进程和worker之间使用的是uwsgi协议
- http-socket: 不会产生http进程, 一般用于在前端webserver不支持uwsgi而仅支持http时使用, 他产生的worker使用的是http协议

因此, http 一般是作为独立部署的选项; http-socket 在前端webserver不支持uwsgi时使用,
如果前端webserver支持uwsgi, 则直接使用socket即可