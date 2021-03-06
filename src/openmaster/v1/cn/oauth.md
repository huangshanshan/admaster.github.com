---
weight: 3
layout: default
category: openmaster
title: OAuth 认证
---

# OAuth 认证

* TOC
{:toc}

OAuth（开放授权）是一个开放标准，允许用户让第三方应用访问该用户在 OpenMaster 的资源，而无需将用户名和密码提供给第三方应用。

OAuth2.0 是从2006年开始设计 OAuth 协议的下一个版本，OAuth2.0 同时提供 Web，桌面和移动应用程序的支持，并较1.0相比整个授权验证流程更简单更安全。

开发者需要先在[应用注册页面](http://open.admaster.com.cn/app/new) 申请创建一个应用，填入应用的描述信息，从而获得Client ID和Client Secret，这个Client ID用于唯一标识你的应用，Client Secret应严格保密。创建完应用以后，使用 OpenMaster OAuth2.0 对用户进行验证，保障用户的隐私和安全性。

## Web 应用开发流程

下面是第三方应用使用 OAuth 接入 OpenMaster 的流程介绍。

### 1. 重定向用户到 OpenMaster OAuth用户验证页面

    GET http://open.admaster.com.cn/oauth/authorize

**参数**

`client_id`
: _必选_ **string** - 这个 client ID 是你在 OpenMaster [应用注册页面](http://open.admaster.com.cn/app/new)获得的。

`response_type`
: _必选_ **Enum** - 返回类型，`code`, `token`

`redirect_uri`
: _可选_ **string** - 在用户验证后，重定向到你的应用的地址。

`scope`
: _可选_ **string** - 逗号分割的 scopes，受保护资源的作用域。

### 2. OpenMaster 重定向回你的应用

如果用户接受你应用的请求，OpenMaster 重定向回你的应用，并携带code参数。
你可以以此来获取 access token：

    POST http://open.admaster.com.cn/oauth/access_token

**参数**

`client_id`
: _必选_ **string** - 这个 client ID 是你在 OpenMaster [应用注册页面](http://open.admaster.com.cn/app/new)获得的。

`client_secret`
: _必选_ **string** - 这个 client secret 是你在 OpenMaster [应用注册页面](http://open.admaster.com.cn/app/new)获得的。

`grant_type`
: _必选_ **enum** - `authorization_code` 根据code获取token `password` 根据密码获取token `refresh_token` 刷新token

`redirect_uri`
: _可选_ **string**

`code`
: _可选_ **string** - 在第一步中重定向返回的参数，当`grant_type`为`authorization_code`时传递该参数。

`email`
: _可选_ **string** - 用户邮箱，当`grant_type`为`password`时传递该参数

`password`
: _可选_ **string** - 用户密码，当`grant_type`为`password`时传递该参数

`refresh_token`
: _可选_ **string** - 刷新令牌，当`grant_type`为`refresh_token`时传递该参数

**响应**

{:.prettyprint}
    {
      "access_token": "7a68b4d65ddd6a6191ef0cbf9cadb06528d92d67",
      "expires_in": "1800000",
      "refresh_token": "23a89c9944afc0525a25d15d180c6bce03efa331"
    }


### 3. 使用 access token 访问 API

使用 access token 允许你来请求用户的信息。

    GET http://open.admaster.com.cn/user?access_token=...

**响应**

{:.prettyprint}
    {
      "id": 98,
      "email": "hello@admaster.com.cn",
      "username": "hello"
    }


## 非Web应用请求流程

通过创建新认证来创建一个 OAuth2 token，这项技术，用户名和密码可以不用永久存储，并且用户可以随时取消访问。

## 重定向 URLs

`redirect_uri` 参数是可选的。如果为空，OpenMaster 将用户重定向到在应用设置里的回调URL，如果不为空，将重定向到此URL，并且此URL必须与回调URL的主机名相同。

    CALLBACK: http://foo.com

    GOOD: http://foo.com
    GOOD: http://foo.com/bar
    BAD:  http://foo.com:8080
    BAD:  http://oauth.foo.com:8080
    BAD:  http://bar.com

## 作用域 Scopes

作用域允许你提供你想要的资源类型。这些将在用户授权表单页面显示。

检查Http头部信息来确认不同API所需要的资源作用域。

    $ curl -H "Authorization: bearer TOKEN" http://open.admaster.com.cn/user/1 -I
    HTTP/1.1 200 OK
    X-OAuth-Scopes: brand, user
    X-Accepted-OAuth-Scopes: user

`X-OAuth-Scopes` 列出你的token已授权的作用域。
`X-Accepted-OAuth-Scopes` 列出当前API检查的作用域。

没有作用域(no scope)
: 公共只读访问 (包含公共用户资料等).

user : 当前用户可以访问修改的资源。

注意：你的应用在初始化重定向的时候来请求作用域。你可以用逗号分隔开多个作用域。

    http://open.admaster.com.cn/oauth/authorize?client_id=...&scope=user,brand


## 更多信息

你可能对使用 OAuth 有一些疑惑，或许下面的这些链接对你有帮助：

* [OAuth 2 spec](http://tools.ietf.org/html/draft-ietf-oauth-v2-07)
* [Facebook API](http://developers.facebook.com/docs/authentication/)
* [Ruby OAuth2 lib](http://github.com/intridea/oauth2)
* [simple ruby/sinatra example](http://gist.github.com/9fd1a6199da0465ec87c)
* [simple python example](http://gist.github.com/e3fbd47fbb7ee3c626bb) using [python-oauth2](http://github.com/dgouldin/python-oauth2)
* [Ruby OmniAuth example](http://github.com/intridea/omniauth)

