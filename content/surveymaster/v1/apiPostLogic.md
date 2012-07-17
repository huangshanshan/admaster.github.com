---
title: 后置逻辑
---
# 后置逻辑

<h2 id="p1">获取指定问卷的逻辑结构</h2>

	GET /surveys/:id/logics

### 响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">

	[
		{
			"logic_id": "1",
			"logic_type": "pre_logic",//前置逻辑
			"affect_question": "question_id",
			"condition_question": 
			[
				"question_id": "1",
				"question_id": "2",
				"question_id": "3",
			]		
		},
		{
			"logic_id": "2",
			"logic_type": "post_logic",//后置逻辑
			"judge_question": "question_id",
			"skip_question:
			[
				"question_id": "4",
				"question_id": "5",
				"question_id": "7",
			]
		},
	]

</code></pre>

<h2 id="p2">获取单选题后置逻辑</h2>

	GET /surveys/:survey_id/logic/:logic_id

### 响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">

	{		
		"logic_id": "1",
		"logic_type" "post_logic",
		"judge_question": "question_id",
		"question_type": "single_choice",
		"judgements": 
		[
			{
				"judge_type": "select",
				"options": 
				[
					"option_content": "option_A"
				]
				"skip_question": "question_id"
			},
			//OR
			{
				"judge_type": "unselect",
				"options": 
				[
					"option_content": "option_B",
					"option_content": "option_C"
				]
				"skip_question": "question_id"
			}
		]
	}		

</code></pre>

<h2 id="p3">获取多选题后置逻辑</h2>

	GET /surveys/:survey_id/logic/:logic_id

### 响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">

	{		
		"logic_id": "1",
		"logic_type" "post_logic",
		"judge_question": "question_id",
		"question_type": "multiple_choices",
		"judgements": 
		[
			//"OR"
			{				
				//"AND"
				"condition": 
				[
					{
						"judge_type": "any",
						"options": 
						[
							"option_content": "option_A",
							"option_content": "option_B",
							"option_content": "option_C",
							"option_content": "option_D"
						]
					},
					{
						"judge_type": "none",
						"options": 
						[
							"option_content": "option_C",
							"option_content": "option_D"
						]
					}
				],
				"skip_question": "question_id"
			},

			{
				"judge_type": "all",
				"options": 
				[
					"option_content": "option_A",
					"option_content": "option_B",
					"option_content": "option_C"
				]
				"skip_question": "question_id"
			}
		]
	}	



<h2 id="p4">获取单行文本的后置逻辑</h2>

	GET /surveys/:survey_id/logic/:logic_id

### 响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">

	{
		"logic_id": "3",
		"logic_type" "post_logic",
		"judge_question": "question_id",
		"question_type": "single_line",
		"judgements": 
		[
			{
				"condition":
				[
					{
						"judge_type": "contain",
						"judge_value": "abcdef..."
					},
					{
						"judge_type": "not_contain",
						"judge_value": "zyxw..."
					}
				]	
				"skip_question": "question_id",
			},
			{
				"condition":
				[
					{
						"judge_type": ">",
						"judge_value": "30"
					},
					{
						"judge_type": "<=",
						"judge_value": "10086"
				]	
				"skip_question": "question_id",
			},

		]
					}
	}

</code></pre>

<h2 id="p5">获取多行文本的后置逻辑</h2>

	GET /surveys/:survey_id/logic/:logic_id

### 响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">

	{
		"logic_id": "4",
		"logic_type" "post_logic",
		"judge_question": "question_id",
		"question_type": "comment_box",
		"judgements": 
		[
			{
				"condition":
				[
					{
						"judge_type": "contain",
						"judge_value": "abcdef..."
					},
					{
						"judge_type": "not_contain",
						"judge_value": "zyxw..."
					}
				]	
				"skip_question": "question_id",
			},
			{
				"condition":
				[
					{
						"judge_type": "contain",
						"judge_value": "hello world"
					}
				]	
				"skip_question": "question_id",
			},
			{
				"condition":
				[
					{
						"judge_type": "not_contain",
						"judge_value": "I love REST..."
					}
				]	
				"skip_question": "question_id",
			},
		]
	}
</code></pre>