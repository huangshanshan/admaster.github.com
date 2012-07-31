---
title: SurveyMaster API - 后置逻辑相关接口（共5个）
---

<h2 id="p1">1. 获取指定页的后置逻辑列表</h2>
	GET /surveys/:survey_id/pages/:page_id/postlogics

###响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">
[/* 每一个数组元素就是一条逻辑，按先后顺序依次检查组内各逻辑，一旦存在符合条件的逻辑，检查即终止 */
	{
		"id" : 1,
		"goto" : 8,/* 跳转到第几页 */
		"conditions" : [/* 每一个数组元素就是一个条件，组内各条件都是 AND 的关系 */
			{/* 单选题 */
				"question_id" : 1,
				"range" : [1,3]
			},
			{/* 多选题，选项包括了“其他” */
				"question_id" : 2,
				"range" : [2,-1],
				"type" : "all/any/none"
			}
		]
	},

	{
		"id" : 2,
		"goto" : 10,/* 跳转到第几页 */
		"conditions" : [/* 每一个数组元素就是一个条件，组内各条件都是 AND 的关系 */
			{/* 单行文本 */
				"question_id" : 4,
				"include" : ["admaster","好"],
				"exclude" : ["不好"]
			},
			{/* 单行文本，只允许输入number */
				"question_id" : 5,
				"min" : 3/* 至少输入min个字符 */
			},
			{/* 多行文本 */
				"question_id" : 6,
				"include" : ["99click","好"],
				"exclude" : ["不好"]
			}
		]
	}
]
</code></pre>

<h2 id="p2">2. 获取指定的后置逻辑（页逻辑）</h2>
	GET /surveys/:survey_id/pages/:page_id/postlogics/:id

###响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
	"goto" : 10,/* 跳转到第几页 */
	"conditions" : [/* 每一个数组元素就是一个条件，组内各条件都是 AND 的关系 */
		{/* 单选题 */
			"question_id" : 1,
			"range" : [1,3]
		},
		{/* 多选题，选项包括了“其他” */
			"question_id" : 2,
			"range" : [2,-1],
			"type" : "all/any/none"
		},
		{/* 多选题 */
			"question_id" : 3,
			"range" : [4,5],
			"type" : "all/any/none"/* ENUM all:全部选中range范围内的选项 any:range范围内的选项任意选中一个 none:all取反 */
		},
		{/* 单行文本 */
			"question_id" : 4,
			"include" : ["admaster","好"],
			"exclude" : ["不好"]
		},
		{/* 单行文本，只允许输入number */
			"question_id" : 5,
			"min" : 3/* 至少输入min个字符 */
		},
		{/* 多行文本 */
			"question_id" : 6,
			"include" : ["99click","好"],
			"exclude" : ["不好"]
		}
	]
}
</code></pre>

<h2 id="p3">3. 添加后置逻辑</h2>
	POST /surveys/:survey_id/pages/:page_id/postlogics

###请求
<pre class="highlight">
<code class="language-javascript">
{
	"goto" : 10,/* 跳转到第几页 */
	"conditions" : [/* 每一个数组元素就是一个条件，组内各条件都是 AND 的关系 */
		{/* 单选题 */
			"question_id" : 1,
			"range" : [1,3]
		},
		{/* 多选题，选项包括了“其他” */
			"question_id" : 2,
			"range" : [2,-1],
			"type" : "all/any/none"
		},
		{/* 多选题 */
			"question_id" : 3,
			"range" : [4,5],
			"type" : "all/any/none"/* ENUM all:全部选中range范围内的选项 any:range范围内的选项任意选中一个 none:all取反 */
		},
		{/* 单行文本 */
			"question_id" : 4,
			"include" : ["admaster","好"],
			"exclude" : ["不好"]
		},
		{/* 单行文本，只允许输入number */
			"question_id" : 5,
			"min" : 3/* 至少输入min个字符 */
		},
		{/* 多行文本 */
			"question_id" : 6,
			"include" : ["99click","好"],
			"exclude" : ["不好"]
		}
	]
}
</code></pre>

<h2 id="p4">4. 修改指定的后置逻辑</h2>
	PATCH /surveys/:survey_id/pages/:page_id/postlogics/:id
###请求
<pre class="highlight">
<code class="language-javascript">
{
	"goto" : 10,/* 跳转到第几页 */
	"conditions" : [/* 每一个数组元素就是一个条件，组内各条件都是 AND 的关系 */
		{/* 单选题 */
			"question_id" : 1,
			"range" : [1,3]
		},
		{/* 多选题，选项包括了“其他” */
			"question_id" : 2,
			"range" : [2,-1],
			"type" : "all/any/none"
		},
		{/* 多选题 */
			"question_id" : 3,
			"range" : [4,5],
			"type" : "all/any/none"/* ENUM all:全部选中range范围内的选项 any:range范围内的选项任意选中一个 none:all取反 */
		},
		{/* 单行文本 */
			"question_id" : 4,
			"include" : ["admaster","好"],
			"exclude" : ["不好"]
		},
		{/* 单行文本，只允许输入number */
			"question_id" : 5,
			"min" : 3/* 至少输入min个字符 */
		},
		{/* 多行文本 */
			"question_id" : 6,
			"include" : ["99click","好"],
			"exclude" : ["不好"]
		}
	]
}
</code></pre>

<h2 id="p5">5. 删除指定的后置逻辑</h2>
	DELETE /surveys/:survey_id/pages/:page_id/postlogics/:id

