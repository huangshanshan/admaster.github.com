---
title: API - 创意接口
---

#API - 创意接口

<h2 id="p1">获取指定项目所有创意</h2>

    GET /networks/advertisers/campaigns/:campaign_id/creatives

###响应

<pre class="headers">
<code>Status: 200 OK
Link: <http://api.trackmaster.com.cn/networks/advertisers/campaigns/123/creatives?page=2>; rel="next",
      <http://api.trackmaster.com.cn/networks/advertisers/campaigns/123/creatives?page=10>; rel="last"
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
[
  {
    //创意ID，全局唯一
    "id": 1,
    //获取详情接口地址
    "url": "http://api.trackmaster.com.cn/networks/advertisers/campaigns/creatives/1",
    //创意名称
    "name": "这是一个很不错的创意",
    //创意名缩写
    "shortname": "GO",
    //创意描述
    "description": "这个很不错的创意受到了全国人民的一致认可",
    //创意颜色标识
    "color": "#ff00ff",
    //创意附属文件
    "file": {
        "id": 293,
        "name": "创意.jpg",
        "type": "jpg",
        "access_url": "http://www.trackmaster.com.cn/data/upload/2011/0608/0/1_3a35e4a11b.jpg",
        "width": 400,
        "height": 300
    },
    //创意点击目标地址
    "target_url": "http://www.admaster.com.cn/",
    //创建时间
    "created_at": "2012-09-06T20:39:23Z"
  }
]
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon]  

###适用版本

[v1.0][version]

<h2 id="p2">获取项目下指定创意信息</h2>

    GET /networks/advertisers/campaigns/creatives/:id

###响应

<pre class="headers">
<code>Status: 200 OK
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
    //创意ID，全局唯一
    "id": 1,
    //获取详情接口地址
    "url": "http://api.trackmaster.com.cn/networks/advertisers/campaigns/creatives/1",
    //创意名称
    "name": "这是一个很不错的创意",
    //创意名缩写
    "shortname": "GO",
    //创意描述
    "description": "这个很不错的创意受到了全国人民的一致认可",
    //创意颜色标识
    "color": "#ff00ff",
    //创意附属文件
    "file": {
        "id": 293,
        "name": "创意.jpg",
        "type": "jpg",
        "access_url": "http://www.trackmaster.com.cn/data/upload/2011/0608/0/1_3a35e4a11b.jpg",
        "width": 400,
        "height": 300
    },
    //创意点击目标地址
    "target_url": "http://www.admaster.com.cn/",
    //创建时间
    "created_at": "2012-09-06T20:39:23Z"
}
</code></pre>
关于错误返回值与错误代码，参见[错误代码说明][apiCommon]  

###适用版本

[v1.0][version]

<h2 id="p3">在指定项目下添加创意</h2>

    POST /networks/advertisers/campaigns/:campaign_id/creatives

###参数

name
: _必选_ *String* - 创意名称 长度为 3 - 100个字符
    //创意名缩写

shortname
: _必选_ *String* - 创意短名称 长度为2个字节，字母数字类型

color
: _必选_ *String* - 创意颜色 标准颜色代码 例如：\#ff00ff

description
: _可选_ *String* - 创意描述 最大长度为 1000个字符

file
: _可选_ *Object* - 创意物料

<pre class="highlight">
<code class="language-javascript">
{
    "name": "创意.jpg",//物料名称
    "type": "jpg"//物料类型
    "access_url": "http://www.trackmaster.com.cn/data/upload/2011/0608/0/1_3a35e4a11b.jpg",//物料地址
    "width": 400
    "height": 300
}
</code></pre>

target\_url
: _可选_ *Url* - 创意点击目标地址

###请求

<pre class="highlight">
<code class="language-javascript">
{
    "name": "这是一个很不错的创意",
    "shortname": "GO",
    "description": "这个很不错的创意受到了全国人民的一致认可",
    "color": "#ff00ff",
    "file": {
        "name": "创意.jpg",//物料名称
        "type": "jpg"//物料类型
        "access_url": "http://www.trackmaster.com.cn/data/upload/2011/0608/0/1_3a35e4a11b.jpg",//物料地址
        "width": 400
        "height": 300
    }
    "target_url": "http://www.admaster.com.cn/",
}
</code></pre>

###响应

<pre class="headers">
<code>Status: 201 Created
Location: http://api.trackmaster.com.cn/networks/advertisers/campaigns/creatives/1
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
    //创意ID，全局唯一
    "id": 1,
    //获取详情接口地址
    "url": "http://api.trackmaster.com.cn/networks/advertisers/campaigns/creatives/1",
    //创意名称
    "name": "这是一个很不错的创意",
    //创意名缩写
    "shortname": "GO",
    //创意描述
    "description": "这个很不错的创意受到了全国人民的一致认可",
    //创意颜色标识
    "color": "#ff00ff",
    "file": {
        "id": 293,
        "name": "创意.jpg",
        "type": "jpg",
        "access_url": "http://www.trackmaster.com.cn/data/upload/2011/0608/0/1_3a35e4a11b.jpg",
        "width": 400,
        "height": 300
    },
    //创意点击目标地址
    "target_url": "http://www.admaster.com.cn/",
    //创建时间
    "created_at": "2012-09-06T20:39:23Z"
}
</code></pre>
关于错误返回值与错误代码，参见[错误代码说明][apiCommon]  

###适用版本

[v1.0][version]

<h2 id="p4">删除指定的创意</h2>

    DELETE /networks/advertisers/campaigns/creatives/:id

###响应
<pre class="headers no-response">
<code>Status: 204 No Content
Location: http://api.trackmaster.com.cn/networks/advertisers/campaigns/123/creatives
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

<h2 id="p5">修改指定的创意属性</h2>

    PATCH /networks/advertisers/campaigns/creatives/:id

###参数

name
: _必选_ *String* - 创意名称 长度为 3 - 100个字符
    //创意名缩写

shortname
: _必选_ *String* - 创意短名称 长度为2个字节，字母数字类型

color
: _可选_ *String* - 创意颜色 标准颜色代码 例如：\#ff00ff

description
: _可选_ *String* - 创意描述 最大长度为 1000个字符

file
: _可选_ *Object* - 创意物料

<pre class="highlight">
<code class="language-javascript">
{
    "name": "创意.jpg",//物料名称
    "type": "jpg"//物料类型
    "access_url": "http://www.trackmaster.com.cn/data/upload/2011/0608/0/1_3a35e4a11b.jpg",//物料地址
    "width": 400
    "height": 300
}
</code></pre>

target\_url
: _可选_ *Url* - 创意点击目标地址

###请求

<pre class="highlight">
<code class="language-javascript">
{
    "name": "这是一个很不错的创意",
    "shortname": "GO",
    "description": "这个很不错的创意受到了全国人民的一致认可",
    "color": "#ff00ff",
    "target_url": "http://www.admaster.com.cn/",
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


[version]: /trackmaster/v1/apiVersion/
[apiCommon]:/trackmaster/v1/apiCommon/#p5
