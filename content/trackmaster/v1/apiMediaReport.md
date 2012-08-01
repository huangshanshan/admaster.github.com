---
title: API - 媒体报告
---
#API - 媒体报告

<h2 id="p1">获取当前授权用户有权操作的所有媒体项目</h2>

    GET /user/medias/campaigns

###响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">
[
  {
    "id": 1,
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
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon]。


###适用版本
[v1.0][version]


<h2 id="p2">获取指定项目日报告</h2>

    GET /medias/campaigns/:campaign_id/daily_reports

###参数

start\_time
: _可选_ *Hour* - 项目开始时间，会列出项目开始日期大于等于此设定的项目

end\_time
: _可选_ *Hour* - 项目结束时间，会列出项目结束日期小于等于此设定的项目

sort
: _可选_ *String* - 列表排序以什么排序

* `time` - 按照时间排序
* `imp` - 按照曝光排序
* `clk` - 按照点击排序
* `uimp` - 按照独立曝光排序
* `uclk` - 按照独立点击排序

direction
: _可选_ *String* - 排序方式

* `asc` 升序 (_默认_)
* `desc` 降序

###响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">
[
  {
    "time": "2012-08-01", // 时间
    "imp": 23, //曝光
    "uimp": 20, //独立曝光
    "clk": 20, //点击
    "uclk": 10, //独立点击
  }
]
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon]。


###适用版本

[v1.0][version]


[version]: /trackmaster/v1/apiVersion/
[apiCommon]:/trackmaster/v1/apiCommon/#p5
