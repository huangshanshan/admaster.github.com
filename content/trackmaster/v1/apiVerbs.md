---
title: API - 协议及请求方式
---

#API - AdMAster API


本文讲述了组成官方 AdMaster API 的资源信息。本API处于测试状态。可能会有一些重大更改。

- <a href="#p1">架构</a>
- <a href="#p2">客户端错误</a>
- <a href="#p3">HTTP谓词</a>
- <a href="#p4">认证</a>
- <a href="#p5">分页</a>
- <a href="#p6">速度限制</a>
- <a href="#p7">交叉资源共享</a>
- <a href="#p8">JSON-P回调</a>

<h2 id="p1"> 架构 </h2>

所有API的访问都是通过 HTTP 执行的，而且访问都是来自`api.admaster.com.cn`域名。所有被发送和接受的的数据都是 JSON。

<pre class="terminal">
$ curl -i https://api.admaster.com.cn
HTTP/1.1 302 Found
Server: nginx/1.0.12
Date: Mon, 20 Feb 2012 11:15:49 GMT
Content-Type: text/html;charset=utf-8
Connection: keep-alive
Status: 302 Found
X-RateLimit-Limit: 5000
ETag: "d41d8cd98f00b204e9800998ecf8427e"
Location: http://developer.admaster.com.cn
X-RateLimit-Remaining: 4999
Content-Length: 0
</pre>

空白区域作为null而不是被忽略。

所有的时间戳返回格式是ISO 8601：`YYYY-MM-DDTHH:MM:SSZ`

<h2 id="p2">  客户端错误 </h2>

调用API客户端的错误有三种可能类型，它们收到的请求主体是：

1.发送无效 JSON将导致400个错误请求响应。

<pre><code>HTTP/1.1 400 Bad Request
 Content-Length: 35

 {"message":"Problems parsing JSON"}
</code></pre>


2.发送错误类型的JSON值将导致400错误请求响应

<pre><code>HTTP/1.1 400 Bad Request
Content-Length: 40

{"message":"Body should be a JSON Hash"}
</code></pre>

3.发送无效文件将导致422无法处理的实体响应。
<pre><code>HTTP/1.1 422 Unprocessable Entity
 Content-Length: 149

 {
   "message": "Validation Failed",
   "errors": [
     {
       "resource": "Issue",
       "field": "title",
       "code": "missing_field"
     }
   ]
 }
</code></pre>
所有的错误对象都有资源和字段属性，您的客户端可以说明问题所在。还有一个错误代码让您知道什么是错误区域，下面这些都是可能的验证错误代码：

**missing**

这意味着资源不存在。

**missing_field**

这意味着对资源所需的领域尚未确定。

**invalid**


这意味着领域格式不合法。资源文档应该给您提供更专业的信息。

**already_exists**

这意味着已经存在和该领域同样值的资源了。这就要求要有独立的key（如：标签名称）

如果资源有自定义的验证错误，他们将用资源来记录。

<h2 id="p3">  HTTP 谓词 </h2>

对于每一个动作，API v3尽可能的驱使您使用 HTTP 谓词。

**HEAD**

只获取HTTP的头信息，不管其他资源信息

**GET**

用于检索资源

**POST**

用于创建资源、执行自定义动作（如合并，推送）

**PATCH**

利用部分 JSON 数据更新资源，例如，一个资源有title和body属性。一个PATCH需求可能是通过接收一个或多个属性进行资源更新。PATCH是一个相对较新的和不常见的HTTP谓词，所以资源端点也接收POST需求。

**PUT**

用于收集或代替资源。PUT需求没有 body 属性，所以要确定设置内容长度为0.

**DELETE**

用于删除资源。

<h2 id="p4"> 认证 </h2>


OAuth2 Token (头部发送):

<pre class="terminal">
$ curl -H "Authorization: token OAUTH-TOKEN" https://api.admaster.com.cn
</pre>

OAuth2 Token (作为参数发送):

<pre class="terminal">$ curl https://api.admaster.com.cn?access_token=OAUTH-TOKEN
</pre>

在某些地方，对认证的需求将返回 404，而不是403。这是为了防止意外泄漏给未经授权的用户的私人资料。

<h2 id="p5"> 分页 </h2>

默认情况下，多项目请求将会被分页成30项。您可以利用参数`?page`指定进一步页，您也可以利用参数`?per_page`自定义页大小到100.


<pre class="terminal">$ curl https://api.admaster.com.cn/repos?page=2&amp;per_page=100
</pre>

分页信息包含在 the link header：


<pre><code>Link: &lt;https://api.github.com/repos?page=3&amp;per_page=100&gt;; rel="next",
https://api.github.com/repos?page=50&amp;per_page=100&gt;; rel="last"
</code></pre>

包括换行以提高可读性。


`rel`的可能值有：

`next`

立即显示下页结果的URL。

`last`

