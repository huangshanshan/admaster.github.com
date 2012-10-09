---
weight: 3
layout: default
category: trackmaster
subcategory: agency
title: 媒体
---

# 媒体

* TOC
{:toc}

## 获取系统媒体库列表

    GET /medias

**参数**

`sort`
: _可选_ **string** - 列表排序以什么排序

  * `id` - 按照媒体ID排序
  * `name` - 按照媒体名称排序
  * `create_time` - 按照创建日期排序

`direction`
: _可选_ **string** - 排序方式

  * `asc` 升序 (_默认_)
  * `desc` 降序

`page`
: _可选_ **integer** - 显示页码

`per_page`
: _可选_ **integer** - 分页数量，默认每页30条

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/medias?page=2>; rel="next",
          <http://{{site.track_api_host}}/medias?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
        "id": 1,
        "url": "http://{{site.track_api_host}}/medias/1",
        "name": "新浪",
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/1.ico",
        "domain": "sina.com.cn",
        "tag": "综合其他",
        "created_at": "2012-09-06T20:39:23Z"
      }
    ]


## 获取指定系统媒体详细信息

    GET /medias/:id

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 1,
        "url": "http://{{site.track_api_host}}/medias/1",
        "name": "新浪",
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/1.ico",
        "domain": "sina.com.cn",
        "tag": "综合其他",
        "created_at": "2012-09-06T20:39:23Z"
    }


## 媒体用户获取iab数据

    GET /medias/:id/ies

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/medias/1/ies?page=2>; rel="next",
          <http://{{site.track_api_host}}/medias/1/ies?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

**参数**

`pubid`
: _可选_ **string** - pubid 指定后只获取该pubid的数据

`date`
: _可选_ **date** - 日期，要查看的数据日期，YYYY-mm-dd 例如: 2012-06-08 ,不指定则获取头一天的数据

`page`
: _可选_ **integer** - 显示页码

{:.prettyprint}
    [
      {
        "date_hour": 2012061015,
        "pubid": "IYK_IMloxnwepMEqlx",
        "city": "北京",
        "geoid": 110000,
        "impression": 12039423,
        "click": 43432,
      }
    ]


## 获取指定工作网络下媒体库列表

    GET /networks/:network_id/medias

**参数**

`sort`
: _可选_ **string** - 列表排序以什么排序

  * `id` - 按照网络媒体ID排序
  * `name` - 按照网络媒体名称排序
  * `status` - 按照状态排序
  * `framework` - 按照框架排序

`direction`
: _可选_ **string** - 排序方式

  * `asc` 升序 (_默认_)
  * `desc` 降序

`page`
: _可选_ **integer** - 显示页码

`per_page`
: _可选_ **integer** - 分页数量，默认每页30条

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/1/medias?page=2>; rel="next",
          <http://{{site.track_api_host}}/networks/1/medias?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
        "id": 1,
        "url": "http://{{site.track_api_host}}/networks/1/medias/2",
        "name": "新浪",
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/1.ico",
        "domain": "sina.com.cn",
        "tag": "综合其他",
        "status": "enabled"
        "created_at": "2012-09-06T20:39:23Z"
        "media_id": 150
        "framework": "no"
      }
    ]


## 获取指定工作网络下指定媒体信息

    GET /networks/:network_id/medias/:media_id

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 1,
        "url": "http://{{site.track_api_host}}/networks/1/medias/2",
        "name": "新浪",
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/1.ico",
        "domain": "sina.com.cn",
        "tag": "综合其他",
        "status": "enabled"
        "created_at": "2012-09-06T20:39:23Z"
        "media_id": 150
        "framework": "no"
    }


## 给指定工作网络添加一个媒体

    POST /networks/:network_id/medias

**请求**

{:.prettyprint}
    {
        'media_id': 8982
    }

`media_id`: _必选_ **integer** - 系统媒体ID

**响应**

    Status: 201 Created
    Location: http://{{site.track_api_host}}/networks/1/medias/2
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 1,
        "url": "http://{{site.track_api_host}}/networks/1/medias/2",
        "name": "新浪",
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/1.ico",
        "domain": "sina.com.cn",
        "tag": "综合其他",
        "status": "enabled"
        "created_at": "2012-09-06T20:39:23Z"
        "media_id": 8982
        "framework": "no"
    }

## 删除指定工作网络下的媒体

    DELETE /networks/medias/:id

**响应**

    Status: 204 No Content
    Location: http://{{site.track_api_host}}/networks/1/medias
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## 修改指定工作网络下指定媒体属性

    PATCH /networks/:network_id/medias/:media_id

**请求**

{:.prettyprint}
    {
        "name": "新浪财经",
        "framework": "no",
        "status": "enabled"
    }

`name`
: _可选_ **string** - 网络媒体名称

`framework`
: _可选_ **enum** - 是否有框架 `yes`, `no`

`status`
: _可选_ **enum** - 状态 `enabled`, `disabled`


**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 1,
        "url": "http://{{site.track_api_host}}/networks/1/medias/2",
        "name": "新浪财经",
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/1.ico",
        "domain": "sina.com.cn",
        "tag": "综合其他",
        "status": "enabled"
        "created_at": "2012-09-06T20:39:23Z"
        "media_id": 8982
        "framework": "no"
    }


## 获取指定项目下已添加的媒体属性列表

    GET /networks/advertisers/campaigns/:campaign_id/medias/attributes

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
        "id": 1314,
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/10092/medias/1314",
        "name": "新浪",
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/1.ico",
        "created_at": "2012-09-06T20:39:23Z"
      }
    ]

## 获取指定项目下指定媒体属性

    GET /networks/advertisers/campaigns/:campaign_id/medias/:network_media_id/attributes

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 1314,
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/10092/medias/1314",
        "name": "新浪",
        "logo": "http://www.trackmaster.com.cn/data/mediaIcon/1.ico",
        "created_at": "2012-09-06T20:39:2"
    }

## 判断指定项目下是否有指定媒体

    GET /networks/advertisers/campaigns/:campaign_id/medias/:network_media_id

**响应**

指定媒体在指定项目下

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

指定媒体不在指定项目下

    Status: 404 Not Found
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


##为指定项目添加指定媒体

    PUT /networks/advertisers/campaigns/:campaign_id/medias/:network_media_id

**响应**

    Status: 204 No Content
    Location: http://{{site.track_api_host}}/networks/advertisers/campaigns/12/medias/123/attributes
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## 删除指定项目下指定的媒体

    DELETE /networks/advertisers/campaigns/:campaign_id/medias/:network_media_id

**响应**

    Status: 204 No Content
    Location: http://{{site.track_api_host}}/networks/advertisers/campaigns/12/medias/attributes
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
