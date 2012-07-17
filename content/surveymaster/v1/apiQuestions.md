---
title: 问题
---

# 问题

##  获取指定某个问题

	GET /questions/:id 

### 响应

<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">

Details of Multiple Choice ( Only One Answer )

	{
	
		"id": "1",
		"type": "one_answer",
		"title": "This is a multiple choices question with one answer. ",
		"description": "//HTML can be embeded.",
		"options": 
		[
			"option": "选项A",
			"option": "选项B",
			"option": "选项C",
			"option": "选项D",
		],
		"other_status": true,
		"other_content" "Other/Other, specify",
		"specify": true,

		//"string", "number", "integer", "datetime", "weblink", "email"
		"specify_type": "integer",
		"specify_prompt": "please input a integer",
		
		//"string", string.length; "number", range; "integer", range.
		"specify_restrain_max": 100,
		"specify_restrain_min": 0,

		"require_answer": true，
		"require_answer_prompt": "please make a choice"，

		//0, dropdown; 1, one choice per line; 2, two choices per line; 3, three choices per line;  4, four choices per line; at most four.
		"display_style": 0,

		"random": true,
			
	},


Details of Multiple Choice ( Multiple Answers )

	{
	
		"id": "2",
		"type": "multiple_answers",
		"title": "This is a multiple choices question. ",
		"description": "//HTML can be embeded.",
		"options": 
		{
			"reference":
			{
				[
					{},
					{},
				]
			}
			"选项A",
			"选项B",
			"选项C",
			"选项D",
		},
		"other_status": true,
		"other_content" "Other / Other, specify",
		"specify": true,

		//"string", "number", "integer", "datetime", "weblink", "email"
		"specify_type": "integer",
		"specify_prompt": "please input a integer",
		
		"specify_restrain_max": 100,
		"specify_restrain_min": 0,

		"exclusive_status": true,
		"exclusive_content": "Exclusive",
		"random": true,

		"require_answer": true，
		"require_answer_prompt": "please make a choice"，
		
		//"at least"; "at most"; "range"; "specify"
		"require_answer_type": "at least",
		"require_answer_max": "options_amount",
		"require_answer_min": "1",

		//1, one choice per line; 2, two choices per line; 3, three choices per line;  4, four choices per line; at most four.
		"display_style": 1,

	},



Details of Single Line Input

	{
		"id": "3",
		"tpye": "single_input",
		"title": "input text in one line",
		"description": "bless you",
		"require_answer": ture,
		"require_answer_prompt": "you need fill this blank.",
		
		//"string", "number", "integer"; Following type have no length restrain: "datetime", "weblink", "email"
		"restrain_type": "string",
		"restrain_max": 50,
		"restrain_min": 3,
		"restrain_prompt": "invalidate input"
	},



Details of Comment Box

	{
		"id": "4",
		"tpye": "comment_box",
		"title": "input text in one line",
		"description": "bless you",
		"require_answer": ture,
		"require_answer_prompt": "you need fill this blank.",
		"restrain_max": 50,
		"restrain_min": 3,
		"restrain_prompt": "invalidate input"
	},

</code></pre>
