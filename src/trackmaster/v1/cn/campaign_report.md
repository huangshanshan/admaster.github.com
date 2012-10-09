---
weight: 12
layout: default
category: trackmaster
subcategory: agency
title: 项目报告
---

# 项目报告

* TOC
{:toc}

## 获取指定项目下有操作权限的项目报告列表

    GET /campaigns/:campaign_id/reports

**参数**

`time`
: _必选_ **string** - 数据时间类型

  * `hourly` 获取小时数据
  * `daily` 获取日数据
  * `weekly` 获取周数据
  * `monthly` 获取月数据

`dims`
: _必选_ **string** - 数据聚合维度,多个选项直接用`,`分开

  * `media` 按媒体维度聚合
  * `placement` 按广告位维度聚合
  * `keyword` 按关键字维度聚合
  * `creative` 按创意维度聚合
  * `geo` 按地域维度聚合
  * `time` 按时间维度聚合

`network_media_id`
: _可选_ **integer** - 网络媒体ID

`placement_id`
: _可选_ **integer** - 广告位ID

`keyword_id`
: _可选_ **integer** - 关键字ID

`creative_id`
: _可选_ **integer** - 创意ID

`geo_id`
: _可选_ **integer** - 地域ID

`start_time`
: _可选_ **hour** - 项目开始时间，会列出项目开始日期大于等于此设定的项目

`end_time`
: _可选_ **hour** - 项目结束时间，会列出项目结束日期小于等于此设定的项目

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
    Link: <http://{{site.track_api_host}}/campaigns/12/reports?page=2>; rel="next",
          <http://{{site.track_api_host}}/campaigns/12/reports?page=10>; rel="last"

{:.prettyprint}
    [
      {
        "campaign_id": 10185,
        "network_media_id": 1484,
        "time": "2012-08-03",
        "imp": 9,
        "uimp": 6,
        "ipuimp": 6,
        "clk": 3,
        "uclk": 3,
        "ipuclk": 2
      }
    ]


**字段说明**

返回值字段 | 字段类型     | 字段说明
imp      | integer     | 曝光
uimp     | integer     | 独立曝光
ipuimp   | integer     | IP独立曝光
clk      | integer     | 点击
uclk     | integer     | 独立点击
ipuclk   | integer     | IP独立点击