显示上页结果的URL。

`first`

显示第一页结果的URL。

`prev`

立即显示前页结果的URL。


<h2 id="p6"> 速度限制 </h2>

我们以每小时5000限制的API v3的要求。这是键入了您的登录，您的OAuth的令牌，或请求的IP。您可以检查返回的API请求的HTTP头，查看您当前的状态：

<pre class="terminal">
$ curl -i https://api.admaster.com.cn/users/whatever

HTTP/1.1 200 OK
Status: 200 OK
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4966
</pre>

你可以联系我们要求进行您应用程序白名单访问，我们更喜欢为用户设置OAuth 应用。

<h2 id="p7"> 交叉资源共享 </h2>

对于AJAX需求的，API支持交叉资源共享。你可以从HTML5安全指南中阅读CORS W3C working draft, 或者 this intro。


下面是一个发自浏览器的示例需求`http://some-site.com`：

<pre><code>$ curl -i https://api.admaster.com.cn -H "Origin: http://some-site.com" 
HTTP/1.1 302 Found
</code></pre>
任何一个被接受的域名都是作为OAUTH应用程序注册的。下面是一个示例需求，用于浏览器触及 Calendar About Nothing:


<pre><code>$ curl -i https://api.admaster.com.cn -H "Origin: http://calendaraboutnothing.com" 
HTTP/1.1 302 Found
Access-Control-Allow-Origin: http://calendaraboutnothing.com
Access-Control-Expose-Headers: Link, X-RateLimit-Limit, X-RateLimit-Remaining, X-OAuth-Scopes, X-Accepted-OAuth-Scopes
Access-Control-Allow-Credentials: true
</code></pre>


下面是CORS系统预检请求看起来的样子：


<pre><code>$ curl -i https://api.admaster.com.cn -H "Origin: http://calendaraboutnothing.com" -X OPTIONS   
HTTP/1.1 204 No Content
Access-Control-Allow-Origin: http://calendaraboutnothing.com
Access-Control-Allow-Headers: Authorization, X-Requested-With
Access-Control-Allow-Methods: GET, POST, PATCH, PUT, DELETE
Access-Control-Expose-Headers: Link, X-RateLimit-Limit, X-RateLimit-Remaining, X-OAuth-Scopes, X-Accepted-OAuth-Scopes
Access-Control-Max-Age: 86400
Access-Control-Allow-Credentials: true
</code></pre>


<h2 id="p8"> JSON-P回调 </h2>

你可以发送参数`?callback`到任何GET回调函数以获得JSON函数的结果包裹。浏览器通过跨域方式利用网页嵌入AdMaster 内容就是一种典型的应用。
响应包括定期API相同的数据输出，加上相关的HTTP头信息。

<pre class="terminal">$ curl https://api.admaster.com.cn?callback=foo

foo({
  "meta": {
    "status": 200,
    "X-RateLimit-Limit": "5000",
    "X-RateLimit-Remaining": "4966",
    "Link": [ // pagination headers and other links
      ["https://api.admaster.com.cn?page=2", {"rel": "next"}]
    ]
  },
  "data": {
    // the data
  }
})
</pre>

你可以写一个javascript处理程序来处理这样的回调：


<pre class="terminal">$ curl https://api.admaster.com.cn?callback=foo

foo({
  "meta": {
    "status": 200,
    "X-RateLimit-Limit": "5000",
    "X-RateLimit-Remaining": "4966",
    "Link": [ // pagination headers and other links
      ["https://api.admaster.com.cn?page=2", {"rel": "next"}]
    ]
  },
  "data": {
    // the data
  }
})
</pre>


头都是相同的字符串值作为HTTP头，有一个例外：link。通过数组`[url, options]`阵列，link头部预先为您解析。

所谓的link，如下：

<pre><code>Link: &lt;url1&gt;; rel="next", &lt;url2&gt;; rel="foo"; bar="baz"
</code></pre>


...在回调输出中是这样的：

<pre class="highlight"><code class="language-javascript"><span class="p">{</span>
  <span class="s2">"Link"</span><span class="o">:</span> <span class="p">[</span>
    <span class="p">[</span>
      <span class="s2">"url1"</span><span class="p">,</span>
      <span class="p">{</span>
        <span class="s2">"rel"</span><span class="o">:</span> <span class="s2">"next"</span>
      <span class="p">}</span>
    <span class="p">],</span>
    <span class="p">[</span>
      <span class="s2">"url2"</span><span class="p">,</span>
      <span class="p">{</span>
        <span class="s2">"rel"</span><span class="o">:</span> <span class="s2">"foo"</span><span class="p">,</span>
        <span class="s2">"bar"</span><span class="o">:</span> <span class="s2">"baz"</span>
      <span class="p">}</span>
    <span class="p">]</span>
  <span class="p">]</span>
<span class="p">}</span>
</code></pre>
