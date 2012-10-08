---
weight: 5
layout: default
category: trackmaster
title: 品牌
---

# 品牌

* TOC
{:toc}


## 获取指定网络下指定广告主下的所有品牌

    GET /networks/:network_id/advertisers/:advertiser_id/brands

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


{:.prettyprint}
    [
      {
        "id": 1,
        "name": "巧乐兹",
        "created_at": "2012-09-06T20:39:23Z"
      }
    ]


## 获取指定 ID 品牌详细信息

    GET /networks/advertisers/brands/:id

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 1,
        "network_id": 1,
        "advertiser_id": 10231,
        "name": "巧乐兹",
        "url": "http://{{site.track_api_host}}/networks/advertisers/brands/1",
        "created_at": "2012-09-06T20:39:23Z"
    }


## 添加指定品牌到指定网络广告主下

    POST /networks/:network_id/advertisers/:advertiser_id/brands

**请求**

    {
        "name": "巧乐兹"
    }

`name`
: _必填_ **string** - 品牌名称

**响应**

    Status: 201 Created 
    Location: http://{{site.track_api_host}}/networks/1/advertisers/10231/brands
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 1,
        "network_id": 1,
        "advertiser_id": 10231,
        "name": "巧乐兹",
        "url": "http://{{site.track_api_host}}/networks/advertisers/brands/1",
        "created_at": "2012-09-06T20:39:23Z"
    }


## 修改指定的网络广告主下品牌名称

    PATCH /networks/advertisers/brands/:id

**请求**

{:.prettyprint}
    {
        "name": "巧乐鸡"
    }

`name`
: _必选_ **string** - 品牌名称


**响应**

    Status: 204 No Content 
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## 删除指定的网络广告主下品牌

    DELETE /networks/advertisers/brands/:id

**响应**

{:.prettyprint}
    Status: 204 No Content 
    Location: http://{{site.track_api_host}}/networks/1/advertisers/10231/brands
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
