---
weight: 13
layout: default
category: trackmaster
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

    GET /medias/campaigns/daily_reports/code/:code

**响应**

    Status: 204 No Content
    Link: <http://{{site.track_api_host}}/medias/1308/campaigns/10256/daily_reports>; rel="campaigns"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
