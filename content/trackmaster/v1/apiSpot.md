#API - 点位接口

<h2 id="p1">获取指定项目下指定时间段内的点位</h2>

    GET /networks/advertisers/campaigns/:campaign_id/spots

###参数

start\_date
: _必选_ *Date* - 开始日期 格式为: yyyy-mm-dd 例如: 2012-04-12

end\_date
: _必选_ *Date* - 结束日期 格式为: yyyy-mm-dd 例如: 2012-04-30

page
: _可选_ *Int* - 显示页码

per_page
: _可选_ *Int* - 分页数量，默认每页30条

###响应

<pre class="headers">
<code>Status: 200 OK
Link: <http://api.trackmaster.com.cn/networks/advertisers/campaigns/:campaign_id/spots?page=2>; rel="next",
      <http://api.trackmaster.com.cn/networks/advertisers/campaigns/:campaign_id/spots?page=10>; rel="last"
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
[
  {
    /*广告位 ID*/
    "placement_id": 200019261,
    /*排期日期*/
    "online_date": "2012-04-13",
    //创意ID
    "creative_id": 200019827,
    //购买量
    "units": 23,
  }
]
</code></pre>

<h2 id="p2">修改指定点位</h2>

    PUT /networks/advertisers/campaigns/placements/:placement_id/spots/:date

###请求

units
: _必选_ *Int* - 购买量，不上线可以设置为0

creative\_id
: _可选_ *Int* - 创意ID

###响应

<pre class="headers no-response">
<code>Status: 204 No Content
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>

