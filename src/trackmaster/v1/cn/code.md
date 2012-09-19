---
weight: 10
layout: default
category: trackmaster
title: 代码
---

#API - 代码

<h2 id="p1">获取指定广告位下的代码</h2>

    GET /networks/advertisers/campaigns/placements/:placement_id/codes

###参数

###响应

<pre class="headers">
<code>Status: 200 OK
X-RateLimit-Limit: 5000
X-RateLimit-Remaining: 4999
</code></pre>
<pre class="highlight">
<code class="language-javascript">
[
  {
    // 创意 ID
    "creative_id": 0,

    // 创意名称
    "creative_name": "默认创意",

    // 点击代码
    "clktag": "http://c.admaster.com.cn/c/a23,b43,c14,i0,m101,h",

    // 曝光代码
    "imptag": "http://v.admaster.com.cn/i/a23,b43,c14,i0,m202,h",

    // 曝光Flash AS2代码
    "imptag_flash_as2": "if(_root[\"adCnt\"]!=\"ldd\") {\n_root[\"adCnt\"]=\"ldd\";var hstr=\"\",u3rd=\"\";\nloadMovie(\"http:\/\/v.admaster.com.cn\/i\/a23,b43,c14,i0,m201,h\"+escape(hstr)+\",d\"+escape(_url)+\",u\"+escape(u3rd),createEmptyMovieClip(\"MSd\",this.getNextHighestDepth()));\n}",

    // 曝光Flash AS3代码
    "imptag_flash_as3": "if(root[\"adCnt\"]!=\"ldd\") {\nroot[\"adCnt\"]=\"ldd\"; var hstr=\"\",u3rd=\"\";\nvar MSd=new Loader();MSd.load(new URLRequest(\"http:\/\/v.admaster.com.cn\/i\/a23,b43,c14,i0,m201,h\"+escape(hstr)+\",d\"+escape(loaderInfo.loaderURL)+\",u\"+escape(u3rd)));this.addChild(MSd);\n}",

    // 曝光图片代码
    "imptag_img": "<img src=\"http:\/\/v.admaster.com.cn\/i\/a23,b43,c14,i0,m203,h\" width=\"1\" height=\"1\" \/>",

    // 曝光JavaScript代码
    "imptag_js": "<script language=\"javascript\">var actId=23,sptId=43,medId=14,invId=0,hstr=\"\";<\/script>\n<script language=\"javascript\" src=\"http:\/\/v.admaster.com.cn\/sodv3\/admTracker.js\"><\/script>",

    // 曝光Flash代码
    "imptag_flash": "<object classid=\"clsid:d27cdb6e-ae6d-11cf-96b8-444553540000\" id=\"TrackMasterBeacon\" align=\"middle\" width=\"1\" height=\"1\"><param name=\"movie\" value=\"http:\/\/v.admaster.com.cn\/i\/a23,b43,c14,i0,m204,h\" \/><param name=\"allowScriptAccess\" value=\"always\" \/><param name=\"quality\" value=\"high\" \/>\n<embed src=\"http:\/\/v.admaster.com.cn\/i\/a23,b43,c14,i0,m204,h\" quality=\"high\" swLiveConnect=true id=\"TrackMasterBeacon\" name=\"TrackMasterBeacon\" width=\"1\" height=\"1\" align=\"middle\" allowScriptAccess=\"always\" type=\"application\/x-shockwave-flash\" \/><\/object>"
  }
]
</code></pre>

