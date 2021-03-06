---
title: API - 媒体报告
---
#API - 媒体报告

<h2 id="p1">获取指定媒体下的项目</h2>

    GET /medias/:media_id/campaigns

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
    "start_date": "2012-01-03",
    "end_date": "2012-06-23",
    "created_at": "2012-09-06T20:39:23Z"
  }
]
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon]。


###适用版本
[v1.0][version]


<h2 id="p2">获取指定项目下的日报告</h2>

    GET /medias/:media_id/campaigns/:campaign_id/daily_reports

###参数

start\_time
: _可选_ *Date* - 项目开始日期，例如2012-08-01，会列出项目开始日期大于等于此设定的项目

end\_time
: _可选_ *Date* - 项目结束日期，例如2012-08-02，会列出项目结束日期小于等于此设定的项目

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

<h2 id="p1">获取指定监测代码下的项目日报告</h2>

    GET /medias/campaigns/daily_reports/codes

###参数

code
: _必选_ *string* - 项目监测代码

###响应
<pre class="headers no-response">
<code>Status: 204 No Content
Link: <http://api.trackmaster.com.cn/medias/1308/campaigns/10256/daily_reports>; rel="campaigns"
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

###适用版本
[v1.0][version]

[version]: /trackmaster/v1/apiVersion/
[apiCommon]:/trackmaster/v1/apiCommon/#p5
