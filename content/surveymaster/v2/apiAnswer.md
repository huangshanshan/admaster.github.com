---
SurveyMaster API - 答案相关接口（共6个）
---

  
<h2 id="p1">1. 新增答案</h2>
	POST /answers 

###请求
<pre class="highlight">
<code class="language-javascript">
{
	"respondent_id" : 1,/* 答题人id */
	"collector_id" : 1,/* 渠道id */
	"answers" : {
		1 : {/* 键代表问题id */
			"timestamp" : 123456789,/* 答题时间 */
			"1" : 1/* 键代表选项id */
		},
		2 : {
			"timestamp" : 123456789,/* 答题时间 */
			"-1" : 1,/* 键-1代表"其他"选项 */
			"other" : '篮球'
		},
		8 : {
			"timestamp" : 123456789,/* 答题时间 */
			"1" : 1,
			"quote" : [/* 引用其他题 */
				1 : {/* 键代表引用题的id */
					"1" : 1/* 键代表引用题选项id */
				}
			]
		},
		3 : {/* 多选题 */
			"timestamp" : 123456789,/* 答题时间 */
			"1" : 1,
			"3" : 1
		},
		9 : {
			"timestamp" : 123456789,/* 答题时间 */
			"1" : 1,
			"3" : 1,
			"quote" : [
				3 : {
					"1" : 1,
					"3" : 1
				}
			]
		},
		4 : {
			"timestamp" : 123456789,/* 答题时间 */
			"4" : 1,
			"-1" : 1,
			"other" : "红酒"
		},
		5 : {
			"-2" : 1/* 键-2代表选中了“排他”选项 */
		},
		10 : {
			"timestamp" : 123456789,/* 答题时间 */
			"1" : 1,
			"3" : 1,
			"quote" : [
				3 : {
					"1" : 1,
					"3" : 1
				},
				4 : {
					"4" : 1
				}
			]
		},
		6 : {
			"timestamp" : 123456789,/* 答题时间 */
			"1" : "单行输入"
		},
		7 : {
			"timestamp" : 123456789,/* 答题时间 */
			"1" : "多行输入"
		}
	}
}
</code></pre>

<h2 id="p2">2. 获取指定渠道、指定受访者的答案</h2>
	GET /collectors/:collector_id/respondents/:respondent_id/answers

###响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
	"id" : 1,/* 答案id */
	"answers" : {
		1 : {/* 键代表问题id */
			"timestamp" : 123456789,/* 答题时间 */
			"1" : 1/* 键代表选项id */
		},
		2 : {
			"timestamp" : 123456789,/* 答题时间 */
			"-1" : 1,/* 键-1代表"其他"选项 */
			"other" : '篮球'
		},
		8 : {
			"timestamp" : 123456789,/* 答题时间 */
			"1" : 1,
			"quote" : [/* 引用其他题 */
				1 : {/* 键代表引用题的id */
					"1" : 1/* 键代表引用题选项id */
				}
			]
		},
		3 : {/* 多选题 */
			"timestamp" : 123456789,/* 答题时间 */
			"1" : 1,
			"3" : 1
		},
		9 : {
			"timestamp" : 123456789,/* 答题时间 */
			"1" : 1,
			"3" : 1,
			"quote" : [
				3 : {
					"1" : 1,
					"3" : 1
				}
			]
		},
		4 : {
			"timestamp" : 123456789,/* 答题时间 */
			"4" : 1,
			"-1" : 1,
			"other" : "红酒"
		},
		5 : {
			"-2" : 1/* 键-2代表选中了“排他”选项 */
		},
		10 : {
			"timestamp" : 123456789,/* 答题时间 */
			"1" : 1,
			"3" : 1,
			"quote" : [
				3 : {
					"1" : 1,
					"3" : 1
				},
				4 : {
					"4" : 1
				}
			]
		},
		6 : {
			"timestamp" : 123456789,/* 答题时间 */
			"1" : "单行输入"
		},
		7 : {
			"timestamp" : 123456789,/* 答题时间 */
			"1" : "多行输入"
		}
	}
}
</code></pre>

