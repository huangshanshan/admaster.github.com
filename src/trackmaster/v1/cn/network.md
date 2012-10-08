---
weight: 4
layout: default
category: trackmaster
title: 工作网络
---

# 工作网络

* TOC
{:toc}

## 获取当前授权用户有权操作的所有工作网络

    GET /user/networks

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
       {
        "id": 1,
        "url": "https://api.trackmaster.com.cn/networks/1",
        "name": "测试工作网络", //别名
        "created_at": "2012-09-06T20:39:23Z" //创建时间
        "account": {
            "status": "enabled", //`enabled` 可用, `disabled` 禁用, `unactive` 未激活
            "created_at": "2012-01-10T02:30:59Z", //当前用户加入网络的时间
            "role": {
                "id": 1,
                "name": "高级管理员(super admin)"
             }
          }
       }
    ]

## 获取指定 ID 工作网络信息

    GET /networks/:id

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/1/advertisers>; rel="advs"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
      "id": 1,
      "url": "https://api.trackmaster.com.cn/networks/1",
      "name": "测试工作网络",//别名
      "created_at": "2012-09-06T20:39:23Z" //创建时间
    }
