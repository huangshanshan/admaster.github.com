---
title: API - 问卷结构
---
# API - 问卷结构

<h2 id="p1">获取问卷所有问题</h2>
	GET /surveys/:id/pages/questions  

###响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">
	
	{
	
		{
	
			"id": "1",
			"title": "",
			"type": "sc",
		},
		{
	
			"id": "2",
			"title": "balabalabala",
			"type": "mc"
		},
		{
	
			"id": "3",
			"title": "",
			"type": "sl"
		},
		{
	
			"id": "3",
			"title": "",
			"type": "cm"
		}
		
	}
</code></pre>

<h2 id="p2">获取某个 page 下的所有问题内容（精简版结构，编辑时使用）</h2>

    GET /surveys/:survey_id/pages/questions

page 编号，按照传参标准

  
### 响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">
	[

		{
	
			"id": "1",
			"type": "single_choice",
			"title": "This is a multiple choices question with one answer. ",
			"description": "",
			"options": 
			[
				"选项A",
				"选项B",
				"选项C",
			],
			"other_status": true,
			"other_content" "其他",
			"specify": true,
			//0, dropdown; 1, one choice per line; 2, two choices per line; 3, three choices per line;  4, four choices per line; at most four.
			"display_style": 0,
			"require_answer": ture,
			
		},

		{
			"id": "2",
			"type": "multiple_choices",
			"title": "This is a multiple choices question with multiple answers. ",
			"description": "",
			"options": 
			[
				"option": "选项A",
				"option": "选项B",
				"option": "选项C",
			],
			"other_status": true,
			"other_content" "Other, speicfy please. ",
			"specify": true,
			"exclusive": true,
			"exclusive_content": "None of all",
			//at most 4
			"options_perline": 4,
			"require_answer": ture,
		},

		{
			"id": "3",
			"tpye": "single line",
			"title": "input text in one line",
			"description": "bless you",
			"require_answer": ture,
		},

		{
			"id": "4",
			"tpye": "comment box",
			"title": "input comment",
			"description": "bless you",
			*//To make a distinction，for those required questions, we will add a "*" to the questionnaire.*
			"require_answer": false,
		}

	]
</code></pre>