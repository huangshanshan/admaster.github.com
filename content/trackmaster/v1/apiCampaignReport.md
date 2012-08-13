---
title: API - 项目报告接口
---

# API - 项目报告接口

<h2 id="p1">获取指定项目下有操作权限的项目报告</h2>

###列表参数

start\_time
: _可选_ *Hour* - 项目开始时间，会列出项目开始日期大于等于此设定的项目

end\_time
: _可选_ *Hour* - 项目结束时间，会列出项目结束日期小于等于此设定的项目

sort
: _可选_ *String* - 列表排序以什么排序

* `time` - 按照时间排序
* `imp` - 按照曝光排序
* `clk` - 按照点击排序
* `uimp` - 按照独立曝光排序
* `uclk` - 按照独立点击排序

direction
: _可选_ *String* - 排序方式

* `asc` 升序 (_默认_)
* `desc` 降序

###列表响应
<pre class="headers">
<code>Status: 200 OK
Link: <http://api.trackmaster.com.cn/campaigns/12/daily_reports?page=2>; rel="next",
      <http://api.trackmaster.com.cn/campaigns/12/daily_reports?page=10>; rel="last"
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

###接口列表

    # 获取项目报告按小时数据列表
    GET /campaigns/:campaign_id/hourly_reports

    # 获取指定项目报告小时数据
    GET /campaigns/:campaign_id/hourly_reports/:hour

    # 获取项目报告按日数据列表
    GET /campaigns/:campaign_id/daily_reports

    # 获取指定项目报告日数据
    GET /campaigns/:campaign_id/daily_reports/:day

    # 获取项目报告按周数据列表
    GET /campaigns/:campaign_id/weekly_reports

    # 获取指定项目报告周数据
    GET /campaigns/:campaign_id/weekly_reports/:week

    # 获取项目报告按月数据列表
    GET /campaigns/:campaign_id/monthly_reports

    # 获取指定项目报告月数据
    GET /campaigns/:campaign_id/monthly_reports/:month

    # 获取项目媒体报告按小时数据列表
    GET /campaigns/:campaign_id/medias/:network_media_id/hourly_reports

    # 获取指定项目媒体报告小时数据
    GET /campaigns/:campaign_id/medias/:network_media_id/hourly_reports/:hour

    # 获取项目媒体报告按日数据列表
    GET /campaigns/:campaign_id/medias/:network_media_id/daily_reports

    # 获取指定项目媒体报告日数据
    GET /campaigns/:campaign_id/medias/:network_media_id/daily_reports/:day

    # 获取项目媒体报告按周数据列表
    GET /campaigns/:campaign_id/medias/:network_media_id/weekly_reports

    # 获取指定项目媒体报告周数据
    GET /campaigns/:campaign_id/medias/:network_media_id/weekly_reports/:week

    # 获取项目媒体报告按月数据列表
    GET /campaigns/:campaign_id/medias/:network_media_id/monthly_reports

    # 获取指定项目媒体报告月数据
    GET /campaigns/:campaign_id/medias/:network_media_id/monthly_reports/:month

    # 获取项目媒体广告位报告按小时数据列表
    GET /campaigns/:campaign_id/medias/:network_media_id/placements/:placement_id/hourly_reports

    # 获取指定项目媒体广告位报告小时数据
    GET /campaigns/:campaign_id/medias/:network_media_id/placements/:placement_id/hourly_reports/:hour

    # 获取项目媒体广告位报告按日数据列表
    GET /campaigns/:campaign_id/medias/:network_media_id/placements/:placement_id/daily_reports

    # 获取指定项目媒体广告位报告日数据
    GET /campaigns/:campaign_id/medias/:network_media_id/placements/:placement_id/daily_reports/:day

    # 获取项目媒体广告位报告按周数据列表
    GET /campaigns/:campaign_id/medias/:network_media_id/placements/:placement_id/weekly_reports

    # 获取指定项目媒体广告位报告周数据
    GET /campaigns/:campaign_id/medias/:network_media_id/placements/:placement_id/weekly_reports/:week

    # 获取项目媒体广告位报告按月数据列表
    GET /campaigns/:campaign_id/medias/:network_media_id/placements/:placement_id/monthly_reports

    # 获取指定项目媒体广告位报告月数据
    GET /campaigns/:campaign_id/medias/:network_media_id/placements/:placement_id/monthly_reports/:month

    # 获取项目媒体广告位关键字报告按小时数据列表
    GET /campaigns/:campaign_id/medias/:network_media_id/placements/:placement_id/keywords/:keyword_id/hourly_reports

    # 获取指定项目媒体广告位关键字报告小时数据
    GET /campaigns/:campaign_id/medias/:network_media_id/placements/:placement_id/keywords/:keyword_id/hourly_reports/:hour

    # 获取项目媒体广告位关键字报告按日数据列表
    GET /campaigns/:campaign_id/medias/:network_media_id/placements/:placement_id/keywords/:keyword_id/daily_reports

    # 获取指定项目媒体广告位关键字报告日数据
    GET /campaigns/:campaign_id/medias/:network_media_id/placements/:placement_id/keywords/:keyword_id/daily_reports/:day

    # 获取项目媒体广告位关键字报告按周数据列表
    GET /campaigns/:campaign_id/medias/:network_media_id/placements/:placement_id/keywords/:keyword_id/weekly_reports

    # 获取指定项目媒体广告位关键字报告周数据
    GET /campaigns/:campaign_id/medias/:network_media_id/placements/:placement_id/keywords/:keyword_id/weekly_reports/:week

    # 获取项目媒体广告位关键字报告按月数据列表
    GET /campaigns/:campaign_id/medias/:network_media_id/placements/:placement_id/keywords/:keyword_id/monthly_reports

    # 获取指定项目媒体广告位关键字报告月数据
    GET /campaigns/:campaign_id/medias/:network_media_id/placements/:placement_id/keywords/:keyword_id/monthly_reports/:month

    # 获取项目地域报告按小时数据列表
    GET /campaigns/:campaign_id/geos/:geo_id/hourly_reports

    # 获取指定项目地域报告小时数据
    GET /campaigns/:campaign_id/geos/:geo_id/hourly_reports/:hour

    # 获取项目地域报告按日数据列表
    GET /campaigns/:campaign_id/geos/:geo_id/daily_reports

    # 获取指定项目地域报告日数据
    GET /campaigns/:campaign_id/geos/:geo_id/daily_reports/:day

    # 获取项目媒体地域报告按小时数据列表
    GET /campaigns/:campaign_id/medias/:network_media_id/geos/:geo_id/hourly_reports

    # 获取指定项目媒体地域报告小时数据
    GET /campaigns/:campaign_id/medias/:network_media_id/geos/:geo_id/hourly_reports/:hour

    # 获取项目媒体地域报告按日数据列表
    GET /campaigns/:campaign_id/medias/:network_media_id/geos/:geo_id/daily_reports

    # 获取指定项目媒体地域报告日数据
    GET /campaigns/:campaign_id/medias/:network_media_id/geos/:geo_id/daily_reports/:day

    # 获取项目媒体广告位地域报告按小时数据列表
    GET /campaigns/:campaign_id/medias/:network_media_id/placements/:placement_id/geos/:geo_id/hourly_reports

    # 获取指定项目媒体广告位地域报告小时数据
    GET /campaigns/:campaign_id/medias/:network_media_id/placements/:placement_id/geos/:geo_id/hourly_reports/:hour

    # 获取项目媒体广告位地域报告按日数据列表
    GET /campaigns/:campaign_id/medias/:network_media_id/placements/:placement_id/geos/:geo_id/daily_reports

    # 获取指定项目媒体广告位地域报告日数据
    GET /campaigns/:campaign_id/medias/:network_media_id/placements/:placement_id/geos/:geo_id/daily_reports/:day

    # 获取项目创意报告按小时数据列表
    GET /campaigns/:campaign_id/creatives/:creative_id/hourly_reports

    # 获取指定项目创意报告小时数据
    GET /campaigns/:campaign_id/creatives/:creative_id/hourly_reports/:hour

    # 获取项目媒体创意报告按小时数据列表
    GET /campaigns/:campaign_id/medias/:network_media_id/creatives/:creative_id/hourly_reports

    # 获取指定项目媒体创意报告小时数据
    GET /campaigns/:campaign_id/medias/:network_media_id/creatives/:creative_id/hourly_reports/:hour

    # 获取项目媒体广告位创意报告按小时数据列表
    GET /campaigns/:campaign_id/medias/:network_media_id/placements/:placement_id/creatives/:creative_id/hourly_reports

    # 获取指定项目媒体广告位创意报告小时数据
    GET /campaigns/:campaign_id/medias/:network_media_id/placements/:placement_id/creatives/:creative_id/hourly_reports/:hour

    # 获取指定项目地域日报告
    GET /campaigns/:campaign_id/geos/daily_reports

    # 获取指定项目媒体报告日数据
    GET /campaigns/:campaign_id/medias/daily_reports

    # 获取指定项目媒体地域报告日数据
    GET /campaigns/:campaign_id/medias/geos/daily_reports

    # 获取指定项目媒体广告位报告日数据
    GET /campaigns/:campaign_id/medias/placements/daily_reports

    # 获取指定项目媒体广告位地域报告日数据
    GET /campaigns/:campaign_id/medias/placements/geos/daily_reports

    # 获取指定项目媒体广告位关键字报告日数据
    GET /campaigns/:campaign_id/medias/placements/keywords/daily_reports

    # 获取指定项目创意小时报告
    GET /campaigns/:campaign_id/creatives/hourly_reports

    # 获取指定项目地域小时报告
    GET /campaigns/:campaign_id/geos/hourly_reports

    # 获取指定项目媒体小时报告
    GET /campaigns/:campaign_id/medias/hourly_reports

    # 获取指定项目媒体创意小时报告
    GET /campaigns/:campaign_id/medias/creatives/hourly_reports

    # 获取指定项目媒体地域小时报告
    GET /campaigns/:campaign_id/medias/geos/hourly_reports

    # 获取指定项目媒体广告位小时报告
    GET /campaigns/:campaign_id/medias/placements/hourly_reports

    # 获取指定项目媒体广告位创意小时报告
    GET /campaigns/:campaign_id/medias/placements/creatives/hourly_reports

    # 获取指定项目媒体广告位地域小时报告
    GET /campaigns/:campaign_id/medias/placements/geos/hourly_reports

    # 获取指定项目媒体广告位关键字小时报告
    GET /campaigns/:campaign_id/medias/placements/keywords/hourly_reports

    # 获取指定项目媒体月报告
    GET /campaigns/:campaign_id/medias/monthly_reports

    # 获取指定项目媒体广告位月报告
    GET /campaigns/:campaign_id/medias/placements/monthly_reports

    # 获取指定项目媒体广告位关键字月报告
    GET /campaigns/:campaign_id/medias/placements/keywords/monthly_reports

    # 获取指定项目媒体周报告
    GET /campaigns/:campaign_id/medias/weekly_reports

    # 获取指定项目媒体广告位周报告
    GET /campaigns/:campaign_id/medias/placements/weekly_reports

    # 获取指定项目媒体广告位关键字周报告
    GET /campaigns/:campaign_id/medias/placements/keywords/weekly_reports


###适用版本

[v1.0][version]

[version]: /trackmaster/v1/apiVersion/
[apiCommon]:/trackmaster/v1/apiCommon/#p5
