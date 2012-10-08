---
weight: 2
layout: default
category: trackmaster
title: 广告主
---

# 广告主

* TOC
{:toc}

## 获取系统广告主列表

    GET /advertisers

**参数**

`sort`
: _可选_ **string** - 列表排序以什么排序

  * `id` - 按照广告主ID排序
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
    Link: <http://{{site.track_api_host}}/advertisers?page=2>; rel="next",
          <http://{{site.track_api_host}}/advertisers?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
        "id": 1,
        "url": "http://{{site.track_api_host}}/advertisers/1",
        "name": {"zh_cn" => "腾讯", "en_us" => "tencent"},   //广告主名称
        "logo": "http://www.trackmaster.com.cn/data/advIcon/1.jpg",  //Logo URL
        "created_at": "2012-09-06T20:39:23Z"  //创建时间
      }
    ]


## 获取指定系统广告主信息

    GET /advertisers/:id

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 1,
        "url": "http://{{site.track_api_host}}/advertisers/1",
        "name": {"zh_cn" => "腾讯", "en_us" => "tencent"},   //广告主名称
        "logo": "http://www.trackmaster.com.cn/data/advIcon/1.jpg",  //Logo URL
        "created_at": "2012-09-06T20:39:23Z"  //创建时间
    }


## 获取指定工作网络下所有广告主属性列表

    GET /networks/:network_id/advertisers

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
        "advertiser_id": 1,
        "url": "http://{{site.track_api_host}}/networks/1/advertisers/1",
        "name": {"zh_cn" => "腾讯", "en_us" => "tencent"},   //广告主名称
        "status": "enabled",
        "alias": "ibm",
        "logo": "http://www.trackmaster.com.cn/data/advIcon/1.jpg",  //Logo URL
        "created_at": "2012-09-06T20:39:23Z"  //创建时间
      }
    ]

## 获取指定网络下的指定广告主属性

    GET /networks/:network_id/advertisers/:advertiser_id

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/1/advertisers/1/campaigns>; rel="campaigns"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "advertiser_id": 1,
        "url": "http://{{site.track_api_host}}/networks/1/advertisers/1",
        "name": {"zh_cn" => "通用电器", "en_us" => "GM"},   //广告主名称
        "status": "enabled"
        "alias": "通用电器",
        "logo": "http://www.trackmaster.com.cn/data/advIcon/1.jpg",  //Logo URL
        "created_at": "2012-09-06T20:39:23Z" //创建时间
    }

## 添加指定系统广告主到指定工作网络下

    PUT /networks/:network_id/advertisers/:advertiser_id

**响应**

    Status: 204 No Content
    Link: <http://{{site.track_api_host}}/networks/1/advertisers/1/campaigns>; rel="campaigns"
    Location: http://{{site.track_api_host}}/networks/1/advertisers/1
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## 修改指定网络下的指定广告主属性

    PATCH /networks/:network_id/advertisers/:advertiser_id

**请求**

{:.prettyprint}
    {
        "alias": "通用电器",
        "status": "enabled"
    }


`alias`
: _可选_ **string** - 别名

`status`
: _可选_ `enabled`, `disabled`

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/1/advertisers/1/campaigns>; rel="campaigns"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "advertiser_id": 1,
        "url": "http://{{site.track_api_host}}/networks/1/advertisers/1",
        "name": {"zh_cn" => "通用电器", "en_us" => "GM"},   //广告主名称
        "status": "enabled"
        "alias": "通用电器",
        "logo": "http://www.trackmaster.com.cn/data/advIcon/1.jpg",  //Logo URL
        "created_at": "2012-09-06T20:39:23Z" //创建时间
    }

## 删除指定工作网络下的指定广告主

    DELETE /networks/:network_id/advertisers/:advertiser_id

**响应**

    Status: 204 No Content
    Link: <http://{{site.track_api_host}}/networks/1/advertisers>; rel="campaigns"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

