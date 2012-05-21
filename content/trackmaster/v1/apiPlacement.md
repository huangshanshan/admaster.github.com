---
title: API - 广告位接口
---

#API - 广告位接口

<h2 id="p1">获取指定项目下指定媒体的广告位列表</h2>

    GET /networks/advertisers/campaigns/:campaign_id/placements

###参数

name
: _可选_ *String* - 广告位名称，支持模糊搜索

media\_id
: _可选_ *Int* - 限定工作网络媒体ID

###响应
<pre class="headers">
<code>Status: 200 OK
Link: <http://api.trackmaster.com.cn/networks/advertisers/campaigns/:campaign_id/placements?page=2>; rel="next",
      <http://api.trackmaster.com.cn/networks/advertisers/campaigns/:campaign_id/placements?page=10>; rel="last"
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
[
  {
    //广告位ID，全局唯一
    "id": 1,
    //获取详情接口地址
    "url": "http://api.trackmaster.com.cn/networks/advertisers/campaigns/placements/1",
    //广告位位置名称
    "name": "这是一个测试广告位",
    //工作网络下媒体ID
    "media_id": 1314,
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
        "materia_type": 'flash',
        //物料的显示尺寸，单位像素 格式如 400x300 宽度为400px 高度为300px
        "materia_dimension": "400x300",
        //物料文件大小，单位由 materia_size_unit 指定
        "materia_size": 200,
        //物料文件大小单位，Byte KByte MByte
        "materia_size_unit": "Byte"
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
    //物料类型 `flash`，`image`，`video`, `textlink`, `other` 默认：`flash`
    "materia_type": 'flash',
    //物料的显示尺寸，单位像素 格式如 400x300 宽度为400px 高度为300px
    "materia_dimension": "400x300",
    //物料文件大小，单位由 materia_size_unit 指定
    "materia_size": 200,
    //物料文件大小单位，Byte KByte MByte
    "materia_size_unit": "Byte",
    //广告位在第几屏幕
    "screen": 3,
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
</code></pre>
关于错误返回值与错误代码，参见[错误代码说明][apiCommon]

###适用版本

[v1.0][version]

<h2 id="p2">获取指定广告位信息</h2>

    GET /networks/advertisers/campaigns/placements/:id

###响应
<pre class="headers">
<code>Status: 200 OK
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
//广告位ID，全局唯一
"id": 1,
//获取详情接口地址
"url": "http://api.trackmaster.com.cn/networks/advertisers/campaigns/placements/1",
//广告位位置名称
"name": "这是一个测试广告位",
//工作网络下媒体ID
"media_id": 1314,
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
    "materia_type": 'flash',
    //物料的显示尺寸，单位像素 格式如 400x300 宽度为400px 高度为300px
    "materia_dimension": "400x300",
    //物料文件大小，单位由 materia_size_unit 指定
    "materia_size": 200,
    //物料文件大小单位，Byte KByte MByte
    "materia_size_unit": "Byte"
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
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon]

###适用版本

[v1.0][version]

<h2 id="p3">添加一个广告位在指定项目下</h2>

    POST /networks/advertisers/campaigns/:campaign_id/placements

###请求

name
: _必选_ *String* - 广告位位置名称，字符串，长度为 3 - 100个字符

media\_id
: _必选_ *String* - 广告位所属工作网络媒体ID,

channel
: _必选_ *Object* - 广告位频道信息

###示例

<pre class="highlight">
<code class="language-javascript"> 
{
    //频道名称 _必选_
    "name": "体育新闻",
    //`webpage` 网页, `video` 视频广告, `client` 客户端, `se` 搜索引擎, `email` 邮件, `other` 其他 _可选_ 默认 : webpage
    "type": "webpage",
    //广告位在第几屏幕 _可选_ 默认: 0
    "screen": 3,
    //频道地址 _可选_
    "home": "http://www.admaster.com.cn/",
    //物料类型 _可选_ `flash`，`image`，`video`, `textlink`, `other` 默认：`flash`
    "materia_type": 'flash',
    //物料的显示尺寸 _可选_ 单位像素 格式如 400x300 宽度为400px 高度为300px
    "materia_dimension": "400x300",
    //物料文件大小_可选_ 单位由 materia_size_unit 指定
    "materia_size": 200,
    //物料文件大小单位 _可选_ `B`, `K`, `M` 默认: K
    "materia_size_unit": "K"
}
</code></pre>

rotation
: _可选_ *String* 轮播属性, `1/1` 固定，`1/2` 二分之一轮播，一次类推，默认: `1/1`

target\_url
: _可选_ *Url* 点击目标地址, 默认为空，继承项目的点击目标地址

payment\_type
: _可选_ *Enum* - 支付类型

* `purchase` 购买 _默认值_
* `offering` 配送
* `framework` 框架
* `Compensation` 补偿
* `other` 其他

cost\_type
: _可选_ *Enum* - 单位收费类型

* `day` 天 _默认值_
* `week` 周
* `month` 月
* `cpc` 每次点击成本
* `cpm` 千人展示成本
* `cpa` 每次行动成本
* `article` 文章
* `kmail` 千封邮件
* `other` 其他 

cost\_per\_unit
: _可选_ *Float* - 单位成本

est\_imp\_per\_unit
: _可选_ *Int* - 单位预估曝光数

est\_clk\_per\_unit
: _可选_ *Int* - 单位预估点击

other\_requirement
: _可选_ *String* - 其他要求

###示例

<pre class="highlight">
<code class="language-javascript"> 
{
    "name": "这是一个测试广告位",
    "media_id": 1314,
    "channel": {
      "name": "体育新闻",
      "type": "webpage",
      "screen": 3,
      "home": "http://www.admaster.com.cn/",
      "materia_type": 'flash',
      "materia_dimension": "400x300",
      "materia_size": 200,
      "materia_size_unit": "Byte"
    },
    "rotation" : "1/4",
    "target_url": "http://www.admaster.com.cn/",
    "payment_type": "purchase",
    "cost_type": "day"
    "cost_per_unit": 873.12,
    "est_imp_per_unit": 239,
    "est_clk_per_unit": 3,
    "other_requirement": "没有什么要求",
}
</code></pre>
    
###响应
<pre class="headers">
<code>Status: 201 Created
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
    "id": 1,
    "url": "http://api.trackmaster.com.cn/networks/advertisers/campaigns/placements/1",
    "name": "这是一个测试广告位",
    "media_id": 1314,
    "channel": {
        "id": 1025,
        "name": "体育新闻",
        "type": "webpage",
        "screen": 3,
        "home": "http://www.admaster.com.cn/",
        "materia_type": 'flash',
        "materia_dimension": "400x300",
        "materia_size": 200,
        "materia_size_unit": "Byte"
    },
    "rotation" : "1/4",
    "target_url": "http://www.admaster.com.cn/",
    "payment_type": "purchase",
    "cost_type": "day"
    "cost_per_unit": 873.12,
    "est_imp_per_unit": 239,
    "est_clk_per_unit": 3,
    "units": 58,
    "other_requirement": "没有什么要求",
    "est_imp": 871821,
    "est_clk": 1231,
    "created_at": "2012-09-06T20:39:23Z"
}
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon]

