---
SurveyMaster API - 问题相关接口（共4个）
---

<h2 id="p1">1. 创建页</h2>
	POST /surveys/:survey_id/pages

###参数

	survey_id
		: _必选_ *Int* - 问卷ID

	questions
		: _可选_ *String* - 问题列表，以逗号分隔

###请求

	{
	  "survey_id" : 112,
	  "questions" : "1, 2, 3"
	}

###响应

> Status: 201 CREATED

> Location: http://api.surveymaster.com.cn/survey

> X-RateLimit-Limit: 5000

> X-RateLimit-Remaining: 4999

	{
	  "id" : 1,
	  "survey_id" : 112,
	  "questions" : [1, 2, 3],
	}

<h2 id="p2">2. 获取指定页详情</h2>
	GET /surveys/:survey_id/pages/:page_id

###参数

	survey_id
		: _必选_ *Int* - 问卷ID

	page_id
		: _必选_ *Int* - 页号

###响应

> Status: 200 OK

> Location: http://api.surveymaster.com.cn/surveys

> X-RateLimit-Limit: 5000

> X-RateLimit-Remaining: 4999

	{
	  "survey_id" : 112,
	  "page_id" : 1,
	  "questions" : [1, 2, 3],
	}

<h2 id="p3">3. 修改指定页</h2>

	PATCH /surveys/:survey_id/pages/:page_id

###参数

	survey_id
		: _必选_ *Int* - 问卷ID

	page_id
		: _必选_ *Int* - 页号

	questions
		: _必选_ *String* - 问题ID列表

##请求

	{
	  "survey_id" : 112,
	  "page_id" : 1,
	  "questions" : "1, 2, 3"
	}

###响应

>Status: 204 NO CONTENT

> Location: http://api.surveymaster.com.cn/surveys

> X-RateLimit-Limit: 5000

> X-RateLimit-Remaining: 4999

<h2 id="p4">4. 删除指定页（标记状态）</h2>
	DELETE /surveys/:survey_id/pages/:page_id

###参数

	survey_id
		: _必选_ *Int* - 问卷ID

	page_id
		: _必选_ *Int* - 页号

###请求

	{
	  "survey_id" : 112,
	  "page_id" : 1
	}

###响应

> Status: 204 NO CONTENT

> Location: http://api.surveymaster.com.cn/surveys

> X-RateLimit-Limit: 5000

> X-RateLimit-Remaining: 4999
