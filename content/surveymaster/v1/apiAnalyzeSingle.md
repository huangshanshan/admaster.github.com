---
title: 查看单个分析
---
# 查看单个分析

<h2 id="p1">获取指定问卷的所有答案</h2>

	GET /surveys/:survey_id/respondents

### 参数

collector	

* `参数空` (为获取所有渠道)  
* `渠道 id` （该问卷下的渠道 id ， 只能一个）

per_page  
: _可选_ *int*，每页显示问卷数量。  

* `20`（_默认_）
* `10`
* `50`
* `100`

### 响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">	

	[	
		{
			"respondent_id": "1",
			"collector_name": "Open_link_001",
			"created": "2012-12-23 08:23",
			"submited": "2012-12-23 23:59",
		}
		{
			"respondent_id": "1",
			"collector_name": "EDM_001",
			"started": "2012-12-23 08:23",
			"submited": "2012-12-23 23:59",
		}
	]
</code></pre>

<h2 id="p2">获取单个答案</h2>

	GET /respondents/:id

### 响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">
	
	{
		"respondent_id": "1",
		"respondent_name": "Dongling Zhao",
		"collector_name": "youku_视频弹窗_开放链接_001",
		"started": "2012-12-23 08:23",
		"submited": "2012-12-23 23:59",
		"ip_address": 123.123.123.1,
		"email": "zhaodongling@admaster.com.cn",
		"Location": "Beijing",
		"questions": 
		[
			{	
				"question_id": "1",
				"title": "你的性别是？",
				"type": "single_choice",
				"selected": "",
				"other":"",
				"specify": "原地满状态复活"
			}
			{	
				"question_id": "2",
				"title": "你喜欢什么歌",
				"type": "multiple_choices",
				"selcted"
				[	
					"selected": "爱情买卖",
					"selected": "忐忑",
					"selected": "伤不起",
					"other": "其他",
					"specify": ""
				]
			}
			{	
				"question_id": "3",
				"title": "你的电话",
				"type": "single_input",
				"input_content": "13928371823",
			}
		]
	}
</code></pre>