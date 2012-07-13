---
title: API - 广告主
---

#API - 广告主


<h2 id="p1">获取系统广告主列表</h2>

    GET /advertisers

###参数

sort
: _可选_ *String* - 列表排序以什么排序

* `id` - 按照广告主ID排序
* `name` - 按照广告主名称排序
* `create_time` - 按照创建日期排序

direction
: _可选_ *String* - 排序方式

* `asc` 升序 (_默认_)
* `desc` 降序

page
: _可选_ *Int* - 显示页码

per_page
: _可选_ *Int* - 分页数量，默认每页30条

###响应
<pre class="headers">
<code>Status: 200 OK
Link: <http://api.trackmaster.com.cn/advertisers?page=2>; rel="next",
      <http://api.trackmaster.com.cn/advertisers?page=10>; rel="last"
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
[
  {
    "id": 1,
    "url": "http://api.trackmaster.com.cn/advertisers/1",
    "name": {"zh_cn" => "腾讯", "en_us" => "tencent"},   //广告主名称
    "logo": "http://www.trackmaster.com.cn/data/advIcon/1.jpg",  //Logo URL
    "created_at": "2012-09-06T20:39:23Z"  //创建时间
  }
]
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon]。  


###适用版本

[v1.0][version]

<h2 id="p2">获取指定系统广告主信息</h2>

    GET /advertisers/:id

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
    "url": "http://api.trackmaster.com.cn/advertisers/1",
    "name": {"zh_cn" => "腾讯", "en_us" => "tencent"},   //广告主名称
    "logo": "http://www.trackmaster.com.cn/data/advIcon/1.jpg",  //Logo URL
    "created_at": "2012-09-06T20:39:23Z"  //创建时间
}
</code></pre>
关于错误返回值与错误代码，参见[错误代码说明][apiCommon]。  

###适用版本

[v1.0][version]

<h2 id="p3">获取指定工作网络下所有广告主属性列表</h2>

    GET /networks/:network_id/advertisers/attributes

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
    "advertiser_id": 1,
    "url": "http://api.trackmaster.com.cn/networks/1/advertisers/1",
    "name": {"zh_cn" => "腾讯", "en_us" => "tencent"},   //广告主名称
    "status": "enabled",
    "alias": "ibm",
    "logo": "http://www.trackmaster.com.cn/data/advIcon/1.jpg",  //Logo URL
    "created_at": "2012-09-06T20:39:23Z"  //创建时间
  }
]
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon]。

###适用版本

[v1.0][version]

<h2 id="p4">获取指定网络下的指定广告主属性</h2>

    GET /networks/:network_id/advertisers/:advertiser_id/attributes

###响应
<pre class="headers">
<code>Status: 200 OK
Link: <http://api.trackmaster.com.cn/networks/1/advertisers/1/campaigns>; rel="campaigns"
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
    "advertiser_id": 1,
    "url": "http://api.trackmaster.com.cn/networks/1/advertisers/1",
    "name": {"zh_cn" => "通用电器", "en_us" => "GM"},   //广告主名称
    "status": "enabled"
    "alias": "通用电器",
    "logo": "http://www.trackmaster.com.cn/data/advIcon/1.jpg",  //Logo URL
    "created_at": "2012-09-06T20:39:23Z" //创建时间
}
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon]。

###适用版本

[v1.0][version]

<h2 id="p5">判断指定网络下是否有指定广告主</h2>

    GET /networks/:network_id/advertisers/:advertiser_id

###指定广告主在指定网络下
<pre class="headers no-response">
<code>Status: 204 No Content
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

###指定广告主不在指定网络下
<pre class="headers no-response">
<code>Status: 404 Not Found
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

###适用版本
[v1.0][version]

<h2 id="p6">添加指定系统广告主到指定工作网络下</h2>

    PUT /networks/:network_id/advertisers/:advertiser_id

###响应
<pre class="headers no-response">
<code>Status: 204 No Content 
Link: <http://api.trackmaster.com.cn/networks/1/advertisers/1/campaigns>; rel="campaigns"
Location: http://api.trackmaster.com.cn/networks/1/advertisers/1/attributes
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

###适用版本

[v1.0][version]


<h2 id="p7">修改指定网络下的指定广告主属性</h2>

    PATCH /networks/:network_id/advertisers/:advertiser_id/attributes

###请求
<pre class="highlight">
<code class="language-javascript">	
{
    "alias": "通用电器",
    "status": "enabled"
}
</code></pre>
alias
: _可选_ **String** - 别名

status
: _可选_ `enabled`, `disabled`

###响应
<pre class="headers">
<code>Status: 200 OK
Link: <http://api.trackmaster.com.cn/networks/1/advertisers/1/campaigns>; rel="campaigns"
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
    "advertiser_id": 1,
    "url": "http://api.trackmaster.com.cn/networks/1/advertisers/1",
    "name": {"zh_cn" => "通用电器", "en_us" => "GM"},   //广告主名称
    "status": "enabled"
    "alias": "通用电器",
    "logo": "http://www.trackmaster.com.cn/data/advIcon/1.jpg",  //Logo URL
    "created_at": "2012-09-06T20:39:23Z" //创建时间
}
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon]。

###适用版本

[v1.0][version]

<h2 id="p8">删除指定工作网络下的指定广告主</h2>

    DELETE /networks/:network_id/advertisers/:advertiser_id

###响应
<pre class="headers no-response">
<code>Status: 204 No Content 
Link: <http://api.trackmaster.com.cn/networks/1/advertisers>; rel="campaigns"
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

###适用版本

[v1.0][version]


[version]: /trackmaster/v1/apiVersion/
[apiCommon]:/trackmaster/v1/apiCommon/#p5
