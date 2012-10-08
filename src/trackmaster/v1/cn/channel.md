---
weight: 6
layout: default
category: trackmaster
title: 频道
---

# 频道

* TOC
{:toc}


## 获取指定媒体频道列表

    GET /medias/:media_id/channels

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/channels?page=2>; rel="next",
          <http://{{site.track_api_host}}/channels?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
       {
            //频道ID，全局唯一
            "id": 1025,
            //频道名称
            "name": "体育新闻",
            //`webpage` 网页, `video` 视频广告, `client` 客户端, `se` 搜索引擎, `email` 邮件, `other` 其他
            "type": "web",
            //广告位在第几屏幕
            "screen": 3,
            //频道地址
            "home": "http://www.admaster.com.cn/",
            //物料类型 `flash`，`image`，`video`, `textlink`, `other` 默认：`flash`
            "material_type": 'flash',
            //物料的显示尺寸，单位像素 格式如 400x300 宽度为400px 高度为300px
            "material_dimension": "400x300",
            //物料文件大小，单位由 material_size_unit 指定
            "material_size": 200,
            //物料文件大小单位，B K M 默认：`K`
            "material_size_unit": "B"
        }
    ]

## 获取指定频道详细信息

    GET /medias/channels/:id

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        //频道ID，全局唯一
        "id": 1025,
        //频道名称
        "name": "体育新闻",
        //`webpage` 网页, `video` 视频广告, `client` 客户端, `se` 搜索引擎, `email` 邮件, `other` 其他
        "type": "web",
        //广告位在第几屏幕
        "screen": 3,
        //频道地址
        "home": "http://www.admaster.com.cn/",
        //物料类型 `flash`，`image`，`video`, `textlink`, `other` 默认：`flash`
        "material_type": 'flash',
        //物料的显示尺寸，单位像素 格式如 400x300 宽度为400px 高度为300px
        "material_dimension": "400x300",
        //物料文件大小，单位由 material_size_unit 指定
        "material_size": 200,
        //物料文件大小单位，B K M 默认：`K`
        "material_size_unit": "B"
    }


## 为指定媒体新增频道

    POST /medias/:media_id/channels

**参数**

`name`
: _必选_ **string** - 频道名称

`type`
: _可选_ **string** - 类型

  * `webpage`： 网页
  * `video`： 视频广告
  * `client`： 客户端
  * `se`： 搜索引擎
  * `email`： 邮件
  * `other`： 其他

`screen`
: _可选_ **string** - 广告位在第几屏幕

`home`
: _可选_ **string** - 频道地址

`material_type`
: _可选_ **string** - 物料类型 

  * `flash`:flash (默认)
  * `image`:图片
  * `video`: 视频
  * `textlink`: 文字链接
  * `other`: 其他

`material_dimension`
: _可选_ **string** - 物料的显示尺寸，单位像素 格式如 400x300 宽度为400px 高度为300px

`material_size`
: _可选_ **enum** - 物料文件大小，单位由 material_size_unit 指定

`material_size_unit`
: _可选_ **string** - 物料文件大小单位

  * `B`:Byte
  * `K`:Kbyte (默认)
  * `M`:Mbyte

**请求**

{:.prettyprint}
    {
        //频道名称
        "name": "体育新闻",
        //`webpage` 网页, `video` 视频广告, `client` 客户端, `se` 搜索引擎, `email` 邮件, `other` 其他
        "type": "web",
        //广告位在第几屏幕
        "screen": 3,
        //频道地址
        "home": "http://www.admaster.com.cn/",
        //物料类型 `flash`，`image`，`video`, `textlink`, `other` 默认：`flash`
        "material_type": 'flash',
        //物料的显示尺寸，单位像素 格式如 400x300 宽度为400px 高度为300px
        "material_dimension": "400x300",
        //物料文件大小，单位由 material_size_unit 指定
        "material_size": 200,
        //物料文件大小单位，B K M
        "material_size_unit": "B"
    }


**响应**

    Status: 204 No Content
    Location: http://{{site.track_api_host}}/channel/123
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