<h2 id="p3">3. 编辑指定答案（注意：特殊功能，使用者非受访者本人）</h2>
	PATCH /answers/:id
###请求
<pre class="highlight">
<code class="language-javascript">
{
	1 : {/* 键代表问题id */
		"1" : 1/* 键代表选项id */
	},
	2 : {
		"-1" : 1,/* 键-1代表"其他"选项 */
		"other" : '篮球'
	},
	8 : {
		"1" : 1,
		"quote" : [/* 引用其他题 */
			1 : {/* 键代表引用题的id */
				"1" : 1/* 键代表引用题选项id */
			}
		]
	},
	3 : {/* 多选题 */
		"1" : 1,
		"3" : 1
	},
	9 : {
		"1" : 1,
		"3" : 1,
		"quote" : [
			3 : {
				"1" : 1,
				"3" : 1
			}
		]
	},
	4 : {
		"4" : 1,
		"-1" : 1,
		"other" : "红酒"
	},
	5 : {
		"-2" : 1/* 键-2代表选中了“排他”选项 */
	},
	10 : {
		"1" : 1,
		"3" : 1,
		"quote" : [
			3 : {
				"1" : 1,
				"3" : 1
			},
			4 : {
				"4" : 1
			}
		]
	},
	6 : {
		"1" : "单行输入"
	},
	7 : {
		"1" : "多行输入"
	}
}
</code></pre>

<h2 id="p4">4. 删除指定答案</h2>
	DELETE /answers/:id
###请求
<pre class="highlight">
<code class="language-javascript">
{

}
</code></pre>

<h2 id="p5">5. 删除指定渠道的所有答案</h2>
	DELETE /collectors/:collector_id/answers

###请求
<pre class="highlight">
<code class="language-javascript">
{

}
</code></pre>

<h2 id="p6">6. 获取指定答案的详情</h2>
	GET /answers/:id

###响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
	"_id" : ObjectId("5008f2e1c4cbae3414747a10"),
	"id" : 1,
	"respondent_id" : 1,/* 答题人id */
	"collector_id" : 1,/* 渠道id */
	"answers" : {
		1 : {/* 键代表问题id */
			"timestamp" : 123456789,/* 答题时间 */
			"1" : 1/* 键代表选项id */
		},
		2 : {
			"timestamp" : 123456789,/* 答题时间 */
			"-1" : 1,/* 键-1代表"其他"选项 */
			"other" : '篮球'
		},
		8 : {
			"timestamp" : 123456789,/* 答题时间 */
			"1" : 1,
			"quote" : [/* 引用其他题 */
				1 : {/* 键代表引用题的id */
					"1" : 1/* 键代表引用题选项id */
				}
			]
		},
		3 : {/* 多选题 */
			"timestamp" : 123456789,/* 答题时间 */
			"1" : 1,
			"3" : 1
		},
		9 : {
			"timestamp" : 123456789,/* 答题时间 */
			"1" : 1,
			"3" : 1,
			"quote" : [
				3 : {
					"1" : 1,
					"3" : 1
				}
			]
		},
		4 : {
			"timestamp" : 123456789,/* 答题时间 */
			"4" : 1,
			"-1" : 1,
			"other" : "红酒"
		},
		5 : {
			"-2" : 1/* 键-2代表选中了“排他”选项 */
		},
		10 : {
			"timestamp" : 123456789,/* 答题时间 */
			"1" : 1,
			"3" : 1,
			"quote" : [
				3 : {
					"1" : 1,
					"3" : 1
				},
				4 : {
					"4" : 1
				}
			]
		},
		6 : {
			"timestamp" : 123456789,/* 答题时间 */
			"1" : "单行输入"
		},
		7 : {
			"timestamp" : 123456789,/* 答题时间 */
			"1" : "多行输入"
		}
	}
}
</code></pre>
