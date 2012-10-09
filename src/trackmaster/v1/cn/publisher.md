---
weight: 14
layout: default
category: trackmaster
title: 媒体
---


# 媒体对接指南

* TOC
{:toc}


TrackMaster™ 所有API的访问都是通过 HTTP 执行的，所有被发送和接受的的数据都是 JSON。

TrackMaster™ 使用 OAuth2.0 对用户进行验证，保障用户的隐私和安全性。


## 第一步 获取访问令牌

    POST http://open.admaster.com.cn/oauth/access_token

**参数**

    {
      "client_id": "***",
      "client_secret": "***",
      "grant_type": "password",
      "email": "your@email.com",
      "password": "***"
    }

**响应**

    {
      "access_token": "7a68b4d65ddd6a6191ef0cbf9cadb06528d92d67",
      "expires_in": "18000",
      "refresh_token": "23a89c9944afc0525a25d15d180c6bce03efa331"
    }

`access_token`在`expires_in`秒内有效，超期后请重新访问该接口获取新的访问令牌，携带参数：

    {
      "client_id": "***",
      "client_secret": "***",
      "grant_type": "refresh_token",
      "refresh_token": "***"
    }


## 第二步 获取媒体项目列表

    GET http://track.admasterapi.com/medias/:media_id/campaigns

**参数**

第一步中获取到的`access_token`

    access_token=***

**响应**

    [
      {
        "id": 1,
        "name": "这是一个测试项目",
        "start_date": "2012-01-03",
        "end_date": "2012-06-23",
        "created_at": "2012-09-06T20:39:23Z"
      }
    ]


## 第三步 获取项目媒体报告

    GET http://track.admasterapi.com/medias/:media_id/campaigns/:campaign_id/daily_reports

**参数**

    :media_id 必选 Integer - TrackMaster分配的媒体ID
    :campaign_id 必选 Integer - 项目ID

    access_token=***
    start_time 可选 Date - 项目开始日期，例如2012-08-01，会列出项目开始日期大于等于此设定的项目
    end_time 可选 Date - 项目结束日期，例如2012-08-02，会列出项目结束日期小于等于此设定的项目
    sort 可选 String - 列表排序以什么排序
    direction 可选 String - 排序方式


**响应**

    Status: 200 OK

    [
      {
        "time": "2012-08-01", // 时间
        "imp": 23, //曝光
        "uimp": 20, //独立曝光
        "clk": 20, //点击
        "uclk": 10, //独立点击
      }
    ]



## 详情参见

[媒体报告](/doc/trackmaster/v1/cn/media_report.html)
[协议及请求说明](/doc/openmaster/v1/cn/verbs.html)

