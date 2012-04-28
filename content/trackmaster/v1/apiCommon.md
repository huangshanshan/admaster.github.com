---
title: API - 接口定义 - 通用说明
---

# API - 接口定义 - 通用说明

<h2 id="p1">全局名称定义</h2>
![trackmast结构示意图](/images/trackmaster.png)
<em>待添加</em>


<h2 id="p2">通用参数说明</h2>

* #### access_token
	oauth 验证串，通过授权验证可以得到，请求授权数据的时候需要携带，具体查看[oauth 验证][apiOauth]
	
* #### start
	获取列表数据时，指定返回的结果开始位置，用来实现分页

* #### count
	获取列表数据是，指定返回的结果条目数，最大值为50

* #### q
	提供搜索功能的接口可以指定 q 来实现搜索，搜索一般为名称的部分或 id 的全部


<h2 id="p3">通用元素说明</h2>

<em> 通用元素是指请求数据返回的结果中的一些通用的含义 </em>

* ####id
	元素中的 id 为该元素的唯一标识，全局唯一，特例的话会特别说明

* ####_total
	获取列表数据时，total 为符合条件的记录总数，客户端程序用请求参数中的 start, count 和元素中的 total 来实现分页功能.

* ####_list
	获取列表数据时，具体的结果集和会放在 list 元素下，list 为数组格式，需要配合分页来呈现

* ####_all
	获取所有数据时，具体的结果集会放在 all 元素下，all 为数组格式，all 的结果不需要分页

* ####dateline
	dateline代表的是该数据产生的时间，用时间戳(int 型)来表示

* ####error_code
	错误码，在调用接口的时候发生内部逻辑错误时，在得到的结果中会有 error_code，具体参考本页下方的错误码字典

* ####error_msg
	同上，在内部错误的时候，会有 error_msg 记录这错误的信息

<h2 id="p4">返回状态说明</h2>

**返回状态在请求返回的头部信息**
	
* ####200 OK
	请求成功，只是请求成功，不代表没有逻辑错误，逻辑错误记录在 error_code, error_msg 元素中

* ####201 CREATED
	创建成功

* ####202 ACCEPTED
	更新、修改成功

* ####400 BAD REQUEST
	请求地址不存在或者带有不支持的参数

* ####401 UNAUTHORIZED
	未经授权

* ####403 FORBIDDEN
	禁止访问

* ####404 NOT FOUND
	请求的资源不存在

* ####500 INTERNAL SERVER ERROR
	服务器内部错误

<h2 id="p5">错误代码说明</h2>

<em>待续</em>

[apiOauth]: /trackmaster/v1/apiOauth/
