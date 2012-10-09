---
weight: 7
layout: default
category: trackmaster
subcategory: agency
title: 项目
---

# 项目

* TOC
{:toc}

## 获取指定工作网络下某个广告主有操作权限的项目列表

    GET /networks/:network_id/advertisers/:advertiser_id/campaigns

**参数**

`name`
: _可选_ **string** - 项目名称，支持模糊搜索，例如：名称为 “这是一个测试项目” 搜索 “一个”即可找到改项目

`network_brand_id`
: _可选_ **integer** - 项目所属网络品牌ID

`status`
: _可选_ *Enum* - 项目状态

  * `all` - 所有状态, (_默认_)
  * `typing` - 拟稿中
  * `testing` - 测试中
  * `kickoff` - 项目初期
  * `midterm` - 项目中期
  * `teminal` - 项目末期
  * `finished` - 已结束

`start_date`
: _可选_ **date** - 项目开始时间，会列出项目开始日期小于等于此设定的项目

`end_date`
: _可选_ **date** - 项目结束时间，会列出项目结束日期大于等于次设定的项目

`sort`
: _可选_ **string** - 列表排序以什么排序

  * `id` - 按照项目ID排序
  * `network_brand_id` - 按照品牌ID排序
  * `name` - 按照项目名称排序
  * `total_cost` - 按照总成本排序
  * `media_num` - 按照媒体数排序
  * `placement_num` - 按照广告位数排序
  * `start_date` - 按照开始日期排序
  * `end_date` - 按照结束日期排序
  * `est_imp` - 按照总预计曝光排序
  * `est_clk` - 按照总预计点击排序

`direction`
: _可选_ **string** - 排序方式

  * `asc` 升序 (_默认_)
  * `desc` 降序

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/12/advertisers/122/campaigns?page=2>; rel="next",
          <http://{{site.track_api_host}}/networks/12/advertisers/122/campaigns?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
        "id": 1,
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/1",
        "name": "这是一个测试项目",
        "network_brand_id": 10213,
        "cost_type": "CNY",
        "total_cost": 20000000,
        "start_date": "2012-01-03",
        "end_date": "2012-06-23",
        "default_target": "http://www.admaster.com.cn"
        "survey_id": 1024,
        "media_num": 8,
        "placement_num": 258,
        "est_imp": 9183213,
        "est_clk": 12334,
        "status": "typing",
        "is_online": "yes",
        "created_at": "2012-09-06T20:39:23Z"
      }
    ]


## 获取指定项目信息

    GET /networks/advertisers/campaigns/:id

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/advertisers/campaigns/1/medias/attributes>; rel="nwmedias"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 1,
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/1",
        "name": "这是一个测试项目",
        "network_brand_id": 10213,
        "cost_type": "CNY",
        "total_cost": 20000000,
        "start_date": "2012-01-03",
        "end_date": "2012-06-23",
        "default_target": "http://www.admaster.com.cn"
        "survey_id": 1024,
        "media_num": 8,
        "placement_num": 258,
        "target_audience":{
            "age": "19-25",
            "sex": "male"
        },
        "status": "typing",
        "is_online": "yes",
        "created_at": "2012-09-06T20:39:23Z"
    }


## 添加指定项目到指定广告主下

    POST /networks/:network_id/advertisers/:advertiser_id/campaigns

**参数**

`name`
: _必选_ **string** - 项目名称，长度范围 3 - 100 个字符

`network_brand_id`
: _必选_ **integer** - 所属网络品牌ID

`start_date`
: _必选_ **date** - 项目开始日期 YYYY-mm-dd 例如：2012-01-03

`end_date`
: _必选_ **date** - 项目结束日期 YYYY-mm-dd 例如：2012-06-23, 结束日期要大于开始日期

`default_target`
: _必选_ **string** - 项目默认点击目标地址，例如: http://www.admaster.com.cn/

`survey_id`
: _可选_ **integer** - 项目关联的 SurveyMaster 系统下的问卷ID,

