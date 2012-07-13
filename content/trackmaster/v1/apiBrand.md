---
title: API - 品牌接口
---

#API - 品牌接口


<h2 id="p1">获取指定网络下指定广告主下的所有品牌</h2>

    GET /networks/:network_id/advertisers/:advertiser_id/brands

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
    "id": 1,
    "name": "巧乐兹",
    "created_at": "2012-09-06T20:39:23Z"
  }
]
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon]  

###适用版本
[v1.0][version]

<h2 id="p2">获取指定 ID 品牌详细信息</h2>

    GET /networks/advertisers/brands/:id

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
    "network_id": 1,
    "advertiser_id": 10231,
    "name": "巧乐兹",
    "url": "http://api.trackmaster.com.cn/networks/advertisers/brands/1",
    "created_at": "2012-09-06T20:39:23Z"
}
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon]  

###适用版本
[v1.0][version]

<h2 id="p3">添加指定品牌到指定网络广告主下</h2>

    POST /networks/:network_id/advertisers/:advertiser_id/brands

###请求
<pre class="highlight">
<code class="language-javascript">	
{
    "name": "巧乐兹"
}
</code></pre>
name
: _必填_ *String* - 品牌名称

###响应
<pre class="headers">
<code>Status: 201 Created 
Location: http://api.trackmaster.com.cn/networks/1/advertisers/10231/brands
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
    "id": 1,
    "network_id": 1,
    "advertiser_id": 10231,
    "name": "巧乐兹",
    "url": "http://api.trackmaster.com.cn/networks/advertisers/brands/1",
    "created_at": "2012-09-06T20:39:23Z"
}
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon]

###适用版本
[v1.0][version]

<h2 id="p4">修改指定的网络广告主下品牌名称</h2>

    PATCH /networks/advertisers/brands/:id

###请求
<pre class="highlight">
<code class="language-javascript">
{
    "name": "巧乐鸡"
}
</code></pre>
name
: _必选_ *String* - 品牌名称


##响应
<pre class="headers no-response">
<code>Status: 204 No Content 
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon]  


###适用版本
[v1.0][version]

<h2 id="p5">删除指定的网络广告主下品牌</h2>

    DELETE /networks/advertisers/brands/:id

###响应
<pre class="headers no-response">
<code>Status: 204 No Content 
Location: http://api.trackmaster.com.cn/networks/1/advertisers/10231/brands
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon]  

###适用版本
[v1.0][version]

[version]: /trackmaster/v1/apiVersion/
[apiCommon]:/trackmaster/v1/apiCommon/#p5
