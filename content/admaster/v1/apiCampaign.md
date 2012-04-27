---
title: API - 项目接口
---

# API - 项目接口

<h2 id="p1">获取指定工作网络下某个广告主有操作权限的项目列表</h2>

    GET /networks/:network/advs/:adv/campaigns

###参数

name
: _可选_ *String* - 项目名称，支持模糊搜索，例如：名称为 “这是一个测试项目” 搜索 “一个”即可找到改项目

brand\_id
: _可选_ *Int* - 项目所属网络品牌ID

status
: _可选_ *Enum* - 项目状态

* `all` - 所有状态, (_默认_)
* `typing` - 拟稿中
* `testing` - 测试中
* `kickoff` - 项目初期
* `midterm` - 项目中期
* `teminal` - 项目末期
* `finished` - 已结束

start\_date
: _可选_ *Date* - 项目开始时间，会列出项目开始日期小于等于此设定的项目

end\_date
: _可选_ *Date* - 项目结束时间，会列出项目结束日期大于等于次设定的项目

sort
: _可选_ *String* - 列表排序以什么排序

* `id` - 按照项目ID排序
* `brand_id` - 按照品牌ID排序
* `name` - 按照项目名称排序
* `total_cost` - 按照总成本排序
* `media_num` - 按照媒体数排序
* `placement_num` - 按照广告位数排序
* `start_date` - 按照开始日期排序
* `end_date` - 按照结束日期排序
* `est_imp` - 按照总预计曝光排序
* `est_clk` - 按照总预计点击排序

direction
: _可选_ *String* - 排序方式

* `asc` 升序 (_默认_)
* `desc` 降序

###响应
<pre class="headers">
<code>Status: 200 OK
Link: <http://api.trackmaster.com.cn/networks/:network/advs/:adv/campaigns?page=2>; rel="next",
      <http://api.trackmaster.com.cn/networks/:network/advs/:adv/campaigns?page=10>; rel="last"
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
[
  {
    "id": 1,
    "url": "http://api.trackmaster.com.cn/networks/advs/campaigns/1",
    "name": "这是一个测试项目",
    "brand_id": 10213,
    "cost_type": "CNY",
    "total_cost": 20000000,
    "start_date": "2012-01-03",
    "end_date": "2012-06-23",
    "default_target": 
    "survey_id": 1024, 
    "media_num": 8,
    "placement_num": 258,
    "est_imp": 9183213,
    "est_clk": 12334,
    "status": "online", 
    "is_online": "yes",
    "created_at": "2012-09-06T20:39:23Z"
  }
]
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon]  

###字段说明

参见页面底部说明


###适用版本
[v1.0][version]


<h2 id="p2">获取指定项目信息</h2>

    GET /networks/advs/campaigns/:id

###响应
<pre class="headers">
<code>Status: 200 OK
Link: <http://api.trackmaster.com.cn/networks/advs/campaigns/1/nwmedias>; rel="nwmedias" 
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
    "id": 1,
    "url": "http://api.trackmaster.com.cn/networks/advs/campaigns/1",
    "name": "这是一个测试项目",
    "brand_id": 10213,
    "cost_type": "CNY",
    "total_cost": 20000000,
    "start_date": "2012-01-03",
    "end_date": "2012-06-23",
    "default_target": 
    "survey_id": 1024, 
    "media_num": 8,     
    "placement_num": 258,
    "target_audience":{
        "age": "19_25",
        "sex": ["2"]
    }, 
    "status": "online", 
    "is_online": "yes",     
    "created_at": "2012-09-06T20:39:23Z"
}
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon] 

###字段说明

参见页面底部说明

###适用版本
[v1.0][version]

<h2 id="p3">添加指定项目到指定广告主下</h2>

    POST /networks/:network/advs/:adv/campaigns

###请求

name
: _必选_ *String* - 项目名称，长度范围 3 - 100 个字符

brand\_id
: _必选_ *Int* - 所属网络品牌ID

start\_date
: _必选_ *Date* - 项目开始日期 YYYY-mm-dd 例如：2012-01-03

end\_date
: _必选_ *Date* - 项目结束日期 YYYY-mm-dd 例如：2012-06-23, 结束日期要大于开始日期

default\_target
: _必选_ *URL* - 项目默认点击目标地址，例如: http://www.admaster.com.cn/

survey\_id
: _可选_ *Int* - 项目关联的 SurveyMaster 系统下的问卷ID, 

cost\_type
: _可选_ *Int* - 媒体预算货币类型 

* `None` 不设置媒体预算 _默认值_
* `CNY` 人民币
* `USD` 美元

target\_audience
: _可选_ *Object* - 目标受众人群

<pre class="highlight">
<code class="language-javascript">
{
    "age": "19_25",//年龄设定，例如: 16_20  16岁到20岁
    "sex": "male"//性别设定，`male` 男, `female` 女
}


