---
title: 监控 - 筛选功能
---
//Lastest Data Report Board   
//Lastest not means realtime
# 监控 - 筛选功能

<h2 id="p1">获取指定筛选条件下的问卷内容</h2>

	GET /surveys/:survey_id/collectors

###参数

survey _ id  
:_可选_ *int* - 所要筛选的问卷ID

collector _ id  
:_可选_ *int* - 所要筛选的渠道ID  

start _ date
:_可选_ *date* - 筛选的开始时间

end _ date
:_可选_ *date* - 筛选的结束时间

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
        "average_time": 10分20秒
        "avg_amount":998
    }

</code></pre>


<h2 id="p2">添加board</h2>

	POST /boards

###请求
<pre class="highlight">
<code class="language-javascript">
[
	{
		num: 4,//最多5个
	}

]
</code></pre>

<h2 id="p3">编辑board</h2>

	PATCH /boards

<h2 id="p4">删除board</h2>

	DELETE /board/:id

### 响应
<pre class="headers">
<code>Status: 204 No Content
</code></pre>





