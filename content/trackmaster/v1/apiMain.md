#TrackMaster™ API - 首页
此 API 接口是 TrackMaster™ 提供给第三方开发者的编程接口。您可以通过 API 操作有关广告主、广告位、点位等项目信息。  

在开发之前你需要在[管理应用页面](http://api.trackmaster.com.cn/app/new)申请创建一个应用，填入应用的描述信息，从而获得 Client ID 和 Client Secret，这个 Client ID 用于唯一标识你的应用。创建完应用以后，使用 OAuth2.0 对用户进行验证，保障用户的隐私和安全性。  

使用 TrackMaster™ API 进行应用开发，请先阅读[开发者协议][apiLisence]。  

#目录#


###[API快速入门][apiGetStart]
* [创建应用][apiGetStart]
* [用户身份认证][apiGetStart]
* [开始API之旅][apiGetStart]

###[Oauth认证][oauth]

###[通用说明][apiCommon]
* [全局名称定义][apiCommonName]
* [通用参数说明][apiCommonArg]
* [通用元素说明][apiCommonElem]
* [返回状态说明][apiStatus] 
* [错误码字典][apiError]

###[工作网络][apiNetwork]

**API**|说明|参数
:-----:|----|:---:
**[GET /networks][apiNetworkAll]**|获取当前授权用户有权操作的所有工作网络|0
**[GET /networks/:id][apiNetworkOne]**|获取指定 ID 工作网络信息|1

###[广告主][apiAdv]

**API**|说明|参数
:-----:|----|:---:
**[GET /advertisers][apiAdvLib]**|获取系统广告主列表|0
**[GET /advertisers/:id][apiAdvLibOne]**|获取指定 ID 系统广告主信息|1
**[GET /networks/:network/advertisers][apiAdvnw]**|获取指定 ID 工作网络下所有广告主信息|1
**[GET /networks/:network/advertisers/:id][apiAdvnwModify]**|获取指定 ID 网络下的指定 ID 广告主信息|2
**[PUT /networks/:network/advertisers/:id][apiAdvnwOne]**|添加指定 ID 系统广告主到指定 ID 工作网络下|2
**[PATCH /networks/:network/advertisers/:id][apiAdvnwAdd]**|修改指定 ID 网络下的指定 ID 广告主|2
**[DELETE /networks/:network/advertisers/:id][apiAdvnwDel]**|删除指定 ID 工作网络下的指定 ID 广告主|2

###[品牌][apiBrand]

**API**|说明|参数
:-----:|----|:---:
**[GET /networks/:network/advertisers/:adv/brands][apiBrandAdvAll]**|获取指定 ID 网络下指定 ID 广告主下的所有品牌|2
**[GET /networks/advertisers/brands/:id][apiBrandAdvDetail]**|获取指定 ID 品牌详细信息|1
**[POST /networks/:network/advertisers/:adv/brands][apiBrandAdvAdd]**|添加指定 ID 品牌到指定 ID 网络广告主下|2
**[PATCH /networks/advertisers/brands/:id][apiBrandAdvModify]**|修改特定 ID 的网络广告主下品牌名称|1
**[DELETE /networks/advertisers/brands/:id][apiBrandAdvDel]**|删除指定 ID 的网络广告主下品牌|1

###[媒体][apiMedia]

**API**|说明|参数
:-----:|----|:---:
**[GET /medias][apiMediaLib]**|获取系统媒体库列表|0
**[GET /medias/:id][apiMediaLibDet]**|获取指定系统媒体详细信息|1
**[GET /networks/:network/medias][apiMediaNw]**|获取指定工作网络下媒体库列表|1
**[GET /networks/medias/:id][apiMediaNwOne]**|获取指定工作网络下指定媒体信息|1
**[POST /networks/:network/medias][apiMediaNwAdd]**|给指定工作网络添加一个媒体|1
**[DELETE /networks/medias/:id][apiMediaNwDel]**|删除指定工作网络下的媒体|1
**[PATCH /networks/medias/:id][apiMediaNwModify]**|修改指定工作网络下指定媒体属性|1
**[GET /networks/adv/campaigns/:campaign/medias][apiMediaCp]**|获取指定项目下已添加的媒体|1
**[GET /networks/advertisers/campaigns/:campaign/medias/:id][apiMediaNwOne]**|获取指定项目下指定媒体详细信息|2
**[PUT /networks/advertisers/campaigns/:campaign/medias/:id][apiMediaNwPro]**|为指定项目添加指定媒体|2
**[DELETE /networks/advertisers/campaigns/:campaign/medias/:id][apiMediaNwDel]**|删除指定项目下某个媒体|2


###[项目][apiCampaign]

**API**|说明|参数
:-----:|----|:---:
**[GET /networks/:network/advertisers/:adv/campaigns][apiCampaignList]**|获取指定网络下某个广告主有操作权限的项目列表|2
**[GET /networks/advertisers/campaigns/:id][apiCampaignOne]**|获取指定项目信息|1
**[POST /networks/:network/advertisers/:adv/campaigns][apiCampaignAdd]**|添加指定项目到指定广告主下|2
**[DELETE /networks/advertisers/campaigns/:id][apiCampaignDel]**|删除指定项目|1
**[PATCH /networks/advertisers/campaigns/:id][apiCampaignModify]**|修改指定项目属性|1


###[广告位][apiPlacement]

**API**|说明|参数
:-----:|----|:---:
**[GET /networks/advertisers/campaigns/:campaign/placements][apiPlacementList]**|获取指定项目下指定媒体的广告位列表|1
**[GET /networks/advertisers/campaigns/placements/:id][apiPlacementOne]**|获取指定广告位信息|1
**[POST /networks/advertisers/campaigns/:campaign/placements][apiPlacementAdd]**|添加一个广告位在指定项目下|1
**[DELETE /networks/advertisers/campaigns/placements/:id][apiPlacementDel]**|删除指定的广告位|1
**[PATCH /networks/advertisers/campaigns/placements/:id][apiPlacementModify]**|修改指定的广告位属性|1



###[创意][apiCreative]

**API**|说明|参数
:-----:|----|:---:
**[GET /networks/advertisers/campaigns/:campaign/creatives][apiCreativeCpAll]**|获取指定项目所有创意|1
**[GET /networks/advertisers/campaigns/creatives/:id][apiCreativeCpOne]**|获取项目下指定创意信息|1
**[POST /networks/advertisers/campaigns/:campaign/creatives][apiCreativeCpAdd]**|在指定项目下添加创意|1
**[DELETE /networks/advertisers/campaigns/creatives/:id][apiCreativeDel]**|删除指定的创意|1
**[PATCH /networks/advertisers/campaigns/creatives/:id][apiCreativeModify]**|修改指定的创意属性|1



###[点位][apiSpot]

**API**|说明|参数
:-----:|----|:---:
**[GET /networks/advertisers/campaigns/:campaign/spotss][apiSpotAll]**|获取指定项目下指定时间段内的点位|1
**[PATCH /networks/advertisers/campaigns/spots/:placement/:date][apiSpotModify]**|修改指定点位|2





[oauth]: apiOauth
[apiGetStart]:apiGetStart
[apiCommon]: apiCommon
[apiCommonName]: apiCommon#name
[apiCommonArg]: apiCommon#arg
[apiCommonElem]: apiCommon#elem
[apiStatus]: apiCommon#status
[apiLisence]:apiLisence
[apiError]: apiCommon#error

[apiNetwork]: apiNetwork
[apiNetworkAll]: apiNetwork#all
[apiNetworkOne]: apiNetwork#one

[apiAdv]: apiAdv
[apiAdvLib]: apiAdv#liblist
[apiAdvLibOne]: apiAdv#libone
[apiAdvnw]: apiAdv#nwlist
[apiAdvnwModify]: apiAdv#nwModify
[apiAdvnwOne]: apiAdv#nwone
[apiAdvnwAdd]: apiAdv#nwadd
[apiAdvnwDel]: apiAdv#nwdel

[apiBrand]: apiBrand
[apiBrandAdvAll]: apiBrand#advall
[apiBrandAdvAdd]: apiBrand#advadd
[apiBrandAdvModify]: apiBrand#advmodify
[apiBrandAdvDel]: apiBrand#advdel
[apiBrandAdvDetail]:apiBrand#Detail

[apiMedia]: apiMedia
[apiMediaLibDet]: apiMedia#Det
[apiMediaLib]: apiMedia#lib
[apiMediaNw]: apiMedia#nw
[apiMediaNwOne]: apiMedia#one
[apiMediaNwDel]: apiMedia#one
[apiMediaNwModify]: apiMedia#nwmodify
[apiMediaCp]: apiMedia#cp
[apiMediaNwAdd]: apiMedia#nwadd
[apiMediaCpAdd]: apiMedia#cpadd
[apiMediaNwPro]: apiMediaNwPro#Pro

[apiCampaign]: apiCampaign
[apiCampaignList]: apiCampaign#list
[apiCampaignOne]: apiCampaign#one
[apiCampaignModify]: apiCampaign#modify
[apiCampaignAdd]: apiCampaign#add
[apiCampaignDel]: apiCampaign#del

[apiPlacement]: apiPlacement
[apiPlacementList]: apiPlacement#list
[apiPlacementOne]: apiPlacement#one
[apiPlacementModify]: apiPlacement#modify
[apiPlacementDel]: apiPlacement#del
[apiPlacementAdd]: apiPlacement#add

[apiCreative]: apiCreative
[apiCreativeCpAll]: apiCreative#cpAll
[apiCreativeCpAdd]: apiCreative#cpAdd
[apiCreativeCpOne]: apiCreative#cpOne
[apiCreativeModify]: apiCreative#modify
[apiCreativeDel]: apiCreative#del

[apiSpot]: apiSpot
[apiSpotAll]: apiSpot#all
[apiSpotModify]: apiSpot#modify