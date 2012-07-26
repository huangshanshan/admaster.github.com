---
SurveyMaster API - 统计相关接口（共1个）
---

  
<h2 id="p1">1. 获取指定问卷的所有答案的统计信息</h2>
	GET /surveys/:id/stats
### 参数

collector_id
: _可选_ *int* - 渠道id  (获取指定问卷指定渠道的所有答案的统计信息)
  
* `2`
* `5`
* `16`
* `31`

###响应
<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
	"landing" : 7788256,
	"answered" : 4210000,
	"finished" : 1950000,
	"respondents" : 7788256,/* 答题人数量 */
	"first" : 123456789,/* 第一个答题人的答题时间 */
	"last" : 123456789,/* 最后一个答题人的答题时间 */
	"opendays" : 65,/* 问卷开放时间(天) */
	"questions" : [
		"1" : {/* 问题的id（自增 全局唯一） */
			"type" : "radio",/* ENUM radion:单选 checkbox:多选 text:单行文本 textarea:多行文本 */
			"title" : "我是一个单选",
			"skiped" : 5555,/* 跳过此题的受访者数量 */
			"answered" : 3167,/* 回答了此题的受访者数量 */
			"options" : [
				"1" : {/* 键代表选项id */
					"option" : "《九歌》",/* 选项名称 */
					"count" : 476,/* 选择了此选项的受访者数量 */
					"percent" : "40%"/* 选择了此选项的受访者百分比(注意：分母是什么？) */
				},
				"2" : {
					"option" : "《天问》",
					"count" : 140,
					"percent" : "15%"
				},
				"3" : {
					"option" : "《最炫民族风》",
					"count" : 48,
					"percent" : "5%"
				},
				"4" : {
					"option" : "《楚辞》",
					"count" : 194,
					"percent" : "20%"
				},
				"-1" : {
					"option" : "其他",
					"count" : 193,
					"percent" : "20%"
				}
			]
		},

		"2" : {
			"type" : "checkbox",
			"title" : "我是一个多选",
			"skiped" : 5555,
			"answered" : 3167,
			"options" : [
				"1" : {
					"option" : "美利坚合众国",
					"count" : 476,
					"percent" : "40%"
				},
				"2" : {
					"option" : "黑齿国",
					"count" : 140,
					"percent" : "15%"
				},
				"3" : {
					"option" : "恐龙王国",
					"count" : 48,
					"percent" : "5%"
				},
				"4" : {
					"option" : "犬封国",
					"count" : 194,
					"percent" : "20%"
				},
				"-1" : {
					"option" : "其他",
					"count" : 193,
					"percent" : "20%"
				}
			]
		},

		"3" : {
			"type" : "text",
			"title" : "我是一个单行文本",
			"skiped" : 5555,
			"answered" : 3167
		},

		"4" : {
			"type" : "textarea",
			"title" : "我是一个多行文本",
			"skiped" : 5555,
			"answered" : 3167
		}
	]
}
</code></pre>

