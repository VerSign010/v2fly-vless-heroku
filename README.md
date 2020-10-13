# VLESS Heroku

## 概述

用于在 Heroku 上部署 vless+websocket+tls，vless 性能更加优秀，占用资源更少。

## 镜像

经测试本镜像不会因为大量占用资源而被封号。

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://dashboard.heroku.com/new?template=https%3A%2F%2Fgithub.com%2FVerSign010%2Fv2fly-vless-heroku)

## 注意

### 端口

`端口` 为 `443` 。

### UUID

`UUID` 默认为 `76709679-6b5f-4191-b17c-5c6d7d7783ef` 可自行设置。

UUID生成网址：https://www.uuidgenerator.net/

## 流量中转

可以使用cloudflare的workers来`中转流量`，配置为：  

addEventListener(  
    "fetch",event => {  
        let url=new URL(event.request.url);  
        url.hostname="应用名称.herokuapp.com";  
        let request=new Request(url,event.request);  
        event. respondWith(  
            fetch(request)  
        )  
    }  
)  
