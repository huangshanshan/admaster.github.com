---
title: SurveyMaster API - 问卷相关
---

#API - 问卷相关

<h2 id="p1">获取当前授权用户的问卷</h2>

    GET /user/surveys

###参数

owner
: _必选_ *Int* - 所有者ID

fields
: _可选_ *String* - 字段列表

sort
: _可选_ *String* - 指定排序方式，例：created:-1 -> 按建立时间倒序排列，1为升序排列，-1为倒序排列，默认为升序排列

start_time/end_time
: _可选_ *Int* - 指定提取问卷列表（created）的开始及结束时间，不指定start_time，则不限定开始时间，不指定end_time，则不限定结束时间

start/limit（可选）
: _可选_ *Int* - 指定返回结果集区间，不指定start，则从开始取limit条文档，不指定limit，则取从start开始的所有文档

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
    "title" : "伊利8月新生活",
    "label" : "第一波",
    "owner" : 123,
    "created" : "123456789",
    "modified" : "123456789",
    "landing" : 50000,
    "answered" : 30000,
    "finished" : 5000,
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

错误错误及代码参见TrackMaster API[错误代码说明][apiCommon]


<h2 id="p2">获取所有用户的问卷</h2>

    GET /surveys

###参数

fields
: _可选_ *String* - 字段列表

sort
: _可选_ *String* - 指定排序方式，例：created:-1 -> 按建立时间倒序排列，1为升序排列，-1为倒序排列，默认为升序排列

start_time/end_time
: _可选_ *Int* - 指定提取问卷列表（created）的开始及结束时间，不指定start_time，则不限定开始时间，不指定end_time，则不限定结束时间

start/limit（可选）
: _可选_ *Int* - 指定返回结果集区间，不指定start，则从开始取limit条文档，不指定limit，则取从start开始的所有文档

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
    "title" : "伊利8月新生活",
    "label" : "第一波",
    "owner" : 123,
    "created" : "123456789",
    "modified" : "123456789",
    "landing" : 50000,
    "answered" : 30000,
    "finished" : 5000,
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

错误错误及代码参见TrackMaster API[错误代码说明][apiCommon]


<h2 id="p3">创建问卷</h2>

    POST /survey

###参数

title
: _必选_ *String* - 问卷标题，长度范围2 - 100个字符

label
: _可选_ *String* - 问卷说明

owner
: _可选_ *Int* - 创建者ID

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

page_numbering
: _可选_ *Boolean* - 是否在每一页显示问题重新编号

question_numbering
: _可选_ *String* - 问题编号采用全局方式(global)或是页内方式(in_page)

###请求

<pre class="highlight">
<code class="language-javascript">
{
  "title" : "伊利8月新生活",
  "label" : "第一波",
  "owner" : 123,
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

###响应

<pre class="headers">
<code>Status: 201 CREATED
Location: http://api.surveymaster.com.cn/survey
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
  "id" : 112,
  "title" : "伊利8月新生活",
  "label" : "第一波",
  "owner" : 123,
  "created" : "123456789",
  "modified" : "123456789",
  "landing" : 0,
  "answered" : 0,
  "finished" : 0,
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

<h2 id="p4">获取指定问卷详情</h2>

    GET /survey/:survey_id

###参数

owner
: _必选_ *Int* - 建立者ID

survey_id
: _必选_ *Int* - 问卷ID

###响应
<pre class="headers">
<code>Status: 200 OK
Location: http://api.surveymaster.com.cn/survey
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
  "id" : 112,
  "title" : "伊利8月新生活",
  "label" : "第一波",
  "owner" : 123,
  "created" : "123456789",
  "modified" : "123456789",
  "landing" : 0,
  "answered" : 0,
  "finished" : 0,
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

<h2 id="p5">修改指定问卷</h2>

    PATCH /survey/:survey_id

###参数

title
: _可选_ *String* - 问卷标题，长度范围2 - 100个字符

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

page_numbering
: _可选_ *Boolean* - 是否在每一页显示问题重新编号

question_numbering
: _可选_ *String* - 问题编号采用全局方式(global)或是页内方式(in_page)

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

###响应
<pre class="headers">
<code>Status: 204 NO CONTENT
Location: http://api.surveymaster.com.cn/survey
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
</code></pre>

<h2 id="p6">删除指定问卷（标记状态）</h2>

    DELETE /survey/:survey_id

###参数

owner
: _必选_ *Int* - 建立者ID

survey_id
: _必选_ *Int* - 问卷ID

###请求

<pre class="highlight">
<code class="language-javascript">
{
  "owner" : 123,
  "survey_id" : 112
}
</code></pre>

###响应
<pre class="headers">
<code>Status: 204 NO CONTENT
Location: http://api.surveymaster.com.cn/survey
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
</code></pre>
