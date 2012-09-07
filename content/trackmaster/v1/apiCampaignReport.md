---
title: API - 项目报告接口
---

# API - 项目报告接口

<h2 id="p1">获取指定项目下有操作权限的项目报告列表</h2>

    GET /campaigns/:campaign_id/reports

###列表参数

`time`
: _必选_ *String* - 数据时间类型

* `hourly` 获取小时数据
* `daily` 获取日数据
* `weekly` 获取周数据
* `monthly` 获取月数据


`dims`
: _必选_ *String* - 数据聚合维度,多个选项直接用`,`分开

* `media` 按媒体维度聚合
* `placement` 按广告位维度聚合
* `keyword` 按关键字维度聚合
* `creative` 按创意维度聚合
* `geo` 按地域维度聚合
* `time` 按时间维度聚合

`network_media_id`
: _可选_ *Int* - 网络媒体ID

`placement_id`
: _可选_ *Int* - 广告位ID

`keyword_id`
: _可选_ *Int* - 关键字ID

`creative_id`
: _可选_ *Int* - 创意ID

`geo_id`
: _可选_ *Int* - 地域ID

`start_time`
: _可选_ *Hour* - 项目开始时间，会列出项目开始日期大于等于此设定的项目

`end_time`
: _可选_ *Hour* - 项目结束时间，会列出项目结束日期小于等于此设定的项目

`sort`
: _可选_ *String* - 列表排序以什么排序

* `time` - 按照时间排序
* `imp` - 按照曝光排序
* `clk` - 按照点击排序
* `uimp` - 按照独立曝光排序
* `uclk` - 按照独立点击排序


`direction`
: _可选_ *String* - 排序方式

* `asc` 升序 (_默认_)
* `desc` 降序


###列表响应

<pre class="headers">
<code>Status: 200 OK
Link: <http://api.trackmaster.com.cn/campaigns/12/reports?page=2>; rel="next",
      <http://api.trackmaster.com.cn/campaigns/12/reports?page=10>; rel="last"
</code></pre>
<pre class="highlight">
<code class="language-javascript">
[
  {
    "imp": 9183213,
    "uimp": 1183213,
    "clk": 12334,
    "uclk": 2334
  }
]
</code></pre>

关于错误返回值与错误代码，参见[错误代码说明][apiCommon]  

###字段说明

<table cellspacing="0" cellpadding="6" border="1">
  <tr>
    <td> 返回值字段 </td>
    <td> 字段类型 </td>
    <td> 字段说明 </td>
  </tr>
  <tr>
    <td>imp</td>
    <td>int</td>
    <td>曝光</td>
  </tr>
  <tr>
    <td>uimp</td>
    <td>int</td>
    <td>独立曝光</td>
  </tr>
  <tr>
    <td>clk</td>
    <td>int</td>
    <td>点击</td>
  </tr>
  <tr>
    <td>uclk</td>
    <td>int</td>
    <td>独立点击</td>
  </tr>
</table>

###适用版本

[v1.0][version]

[version]: /trackmaster/v1/apiVersion/
[apiCommon]:/trackmaster/v1/apiCommon/#p5
