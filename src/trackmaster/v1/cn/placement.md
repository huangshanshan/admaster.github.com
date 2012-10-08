---
weight: 10
layout: default
category: trackmaster
title: 广告位
---

#广告位

* TOC
{:toc}

## 获取指定项目下指定媒体的广告位列表

    GET /networks/advertisers/campaigns/:campaign_id/placements

**参数**

`name`
: _可选_ **string** - 广告位名称，支持模糊搜索

`network_media_id`
: _可选_ **integer** - 限定工作网络媒体ID

`page`
: _可选_ **integer** - 显示页码

`per_page`
: _可选_ **integer** - 分页数量，默认每页30条

**响应**

    Status: 200 OK
    Link: <http://{{site.track_api_host}}/networks/advertisers/campaigns/123/placements?page=2>; rel="next",
          <http://{{site.track_api_host}}/networks/advertisers/campaigns/123/placements?page=10>; rel="last"
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    [
      {
        //广告位ID，全局唯一
        "id": 1,
        //获取详情接口地址
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/placements/1",
        //广告位位置名称
        "name": "这是一个测试广告位",
        //工作网络下媒体ID
        "network_media_id": 1314,
        //频道信息
        "channel": {
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
            "material_type": "flash",
            //物料的显示尺寸，单位像素 格式如 400x300 宽度为400px 高度为300px
            "material_dimension": "400x300",
            //物料文件大小，单位由 material_size_unit 指定
            "material_size": 200,
            //物料文件大小单位，B K M
            "material_size_unit": "B"
        }
        //note 轮播属性, `1/1` 固定，`1/2` 二分之一轮播，一次类推
        "rotation" : "1/4",
        //点击目标地址
        "target_url": "http://www.admaster.com.cn/",
        //支付类型 `purchase` 购买，`offering` 配送，`framework` 框架，`Compensation` 补偿，`other` 其他
        "payment_type": "purchase",
        //单位收费类型 `day` 天，`week` 周，`month` 月，`cpc`，`cpm`，`cpa`，`article` 文章，`kmail` 千封邮件，`other` 其他
        "cost_type": "day"
        //单位成本
        "cost_per_unit": 873.12,
        //单位预估曝光数
        "est_imp_per_unit": 239,
        //单位预估点击
        "est_clk_per_unit": 3,
        //购买量
        "units": 58,
        //其他要求
        "other_requirement": "没有什么要求",
        //预估曝光
        "est_imp": 871821,
        //预估点击
        "est_clk": 1231,
        //创建时间
        "created_at": "2012-09-06T20:39:23Z"
      }
    ]


## 获取指定广告位信息

    GET /networks/advertisers/campaigns/placements/:id

**响应**

    Status: 200 OK
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
    //广告位ID，全局唯一
    "id": 1,
    //获取详情接口地址
    "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/placements/1",
    //广告位位置名称
    "name": "这是一个测试广告位",
    //工作网络下媒体ID
    "network_media_id": 1314,
    //频道信息
    "channel": {
        //频道ID，全局唯一
        "id": 1025,
        //频道名称
        "name": "体育新闻",
        //`webpage` 网页, `video` 视频广告, `client` 客户端, `se` 搜索引擎, `email` 邮件, `other` 其他
        "type": "webpage",
        //广告位在第几屏幕
        "screen": 3,
        //频道地址
        "home": "http://www.admaster.com.cn/",
        //物料类型 `flash`，`image`，`video`, `textlink`, `other` 默认：`flash`
        "material_type": "flash",
        //物料的显示尺寸，单位像素 格式如 400x300 宽度为400px 高度为300px
        "material_dimension": "400x300",
        //物料文件大小，单位由 material_size_unit 指定
        "material_size": 200,
        //物料文件大小单位，B K M
        "material_size_unit": "B"
    },
    //note 轮播属性, `1/1` 固定，`1/2` 二分之一轮播，一次类推
    "rotation" : "1/4",
    //点击目标地址
    "target_url": "http://www.admaster.com.cn/",
    //支付类型 `purchase` 购买，`offering` 配送，`framework` 框架，`Compensation` 补偿，`other` 其他
    "payment_type": "purchase",
    //单位收费类型 `day` 天，`week` 周，`month` 月，`cpc`，`cpm`，`cpa`，`article` 文章，`kmail` 千封邮件，`other` 其他
    "cost_type": "day"
    //单位成本
    "cost_per_unit": 873.12,
    //单位预估曝光数
    "est_imp_per_unit": 239,
    //单位预估点击
    "est_clk_per_unit": 3,
    //购买量
    "units": 58,
    //其他要求
    "other_requirement": "没有什么要求",
    //预估曝光
    "est_imp": 871821,
    //预估点击
    "est_clk": 1231,
    //创建时间
    "created_at": "2012-09-06T20:39:23Z"
    }

## 添加一个广告位在指定项目下

    POST /networks/advertisers/campaigns/:campaign_id/placements

**参数**

`name`
: _必选_ **string** - 广告位位置名称，字符串，长度为 3 - 100个字符

