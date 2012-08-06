---
title: SurveyMaster API - 渠道相关接口（共5个）
---

<h2 id="p1">1. 获取指定问卷的渠道列表</h2>
	GET /surveys/:survey_id/collectors

###响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">
[
	{
		"id" : 1,
		"url" : 'http://api.surveymaster.com.cn/surveys/collectors/1',
		"type" : 'openlink/edm',
		"name" : '新浪汽车',
		"status" : "on",// off: 关闭 on: 开放
		"landing_count" : 5000,
		"answered_count" : 3000,
		"finished_count" : 500,
		"deadline_time" : 123456789,// 结束时间
	}
]
</code></pre>

<h2 id="p2">2. 获取指定的渠道</h2>
	GET /surveys/collectors/:id

###响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
	"id" : 1,
	"url" : 'http://api.surveymaster.com.cn/surveys/collectors/1',
	"survey_id" : 1,
	"type" : 'openlink/edm',
	"name" : '新浪汽车',
	"status" : "on",// off: 关闭 on: 开放
	"landing_count" : 5000,
	"answered_count" : 3000,
	"finished_count" : 500,
	"deadline_time" : 123456789,// 结束时间
	"passwd" : 'a4$_B8addj_09jhk',
	"max_count" : 2000, // 最多收集多少份
	"freq_control" : "yes", // 是否允许重复答题
	"access_url" : 'url', // 调查链接
	"redirect" : 'url', // 答题结束后跳转地址
	"thanks_content" : '答题结束后感谢语',
	"cross" : {
		status: 1,// 第三方交互
		param: ['psid'],//第三方传递参数
		callback: 'url'//回调地址
	}
}
</code></pre>

<h2 id="p3">3. 添加渠道</h2>
	POST /surveys/:survey_id/collectors

###请求
<pre class="highlight">
<code class="language-javascript">
{
	"type" : 'openlink/edm',
	"name" : '新浪汽车',
	"status" : "on",// off: 关闭 on: 开放
	"deadline_time" : 123456789,// 结束时间
	"passwd" : 'a4$_B8addj_09jhk',
	"max_count" : 2000, // 最多收集多少份
	"freq_control" : "yes", // 是否允许重复答题
	"access_url" : 'url', // 调查链接
	"redirect" : 'url', // 答题结束后跳转地址
	"thanks_content" : '答题结束后感谢语',
	"cross" : {
		status: 1,// 第三方交互
		param: ['psid'],//第三方传递参数
		callback: 'url'//回调地址
	}
}
</code></pre>

<pre class="headers no-response">
<code>Status: 201 No Content
Location: http://api.surveymaster.com.cn/surveys/pages/1/postlogics
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
{
	"id" : 1,/* 渠道id(自增) */
	/* 渠道详情 */
}
</code></pre>

<h2 id="p4">4. 修改指定的渠道</h2>
	PATCH /surveys/collectors/:id
###请求
<pre class="highlight">
<code class="language-javascript">
{
	"type" : 'openlink/edm',
	"name" : '新浪汽车',
	"status" : "on",// off: 关闭 on: 开放
	"deadline_time" : 123456789,// 结束时间
	"passwd" : 'a4$_B8addj_09jhk',
	"max_count" : 2000, // 最多收集多少份
	"freq_control" : "yes", // 是否允许重复答题
	"access_url" : 'url', // 调查链接
	"redirect" : 'url', // 答题结束后跳转地址
	"thanks_content" : '答题结束后感谢语',
	"cross" : {
		status: 1,// 第三方交互
		param: ['psid'],//第三方传递参数
		callback: 'url'//回调地址
	}
}
</code></pre>

###响应

<pre class="headers no-response">
<code>Status: 204 No Content
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

<h2 id="p5">5. 删除指定的渠道</h2>
	DELETE /surveys/collectors/:id

###响应

<pre class="headers no-response">
<code>Status: 204 No Content
Link: http://api.surveymaster.com.cn/surveys/1/collectors; rel="collectors"
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

