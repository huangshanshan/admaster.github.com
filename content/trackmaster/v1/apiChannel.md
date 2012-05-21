---
title: API - 频道接口
---

#API - 媒体接口


<h2 id="p1">获取指定媒体频道列表</h2>

    GET /media/:id/channels

###响应
<pre class="headers">
<code>Status: 200 OK
Link: <http://api.trackmaster.com.cn/channels?page=2>; rel="next",
      <http://api.trackmaster.com.cn/channels?page=10>; rel="last"
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
[
   {
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
]
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon]  

###适用版本
[v1.0][version]

<h2 id="p2">获取指定频道详细信息</h2>

    GET /media/channel/:id

###响应
<pre class="headers">
<code>Status: 200 OK
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
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
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon]

###适用版本
[v1.0][version]

<h2 id="p3">为指定媒体新增频道</h2>

    GET /networks/:network/medias

###响应
<pre class="headers">
<code>Status: 200 OK
Link: <http://api.trackmaster.com.cn/networks/:network/medias?page=2>; rel="next",
      <http://api.trackmaster.com.cn/networks/:network/medias?page=10>; rel="last"
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

[version]: /trackmaster/v1/apiVersion/
[apiCommon]:/trackmaster/v1/apiCommon/#p5
