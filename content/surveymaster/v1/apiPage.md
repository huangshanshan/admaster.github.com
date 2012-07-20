---
title: 问卷页 
---
# 问卷页
<h2 id="p1">获取指定问卷下的所有页</h2>

		GET /surveys/survey_id/pages

### 响应
<pre class="headers">
<code>Status 200 OK
</code></pre>
<pre class="highlight">
<code class="language-javascript">

	{
 		id: "p0001" //页面的id
		question_amount: 4 //此页所包含的问题数量
        post_logic: true //此页有无基于页面的后置逻辑
        questions:
		[
			question:
			{
				question_id: "q0001", //问题id
				title: "您的性别是？", //问题的标题
				type: "single_choice", //问题类型，单选
				number: "1", //问题在所属页的顺序
			},
			question:
			{
				question_id: "q0001", //问题id
				title: "您的性别是？", //问题的标题
				type: "single_choice", //问题类型，单选
				number: "1", //问题在所属页的顺序
			},
			question:
			{
				question_id: "q0001", //问题id
				title: "您的性别是？", //问题的标题
				type: "single_choice", //问题类型，单选
				number: "1", //问题在所属页的顺序
			},
			question:
			{
				question_id: "q0001", //问题id
				title: "您的性别是？", //问题的标题
				type: "single_choice", //问题类型，单选
				number: "1", //问题在所属页的顺序
			}
		]  
	}

</code></pre>

		

		
		