---
weight: 9
layout: default
category: trackmaster
subcategory: agency
title: 创意
---

# 创意

* TOC
{:toc}

## 获取指定项目所有创意

    GET /networks/advertisers/campaigns/:campaign_id/creatives

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/advertisers/campaigns/123/creatives?page=2>; rel="next",
          <http://{{site.track_api_host}}/networks/advertisers/campaigns/123/creatives?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
        //创意ID，全局唯一
        "id": 1,
        //获取详情接口地址
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/creatives/1",
        //创意名称
        "name": "这是一个很不错的创意",
        //创意名缩写
        "shortname": "GO",
        //创意描述
        "description": "这个很不错的创意受到了全国人民的一致认可",
        //创意颜色标识
        "color": "#ff00ff",
        //创意附属文件
        "file": {
            "id": 293,
            "name": "创意.jpg",
            "type": "jpg",
            "access_url": "http://www.trackmaster.com.cn/data/upload/2011/0608/0/1_3a35e4a11b.jpg",
            "width": 400,
            "height": 300
        },
        //创意点击目标地址
        "target_url": "http://www.admaster.com.cn/",
        //创建时间
        "created_at": "2012-09-06T20:39:23Z"
      }
    ]


## 获取项目下指定创意信息

    GET /networks/advertisers/campaigns/creatives/:id

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        //创意ID，全局唯一
        "id": 1,
        //获取详情接口地址
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/creatives/1",
        //创意名称
        "name": "这是一个很不错的创意",
        //创意名缩写
        "shortname": "GO",
        //创意描述
        "description": "这个很不错的创意受到了全国人民的一致认可",
        //创意颜色标识
        "color": "#ff00ff",
        //创意附属文件
        "file": {
            "id": 293,
            "name": "创意.jpg",
            "type": "jpg",
            "access_url": "http://www.trackmaster.com.cn/data/upload/2011/0608/0/1_3a35e4a11b.jpg",
            "width": 400,
            "height": 300
        },
        //创意点击目标地址
        "target_url": "http://www.admaster.com.cn/",
        //创建时间
        "created_at": "2012-09-06T20:39:23Z"
    }


## 在指定项目下添加创意

    POST /networks/advertisers/campaigns/:campaign_id/creatives

**参数**

`name`
: _必选_ **string** - 创意名称 长度为 3 - 100个字符

`shortname`
: _必选_ **string** - 创意短名称 长度为2个字节，字母数字类型

`color`
: _必选_ **string** - 创意颜色 标准颜色代码 例如：`#ff00ff`

`description`
: _可选_ **string** - 创意描述 最大长度为 1000个字符

`file_id`
: _可选_ **integer** - 创意物料ID

`target_url`
: _可选_ **string** - 创意点击目标地址

**请求**

{:.prettyprint}
    {
        "name": "这是一个很不错的创意",
        "shortname": "GO",
        "description": "这个很不错的创意受到了全国人民的一致认可",
        "color": "#ff00ff",
        "file_id": 123,
        "target_url": "http://www.admaster.com.cn/",
    }

**响应**

    Status: 201 Created
    Location: http://{{site.track_api_host}}/networks/advertisers/campaigns/creatives/1
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        //创意ID，全局唯一
        "id": 1,
        //获取详情接口地址
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/creatives/1",
        //创意名称
        "name": "这是一个很不错的创意",
        //创意名缩写
        "shortname": "GO",
        //创意描述
        "description": "这个很不错的创意受到了全国人民的一致认可",
        //创意颜色标识
        "color": "#ff00ff",
        //创意附属文件
        "file": {
            "id": 123,
            "name": "创意.jpg",
            "type": "jpg",
            "access_url": "http://www.trackmaster.com.cn/data/upload/2011/0608/0/1_3a35e4a11b.jpg",
            "width": 400,
            "height": 300
        },
        //创意点击目标地址
        "target_url": "http://www.admaster.com.cn/",
        //创建时间
        "created_at": "2012-09-06T20:39:23Z"
    }

## 删除指定的创意

    DELETE /networks/advertisers/campaigns/creatives/:id

**响应**

    Status: 204 No Content
    Location: http://{{site.track_api_host}}/networks/advertisers/campaigns/123/creatives
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

## 修改指定的创意属性

    PATCH /networks/advertisers/campaigns/creatives/:id

**参数**

`name`
: _必选_ **string** - 创意名称 长度为 3 - 100个字符

`shortname`
: _必选_ **string** - 创意短名称 长度为2个字节，字母数字类型

`color`
: _可选_ **string** - 创意颜色 标准颜色代码 例如：`#ff00ff`

`description`
: _可选_ **string** - 创意描述 最大长度为 1000个字符

`file_id`
: _可选_ **integer** - 创意物料ID

`target_url`
: _可选_ **string** - 创意点击目标地址

**请求**

{:.prettyprint}
    {
        "name": "这是一个很不错的创意",
        "shortname": "GO",
        "description": "这个很不错的创意受到了全国人民的一致认可",
        "color": "#ff00ff",
        "file_id": 123,
        "target_url": "http://www.admaster.com.cn/",
    }

**响应**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

