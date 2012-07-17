---
title: 问卷
---
# 问卷
  
<h2 id="p1">获取问卷列表</h2>
	GET /surveys
### 参数

per_page
: _可选_ *int* - 每页显示问卷数量  
  
* `20`（_默认_）
* `10`
* `50`
* `100`

sort 
: _可选_ *Enum* - 列表以什么方式排序

* `survey\_modify\_date` - 按照修改问卷时间排序
* `survey\_create\_date` - 按照创建问卷时间排序
* `survey\_titile` - 按照标题排序

select
: _可选_ *String* - 排序方式

* `ASC` 升序
* `DESC` 降序

###响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">
	{
		"id"： 1，
		"title"： "AdMaster 互联网用户使用习惯的调研",
		"identity": "六月第三波",
		"updated_at": "2012-09-06T20:39:23Z",
		"created_at": "2012-09-06T20:39:23Z",  
		"respondents_landing": 75362
		"respondents_responsed": 50000
		"respondents_finished":9836
	}
</code></pre>

  
<h2 id="p2">从新创建一份问卷</h2>
	POST /surveys 

###请求
<pre class="highlight">
<code class="language-javascript">
[
	{
		name: "Ipsos Online Survey",
	}

]
</code></pre>


<h2 id="p3">获取指定问卷的问卷属性</h2>
	GET /surveys/:id/options

###响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{

	"title"： "AdMaster 互联网用户使用习惯的调研",
	"identity": "六月第三波",
	"description": "AdMaster 正在进行一项有关用户使用习惯的调查，请您相信这不是在推销任何产品，也不会占用您太多时间。下面有几个问题，请您回答一下，以便帮助我们改善产品，为您提供更安全更方便的服务。认真填写调查问卷的用户，将有机会获得金山毒霸免费赠送的1个月QQ会员业务。非常感谢您的支持！",
	"logo": "http://www.surveymaster.com.cn/data/advIcon/1.jpg",
	"foot": ""这项调研由 AdMaster 旗下的 SurveyMaster 平台负责执行。您的资料将得到可靠的保护。",
	"language": "Chinese",
	"onepage": false,
	"progress_bar": true,
	"page_numbering": true,
	//"disable"不加载问题编号, "everypage"，每一页从头编号, "entire"全局编号
	"question_numbering": "entrie",
	"require_answer": true,

	//will be used only in collector
	"frequency_ctrl": true,

	*//Reserved feature*
	"Activity_ids": "1319,3290"

}
</code></pre>

<h2 id="p4"> 修改已有的问卷</h2>
	PATCH /surveys/:id
###请求
<pre class="highlight">
<code class="language-javascript">
[
	{

	"title": "AdMaster 互联网用户使用习惯的调研",
	"identity": "六月第三波"

	}
]
</code></pre>
