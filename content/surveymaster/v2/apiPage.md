---
title: SurveyMaster API - 页相关
---

#API - 页相关（共4个）

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
  "survey_id" : 112,
  "logic_ids" : [],
  "question_ids" : [],
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
    "logic_ids" : [],/* 逻辑id数组，顺序表示逻辑的优先级 */
    "question_ids" : [],
    "is_deleted" : "no"
}
</code></pre>

<h2 id="p3">3. 修改指定页</h2>

    PATCH /surveys/pages/:id

##请求

<pre class="highlight">
<code class="language-javascript">
{
  "question_ids" : [1, 2, 3],
  "logic_ids" : [1, 2, 3]
}
</code></pre>

###响应

<pre class="headers no-response">
<code>Status: 204 No Content
</code></pre>

<h2 id="p4">4. 删除指定页（标记状态）</h2>

    DELETE /surveys/pages/:id

* 只有空页才允许删除
* 删除页时，会删除相关逻辑

###响应

<pre class="headers no-response">
<code>Status: 204 No Content
Location: http://api.surveymaster.com.cn/surveys/112/pages
</code></pre>
