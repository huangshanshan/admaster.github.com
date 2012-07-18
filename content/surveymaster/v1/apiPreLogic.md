---
title: 前置逻辑
---
# 前置逻辑

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
		}
	]

</code></pre>

<h2 id="p2">获取单选题的前置逻辑</h2>

	GET /surveys/:survey_id/logic/:logic_id

### 响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">

	{
		
		"logic_id": "2",
		"logic_type" "pre_logic",
		"affect_question": "question_id",
		"conditions": 
		//logic_connective: OR
		[
	
			//logic_connective: AND
			{
				//"visiable" / "invisiable"
				"affect_state": "invisiable",
				[
					//单选题逻辑
					{
						"question_id": "1",
						"question_type": "one_answer",
		
						//"select","unselect","range",
						"judgement": "select",
						"options":
						[
							"option_content": "option a"
						]
					}
					
				]
			}

			{
				//"visiable" / "invisiable"
				"affect_state": "visiable",
				[
					//单选题逻辑
					{
						"question_id": "10",
						"question_type": "one_answer",
						//"select","unselect","range",
						"judgement": "range",
						"options":
						[
							"option_content": "option a",
							"option_content": "option b"
						]
					},
					//单选题逻辑		
					{
						"question_id": "10",
						"question_type": "one_answer",
						//"select","unselect","range",
						"judgement": "unselect",
						"options":
						[
							"option_content": "option a"
						]
					}
				]
			}
		]	
	}
</code></pre>

<h2 id="p3">获取多选题的前置逻辑</h2>

	GET /surveys/:survey_id/logic/:logic_id

### 响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">

	{
		
		"logic_id": "2",
		"logic_type" "pre_logic",
		"affect_question": "question_id",
		"conditions": 
		//logic_connective: OR
		[
	
			//logic_connective: AND
			{
				//"visiable" / "invisiable"
				"affect_state": "invisiable",
				[
      				//多选题逻辑
					{
						"question_id": "2",
						"question_type": "multiple_answers",
		
						//"any","none","all", based on selected collection.
						"judgement": "none",
						"collection":
						[
							"option_content": "option a",
							"option_content": "option B",
							"option_content": "Other, specify",
							"option_content": "exclusive",
						]
					}
                ]
            }
        ] 
	}
</code></pre>

<h2 id="p4">获取单行文本的前置逻辑</h2>

	GET /surveys/:survey_id/logic/:logic_id
					
### 响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">

	{
		
		"logic_id": "2",
		"logic_type" "pre_logic",
		"affect_question": "question_id",
		"conditions": 
		//logic_connective: OR
		[
	
			//logic_connective: AND
			{
				//"visiable" / "invisiable"
				"affect_state": "invisiable",
				[
					//单行文本
					{
						"question_id": "3",
						"question_type": "single_input",
		
						//"contain", "not_contain", ">", "<", ">=", "<=", "="
						"judgement": "contain",
						"judge_value": "ROI",
					}
                ]
             }
         ]
	}
</code></pre>

<h2 id="p5">获取多行文本的前置逻辑</h2>

	GET /surveys/:survey_id/logic/:logic_id
					
### 响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">

	{
		
		"logic_id": "2",
		"logic_type" "pre_logic",
		"affect_question": "question_id",
		"conditions": 
		//logic_connective: OR
		[
	
			//logic_connective: AND
			{
				//"visiable" / "invisiable"
				"affect_state": "invisiable",
				[
					//多行文本
					{
						"question_id": "4",
						"question_type": "comment_box",
		
						//"contain", "not_contain"
						"judgement": "not_contain",
						"judge_value": "bad news",
					}	
                ]
             }
         ]
	}
</code></pre>


					





