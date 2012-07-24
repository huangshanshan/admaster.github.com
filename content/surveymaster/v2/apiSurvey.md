---

**SurveyMaster API - 问卷相关接口**

---

#1. 获取问卷列表

<code>

	GET /surveys

</code>

##参数

owner（必填）

* 建立者ID
* 只提取指定用户建立的问题

fields（可选）

* 指定提取的字段列表，以逗号分隔

sort（可选）

* 指定排序方式
* 例：created:-1 -> 按建立时间倒序排列
* 1为升序排列，-1为倒序排列，默认为升序排列
* 默认排序为: modified: -1

start_time/end_time（可选）

* 指定提取问卷列表（created）的开始及结束时间
* 不指定start_time，则不限定开始时间
* 不指定end_time，则不限定结束时间

start/limit（可选）

* 指定返回结果集区间
* 不指定start，则从开始取limit条文档
* 不指定limit，则取从start开始的所有文档

##成功返回

<code>

	{
		ErrorCode: 0
		Data: {
			112: {
				"id" : 112,
				"title" : "伊利8月新生活",
				"label" : "第一波",
				"owner" : 123,
				"created" : "123456789",
				"modified" : "123456789",
				"landing" : 50000,
				"answered" : 30000,
				"finished" : 5000,
				"head" : "首先感谢您参与我们的问卷调查。完成调查的每位用户均有机会参与抽奖,本次调查设置的奖项是：国际知名品牌提供的运动服及运动鞋。请根据您的实际情况逐项填写,您的意见或建议对我们很重要,完成问卷只需花费您短短五分钟",
				"foot" : "这项调查是由AdMaster精硕科技公司携手伊利集团共同执行。AdMaster是知名的专业第三方网络广告效果监测及调研公司,您的资料将得到可靠的保护",
				"progress" : true,
				"logo" : "http://domain.com/img/logo.gif",
				"lang" : "en",
				"onepage" : false,
				"page_numbering" : true,
				"question_numbering" : "global",
				"pages" : [1,2,3,4,5,6]
			},
			211: {
				#另一文档数据
			}
		}
	}

</code>

##错误返回

<code>

	{
		ErrorCode: 1101,
		Message: 参数错误，owner不能为空
	}

</code>

<code>
	
	1101: owner为空
	1102: fields中包含不存在的字段
	1103: sort中包含不存在的字段
	1104: start_time/end_time应使用timestamp格式
	1105: start/limit必须为数字

</code>

#2. 创建问卷

<code>

	POST /survey

</code>

##参数

<code>

	{
		"title" : "伊利8月新生活",						/* 问卷标题 */
		"label" : "第一波",								/* 问卷说明 */
		"owner" : 123,									/* 创建者ID */
		"head" : "首先感谢您参与我们的问卷调查。",			/* 问卷头信息 */
		"foot" : "这项调查是由AdMaster精硕科技公司携手伊利集团共同执行。",		/* 问卷尾信息 */
		"progress" : true,								/* 是否显示进度条 */
		"logo" : "http://domain.com/img/logo.gif",		/* LOGO图标地址 */
		"lang" : "en",									/* 语言 */
		"onepage" : false,								/* 是否在一页显示 */
		"page_numbering" : true,						/* 是否在每一页显示问题重新编号 */
		"question_numbering" : "global"					/* 问题编号采用全局方式(global)或是页内方式(in_page) */
	}

</code>

##成功返回

<code>

	{
		ErrorCode: 0,
		Data: {
			survey_id: 111
		}
	}

</code>

##错误返回

<code>

	{
		ErrorCode: 1201,
		Message: "参数错误，title不能为空"
	}

</code>

<code>

	1201: title为空
	1202: title字数过少或过长
	1203: owner为空
	1204: progress必须为boolean值
	1205: onepage必须为boolean值
	1206: page_numbering必须为boolean值
	1207: question_numbering必须为global或in_page中的一个

</code>

#3. 获取指定问卷详情

<code>

	GET /survey/:survey_id

</code>

##参数

owner（必填）

* 建立者ID

survey_id（必填）

* 问卷ID

##成功返回

<code>

	{

		ErrorCode: 0
		Data: {
			112: {
				"id" : 112,
				"title" : "伊利8月新生活",
				"label" : "第一波",
				"owner" : 123,
				"created" : "123456789",
				"modified" : "123456789",
				"landing" : 50000,
				"answered" : 30000,
				"finished" : 5000,
				"head" : "首先感谢您参与我们的问卷调查。完成调查的每位用户均有机会参与抽奖,本次调查设置的奖项是：国际知名品牌提供的运动服及运动鞋。请根据您的实际情况逐项填写,您的意见或建议对我们很重要,完成问卷只需花费您短短五分钟",
				"foot" : "这项调查是由AdMaster精硕科技公司携手伊利集团共同执行。AdMaster是知名的专业第三方网络广告效果监测及调研公司,您的资料将得到可靠的保护",
				"progress" : true,
				"logo" : "http://domain.com/img/logo.gif",
				"lang" : "en",
				"onepage" : false,
				"page_numbering" : true,
				"question_numbering" : "global",
				"pages" : [1,2,3,4,5,6]
			}
		}
	}

</code>

##错误返回

<code>

	{
		ErrorCode: 1301,
		Message: 参数错误，owner不能为空
	}

</code>

<code>
	
	1301: owner为空
	1302: survey_id为空
	1303: survey_id与owner从属关系错误

</code>

#4. 修改指定问卷

<code>

	PATCH /survey/:survey_id

</code>

##参数

<code>

	{
		"title" : "伊利8月新生活",						/* 问卷标题 */
		"label" : "第一波",								/* 问卷说明 */
		"head" : "首先感谢您参与我们的问卷调查。",			/* 问卷头信息 */
		"foot" : "这项调查是由AdMaster精硕科技公司携手伊利集团共同执行。",		/* 问卷尾信息 */
		"progress" : true,								/* 是否显示进度条 */
		"logo" : "http://domain.com/img/logo.gif",		/* LOGO图标地址 */
		"lang" : "en",									/* 语言 */
		"onepage" : false,								/* 是否在一页显示 */
		"page_numbering" : true,						/* 是否在每一页显示问题重新编号 */
		"question_numbering" : "global"					/* 问题编号采用全局方式(global)或是页内方式(in_page) */
	}

</code>

##成功返回

<code>

	{
		ErrorCode: 0,
		Data: {
			survey_id: 112
		}
	}

</code>

##错误返回

<code>
	
	{
		ErrorCode: 1401,
		Message: 参数错误，owner不能为空
	}

</code>

<code>
	
	1401: title为空
	1402: title字数过少或过长
	1403: progress必须为boolean值
	1404: onepage必须为boolean值
	1405: page_numbering必须为boolean值
	1406: question_numbering必须为global或in_page中的一个

</code>

#5. 删除指定问卷（标记状态）

<code>

	DELETE /survey/:survey_id

</code>

##参数

owner（必填）

* 建立者ID

survey_id（必填）

* 问卷ID

##成功返回

<code>

	{
		ErrorCode: 0,
		Data: {
			survey_id: 112
		}
	}

</code>

##错误返回

<code>

	{
		ErrorCode: 1501,
		Message: 参数错误，owner不能为空
	}

</code>

<code>

	1501: owner为空
	1502: survey_id为空
	1503: survey_id与owner从属关系错误

</code>