`cost_type`
: _可选_ **string** - 媒体预算货币类型

  * `None` 不设置媒体预算 _默认值_
  * `CNY` 人民币
  * `USD` 美元

`target_audience`
: _可选_ *Object* - 目标受众人群

{:.prettyprint}
    {
        "age": "19-25",//年龄设定，例如: 16-20  16岁到20岁
        "sex": "male"//性别设定，`male` 男, `female` 女
    }


**请求**

{:.prettyprint}
    {
        "name": "这是一个测试项目",
        "network_brand_id": 10021,
        "start_date": "2012-01-31",
        "end_date": "2012-04-20",
        "default_target": "http://www.admaster.com.cn/",
        "survey_id": 1002,
        "cost_type": "USD",
        "target_audience": {
            "age": "16-30",
            "sex": "female"
        }
    }

**响应**

    Status: 201 Created
    Location: http://{{site.track_api_host}}/networks/advertisers/campaigns/1
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 1,
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/1",
        "name": "这是一个测试项目",
        "network_brand_id": 10021,
        "cost_type": "USD",
        "total_cost": 0,
        "start_date": "2012-01-31",
        "end_date": "2012-04-20",
        "default_target": "http://www.admaster.com.cn"
        "survey_id": 1002,
        "media_num": 0,
        "placement_num": 0,
        "target_audience":{
            "age": "16-30",
            "sex": "female"
        },
        "status": "typing",
        "is_online": "no",
        "created_at": "2012-09-06T20:39:23Z"
    }

**字段说明**

参见页面底部说明

## 修改指定项目属性

    PATCH /networks/advertisers/campaigns/:id

**参数**

`name`
: _可选_ **string** - 项目名称，长度范围 3 - 100 个字符

`network_brand_id`
: _可选_ **integer** - 所属网络品牌ID

`start_date`
: _可选_ **date** - 项目开始日期 YYYY-mm-dd 例如：2012-01-03

`end_date`
: _可选_ **date** - 项目结束日期 YYYY-mm-dd 例如：2012-06-23, 结束日期要大于开始日期

`default_target`
: _可选_ **string** - 项目默认点击目标地址，例如: http://www.admaster.com.cn/

`survey_id`
: _可选_ **integer** - 项目关联的 SurveyMaster 系统下的问卷ID,

`cost_type`
: _可选_ **string** - 媒体预算货币类型

  * `None` 不设置媒体预算 _默认值_
  * `CNY` 人民币
  * `USD` 美元

`target_audience`
: _可选_ *Object* - 目标受众人群

{:.prettyprint}
    {
        "age": "19-25",//年龄设定，例如: 16_20  16岁到20岁
        "sex": "male"//性别设定，`male` 男, `female` 女
    }

**请求**

{:.prettyprint}
    {
        "name": "这是一个测试项目",
        "network_brand_id": 10021,
        "start_date": "2012-01-31",
        "end_date": "2012-04-20",
        "default_target": "http://www.admaster.com.cn/",
        "survey_id": 1002,
        "cost_type": "USD",
        "target_audience": {
            "age": "16-30",
            "sex": "female"
        }
    }

**响应**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999



## 删除指定项目

    DELETE /networks/advertisers/campaigns/:id

**响应**

    Status: 204 No Content
    Location: http://{{site.track_api_host}}/networks/12/advertisers/123/campaigns
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## 字段说明

返回值字段         | 字段类型 | 字段说明
id               | integer | 项目 ID
url              | string  | 请求URL
name             | string  | 项目名称
network_brand_id | integer | 项目所属网络品牌 ID
cost_type        | string  | 币种
total_cost       | integer | 总花费
start_date       | date    | 开始日期
end_date         | date    | 结束日期
default_target   | date    | 默认目标
survey_id        | integer | 项目关联的 SurveyMaster 系统下的问卷ID
media_num        | integer | 媒体数量
placement_num    | integer | 广告位数量
status           | string  | 状态
is_online        | string  | 是否在线
created_at       | date    | 创建时间

