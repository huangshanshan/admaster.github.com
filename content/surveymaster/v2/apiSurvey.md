---
title: SurveyMaster API - 问卷相关
---

#API - 问卷相关(共5个)

<h2 id="p1">1. 获取当前登录用户的问卷列表</h2>

    GET /users/surveys

###参数

fields
: _可选_ *String* - 字段列表

sort
: _可选_ *String* - 指定排序方式

* `id` - 按问卷ID排序
* `created_at` - 建立时间
* `modified_at` - 最后更新时间
* `landing_count` - 查看问卷用户数
* `answered_count` - 回答问卷用户数
* `finished_count` - 完整回答问卷用户数

direction
: _可选_ *String* - 排序方式

* `asc` 升序
* `desc` 降序 (_默认_)

start\_time/end\_time
: _可选_ *Int* - 指定提取问卷列表（created\_at）的开始及结束时间，不指定start\_at，则不限定开始时间，不指定end\_at，则不限定结束时间

per\_page
: _可选_ *Int* - 每页显示记录数，默认30

* `5`
* `10`
* `20`
* `30` - 默认
* `50`

page
: _可选_ *Int* - 页数，从1开始

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
    "id" : 112,
    "url" : "http://api.surveymaster.com/users/surveys/112",
    "title" : "伊利8月新生活",
    "label" : "第一波",
    "owner" : 123,
    "created_at" : "2012-07-31T09:36:27Z",
    "landing_count" : 50000,
    "answered_count" : 30000,
    "finished_count" : 5000,
    "head" : "首先感谢您参与我们的问卷调查。完成调查的每位用户均有机会参与抽奖,本次调查设置的奖项是：国际知名品牌提供的运动服及运动鞋。请根据您的实际情况逐项填写,您的意见或建议对我们很重要,完成问卷只需花费您短短五分钟",
    "foot" : "这项调查是由AdMaster精硕科技公司携手伊利集团共同执行。AdMaster是知名的专业第三方网络广告效果监测及调研公司,您的资料将得到可靠的保护",
    "progress" : true,
    "logo" : "http://domain.com/img/logo.gif",
    "lang" : "en",
    "onepage" : false,
    "page_numbering" : true,
    "question_numbering" : "global",
    "pages" : [1,2,3,4,5,6]
  },
  {
    /* 另一文档数据 */
  }
]
</code></pre>

<h2 id="p3">2. 创建问卷</h2>

    POST /users/surveys

##请求

<pre class="highlight">
<code class="language-javascript">>
{
  "title" : "伊利8月新生活",
  "label" : "第一波",
  "head" : "首先感谢您参与我们的问卷调查。",
  "foot" : "这项调查是由AdMaster精硕科技公司携手伊利集团共同执行。",
  "progress" : true,
  "logo" : "http://domain.com/img/logo.gif",
  "lang" : "en",
  "onepage" : false,
  "page_numbering" : true,
  "question_numbering" : "global"
}
</code></pre>

title
: _必选_ *String* - 问卷标题，长度范围2 - 100个字符

label
: _可选_ *String* - 问卷说明

head
: _可选_ *String* - 问卷头信息

foot
: _可选_ *String* - 问卷尾信息

progress
: _可选_ *Boolean* - 是否显示进度条

logo
: _可选_ *String* - LOGO图标地址

lang
: _可选_ *String* - 语言

onepage
: _可选_ *Boolean* - 是否在一页显示

page\_numbering
: _可选_ *Boolean* - 是否在每一页显示问题重新编号

question\_numbering
: _可选_ *String* - 问题编号采用全局方式(global)或是页内方式(in_page)

###响应

