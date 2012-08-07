---
title: SurveyMaster API - 页相关
---

#API - 页相关（共3个）

<h2 id="p1">1. 创建页</h2>

    POST /surveys/:survey_id/pages

###响应

<pre class="headers">
<code>Status: 201 Created
Location: http://api.surveymaster.com.cn/surveys/123/pages
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
  "id" : 1,
  "url" : 'http://api.surveymaster.com.cn/surveys/pages/1',
  "survey_id" : 112,    /* 问卷ID */
  "order_num" : 1,   /* 显示顺序 */
  "is_deleted" : "no"
}
</code></pre>

<h2 id="p2">2. 获取指定页详情</h2>

    GET /surveys/pages/:id

###响应

<pre class="headers">
<code>Status: 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">
{
    "id" : 1,
    "url" : 'http://api.surveymaster.com.cn/surveys/pages/1',
    "survey_id" : 112,
    "order_num" : 1,   /* 显示顺序 */
    "is_deleted" : "no"
}
</code></pre>

<h2 id="p3">3. 修改指定页</h2>

    PATCH /surveys/pages/:id

##请求

<pre class="highlight">
<code class="language-javascript">
{
    "order_num" : 1,   /* 显示顺序 */
    "is_deleted" : "no"
}
</code></pre>

###响应

<pre class="headers no-response">
<code>Status: 204 No Content
</code></pre>