{
    "name": "这是一个测试项目",
    "brand_id": 10021,
    "start_date": "2012-01-31",
    "end_date": "2012-04-20",
    "default_target": "http://www.admaster.com.cn/",
    "survey_id": 1002,
    "cost_type": "USD",
    "target_audience": {
        "age": "16_30",
        "sex": "female"
    }
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
    "url": "http://api.trackmaster.com.cn/networks/advs/campaigns/1",
    "name": "这是一个测试项目",
    "brand_id": 10213,
    "cost_type": "CNY",
    "total_cost": 20000000,
    "start_date": "2012-01-03",
    "end_date": "2012-06-23",
    "default_target": 
    "survey_id": 1024, 
    "media_num": 8,     
    "placement_num": 258,
    "target_audience":{
        "age": "19_25",
        "sex": ["2"]
    }, 
    "status": "online", 
    "is_online": "yes",     
    "created_at": "2012-09-06T20:39:23Z"
}
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon] 

###字段说明

参见页面底部说明

###适用版本
[v1.0][version]

<h2 id="p4">删除指定项目</h2>

    DELETE /networks/advs/campaigns/:id

###响应
<pre class="headers no-response">
<code>Status: 204 No Content
Location: http://api.trackmaster.com.cn/networks/:network/advs/:adv/campaigns
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

<h2 id="p5">修改指定项目属性</h2>

    PATCH /networks/advs/campaigns/:id

###请求
name
: _可选_ *String* - 项目名称，长度范围 3 - 100 个字符

brand\_id
: _可选_ *Int* - 所属网络品牌ID

start\_date
: _可选_ *Date* - 项目开始日期 YYYY-mm-dd 例如：2012-01-03

end\_date
: _可选_ *Date* - 项目结束日期 YYYY-mm-dd 例如：2012-06-23, 结束日期要大于开始日期

default\_target
: _可选_ *URL* - 项目默认点击目标地址，例如: http://www.admaster.com.cn/

survey\_id
: _可选_ *Int* - 项目关联的 SurveyMaster 系统下的问卷ID, 

cost\_type
: _可选_ *Int* - 媒体预算货币类型 

* `None` 不设置媒体预算 _默认值_
* `CNY` 人民币
* `USD` 美元

target\_audience
: _可选_ *Object* - 目标受众人群

<pre class="highlight">
<code class="language-javascript">
{
    "age": "19_25",//年龄设定，例如: 16_20  16岁到20岁
    "sex": "male"//性别设定，`male` 男, `female` 女
}


{
    "name": "这是一个测试项目",
    "brand_id": 10021,
    "start_date": "2012-01-31",
    "end_date": "2012-04-20",
    "default_target": "http://www.admaster.com.cn/",
    "survey_id": 1002,
    "cost_type": "USD",
    "target_audience": {
        "age": "16_30",
        "sex": "female"
    }
}
</code></pre>

###响应
<pre class="headers no-response">
<code>Status: 204 No Content 
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

###适用版本
[v1.0][version]

##字段说明
<table cellspacing="0" cellpadding="6" border="1">
  <tr>
    <td> 返回值字段 </td>
    <td> 字段类型 </td>
    <td> 字段说明 </td>
  </tr>
  <tr>
    <td>id</td>
    <td>int</td>
    <td>项目 ID</td>
  </tr>
  <tr>
    <td>url</td>
    <td>string</td>
    <td> 请求URL</td>
  </tr>
  <tr>
    <td>name</td>
    <td>string</td>
    <td>项目名称</td>
  </tr>
  <tr>
    <td>brand_id</td>
    <td>int</td>
    <td>项目所属网络品牌 ID</td>
  </tr>
  <tr>
    <td>cost_type</td>
    <td>string</td>
    <td>币种</td>
  </tr>
  <tr>
    <td>total_cost</td>
    <td>int</td>
    <td>总花费</td>
  </tr>
  <tr>
    <td>start_date</td>
    <td>data</td>
    <td>开始日期</td>
  </tr>
  <tr>
    <td>end_date</td>
    <td>date</td>
    <td>结束日期</td>
  </tr>
 <tr>
    <td>default_target</td>
    <td>date</td>
    <td>默认目标</td>
  </tr>
 <tr>
    <td>survey_id</td>
    <td>int</td>
    <td>结束日期</td>
  </tr>
 <tr>
    <td>media_num</td>
    <td>int</td>
    <td>媒体数量</td>
  </tr>
  <tr>
    <td>placement_num</td>
    <td>int</td>
    <td>广告位数量</td>
  </tr>
  <tr>
    <td>status</td>
    <td>String</td>
    <td>状态</td>
  </tr>
  <tr>
    <td>is_online</td>
    <td>String</td>
    <td>是否在线</td>
  </tr>
  <tr>
    <td>created_at</td>
    <td>date</td>
    <td>创建时间</td>
  </tr>
</table>

[返回列表][apiMain]

[apiMain]: apiMain
[version]: apiVersion
[apiCommon]:apiCommon
