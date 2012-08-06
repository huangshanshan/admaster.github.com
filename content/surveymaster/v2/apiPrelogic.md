---
title: SurveyMaster API - 前置逻辑相关接口（共6个）
---

<h2 id="p1">1. 获取指定问题的前置逻辑列表</h2>
	GET /surveys/questions/:question_id/prelogics

###响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
	"visible" : "yes",/* 此问题是否显示 */
	"logics" : [/* 每一个数组元素就是一条逻辑，按先后顺序依次检查组内各逻辑，一旦存在符合条件的逻辑，逻辑判断即终止 */
		{
			"id" : 1,
			"url" : 'http://api.surveymaster.com.cn/surveys/questions/prelogics/1',
			"order_num" : 1,
			"conditions" : [/* 每一个数组元素就是一个条件，组内各条件都是 AND 的关系 */
				{
					"question_id" : 7,
					"range" : [1,3]
				},
				{
					"question_id" : 8,
					"range" : [2,-1],
					"type" : "all/any/none"
				}
			]
		},

		{
			"id" : 2,
			"url" : 'http://api.surveymaster.com.cn/surveys/questions/prelogics/2',
			"order_num" : 2,
			"conditions" : [/* 每一个数组元素就是一个条件，组内各条件都是 AND 的关系 */
				{
					"question_id" : 11,
					"min" : 6
					"max" : 10
				},
				{
					"question_id" : 12,
					"include" : ["99click","好"],
					"exclude" : ["不好"]
				}
			]
		}
	]
}
</code></pre>

<h2 id="p2">2. 获取指定的前置逻辑</h2>
	GET /surveys/questions/prelogics/:id

###响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
	"id" : 1,/* 前置逻辑的id（自增 全局唯一） */
	"url" : 'http://api.surveymaster.com.cn/surveys/questions/prelogics/1',
	"question_id" : 1,
	"visible" : "yes",/* 此问题是否显示 */
	"order_num" : 1,
	"conditions" : [/* 每一个数组元素就是一个条件，组内各条件都是 AND 的关系 */
		{
			"question_id" : 7,
			"range" : [1,3]
		},
		{
			"question_id" : 8,
			"range" : [2,-1],
			"type" : "all/any/none"
		},
		{
			"question_id" : 9,
			"range" : [4,5],
			"type" : "all/any/none"
		},
		{
			"question_id" : 10,
			"include" : ["admaster","好"],
			"exclude" : ["不好"]
		},
		{
			"question_id" : 11,
			"min" : 6
			"max" : 10
		},
		{
			"question_id" : 12,
			"include" : ["99click","好"],
			"exclude" : ["不好"]
		}
	]
}
</code></pre>

<h2 id="p3">3. 添加前置逻辑</h2>
	POST /surveys/questions/:question_id/prelogics

###请求
<pre class="highlight">
<code class="language-javascript">
{
	"order_num" : 1,
	"conditions" : [/* 每一个数组元素就是一个条件，组内各条件都是 AND 的关系 */
		{
			"question_id" : 7,
			"range" : [1,3]
		},
		{
			"question_id" : 8,
			"range" : [2,-1],
			"type" : "all/any/none"
		},
		{
			"question_id" : 9,
			"range" : [4,5],
			"type" : "all/any/none"
		},
		{
			"question_id" : 10,
			"include" : ["admaster","好"],
			"exclude" : ["不好"]
		},
		{
			"question_id" : 11,
			"min" : 6
			"max" : 10
		},
		{
			"question_id" : 12,
			"include" : ["99click","好"],
			"exclude" : ["不好"]
		}
	]
}
</code></pre>

<pre class="headers no-response">
<code>Status: 201 No Content
Location: http://api.surveymaster.com.cn/surveys/questions/1/prelogics
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

<h2 id="p4">4. 设置指定问题的前置逻辑效果</h2>
	PATCH /surveys/questions/:question_id/prelogics/result
###请求
<pre class="highlight">
<code class="language-javascript">
{
	"visible" : "yes"
}
</code></pre>

###响应

<pre class="headers no-response">
<code>Status: 204 No Content
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

<h2 id="p5">5. 修改指定的前置逻辑</h2>
	PATCH /surveys/questions/prelogics/:id
###请求
<pre class="highlight">
<code class="language-javascript">
{
	"order_num" : 1,
	"conditions" : [/* 每一个数组元素就是一个条件，组内各条件都是 AND 的关系 */
		{
			"question_id" : 7,
			"range" : [1,3]
		},
		{
			"question_id" : 8,
			"range" : [2,-1],
			"type" : "all/any/none"
		},
		{
			"question_id" : 9,
			"range" : [4,5],
			"type" : "all/any/none"
		},
		{
			"question_id" : 10,
			"include" : ["admaster","好"],
			"exclude" : ["不好"]
		},
		{
			"question_id" : 11,
			"min" : 6
			"max" : 10
		},
		{
			"question_id" : 12,
			"include" : ["99click","好"],
			"exclude" : ["不好"]
		}
	]
}
</code></pre>

###响应

<pre class="headers no-response">
<code>Status: 204 No Content
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

<h2 id="p6">6. 删除指定的前置逻辑</h2>
	DELETE /surveys/questions/prelogics/:id

###响应

<pre class="headers no-response">
<code>Status: 204 No Content
Link: http://api.surveymaster.com.cn/surveys/questions/1/prelogics; rel="prelogics"
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

