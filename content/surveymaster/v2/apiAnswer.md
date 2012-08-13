---
title: SurveyMaster API - 答案相关接口（共6个）
---

  
<h2 id="p1">1. 新增答案</h2>
	POST /surveys/collectors/:collector_id/answers
	Set-Cookie: admaster_cookie_id=***

###请求
<pre class="highlight">
<code class="language-javascript">

[
	{
		"question_id" : 1,/* 问题id */
		"duration" : 30,/* 答题所用时间(秒) */
		"value" : ["1"]/* 数组里存放选项id */
	},
	{
		"question_id" : 2,
		"duration" : 30,
		"value" : ["-1"],/* -1代表"其他"选项 */
		"other" : '篮球'
	},
	{
		"question_id" : 8,
		"duration" : 30,
		"value" : ["1","1.1"]
	},
	{/* 多选题 */
		"question_id" : 3,
		"duration" : 30,
		"value" : ["1","3"]
	},
	{
		"question_id" : 9,
		"duration" : 30,
		"value" : ["1","3","3.2"],
	},
	{
		"question_id" : 4,
		"duration" : 30,
		"value" : ["4","-1"],
		"other" : "红酒"
	},
	{
		"question_id" : 5,
		"duration" : 30,
		"value" : ["-2"]/* -2代表选中了“排他”选项 */
	},
	{
		"question_id" : 10,
		"duration" : 30,
		"value" : ["1","3","3.2","4.4"],
	},
	{
		"question_id" : 6,
		"duration" : 30,
		"value" : "单行输入"
	},
	{
		"question_id" : 7,
		"duration" : 30,
		"value" : "多行输入\n多行输入"
	}
]
</code></pre>

<pre class="headers no-response">
<code>Status: 201 No Content
Location: http://api.surveymaster.com.cn/surveys/1/pages/next
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

<h2 id="p2">2. 获取指定问卷的答案列表</h2>
	GET /surveys/:survey_id/answers

### 可选参数

* collector\_id		指定渠道id进行过滤
* status		根据答题情况进行过滤（-1:被甄别 0:未答完 1:完成）
* respondent\_id		根据答题人进行过滤
* per\_page				每页显示记录数，默认30
* page						页数

###响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">
[
	{
		"id" : 1,/* 答案id */
		"url" : 'http://api.surveymaster.com.cn/surveys/collectors/answers/1',
		"respondent_id" : 1,
		"collector_id" : 1,
		"collector_name" : "新浪汽车",
		"created_at" : 123456789,// 开始答题时间
		"updated_at" : 123456789,// 最后答题时间
		"status" : "finished"// ENUM filtered:提前结束 answering:未答完 finished:完成
	}
]
</code></pre>

<h2 id="p3">3. 获取指定答案的详情</h2>
	GET /surveys/answers/:id

###响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
	"survey_id" : 1,/* 问卷id */
	"collector_id" : 1,/* 渠道id */
	"respondent_id" : 1,
	"collector_id" : 1,
	"collector_name" : "新浪汽车",
	"created_at" : 123456789,// 开始答题时间
	"status" : "finished"// ENUM filtered:提前结束 answering:未答完 finished:完成
	"answers" : [
		{
			"question_id" : 1,/* 问题id */
			"duration" : 30,/* 答题时间 */
			"value" : ["1"]/* 数组里存放选项id */
		},
		{
			"question_id" : 2,
			"duration" : 30,
			"value" : ["-1"],/* -1代表"其他"选项 */
			"other" : '篮球'
		},
		{
			"question_id" : 8,
			"duration" : 30,
			"value" : ["1","1.1"]
		},
		{/* 多选题 */
			"question_id" : 3,
			"duration" : 30,
			"value" : ["1","3"]
		},
		{
			"question_id" : 9,
			"duration" : 30,
			"value" : ["1","3","3.1","3.3"]
		},
		{
			"question_id" : 4,
			"duration" : 30,
			"value" : ["4","-1"],
			"other" : "红酒"
		},
		{
			"question_id" : 5,
			"duration" : 30,
			"value" : ["-2"]/* -2代表选中了“排他”选项 */
		},
		{
			"question_id" : 10,
			"duration" : 30,
			"value" : ["1","3","3.1","3.3","4.4"]
		},
		{
			"question_id" : 6,
			"duration" : 30,
			"value" : "单行输入"
		},
		{
			"question_id" : 7,
			"duration" : 30,
			"value" : "多行输入\n多行输入"
		}
	]
}
</code></pre>

<h2 id="p4">4. 编辑指定答卷中某一个问题的答案（注意：特殊功能，使用者非受访者本人）</h2>
	PATCH /surveys/answers/:answer_id/questions/:id
###请求
<pre class="highlight">
<code class="language-javascript">
{
	"value" : ["-1"],/* -1代表"其他"选项 */
	"other" : "篮球"
}
</code></pre>

###响应

<pre class="headers no-response">
<code>Status: 204 No Content
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

<h2 id="p5">5. 删除指定答案</h2>
	DELETE /surveys/answers/:id

###响应

<pre class="headers no-response">
<code>Status: 204 No Content
Link: http://api.surveymaster.com.cn/surveys/1/answers; rel="answers"
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>


<h2 id="p6">6. 删除指定渠道的所有答案</h2>
	DELETE /surveys/collectors/:collector_id/answers

###响应

<pre class="headers no-response">
<code>Status: 204 No Content
Link: http://api.surveymaster.com.cn/surveys/1/answers; rel="answers"
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

