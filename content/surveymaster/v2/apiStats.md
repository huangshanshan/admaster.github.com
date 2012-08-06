---
title: SurveyMaster API - 统计相关接口（共1个）
---

  
<h2 id="p1">1. 获取指定问卷的统计信息</h2>
	GET /surveys/:survey_id/stats
### 可选参数

* collector\_id	渠道id

###响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
	"landing_count" : 7788256,
	"answered_count" : 4210000,
	"finished_count" : 1950000,
	"respondent_count" : 7788256,/* 答题人数量 */
	"first_time" : 123456789,/* 第一个答题人的答题时间 */
	"last_time" : 123456789,/* 最后一个答题人的答题时间 */
	"question_ids" : [1,2,3,4,5]
}
</code></pre>

<h2 id="p2">2. 获取指定问题的统计信息</h2>
	GET /surveys/questions/:question_id/stats

###响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
	"type" : "radio",/* ENUM radion:单选 checkbox:多选 text:单行文本 textarea:多行文本 */
	"title" : "我是一个单选",
	"skiped_count" : 5555,/* 跳过此题的受访者数量 */
	"answered_count" : 3167,/* 回答了此题的受访者数量 */
	"options" : [
		{
			"option" : "《九歌》",/* 选项名称 */
			"count" : 476/* 选择了此选项的受访者数量 */
		},
		{
			"option" : "《天问》",
			"count" : 140
		},
		{
			"option" : "《最炫民族风》",
			"count" : 48
		},
		{
			"option" : "《楚辞》",
			"count" : 194
		},
		{
			"option" : "其他",
			"count" : 193
		}
	]
}
/*
{
	"type" : "checkbox",
	"title" : "我是一个多选",
	"skiped_count" : 5555,
	"answered_count" : 3167,
	"options" : [
		{
			"option" : "美利坚合众国",
			"count" : 476
		},
		{
			"option" : "黑齿国",
			"count" : 140
		},
		{
			"option" : "恐龙王国",
			"count" : 48
		},
		{
			"option" : "犬封国",
			"count" : 194
		},
		{
			"option" : "其他",
			"count" : 193
		}
	]
}

{
	"type" : "text",
	"title" : "我是一个单行文本",
	"skiped_count" : 5555,
	"answered_count" : 3167
}

{
	"type" : "textarea",
	"title" : "我是一个多行文本",
	"skiped_count" : 5555,
	"answered_count" : 3167
}
*/
</code></pre>

