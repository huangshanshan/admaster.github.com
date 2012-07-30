---
SurveyMaster API - 问题相关接口（共5个）
---

  
<h2 id="p1">1. 获取指定问卷的问题列表</h2>
	GET /surveys/:id/questions
### 可选参数

page_id
: _可选_ *int* - 页的id  (获取指定问卷某一页的问题列表)
  
* `2`
* `10`
* `16`
* `101`

###请求
<pre class="highlight">
<code class="language-javascript">
{
}
</code></pre>

###响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
	"1" : [/* page_id为1的问题列表 */
		{
			"_id" : ObjectId("500916d3337d221abed72ac3"),
			"id" : 1,/* 问题的id（自增 全局唯一） */
			"type" : "radio",/* ENUM radion:单选 checkbox:多选 text:单行文本 textarea:多行文本 */
			"title" : "我是一个单选",
			"desc" : "我是一个单选题啊单选题",
			"options" : [/* 数组value为选项内容，数组key为选项的id，数组的顺序即是选项的显示顺序 */
				"option_1",
				"option_2",
				"option_3"
			],
			"logic_id" : 0,/* 逻辑id，0表示此题没有任何逻辑 */
			"quotes" : [],/* 引用题的question_id数组（注意：引用题只能引用当前页之前的题） */
			"other" : {/* 其他选项（注意：这是一个特殊选项，其id为-1） */
				"status" : true,/* 是否显示其他选项 */
				"text" : "其他",/* 自定义选项名称 */
				"box" : {/* 输入框 */
					"status" : true,/* 是否出现输入框 */
					"min" : 1,/* 允许输入的最少字符数 */
					"max" : 10,/* 允许输入的最多字符数 */
					"prompt" : "当输入值不合法时，出现提示"/* 当输入框中的字符数不符合要求时的提示信息 */
				}
			},
			"required" : {/* 必答 */
				"status" : true,/* 是否设为必答题 */
				"prompt" : "这一项是必填的噢！"/* 没有回答时的提示信息 */
			},
			"display" : {/* 显示相关 */
				"style" : "radio/select",/* ENUM radio:单选按钮 select:单选下拉列表(注意：上面的other.status为true时，other的前端实现要与此设置保持一致) */
				"perline" : 2,/* 每行显示选项数（注意：当上面的display.style设置为select时此设置无意义） */
				"random" : false/* 是否随机显示选项（注意：顺序打乱 id不能变） */
			}
		},

		{
			"_id" : ObjectId("500926057e33b020d04a177f"),
			"id" : 2,
			"type" : "checkbox",
			"title" : "我是一个多选",
			"desc" : "我是一个牛13的多选题",
			"options" : [
				"option_1",
				"option_2",
				"option_3"
			],
			"logic_id" : 0,/* 逻辑id，0表示此题没有任何逻辑 */
			"quotes" : [],
			"other" : {
				"status" : true,
				"text" : "其他",
				"box" : {
					"status" : true,
					"min" : 1,
					"max" : 10,
					"prompt" : "当输入值不合法时，出现提示"
				}
			},
			"required" : {
				"status" : true,
				"min" : 1,/* 必须选择至少required.min个选项 */
				"max" : 3,/* 必须选择不超过required.max个选项 */
				"prompt" : "这一项是必填的噢！"
			},
			"display" : {
				"perline" : 2,
				"random" : false
			},
			"exclusive" : {/* 排他选项（注意：这是一个特殊选项，其id为-2） */
				"status" : true,/* 是否出现排他选项 */
				"text" : "以上都不是"/* 自定义选项名称 */
			}
		},

		{
			"_id" : ObjectId("5009261b7e33b020d04a1780"),
			"id" : 3,
			"type" : "text",
			"title" : "我是一个单行文本",
			"desc" : "我是一个单行文本",
			"logic_id" : 0,/* 逻辑id，0表示此题没有任何逻辑 */
			"quotes" : [],
			"limit" : {/* 输入限制 */
				"type" : "char/number/email/url/date",/* ENUM char:字符串 number:数字 email:邮箱 url:链接 date:日期 */
				"min" : 2,
				"max" : 20，
				"prompt" : "请输入2～20个字符"
			},
			"required" : {
				"status" : true,
				"prompt" : "这一项是必填的噢！"
			}
		},

		{
			"_id" : ObjectId("50091700337d221abed72ac4"),
			"id" : 4,
			"type" : "textarea",
			"title" : "我是一个多行文本",
			"desc" : "我是一个多行文本",
			"logic_id" : 1,/* 逻辑id，0表示此题没有任何逻辑 */
			"quotes" : [1,2],
			"limit" : {
				"min" : 2,
				"max" : 20，
				"prompt" : "请输入2～20个字符"
			},
			"required" : {
				"status" : true,
				"prompt" : "这一项是必填的噢！"
			}
		}
	]
}
</code></pre>

  
<h2 id="p2">2. 创建问题</h2>
	POST /question 

