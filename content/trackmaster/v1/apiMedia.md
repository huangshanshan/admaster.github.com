---
title: API - 媒体接口
---

#API - 媒体接口


<h2 id="p1">获取系统媒体库列表</h2>

    GET /medias

###响应
<pre class="headers">
<code>Status: 200 OK
Link: <http://api.trackmaster.com.cn/medias?page=2>; rel="next",
      <http://api.trackmaster.com.cn/medias?page=10>; rel="last"
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
[
  {
    "id": 1,
    "url": "http://api.trackmaster.com.cn/medias/1",
    "name": "新浪",
    "logo": "http://www.trackmaster.com.cn/data/mediaIcon/1.ico",
    "domain": "sina.com.cn",
    "tag": "综合其他",
    "created_at": "2012-09-06T20:39:23Z"
  }
]
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon]  

###适用版本
[v1.0][version]

<h2 id="p2">获取指定系统媒体详细信息</h2>

    GET /medias/:id

###响应
<pre class="headers">
<code>Status: 200 OK
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
    "id": 1,
    "url": "http://api.trackmaster.com.cn/medias/1",
    "name": "新浪",
    "logo": "http://www.trackmaster.com.cn/data/mediaIcon/1.ico",
    "domain": "sina.com.cn",
    "tag": "综合其他",
    "created_at": "2012-09-06T20:39:23Z"
}
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon]

###适用版本
[v1.0][version]

<h2 id="p12">媒体用户获取iab数据</h2>

    GET /medias/:id/ies

###响应
<pre class="headers">
<code>Status: 200 OK
Link: <http://api.trackmaster.com.cn/medias/:id/ies?page=2>; rel="next",
      <http://api.trackmaster.com.cn/medias/:id/ies?page=10>; rel="last"
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

###参数

pubid
: _可选_ *String* - pubid 指定后只获取该pubid的数据

date
: _可选_ *Date* - 日期，要查看的数据日期，YYYY-mm-dd 例如: 2012-06-08 ,不指定则获取头一天的数据


<pre class="highlight">
<code class="language-javascript">
[
  {
    "date_hour": 2012061015,
    "pubid": "IYK_IMloxnwepMEqlx",
    "city": "北京",
    "geoid": 110000,
    "impression": 12039423,
    "click": 43432,
  }
]
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon]

###适用版本
[v1.0][version]


<h2 id="p3">获取指定工作网络下媒体库列表</h2>

    GET /networks/:network_id/medias

###响应
<pre class="headers">
<code>Status: 200 OK
Link: <http://api.trackmaster.com.cn/networks/:network_id/medias?page=2>; rel="next",
      <http://api.trackmaster.com.cn/networks/:network_id/medias?page=10>; rel="last"
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
[
  {
    "id": 1,
    "url": "http://api.trackmaster.com.cn/networks/medias/1",
    "name": "新浪",
    "logo": "http://www.trackmaster.com.cn/data/mediaIcon/1.ico",
    "domain": "sina.com.cn",
    "tag": "综合其他",
    "created_at": "2012-09-06T20:39:23Z"
  }
]
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon]

###适用版本
[v1.0][version]

<h2 id="p4">获取指定工作网络下指定媒体信息</h2>

    GET /networks/medias/:id

###响应

<pre class="headers">
<code>Status: 200 OK
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
    "id": 1,
    "url": "http://api.trackmaster.com.cn/networks/medias/1",
    "name": "新浪",
    "logo": "http://www.trackmaster.com.cn/data/mediaIcon/1.ico",
    "domain": "sina.com.cn",
    "tag": "综合其他",
    "created_at": "2012-09-06T20:39:23Z"
}
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon]

###适用版本
[v1.0][version]

<h2 id="p5">给指定工作网络添加一个媒体</h2>

    POST /networks/:network_id/medias

###请求
<pre class="highlight">
<code class="language-javascript">
{
    'media_id': 8982
}
</code></pre>

media_id: _必选_ *Int* - 系统媒体ID

###响应
<pre class="headers">
<code>Status: 201 Created 
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="language-javascript">
<code>
{
    "id": 1,
    "url": "http://api.trackmaster.com.cn/networks/medias/1",
    "name": "新浪",
    "logo": "http://www.trackmaster.com.cn/data/mediaIcon/1.ico",
    "domain": "sina.com.cn",
    "tag": "综合其他",
    "created_at": "2012-09-06T20:39:23Z"
}
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon]

###适用版本
[v1.0][version]

<h2 id="p6">删除指定工作网络下的媒体</h2>

    DELETE /networks/medias/:id

###响应
<pre class="headers no-response">
<code>
Status: 204 No Content 
Location: http://api.trackmaster.com.cn/networks/:network_id/medias
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

###适用版本

[v1.0][version]

<h2 id="p7">修改指定工作网络下指定媒体属性</h2>

    PATCH /networks/medias/:id

###请求
<pre class="highlight">
<code class="language-javascript">
{
    "name": "新浪财经",
    "framework": "no",
    "status": "enabled"
}
</code></pre>

name
: _可选_ *String* - 网络媒体名称

framework
: _可选_ *Enum* - 是否有框架 `yes`, `no`

status
: _可选_ *Enum* - 状态 `enabled`, `disabled`


###响应
<pre class="headers no-response">
<code>Status: 204 No Content 
Location: http://api.trackmaster.com.cn/networks/medias/1
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

###适用版本
[v1.0][version]


<h2 id="p8">获取指定项目下已添加的媒体</h2>

    GET /networks/advertisers/campaigns/:campaign_id/networks/medias

###响应
<pre class="headers">
<code>Status: 200 OK
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
[
  {
    "id": 1314,
    "url": "http://api.trackmaster.com.cn/networks/advertisers/campaigns/10092/medias/1314",
    "name": "新浪",
    "logo": "http://www.trackmaster.com.cn/data/mediaIcon/1.ico",
    "created_at": "2012-09-06T20:39:23Z"
  }
]
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon] 

###适用版本
[v1.0][version]

<h2 id="p9">获取指定项目下指定媒体详细信息</h2>

    GET /networks/advertisers/campaigns/:campaign_id/medias/:id

###响应
<pre class="headers">
<code>Status: 200 OK
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
    "id": 1314,
    "url": "http://api.trackmaster.com.cn/networks/advertisers/campaigns/10092/medias/1314",
    "name": "新浪",
    "logo": "http://www.trackmaster.com.cn/data/mediaIcon/1.ico",
    "created_at": "2012-09-06T20:39:23Z"
}
</code></pre>
关于错误返回值与错误代码，参见[错误代码说明][apiCommon] 

<h2 id="p10">为指定项目添加指定媒体</h2>

    PUT /networks/advertisers/campaigns/:campaign_id/medias/:id

###响应
<pre class="headers no-response">
<code>Status: 204 No Content
Location: http://api.trackmaster.com.cn/networks/advertisers/campaigns/:campaign_id/medias
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

###适用版本
[v1.0][version]

<h2 id="p11">删除指定项目下指定的媒体</h2>

    DELETE /networks/advertisers/campaigns/:campaign_id/medias/:id

###响应
<pre class="headers no-response">
<code>Status: 204 No Content
Location: http://api.trackmaster.com.cn/networks/advertisers/campaigns/:campaign_id/medias
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

###适用版本
[v1.0][version]


[version]: /trackmaster/v1/apiVersion/
[apiCommon]:/trackmaster/v1/apiCommon/#p5
