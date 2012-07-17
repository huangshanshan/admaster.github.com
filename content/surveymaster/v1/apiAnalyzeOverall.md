---
title: 查看汇总分析
---
# 查看汇总分析

## 获取指定问卷的汇总分析

	GET /surveys/:survey_id/analyzes

### 参数

筛选渠道	

* `参数空` （获取所有渠道）
* `渠道 id` （该问卷下的渠道 id ， 只能一个）

### 响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">	

	{
		"landing": 100000,
		"answered": 10000,
		"finished":  1000,
		"first_come": "2012-01-01 12:34"
		"latest_come": "2012-04-01 03:34"
		"distinct_uid": 9900,
		
		//
		"questions_result":
		[
	
			//单选
			{
				"question_id": "1",
				"type": "single_choice",
				"title": "请选择您的性别",
				"options":
				[
					{
						"option_content": "男",
						"selected": 500,
					}
					{
						"option_content": "女",
						"selected": 510,
					}
					{
						"option_content": "其他，请注明",
						"selected": 510,
						"type": "specify"
					}
				]
				"answered": 2000,
				"skiped": 300,
			}
			//多选
			{
				"question_id": "2",
				"type": "multiple_choices",
				"title": "你喜欢哪些城市",
				"options":
				[
					{
						"option_content": "大连",
						"selected": 400,
					}
					{
						"option_content": "杭州",
						"selected": 210,
					}
					{
						"option_content": "九寨沟",
						"selected": 300,
					}
					{
						"option_content": "其他，请注明",
						"selected": 300,
						"type": "specify"
					}
					{
						"option_content": "我都不喜欢",
						"selected": 300,
						"type": "exclusive"
					}
				]
				"answered": 2000,
				"skiped": 300,
			}
			//单行输入
			{
				"question_id": "3",
				"type": "single_line",
				"title": "输入您的联系方式",
				"count": 700,
				"answered": 2000,
				"skiped": 300,
			}
			//多行文本
			{
				"question_id": "3",
				"type": "comment_box",
				"title": "输入您的联系方式",
				"count": 700,
				"answered": 2000,
				"skiped": 300,			
			}		
		]
	}
</code></pre>

