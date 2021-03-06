# DescribeLiveStreamsControlHistory {#concept_35411_zh .concept}

获取某个域名或应用下的直播流操作记录。

## 请求参数 {#section_k4f_qm1_dfb .section}

|参数|类型|是否必选|示例值|描述|
|:-|:-|:---|:--|:-|
|Action|String|是|DescribeLiveStreamsControlHistory|系统规定参数。取值：DescribeLiveStreamsControlHistory|
|DomainName|String|是|play.yourdomain.com|您的直播加速域名。|
|EndTime|String|是|2017-12-22T08:00:00:00Z| 查询结束时间 UTC 时间 格式：2015-12-01T17:37:00Z。

 EndTime 和 StartTime 之间的间隔不能超过 30 天。

 |
|StartTime|String|是|2017-12-21T08:00:00:00Z|查询开始时间 UTC 时间 格式：2015-12-01T17:36:00Z。|
|AppName|String|否|testApp|直播流所属应用名称。|

## 返回参数 {#section_p4f_qm1_dfb .section}

|名称|类型|示例值|描述|
|:-|:-|:--|:-|
|ControlInfo| | |直播流的操作记录。|
|  └StreamName|String|StreamName|流的名字。|
|  └ClientIP|String|10.207.197.201|用户端的 IP 地址。|
|  └Action|String|DescribeLiveStreamsControlHistory|执行的操作名称。|
|  └TimeStamp|String|2015-12-01T16:36:18Z|操作执行的时间 UTC 时间。|
|RequestId|String|40A4F36D-A7CC-473A-88E7-154F92242566|该条任务请求ID。|

## 示例 {#section_zcx_4j1_dfb .section}

请求示例

```
https://live.aliyuncs.com/?Action=DescribeLiveStreamsControlHistory&DomainName=test101.aliyunlive.com&StartTime=2015-06-25T03:30:50Z&EndTime=2015-12-01T17:37:00Z&<公共请求参数> 
```

**说明：** 关于公共请求参数详细内容，参见 [公共请求参数](cn.zh-CN/API参考/调用方式/公共参数.md#)。

正常返回示例

JSON格式

```
{
    "ControlInfo":{
        "LiveStreamControlInfo":[{
            "Action":"forbid",
            "ClientIP":"10.207.197.201",
            "StreamName":"test101.aliyunlive.com/diaoliang/dd",
            "TimeStamp":"2015-12-01T16:36:18Z"
        }]
    },
    "RequestId":"9C31856F-386D-4DB3-BE79-A0AA493D702A"
}
```

异常返回示例

JSON格式

```
{
    "Code":"InternalError",
    "HostId":"live.aliyuncs.com",
    "Message":"The request processing has failed due to some unknown error.",
    "RequestId":"6EBD1AC4-C34D-4AE1-963E-B688A228BE31"
}
```

## 错误码 {#section_v4f_qm1_dfb .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/live)