###适用版本

[v1.0][version]

<h2 id="p4">删除指定的广告位</h2>

    DELETE /networks/advertisers/campaigns/placements/:id

###响应
<pre class="headers no-response">
<code>Status: 204 No Content
Location: http://api.trackmaster.com.cn/networks/advertisers/campaigns/:campaign_id/placements
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

<h2 id="p5">修改指定的广告位属性</h2>

    PATCH /networks/advertisers/campaigns/placements/:id

###请求

name
: _可选_ *String* - 广告位位置名称，字符串，长度为 3 - 100个字符

channel
: _可选_ *Object* - 广告位频道信息

###示例
<pre class="highlight">
<code class="language-javascript"> 
{
    //频道名称 _可选_
    "name": "体育新闻",
    //`webpage` 网页, `video` 视频广告, `client` 客户端, `se` 搜索引擎, `email` 邮件, `other` 其他 _可选_ 默认 : webpage
    "type": "webpage",
    //广告位在第几屏幕 _可选_ 默认: 0
    "screen": 3,
    //频道地址 _可选_
    "home": "http://www.admaster.com.cn/",
    //物料类型 _可选_ `flash`，`image`，`video`, `textlink`, `other` 默认：`flash`
    "materia_type": 'flash',
    //物料的显示尺寸 _可选_ 单位像素 格式如 400x300 宽度为400px 高度为300px
    "materia_dimension": "400x300",
    //物料文件大小_可选_ 单位由 materia_size_unit 指定
    "materia_size": 200,
    //物料文件大小单位 _可选_ `B`, `K`, `M` 默认: K
    "materia_size_unit": "K"
}
</code></pre>

rotation
: _可选_ *String* 轮播属性, `1/1` 固定，`1/2` 二分之一轮播，一次类推，默认: `1/1`

target\_url
: _可选_ *Url* 点击目标地址, 默认为空，继承项目的点击目标地址

payment\_type
: _可选_ *Enum* - 支付类型

* `purchase` 购买 _默认_
* `offering` 配送
* `framework` 框架
* `Compensation` 补偿
* `other` 其他 

cost\_type
: _可选_ *Enum* - 单位收费类型 

* `day` 天 _默认_
* `week` 周
* `month` 月
* `cpc` 每次点击成本
* `cpm` 千人展示成本
* `cpa` 每次行动成本
* `article` 文章
* `kmail` 千封邮件
* `other` 其他 

cost\_per\_unit
: _可选_ *Float* - 单位成本

est\_imp\_per\_unit
: _可选_ *Int* - 单位预估曝光数

est\_clk\_per\_unit
: _可选_ *Int* - 单位预估点击

other\_requirement
: _可选_ *String* - 其他要求

###示例    
<pre class="highlight">
<code class="language-javascript">
{
    "name": "这是一个测试广告位",
    "media_id": 1314,
    "channel": {
      "name": "体育新闻",
      "type": "webpage",
      "screen": 3,
      "home": "http://www.admaster.com.cn/",
      "materia_type": 'flash',
      "materia_dimension": "400x300",
      "materia_size": 200,
      "materia_size_unit": "Byte"
    },
    "rotation" : "1/4",
    "target_url": "http://www.admaster.com.cn/",
    "payment_type": "purchase",
    "cost_type": "day"
    "cost_per_unit": 873.12,
    "est_imp_per_unit": 239,
    "est_clk_per_unit": 3,
    "other_requirement": "没有什么要求",
}
</code></pre>

###响应
<pre class="headers no-response">
<code>Status: 204 No Content
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon]

###适用版本

[v1.0][version]

[version]: /trackmaster/v1/apiVersion/
[apiCommon]:/trackmaster/v1/apiCommon/#p5
