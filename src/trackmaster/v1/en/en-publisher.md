---
weight: 14
layout: default
category: trackmaster
title: Media
---


# TrackMaster API for Publishers

* TOC
{:toc}


TrackMaster provides an API for programmatic access to account data. All API access is over HTTPS. All data is sent and received as JSON.

TrackMaster APIs use the OAuth 2.0 protocol for authentication and authorization.

All developers need to register their application before getting started. A registered OAuth application is assigned a unique `client_id` and `client_secret`. The client_secret should not be shared.


## Step One  Getting the access_token
Before your application can access a TrackMaster API, it must obtain an access token that grants access to that API. 

    POST http://open.admaster.com.cn/oauth/access_token

**Parameters**

    {
      "client_id": "***",
      "client_secret": "***",
      "grant_type": "password",
      "email": "your@email.com",
      "password": "***"
    }

**Response**

    {
      "access_token": "7a68b4d65ddd6a6191ef0cbf9cadb06528d92d67",
      "expires_in": "18000",
      "refresh_token": "23a89c9944afc0525a25d15d180c6bce03efa331"
    }



Access tokens have a limited lifetime and, in some cases, an application needs access to a TrackMaster API beyond the lifetime of `expires_in`. When this is the case, your application can obtain what is called a refresh token. A refresh token and some parameters allow your application to obtain new access tokens. 

**Parameters**

    {
      "client_id": "***",
      "client_secret": "***",
      "grant_type": "refresh_token",
      "refresh_token": "***"
    }


## Step Two Getting the campaigns list

    GET http://track.admasterapi.com/medias/:media_id/campaigns

**Parameters**

The `access_token` you received as a response to Step One.

    access_token=***

**Response**

    [
      {
        "id": 1,
        "name": "This is a testing campaign",
        "start_date": "2012-01-03",
        "end_date": "2012-06-23",
        "created_at": "2012-09-06T20:39:23Z"
      }
    ]


## Step Three Getting the media report 

    GET http://track.admasterapi.com/medias/:media_id/campaigns/:campaign_id/daily_reports

**Parameters**

    :media_id Required Integer - The media ID you received from TrackMaster.
    :campaign_id Required Integer - The campaign ID you received from TrackMaster.

    access_token=***
    start_time Optional Date - Beginning date to retrieve data in format YYYY-MM-DD. Example:2012-08-01，listing campaigns which beginning time earlier than  `start_time`.
    end_time Optional Date - Final date to retrieve data in format YYYY-MM-DD. Example:2012-08-02，listing campaigns which final time later than  `end_time`
    sort Optional String - The order to retrieve the results.
    direction Optional String - The direction to retrieve the results.


**Response**

    Status: 200 OK

    [
      {
        "time": "2012-08-01", // time
        "imp": 23, //impression
        "uimp": 20, //unique impression
        "clk": 20, //click
        "uclk": 10, //unique click
      }
    ]



## More information

[媒体报告](/doc/trackmaster/v1/cn/media_report.html)
[协议及请求说明](/doc/openmaster/v1/cn/verbs.html)