###请求
<pre class="highlight">
<code class="language-javascript">
{
	"survey_id" : 1,
	"type" : "radio",/* ENUM radion:单选 checkbox:多选 text:单行文本 textarea:多行文本 */
	"title" : "我是一个单选",
	"desc" : "我是一个单选题啊单选题",
	"options" : [/* 数组value为选项内容，数组key为选项的id，数组的顺序即是选项的显示顺序 */
		"option_1",
		"option_2",
		"option_3"
	],
	"logic_id" : 0,/* 逻辑id，0表示此题没有任何逻辑 */
	"quotes" : [1],
	"other" : {/* 其他选项（注意：这是一个特殊选项，其id为-1） */
		"status" : true,/* 是否显示其他选项 */
		"text" : "其他",/* 自定义选项名称 */
		"box" : {/* 输入框 */
			"status" : true,/* 是否出现输入框 */
			"min" : 1,/* 允许输入的最少字符数 */
			"max" : 10,/* 允许输入的最多字符数 */
			"prompt" : "当输入值不合法时，出现提示"/* 当输入框中的字符数不符合要求时的提示信息 */
		}
	},
	"required" : {/* 必答 */
		"status" : true,/* 是否设为必答题 */
		"prompt" : "这一项是必填的噢！"/* 没有回答时的提示信息 */
	},
	"display" : {/* 显示相关 */
		"style" : "radio/select",/* ENUM radio:单选按钮 select:单选下拉列表(注意：上面的other.status为true时，other的前端实现要与此设置保持一致) */
		"perline" : 2,/* 每行显示选项数（注意：当上面的display.style设置为select时此设置无意义） */
		"random" : false/* 是否随机显示选项（注意：顺序打乱 id不能变） */
	}
}
</code></pre>


<h2 id="p3">3. 获取指定问题详情</h2>
	GET /questions/:id

###响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
	"_id" : ObjectId("500916d3337d221abed72ac3"),
	"id" : 1,/* 问题的id（自增 全局唯一） */
	"survey_id" : 1,
	"type" : "radio",/* ENUM radion:单选 checkbox:多选 text:单行文本 textarea:多行文本 */
	"title" : "我是一个单选",
	"desc" : "我是一个单选题啊单选题",
	"options" : [/* 数组value为选项内容，数组key为选项的id，数组的顺序即是选项的显示顺序 */
		"option_1",
		"option_2",
		"option_3"
	],
	"logic_id" : 0,/* 逻辑id，0表示此题没有任何逻辑 */
	"quotes" : [],
	"other" : {/* 其他选项（注意：这是一个特殊选项，其id为-1） */
		"status" : true,/* 是否显示其他选项 */
		"text" : "其他",/* 自定义选项名称 */
		"box" : {/* 输入框 */
			"status" : true,/* 是否出现输入框 */
			"min" : 1,/* 允许输入的最少字符数 */
			"max" : 10,/* 允许输入的最多字符数 */
			"prompt" : "当输入值不合法时，出现提示"/* 当输入框中的字符数不符合要求时的提示信息 */
		}
	},
	"required" : {/* 必答 */
		"status" : true,/* 是否设为必答题 */
		"prompt" : "这一项是必填的噢！"/* 没有回答时的提示信息 */
	},
	"display" : {/* 显示相关 */
		"style" : "radio/select",/* ENUM radio:单选按钮 select:单选下拉列表(注意：上面的other.status为true时，other的前端实现要与此设置保持一致) */
		"perline" : 2,/* 每行显示选项数（注意：当上面的display.style设置为select时此设置无意义） */
		"random" : false/* 是否随机显示选项（注意：顺序打乱 id不能变） */
	}
}
</code></pre>

<h2 id="p4">4. 修改指定的问题</h2>
	PATCH /questions/:id
###请求
<pre class="highlight">
<code class="language-javascript">
{
	"type" : "radio",/* ENUM radion:单选 checkbox:多选 text:单行文本 textarea:多行文本(注意：允许改题型) */
	"title" : "我是一个单选",
	"desc" : "我是一个单选题啊单选题",
	"options" : [/* 数组value为选项内容，数组key为选项的id，数组的顺序即是选项的显示顺序 */
		"option_1",
		"option_2",
		"option_3"
	],
	"quotes" : [],
	"other" : {/* 其他选项（注意：这是一个特殊选项，其id为-1） */
		"status" : true,/* 是否显示其他选项 */
		"text" : "其他",/* 自定义选项名称 */
		"box" : {/* 输入框 */
			"status" : true,/* 是否出现输入框 */
			"min" : 1,/* 允许输入的最少字符数 */
			"max" : 10,/* 允许输入的最多字符数 */
			"prompt" : "当输入值不合法时，出现提示"/* 当输入框中的字符数不符合要求时的提示信息 */
		}
	},
	"required" : {/* 必答 */
		"status" : true,/* 是否设为必答题 */
		"prompt" : "这一项是必填的噢！"/* 没有回答时的提示信息 */
	},
	"display" : {/* 显示相关 */
		"style" : "radio/select",/* ENUM radio:单选按钮 select:单选下拉列表(注意：上面的other.status为true时，other的前端实现要与此设置保持一致) */
		"perline" : 2,/* 每行显示选项数（注意：当上面的display.style设置为select时此设置无意义） */
		"random" : false/* 是否随机显示选项（注意：顺序打乱 id不能变） */
	}
}
</code></pre>

<h2 id="p5">5. 删除指定的问题</h2>
	DELETE /questions/:id
###请求
<pre class="highlight">
<code class="language-javascript">
{
}
</code></pre>
