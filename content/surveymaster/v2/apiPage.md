---
title: SurveyMaster API - 问卷页相关
---

#API - 问卷页相关

<h2 id="p1">获取指定页的问题列表</h2>

    GET /surveys/:survey_id/pages/:page_id/questions

###参数

survey_id
: _必选_ *Int* - 问卷ID

page_id
: _必选_ *Int* - 页号

sort
: _可选_ *String* - 指定排序字段

direction
: _可选_ *String* - 排序方式，asc升序（默认），desc降序

###响应

<pre class="headers">
<code>Status: 200 OK
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
[
  {/* 单选题 */
    "id" : 1,
    "survey_id" : 112,
    "type" : "radio",
    "title" : "请问您的性别是：",
    "desc" : "",
    "logic" : 0,                /* logic不为0表示此题有显示逻辑 */
    "options" : ["男", "女"],
    "required" : {              /* 是否必填 */
      "status" : true,
      "prompt" : "请选择正确的性别选项"
    },
    "display" : {
      "style" : "radio",
      "perline" : 2,
      "random" : false
    },
    "other" : {
      "status" : true,
      "text" : "其他",
      "box" : {
        "status" : true,
        "min" : 1,
        "max" : 10,
        "prompt" : "请输入您的性别"
      }
    }
  },
  {/* 多选题 */
    "id" : 2,
    "survey_id" : 112,
    "type" : "checkbox",
    "title" : "请问您喜欢的明星是：",
    "desc" : "",
    "logic" : 0,                /* logic不为0表示此题有显示逻辑 */
    "options" : ["陈道明", "葛优"],
    "required" : {              /* 是否必填 */
      "status" : true,
      "prompt" : "请选择您喜欢的明星"
    },
    "display" : {
      "perline" : 2,
      "random" : false
    },
    "other" : {
      "status" : true,
      "text" : "其他",
      "box" : {
        "status" : true,
        "min" : 1,
        "max" : 10,
        "prompt" : "请输入您的性别"
      }
    },
    "exclusive" : {
      "status" : true,
      "text" : "以上都不是"
    }
  },
  {/* 单行文本 */
    "id" : 3,
    "survey_id" : 112,
    "type" : "text",
    "title" : "请输入您最喜欢的运动：",
    "desc" : "",
    "logic" : 0,                /* logic不为0表示此题有显示逻辑 */
    "limit" : {
      "type" : "char",          /* 支持：char/number/email/url/date */
      "prompt" : "请输入2 - 20个字符",
      "min" : 2,
      "max" : 20
    },
    "required" : {              /* 是否必填 */
      "status" : true,
      "prompt" : "请输入您最喜欢的运动"
    }
  },
  {/* 多行文本 */
    "id" : 4,
    "survey_id" : 112,
    "type" : "textarea",
    "title" : "请输入您平时锻炼的方式：",
    "desc" : "",
    "logic" : 0,                /* logic不为0表示此题有显示逻辑 */
    "limit" : {
      "type" : "char",          /* 支持：char/number/email/url/date */
      "prompt" : "请输入2 - 20个字符",
      "min" : 2,
      "max" : 20
    },
    "required" : {              /* 是否必填 */
      "status" : true,
      "prompt" : "请输入您最喜欢的运动"
    }
  }
]
</code></pre>

错误错误及代码参见TrackMaster API[错误代码说明][apiCommon]


<h2 id="p3">创建页</h2>

    POST /surveys/:survey_id/pages

###参数

survey_id
: _必选_ *Int* - 问卷ID

questions
: _可选_ *String* - 问题列表，以逗号分隔

###请求

<pre class="highlight">
<code class="language-javascript">
{
  "survey_id" : 112,
  "questions" : "1, 2, 3"
}
</code></pre>

###响应

<pre class="headers">
<code>Status: 201 CREATED
Location: http://api.surveymaster.com.cn/survey
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
  "id" : 1,
  "survey_id" : 112,
  "questions" : [1, 2, 3],
}
</code></pre>

<h2 id="p4">获取指定页详情</h2>

    GET /surveys/:survey_id/pages/:page_id

###参数

survey_id
: _必选_ *Int* - 问卷ID

page_id
: _必选_ *Int* - 页号

###响应
<pre class="headers">
<code>Status: 200 OK
Location: http://api.surveymaster.com.cn/surveys
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
  "survey_id" : 112,
  "page_id" : 1,
  "questions" : [1, 2, 3],
}
</code></pre>

<h2 id="p5">修改指定页</h2>

    PATCH /surveys/:survey_id/pages/:page_id

###参数

survey_id
: _必选_ *Int* - 问卷ID

page_id
: _必选_ *Int* - 页号

questions
: _必选_ *String* - 问题ID列表

##请求

<pre class="highlight">
<code class="language-javascript">
{
  "survey_id" : 112,
  "page_id" : 1,
  "questions" : "1, 2, 3"
}
</code></pre>

###响应
<pre class="headers">
<code>Status: 204 NO CONTENT
Location: http://api.surveymaster.com.cn/surveys
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
</code></pre>

<h2 id="p6">删除指定页（标记状态）</h2>

    DELETE /surveys/:survey_id/pages/:page_id

###参数

survey_id
: _必选_ *Int* - 问卷ID

page_id
: _必选_ *Int* - 页号

###请求

<pre class="highlight">
<code class="language-javascript">
{
  "survey_id" : 112,
  "page_id" : 1
}
</code></pre>

###响应
<pre class="headers">
<code>Status: 204 NO CONTENT
Location: http://api.surveymaster.com.cn/surveys
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
</code></pre>
