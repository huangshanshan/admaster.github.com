---
title: 问卷渠道 - EDM
---
# 问卷渠道 - EDM

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
		}
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
<h2 id="p2">获取EDM渠道信息</h2>

	GET /collector/:id

### 响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">

	{
		//basic info
		"collector_id": "1",
		"collector_name": "abc..."
		"collector_type": "open_link",
		"status": "open",
		"landing": 100000,
		"answered": 10000,
		"finished": 1000,
	
		//advanced
		"password": "123456",
		"dead_line": "2012-12-23",
		"max_count": 5000,
		"freq_control": true,
		
		//contacts

		"contacts_total": 600,
		"unsent": 200,
		"sent": 400,
		"click": 300,
		"answered": 200,
		"finished": 100,
		"fail":20,
		
		//mails

		"mails_total": 5,
		"draft": 2,
		"scheduled": 3,
		"sending": 2,
		"mailed": 1,
		
	}
</code></pre>

<h2 id="p3">获取EDM指定渠道下的联系人信息</h2>

	get /collectors/:collector_id/contacts/:contact_id

### 响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">	
	
	[
		{
			"email": "abc@admaster.com.cn",
			"firstname": "Vincent",
			"lastname": "Yan",
			"memo": "CEO",
			"send_status": "sent/unsent/fail",
			//click, answered, finished
			"answer_status": "click",
		}
		{
			"email": "abc@admaster.com.cn",
			"firstname": "Vincent",
			"lastname": "Yan",
			"memo": "CEO",
			"send_status": "sent/unsent/fail",
			//click, answered, finished
			"answer_status": "click",
		}
		{
			"email": "abc@admaster.com.cn",
			"firstname": "Vincent",
			"lastname": "Yan",
			"memo": "CEO",
			"send_status": "sent/unsent/fail",
			//click, answered, finished
			"answer_status": "click",
		}
	]
</code></pre>

<h2 id="p4">获取EDM指定渠道下的联系人信息</h2>

	get /collectors/:collector_id/contacts/:contact_id


### 参数

filter

* `sent`
* `unsent`
* `answered`
* `unanswered`
* `fail`

per_page
: _可选_ *int*，每页显示问卷数量。  

* `20`（_默认_）
* `10`
* `50`
* `100`


<h2 id="p5">添加联系人</h2>

	POST /collectors/:collector_id/contacts/

###请求
<pre class="highlight">
<code class="language-javascript">
	{
		"email": "abc@admaster.com.cn",
		"firstname": "Vincent",
		"lastname": "Yan",
		"memo": "CEO"
	}
</code></pre>
---

<h2 id="p6">获取邮件列表</h2>

	get /collector/:collector_id/mails

### 响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">	

	[
		{
			"mail_id": "111",
			"title": "abcde...",
			"status": "draft/scheduled/sending/mailed"
		},
		{
			"mail_id": "111",
			"title": "abcde...",
			"status": "draft/scheduled/sending/mailed"
		},
		{
			"mail_id": "111",
			"title": "abcde...",
			"status": "draft/scheduled/sending/mailed"
		}
	]
	
</code></pre>

<h2 id="p7">获取指定邮件信息</h2>

	GET /collector/:collector_id/mails/:mail_id

### 响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">	

	{
		"mail_id": "111",
		"title": "abcde...",
		"content": "abcdefg..."
		"status": "draft/scheduled/sending/mailed",
		//need detail
		"relevant_contacts": "relevant_id",
		"scheduled_datetime": "2012-12-23 23:23:31"
	}

</code></pre>

<h2 id="p8">创建一个新的邮件</h2>

	POST /collector/:collector_id/mails

###请求
<pre class="highlight">
<code class="language-javascript">

	{	
		"title": "abcde...",
		"content": "abcdefg..."
		"contacts"
		[
			"contact_id": "1",
			"contact_id": "1",
			"contact_id": "1",
			"contact_id": "1",
			"contact_id": "1",
		],
		"send_way": "draft/now/scheduled",
		"scheduled_time": "2012-12-23 07:00:00"
	}

</code></pre>

	