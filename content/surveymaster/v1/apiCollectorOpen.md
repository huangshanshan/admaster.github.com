---
title: 问卷渠道 - 开放链接
---
# 问卷渠道 - 开放链接

<h2 id="p1">获取指定问卷的所有渠道</h2>

	GET /survey/:survey_id/collectors

### 响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">

	[
		{
			"collector_id": "1",
			"collector_type": "open_link",
			"collector_name": "abc",
			"status": "open",
			"landing": 100000,
			"answered": 10000,
			"finished": 1000,
		},
		{
			"collector_id": "2",
			"collector_type": "EDN",
			"collector_name": "abcd",
			"status": "closed",
			"landing": 100000,
			"answered": 10000,
			"finished": 1000,
			"respondents": 200000
		}
	]
</code></pre>

<h2 id="p2">获取开放链接的渠道信息</h2>

	GET /collectors/:id

### 响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">

	{
		//basic info
		"id": "1",
		"name": "abc..."
		"type": "open_link",
		"status": "open",
		"landing": 100000,
		"answered": 10000,
		"finished": 1000,
	
		//advanced
		"password": "123456",
		"dead_line": "2012-12-23",
		"max_count": 5000,
		"freq_control": true,
		
		//
		"access_url": "http://surveymaster.com.cn/s/7Qix84&12"
		//Based on api 
		//Frontstage required	
		//

		
		"redirect": "http://surveymaster.com.cn",
		"thanks_page": "Thank you for your answering...",
		
		//interface
		"cross_status": "active"
		"cross_id_name": "psid",
		//http://jisiba.html/?psid=i9u8y7t&result=1
		"cross_response": "http://jisiba.html/",

		//screening
		"judge_activity": "2123,1394,200130";
		"expusred": "http://www.surveymaster.com.cn/survey/zWGiMTT"
		"control": "http://www.surveymaster.com.cn/survey/zWGJhzW"

	}

</code></pre>

	