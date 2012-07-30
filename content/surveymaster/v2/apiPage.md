---
SurveyMaster API - 问题相关接口（共4个）
---

<h2 id="p1">1. 创建页</h2>
	POST /surveys/:survey_id/pages

###参数

	survey_id
		: _必选_ *Int* - 问卷ID

	questions
		: _可选_ *Array* - 问题列表

###请求

	{
	  "survey_id" : 112,
	  "questions" : [1, 2, 3]
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
	  "questions" : [
		{
			"_id" : ObjectId("500916d3337d221abed72ac3"),
			"id" : 1,/* 问题的id（自增 全局唯一） */
			"type" : "radio",/* ENUM radion:单选 checkbox:多选 text:单行文本 textarea:多行文本 */
			"title" : "我是一个单选",
			"desc" : "我是一个单选题啊单选题",
			"options" : [/* 数组value为选项内容，数组key为选项的id，数组的顺序即是选项的显示顺序 */
				"option_1",
				"option_2",
				"option_3"
			],
			"logic_id" : 0,/* 逻辑id，0表示此题没有任何逻辑 */
			"quotes" : [],/* 引用题的question_id数组（注意：引用题只能引用当前页之前的题） */
			"other" : {/* 其他选项（注意：这是一个特殊选项，其id为-1） */
				"status" : true,/* 是否显示其他选项 */
				"text" : "其他",/* 自定义选项名称 */
				"box" : {/* 输入框 */
					"status" : true,/* 是否出现输入框 */
					"min" : 1,/* 允许输入的最少字符数 */
					"max" : 10,/* 允许输入的最多字符数 */
					"prompt" : "当输入值不合法时，出现提示"/* 当输入框中的字符数不符合要求时的提示信息 */
				}
			},
			"required" : {/* 必答 */
				"status" : true,/* 是否设为必答题 */
				"prompt" : "这一项是必填的噢！"/* 没有回答时的提示信息 */
			},
			"display" : {/* 显示相关 */
				"style" : "radio/select",/* ENUM radio:单选按钮 select:单选下拉列表(注意：上面的other.status为true时，other的前端实现要与此设置保持一致) */
				"perline" : 2,/* 每行显示选项数（注意：当上面的display.style设置为select时此设置无意义） */
				"random" : false/* 是否随机显示选项（注意：顺序打乱 id不能变） */
			}
		},
                {
                        /*另一问题*/
                }
            ]
	}

<h2 id="p3">3. 修改指定页</h2>

	PATCH /surveys/:survey_id/pages/:page_id

###参数

	survey_id
		: _必选_ *Int* - 问卷ID

	page_id
		: _必选_ *Int* - 页号

	questions
		: _必选_ *Array* - 问题ID列表

##请求

	{
	  "survey_id" : 112,
	  "page_id" : 1,
	  "questions" : [1, 2, 3]
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