<pre class="headers">
<code>Status: 201 Created
Location: http://api.surveymaster.com.cn/users/123/surveys
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
  "id" : 112,
  "url" : "http://api.surveymaster.com.cn/users/surveys/112",
  "title" : "伊利8月新生活",
  "label" : "第一波",
  "owner" : 123,
  "created_at" : "2012-07-31T09:36:27Z",
  "modified_at" : "2012-07-31T09:46:27Z",
  "landing_count" : 0,
  "answered_count" : 0,
  "finished_count" : 0,
  "head" : "首先感谢您参与我们的问卷调查。完成调查的每位用户均有机会参与抽奖,本次调查设置的奖项是：国际知名品牌提供的运动服及运动鞋。请根据您的实际情况逐项填写,您的意见或建议对我们很重要,完成问卷只需花费您短短五分钟",
  "foot" : "这项调查是由AdMaster精硕科技公司携手伊利集团共同执行。AdMaster是知名的专业第三方网络广告效果监测及调研公司,您的资料将得到可靠的保护",
  "progress" : true,
  "logo" : "http://domain.com/img/logo.gif",
  "lang" : "en",
  "onepage" : false,
  "page_numbering" : true,
  "question_numbering" : "global",
  "pages" : []
}
</code></pre>

<h2 id="p4">3. 获取指定问卷详情</h2>

    GET /users/surveys/:id

###响应

<pre class="headers">
<code>Status: 200 OK
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
  "id" : 112,
  "url" : "http://api.surveymaster.com.cn/users/surveys/112",
  "title" : "伊利8月新生活",
  "label" : "第一波",
  "owner" : 123,
  "created_at" : "2012-07-31T09:36:27Z",
  "modified_at" : "2012-07-31T09:46:27Z",
  "landing_count" : 0,
  "answered_count" : 0,
  "finished_count" : 0,
  "head" : "首先感谢您参与我们的问卷调查。完成调查的每位用户均有机会参与抽奖,本次调查设置的奖项是：国际知名品牌提供的运动服及运动鞋。请根据您的实际情况逐项填写,您的意见或建议对我们很重要,完成问卷只需花费您短短五分钟",
  "foot" : "这项调查是由AdMaster精硕科技公司携手伊利集团共同执行。AdMaster是知名的专业第三方网络广告效果监测及调研公司,您的资料将得到可靠的保护",
  "progress" : true,
  "logo" : "http://domain.com/img/logo.gif",
  "lang" : "en",
  "onepage" : false,
  "page_numbering" : true,
  "question_numbering" : "global",
  "pages" : []
}
</code></pre>

<h2 id="p5">4. 修改指定问卷</h2>

    PATCH /users/surveys/:id

###请求
<pre class="highlight">
<code class="language-javascript">
{
  "title" : "伊利8月新生活",
  "label" : "第一波",
  "head" : "首先感谢您参与我们的问卷调查。",
  "foot" : "这项调查是由AdMaster精硕科技公司携手伊利集团共同执行。",
  "progress" : true,
  "logo" : "http://domain.com/img/logo.gif",
  "lang" : "en",
  "onepage" : false,
  "page_numbering" : true,
  "question_numbering" : "global"
}
</code></pre>

title
: _可选_ *String* - 问卷标题，长度范围2 ~ 100个字符

label
: _可选_ *String* - 问卷说明

head
: _可选_ *String* - 问卷头信息

foot
: _可选_ *String* - 问卷尾信息

progress
: _可选_ *Boolean* - 是否显示进度条

logo
: _可选_ *String* - LOGO图标地址

lang
: _可选_ *String* - 语言

onepage
: _可选_ *Boolean* - 是否在一页显示

page\_numbering
: _可选_ *Boolean* - 是否在每一页显示问题重新编号

question\_numbering
: _可选_ *String* - 问题编号采用全局方式(global)或是页内方式(in_page)

###响应

<pre class="headers no-response">
<code>Status: 204 No Content
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

<h2 id="p6">5. 删除指定问卷（标记状态）</h2>

    DELETE /users/surveys/:id

###响应

<pre class="headers no-response">
<code>Status: 204 No Content
Link: <http://api.surveymaster.com.cn/users/surveys>; rel="surveys"
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

