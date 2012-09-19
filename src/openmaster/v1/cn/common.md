---
weight: 5
layout: default
category: openmaster
title: 接口定义 - 通用说明
---

# 接口定义 - 通用说明

## 全局名称定义

![trackmast结构示意图](/doc/trackmaster/v1/cn/trackmaster.png)


## 通用参数说明

`access_token`
	oauth 验证串，通过授权验证可以得到，请求授权数据的时候需要携带，具体查看[oauth 验证][apiOauth]
	

## 返回状态说明

**返回状态在请求返回的头部信息**
	
`200 OK`
	请求成功，只是请求成功，不代表没有逻辑错误，逻辑错误记录在 error_code, error_msg 元素中

`201 CREATED`
	创建成功

`202 ACCEPTED`
	更新、修改成功

`204 NO CONTENT`
	无返回内容

`400 BAD REQUEST`
	请求地址不存在或者带有不支持的参数

`401 UNAUTHORIZED`
	未经授权

`403 FORBIDDEN`
	禁止访问

`404 NOT FOUND`
	请求的资源不存在

`500 INTERNAL SERVER ERROR`
	服务器内部错误

## 错误代码说明