`network_media_id`
: _必选_ **string** - 广告位所属工作网络媒体ID,

`channel_id`
: _必选_ **integer** - 广告位频道ID

`rotation`
: _可选_ **string** 轮播属性, `1/1` 固定，`1/2` 二分之一轮播，一次类推，默认: `1/1`

`target_url`
: _可选_ **string** 点击目标地址, 默认为空，继承项目的点击目标地址

`payment_type`
: _可选_ **string** - 支付类型

  * `purchase` 购买 _默认值_
  * `offering` 配送
  * `framework` 框架
  * `Compensation` 补偿
  * `other` 其他

`cost_type`
: _可选_ **string** - 单位收费类型

  * `day` 天 _默认值_
  * `week` 周
  * `month` 月
  * `cpc` 每次点击成本
  * `cpm` 千人展示成本
  * `cpa` 每次行动成本
  * `article` 文章
  * `kmail` 千封邮件
  * `other` 其他 

`cost_per_unit`
: _可选_ **float** - 单位成本

`est_imp_per_unit`
: _可选_ **integer** - 单位预估曝光数

`est_clk_per_unit`
: _可选_ **integer** - 单位预估点击

`other_requirement`
: _可选_ **string** - 其他要求

**请求**

{:.prettyprint} 
    {
        "name": "这是一个测试广告位",
        "network_media_id": 1314,
        "channel_id": 123,
        "rotation" : "1/4",
        "target_url": "http://www.admaster.com.cn/",
        "payment_type": "purchase",
        "cost_type": "day"
        "cost_per_unit": 873.12,
        "est_imp_per_unit": 239,
        "est_clk_per_unit": 3,
        "other_requirement": "没有什么要求",
    }
    
**响应**

    Status: 201 Created
    Location: http://{{site.track_api_host}}/networks/advertisers/campaigns/placements/1
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999

{:.prettyprint}
    {
        "id": 1,
        "url": "http://{{site.track_api_host}}/networks/advertisers/campaigns/placements/1",
        "name": "这是一个测试广告位",
        "network_media_id": 1314,
        "channel": {
            "id": 123,
            "name": "体育新闻",
            "type": "webpage",
            "screen": 3,
            "home": "http://www.admaster.com.cn/",
            "material_type": "flash",
            "material_dimension": "400x300",
            "material_size": 200,
            "material_size_unit": "B"
        },
        "rotation" : "1/4",
        "target_url": "http://www.admaster.com.cn/",
        "payment_type": "purchase",
        "cost_type": "day"
        "cost_per_unit": 873.12,
        "est_imp_per_unit": 239,
        "est_clk_per_unit": 3,
        "units": 0,
        "other_requirement": "没有什么要求",
        "est_imp": 0,
        "est_clk": 0,
        "created_at": "2012-09-06T20:39:23Z"
    }

## 删除指定的广告位

    DELETE /networks/advertisers/campaigns/placements/:id

**响应**

    Status: 204 No Content
    Location: http://{{site.track_api_host}}/networks/advertisers/campaigns/123/placements
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999


## 修改指定的广告位属性

    PATCH /networks/advertisers/campaigns/placements/:id

**请求**

`name`
: _可选_ **string** - 广告位位置名称，字符串，长度为 3 - 100个字符

`channel_id`
: _可选_ **integer** - 广告位频道ID

`rotation`
: _可选_ **string** 轮播属性, `1/1` 固定，`1/2` 二分之一轮播，一次类推，默认: `1/1`

`target_url`
: _可选_ **string** 点击目标地址, 默认为空，继承项目的点击目标地址

`payment_type`
: _可选_ **string** - 支付类型

  * `purchase` 购买 _默认_
  * `offering` 配送
  * `framework` 框架
  * `Compensation` 补偿
  * `other` 其他 

`cost_type`
: _可选_ **string** - 单位收费类型 

  * `day` 天 _默认_
  * `week` 周
  * `month` 月
  * `cpc` 每次点击成本
  * `cpm` 千人展示成本
  * `cpa` 每次行动成本
  * `article` 文章
  * `kmail` 千封邮件
  * `other` 其他 

`cost_per_unit`
: _可选_ **float** - 单位成本

`est_imp_per_unit`
: _可选_ **integer** - 单位预估曝光数

`est_clk_per_unit`
: _可选_ **integer** - 单位预估点击

`other_requirement`
: _可选_ **string** - 其他要求

**请求**

{:.prettyprint}
    {
        "name": "这是一个测试广告位",
        "channel_id": 123,
        "rotation" : "1/4",
        "target_url": "http://www.admaster.com.cn/",
        "payment_type": "purchase",
        "cost_type": "day"
        "cost_per_unit": 873.12,
        "est_imp_per_unit": 239,
        "est_clk_per_unit": 3,
        "other_requirement": "没有什么要求",
    }

**响应**

    Status: 204 No Content
    X-RateLimit-Limit: 5000
    X-RateLimit-Remaining: 4999
