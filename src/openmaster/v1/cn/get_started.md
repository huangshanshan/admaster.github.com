---
weight: 2
layout: default
category: openmaster
title: 快速入门
---

# 快速入门

* TOC
{:toc}

本文档为开发者快速入门提供一个概览，更为完整的 API 信息请参阅 OpenMaster API 文档说明。

在开发之前你需要在 [管理应用页面](http://open.admaster.com.cn/app/new) 申请创建一个应用，填入应用的描述信息，从而获得 Client ID 和 Client Secret Key（CSK）， Client ID 用于唯一标识你的应用。创建完成后，使用 OAuth2.0 对用户进行验证，保障用户的隐私和安全性。

## 第一步：创建应用

为了保护用户的数据，防止 API 被滥用或恶意使用，每个 API 的使用者在 [管理应用页面](http://open.admaster.com.cn/app/new) 创建自己的应用，从而获得 Client ID 以及 Client Secret Key（CSK）。每个 Client ID 唯一标识一个 API 应用。

使用 OpenMaster API 时，每小时最多访问5000次，超过限制的话会被封禁。如果你的应用确实需要超过每小时5000次请求，请与 api@admaster.com.cn 联系。请提供你的应用的详细信息，包括 Client ID、目的、使用 API 的方式、预计请求频次、网站 URL、是否商业行为、访问 API 所使用的服务器的 IP 地址等信息。审核通过后可设置白名单，放宽访问限制。

## 第二步：用户身份认证

大部分 OpenMaster API 的调用需要对用户的身份进行认证。目前 OpenMaster 仅支持 OAuth2.0 认证。关于 OAuth 2.0 的详细说明请参见 [OAuth2.0说明](/doc/openmaster/v1/cn/oauth.html)。

## 第三步：开始API之旅

某些 API 接口需要以特定用户身份来调用，例如获取广告主信息、操作广告位等。您的应用需要先通过 OAuth 认证得到 Access Token，才能够以与之对应的用户身份来调用 API。调用时，需要在每个 API 请求中加入 `access_token` 参数。

某些 API 接口可以不必以特定用户身份调用。如果您的应用不需要验证用户身份，则调用这些 API 时不需要传 access_token 参数，而应该传 Client ID 参数，值为应用的 App ID。

现在让我们真正开始一次 API 的调用，下面通过一个简单的示例来演示 TrackMaster™ API 的使用。这个示例中展示了...

调用：请求的 URL 如下（注意将 source 参数的值设置为您的应用的 App ID）:

    http://track.admasterapi.com/advertisers

返回：请求上面的 URL 之后，返回 JSON 数据。

**响应**

{:.prettyprint}
    [
      {
        "id": 1,
        "url": "http://track.admasterapi.com/advertisers/1",
        "name": {
          "zh_cn": "宝马",
          "en_us": "BMW",
          "zh_tw": "宝马",
          "ko": "BMW",
          "es_es": "BMW"
          },
        "logo": "http://www.trackmaster.com.cn/data/advIcon/1.jpg",
        "created_at": "2011-07-08T09:53:07Z"
      }
    ]
