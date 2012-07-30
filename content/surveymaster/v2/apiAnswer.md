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
	"answers" : [
		{
			"question_id" : 1,/* 问题id */
			"timestamp" : 123456789,/* 答题时间 */
			"selected" : [1]/* 数组里存放选项id */
		},
		{
			"question_id" : 2,
			"timestamp" : 123456789,
			"selected" : [-1],/* -1代表"其他"选项 */
			"other" : '篮球'
		},
		{
			"question_id" : 8,
			"timestamp" : 123456789,
			"selected" : [1],
			"quote" : [/* 引用其他题 */
				{
					"question_id" : 1,
					"selected" : [1]
				}
			]
		},
		{/* 多选题 */
			"question_id" : 3,
			"timestamp" : 123456789,
			"selected" : [1,3]
		},
		{
			"question_id" : 9,
			"timestamp" : 123456789,
			"selected" : [1,3],
			"quote" : [
				{
					"question_id" : 3,
					"selected" : [1,3]
		    }
			]
		},
		{
			"question_id" : 4,
			"timestamp" : 123456789,
			"selected" : [4,-1],
			"other" : "红酒"
		},
		{
			"question_id" : 5,
			"timestamp" : 123456789,
			"selected" : [-2]/* -2代表选中了“排他”选项 */
		},
		{
			"question_id" : 10,
			"timestamp" : 123456789,
			"selected" : [1,3],
			"quote" : [
				{
					"question_id" : 3,
					"selected" : [1,3]
				},
				{
					"question_id" : 4,
					"selected" : [4]
				}
			]
		},
		{
			"question_id" : 6,
			"timestamp" : 123456789,
			"content" : "单行输入"
		},
		{
			"question_id" : 7,
			"timestamp" : 123456789,
			"content" : "多行输入\n多行输入"
		}
	]
}
</code></pre>

<h2 id="p2">2. 获取指定问卷的答案列表</h2>
	GET /surveys/:id/answers

### 可选参数

* collector_id		指定渠道id进行过滤
* status		根据答题情况进行过滤（-1:被甄别 0:未答完 1:完成）
* respondent_id		根据答题人进行过滤

###请求
<pre class="highlight">
<code class="language-javascript">
{
	"collector_id" : 1,
	"status" : 0,
	"respondent_id" : 1
}
</code></pre>

###响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
	"id" : 1,/* 答案id */
	"respondent_id" : "1",
	"collector_id" : 1,
	"collector_name" : "新浪汽车",
	"created" : 123456789,// 开始答题时间
	"status" : "-1/0/1"// -1:被甄别 0:未答完 1:完成
}
</code></pre>

<h2 id="p3">3. 编辑指定答案（注意：特殊功能，使用者非受访者本人）</h2>
	PATCH /answers/:id
###请求
<pre class="highlight">
<code class="language-javascript">
[
	{
		"question_id" : 1,/* 问题id */
		"timestamp" : 123456789,/* 答题时间 */
		"selected" : [1]/* 数组里存放选项id */
	},
	{
		"question_id" : 2,
		"timestamp" : 123456789,
		"selected" : [-1],/* -1代表"其他"选项 */
		"other" : '篮球'
	},
	{
		"question_id" : 8,
		"timestamp" : 123456789,
		"selected" : [1],
		"quote" : [/* 引用其他题 */
			{
				"question_id" : 1,
				"selected" : [1]
			}
		]
	},
	{/* 多选题 */
		"question_id" : 3,
		"timestamp" : 123456789,
		"selected" : [1,3]
	},
	{
		"question_id" : 9,
		"timestamp" : 123456789,
		"selected" : [1,3],
		"quote" : [
			{
				"question_id" : 3,
				"selected" : [1,3]
			}
		]
	},
	{
		"question_id" : 4,
		"timestamp" : 123456789,
		"selected" : [4,-1],
		"other" : "红酒"
	},
	{
		"question_id" : 5,
		"timestamp" : 123456789,
		"selected" : [-2]/* -2代表选中了“排他”选项 */
	},
	{
		"question_id" : 10,
		"timestamp" : 123456789,
		"selected" : [1,3],
		"quote" : [
			{
				"question_id" : 3,
				"selected" : [1,3]
	    },
	    {
				"question_id" : 4,
				"selected" : [4]
	    }
		]
	},
	{
		"question_id" : 6,
		"timestamp" : 123456789,
		"content" : "单行输入"
	},
	{
		"question_id" : 7,
		"timestamp" : 123456789,
		"content" : "多行输入\n多行输入"
	}
]
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
	"respondent_id" : 1,/* 答题人id */
	"respondent_name" : "胡斤品",/* 答题人姓名 */
	"respondent_email" : "abcde@admaster.com.cn",/* 答题人邮箱 */
	"respondent_ip" : "123.123.123.12",/* 答题人IP */
	"respondent_location" : "Beijing - Beijing",/* 答题人所在城市 */
	"collector_id" : 1,/* 渠道id */
	"collector_name" : "youku_视频弹窗_开放链接_001",/* 渠道名称 */
	"created" : 123456789,/* 开始答题时间 */
	"modified" : 123456789,/* 最后活动时间 */
	"answers" : [
		{
			"question_id" : 1,
			"timestamp" : 123456789,/* 答题时间 */
			"title" : "我是一只选择题，单选题啊单选题（单选）",
			"answer" : ["《最炫民族风》"]
		},
		{
			"question_id" : 2,
			"timestamp" : 123456789,/* 答题时间 */
			"title" : "我是一只选择题，单选题啊单选题（单选）",
			"answer" : ["其他(《离骚》)"]/* 答题人选择了“其他”选项，并且输入了“《离骚》” */
		},
		{
			"question_id" : 8,
			"timestamp" : 123456789,/* 答题时间 */
			"title" : "我是一只选择题，单选题啊单选题（单选）",
			"answer" : ["第三题的第一个选项"]/* 答题人选择了引用题的一个选项 */
		},
		{
			"question_id" : 3,
			"timestamp" : 123456789,/* 答题时间 */
			"title" : "我也是一只选择题，不过是多选，多选题，霸气，不解释！（多选）",
			"answer" : ["《最炫民族风》"]
		},
		{
			"question_id" : 9,
			"timestamp" : 123456789,/* 答题时间 */
			"title" : "我也是一只选择题，不过是多选，多选题，霸气，不解释！（多选）",
			"answer" : ["《最炫民族风》", "第一题的第二个选项", "第三题的第一个选项"]
		},
		{
			"question_id" : 4,
			"timestamp" : 123456789,/* 答题时间 */
			"title" : "我也是一只选择题，不过是多选，多选题，霸气，不解释！（多选）",
			"answer" : ["以上都不死是"]/* 答题人选择了排他选项 */
		},
		{
			"question_id" : 6,
			"timestamp" : 123456789,/* 答题时间 */
			"title" : "单行输入",
			"answer" : ["资本主义"]
		},
		{
			"question_id" : 7,
			"timestamp" : 123456789,/* 答题时间 */
			"title" : "多行输入",
			"answer" : ["第一，以人为本的发展观。\n  第二，全面发展观。\n  第三，协调发展观。\n  第四，可持续发展观。"]
		}
	]
}
</code></pre>
