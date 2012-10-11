---
weight: 13
layout: default
category: trackmaster
subcategory: publisher
title: 媒体报告
---

# 媒体报告

* TOC
{:toc}

## 获取指定媒体下的项目

    GET /medias/:media_id/campaigns

**响应**

    Status: 200 OK

{:.prettyprint}
    [
      {
        "id": 1,
        "name": "这是一个测试项目",
        "start_date": "2012-01-03",
        "end_date": "2012-06-23",
        "created_at": "2012-09-06T20:39:23Z"
      }
]

## 获取指定项目下的日报告

    GET /medias/:media_id/campaigns/:campaign_id/daily_reports

**参数**

`start_time`
: _可选_ **date** - 项目开始日期，例如2012-08-01，会列出项目开始日期大于等于此设定的项目

`end_time`
: _可选_ **date** - 项目结束日期，例如2012-08-02，会列出项目结束日期小于等于此设定的项目

`sort`
: _可选_ **string** - 列表排序以什么排序

  * `time` - 按照时间排序
  * `imp` - 按照曝光排序
  * `clk` - 按照点击排序
  * `uimp` - 按照独立曝光排序
  * `uclk` - 按照独立点击排序

`direction`
: _可选_ **string** - 排序方式

  * `asc` 升序 (_默认_)
  * `desc` 降序

**响应**

    Status: 200 OK


{:.prettyprint}
    [
      {
        "time": "2012-08-01", // 时间
        "imp": 23, //曝光
        "uimp": 20, //独立曝光
        "clk": 20, //点击
        "uclk": 10, //独立点击
      }
    ]


## 获取指定监测代码下的项目日报告

    GET /medias/campaigns/daily_reports/codes

**参数**

`code`
: _必选_ **string** - 项目监测代码

**响应**

    Status: 204 No Content
    Link: <http://{{site.track_api_host}}/medias/1308/campaigns/10256/daily_reports>; rel="campaigns"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## 获取指定监测代码下的项目报告

    GET /medias/campaigns/reports/codes

**参数**

`code`
: _必选_ **string** - 项目监测代码

**响应**

    Status: 204 No Content
    Link: <http://{{site.track_api_host}}/medias/1308/campaigns/10256/reports>; rel="campaigns"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


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

## 获取指定媒体项目报告列表

    GET /medias/:media_id/campaigns/:campaign_id/reports

**参数**

`time`
: _必选_ **string** - 数据时间类型

  * `hourly` 获取小时数据
  * `daily` 获取日数据
  * `weekly` 获取周数据
  * `monthly` 获取月数据

`dims`
: _必选_ **string** - 数据聚合维度,多个选项之间用`,`分开

  * `placement` 按广告位维度聚合
  * `keyword` 按关键字维度聚合
  * `creative` 按创意维度聚合
  * `geo` 按地域维度聚合
  * `time` 按时间维度聚合

`placement_id`
: _可选_ **integer** - 广告位ID

`keyword_id`
: _可选_ **integer** - 关键字ID

`creative_id`
: _可选_ **integer** - 创意ID

`geo_id`
: _可选_ **integer** - 地域ID

`start_time`
: _可选_ **hour** - 开始时间，会列出日期大于等于此设定的项目

`end_time`
: _可选_ **hour** - 结束时间，会列出日期小于等于此设定的项目

`sort`
: _可选_ **string** - 列表排序以什么排序

  * `time` - 按照时间排序
  * `imp` - 按照曝光排序
  * `clk` - 按照点击排序
  * `uimp` - 按照独立曝光排序
  * `uclk` - 按照独立点击排序

`direction`
: _可选_ **string** - 排序方式

  * `asc` 升序 (_默认_)
  * `desc` 降序


**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/medias/1/campaigns/12/reports?page=2>; rel="next",
          <http://{{site.track_api_host}}/medias/1/campaigns/12/reports?page=10>; rel="last"

{:.prettyprint}
    [
      {
        "campaign_id": 10185,
        "time": "2012-08-03",
        "imp": 9,
        "uimp": 6,
        "ipuimp": 6,
        "clk": 3,
        "uclk": 3,
        "ipuclk": 2
      }
    ]
