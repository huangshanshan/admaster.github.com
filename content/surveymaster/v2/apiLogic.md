---
title: SurveyMaster API - 逻辑相关接口（共4个）
---


<h2 id="p1">1. 创建逻辑</h2>
	POST /logics

###请求
<pre class="highlight">
<code class="language-javascript">
{
        "survey_id" : 1,
	"target_type" : "page/question",/* ENUM page:为某一页面设置逻辑 question:为某一问题设置逻辑 */
	"target_id" : 11,/* 根据上面的target_type : page_id / question_id */
	"conditions" : [/* 条件数组，数组顺序代表逻辑的优先级，也就是 OR 的关系 */
		[/* 每一个数组元素就是一个条件，共同组成一组逻辑，组内各条件都是 AND 的关系 */
			{/* 单选题 */
				"question_id" : 1,
				"range" : [
					1,
					3
				]
			},
			{/* 多选题，选项包括了“其他” */
				"question_id" : 2,
				"range" : [
					2,
					-1
				],
				"type" : "all/any/none"
			},
			{/* 多选题 */
				"question_id" : 3,
				"range" : [
					4,
					5
				],
				"type" : "all/any/none"/* ENUM all:全部选中range范围内的选项 any:range范围内的选项任意选中一个 none:all取反 */
			},
			{/* 单行文本 */
				"question_id" : 4,
				"include" : [/* 包含哪些字符串 */
					"admaster",
					"好"
				],
				"exclude" : [/* 不包含哪些字符串 */
					"不好"
				]
			},
			{/* 单行文本，只允许输入number */
				"question_id" : 5,
				"min" : 3/* 至少输入min个字符 */
			},
			{/* 多行文本 */
				"question_id" : 6,
				"include" : [
					"99click",
					"好"
				],
				"exclude" : [
					"不好"
				]
			}
		],
		[
			{
				"question_id" : 7,
				"range" : [
					1,
					3
				]
			},
			{
				"question_id" : 8,
				"range" : [
					2,
					-1
				],
				"type" : "all/any/none"
			},
			{
				"question_id" : 9,
				"range" : [
					4,
					5
				],
				"type" : "all/any/none"
			},
			{
				"question_id" : 10,
				"include" : [
					"admaster",
					"好"
				],
				"exclude" : [
					"不好"
				]
			},
			{
				"question_id" : 11,
				"min" : 6
				"max" : 10
			},
			{
				"question_id" : 12,
				"include" : [
					"99click",
					"好"
				],
				"exclude" : [
					"不好"
				]
			}
		]
	]
}
</code></pre>


<h2 id="p2">2. 修改指定的逻辑</h2>
	PATCH /logics/:id
###请求
<pre class="highlight">
<code class="language-javascript">
{
	"conditions" : [/* 条件数组，数组顺序代表逻辑的优先级，也就是 OR 的关系 */
		[/* 每一个数组元素就是一个条件，共同组成一组逻辑，组内各条件都是 AND 的关系 */
			{/* 单选题 */
				"question_id" : 1,
				"range" : [
					1,
					3
				]
			},
			{/* 多选题，选项包括了“其他” */
				"question_id" : 2,
				"range" : [
					2,
					-1
				],
				"type" : "all/any/none"
			},
			{/* 多选题 */
				"question_id" : 3,
				"range" : [
					4,
					5
				],
				"type" : "all/any/none"/* ENUM all:全部选中range范围内的选项 any:range范围内的选项任意选中一个 none:all取反 */
			},
			{/* 单行文本 */
				"question_id" : 4,
				"include" : [/* 包含哪些字符串 */
					"admaster",
					"好"
				],
				"exclude" : [/* 不包含哪些字符串 */
					"不好"
				]
			},
			{/* 单行文本，只允许输入number */
				"question_id" : 5,
				"min" : 3/* 至少输入min个字符 */
			},
			{/* 多行文本 */
				"question_id" : 6,
				"include" : [
					"99click",
					"好"
				],
				"exclude" : [
					"不好"
				]
			}
		],
		[
			{
				"question_id" : 7,
				"range" : [
					1,
					3
				]
			},
			{
				"question_id" : 8,
				"range" : [
					2,
					-1
				],
				"type" : "all/any/none"
			},
			{
				"question_id" : 9,
				"range" : [
					4,
					5
				],
				"type" : "all/any/none"
			},
			{
				"question_id" : 10,
				"include" : [
					"admaster",
					"好"
				],
				"exclude" : [
					"不好"
				]
			},
			{
				"question_id" : 11,
				"min" : 6
				"max" : 10
			},
			{
				"question_id" : 12,
				"include" : [
					"99click",
					"好"
				],
				"exclude" : [
					"不好"
				]
			}
		]
	]
}
</code></pre>

<h2 id="p3">3. 删除指定的逻辑</h2>
	DELETE /logics/:id
###请求
<pre class="highlight">
<code class="language-javascript">
{
}
</code></pre>

<h2 id="p4">4. 获取指定逻辑详情</h2>
	GET /logics/:id

###响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
	"_id" : ObjectId("500916d3337d221abed72ac3"),
	"id" : 1,/* 逻辑的id（自增 全局唯一） */
        "survey_id" : 1,
	"target_type" : "page/question",/* ENUM page:为某一页面设置逻辑 question:为某一问题设置逻辑 */
	"target_id" : 11,/* 根据上面的target_type : page_id / question_id */
	"conditions" : [/* 条件数组，数组顺序代表逻辑的优先级，也就是 OR 的关系 */
		[/* 每一个数组元素就是一个条件，共同组成一组逻辑，组内各条件都是 AND 的关系 */
			{/* 单选题 */
				"question_id" : 1,
				"range" : [
					1,
					3
				]
			},
			{/* 多选题，选项包括了“其他” */
				"question_id" : 2,
				"range" : [
					2,
					-1
				],
				"type" : "all/any/none"
			},
			{/* 多选题 */
				"question_id" : 3,
				"range" : [
					4,
					5
				],
				"type" : "all/any/none"/* ENUM all:全部选中range范围内的选项 any:range范围内的选项任意选中一个 none:all取反 */
			},
			{/* 单行文本 */
				"question_id" : 4,
				"include" : [/* 包含哪些字符串 */
					"admaster",
					"好"
				],
				"exclude" : [/* 不包含哪些字符串 */
					"不好"
				]
			},
			{/* 单行文本，只允许输入number */
				"question_id" : 5,
				"min" : 3/* 至少输入min个字符 */
			},
			{/* 多行文本 */
				"question_id" : 6,
				"include" : [
					"99click",
					"好"
				],
				"exclude" : [
					"不好"
				]
			}
		],
		[
			{
				"question_id" : 7,
				"range" : [
					1,
					3
				]
			},
			{
				"question_id" : 8,
				"range" : [
					2,
					-1
				],
				"type" : "all/any/none"
			},
			{
				"question_id" : 9,
				"range" : [
					4,
					5
				],
				"type" : "all/any/none"
			},
			{
				"question_id" : 10,
				"include" : [
					"admaster",
					"好"
				],
				"exclude" : [
					"不好"
				]
			},
			{
				"question_id" : 11,
				"min" : 6
				"max" : 10
			},
			{
				"question_id" : 12,
				"include" : [
					"99click",
					"好"
				],
				"exclude" : [
					"不好"
				]
			}
		]
	]
}
</code></pre>
