---
title: Try Try Podman
author: 黃馨平
date: 2021-12-17T11:22:54.865Z
tags: [podman,kubernetes,containers]
---

### Try Try Podman
![](images/8419853b7a4f/1*aDXlJ6n1dw7L76RvRmxzsQ.png "")

本篇簡單的紀錄一下，Podman 的一些基礎用法，適合給超級新手村的人快速上手，因為基礎的東西跟 docker 幾乎都一樣，難怪看網路上的人說可以直接這樣，在過程中我也常常太順打成 docker
```
alias docker=podman
```
### Environment

OS: Red Hat Enterprise Linux release 8.4
Podman: 3.3.1
### Step
. Create Dockerfile
. Build image
. Run container
. Stop container

```
# create folder，folder tree like this.
```

Below is my dockerfile. This time I only use python image. Otherwise, I install python package through “requirements.txt”.
###  **Build image** 
```Dockerfile
FROM python:3.6.8-slim

WORKDIR /app

COPY requirements.txt ./
RUN pip3 install -r requirements.txt
```

“requirements.txt” is mean your python package list. when you use this package list. It’s more easily to management your package version and reduce your command.
```Text
paramiko==2.8.0
```

In this crawler_project folder type below command.
```
$ podman build -t jacky_project .
#show image
$ podman images
```
### Run container
```
$ podman run --name jacky_python -v /tmp:/tmp -id localhost/jacky_project
$ podman ps
# Then, you can see container status.
```
###  **Stop container** 
```
$ podman stop jacky_python
```
### Remove Container
```
$ podman rm jacky_python
```

Remove image
```
$ podman rmi localhost/jacky_project
```

原本以為從 docker 轉來 podman 會非常的麻煩，看來真的無縫轉移呢。之後再去玩 podman 的其他特色功能，再跟大家分享。
### 初步使用 podman 後的心得
[薛家燕 食神 評審 嚐 好 好好好 驚艷 不敢相信 美味 一絕 恭喜](https://cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Ftenor.com%2Fembed%2F11497497&display_name=Tenor&url=https%3A%2F%2Ftenor.com%2Fview%2Fnancy-sit-god-of-cookery-judge-delicious-congrats-gif-11497497&image=https%3A%2F%2Fc.tenor.com%2FKe8gWdX4ilIAAAAC%2Fnancy-sit-god-of-cookery.gif&key=a19fcc184b9711e1b4764040d3dc5c07&type=text%2Fhtml&schema=tenor)

Ref:
- [Podman official webiste](https://podman.io/)
- [Podman pod introudce](https://ithelp.ithome.com.tw/articles/10239822)
- [How to write dockerfile](/%E4%B8%80%E5%80%8B%E5%B0%8F%E5%B0%8F%E5%B7%A5%E7%A8%8B%E5%B8%AB%E7%9A%84%E9%9A%A8%E6%89%8B%E7%AD%86%E8%A8%98/docker-%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98-%E5%9B%9B-%E5%A6%82%E4%BD%95%E6%92%B0%E5%AF%ABdockerfile-2a209b485530)
- [Python Docker file](https://docs.docker.com/language/python/build-images/)
- [實作撰寫第一個 Dockerfile](https://ithelp.ithome.com.tw/articles/10191016?sc=hot)
- [小飛機的 podman 介紹](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwjkx6Tql-r0AhXPZt4KHUD6DysQFnoECAcQAQ&url=https%3A%2F%2Fspeakerdeck.com%2Fpichuang%2F20201024-podman-rong-qi-ji-shu-ti-sheng-da-fa&usg=AOvVaw3FLKXgrGp0XQE7j7syea-5)
- [Day 5 關於 Container 的那些大小事](https://ithelp.ithome.com.tw/articles/10193534)
- [An Introduction to Podman](https://www.baeldung.com/ops/podman-intro)



+-----------------------------------------------------------------------------------+

| **[View original post on Medium](https://medium.com/jacky-life/try-try-podman-8419853b7a4f) - Converted by [ZhgChgLi](https://blog.zhgchg.li)/[ZMediumToMarkdown](https://github.com/ZhgChgLi/ZMediumToMarkdown)** |

+-----------------------------------------------------------------------------------+
