# CreateCaster {#reference2291 .reference}

创建导播台。

## 请求参数 { .section}

|参数|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：CreateCaster|
|CasterName|String|否|默认为CasterId|
|ClientToken|String|是|用于保证请求的幂等性。由客户端生成该参数值，要保证在不同请求间唯一，最大不值过 64 个 ASCII 字符。|
|NormType|Integer|是|导播台规格类型 0-播单型 1-通用型|
|ChargeType|String|是|付费方式 PrePaid-预付费 PostPaid-后付费, 目前只支持PostPaid|
|PurchaseTime|String|否|导播台购买时间|
|ExpireTime|String|否|导播台过期时间|
|CasterTemplate|String|否|导播台预设分辨率，采用预付费方式时必输 lp\_ld-流畅,lp\_sd-标清,lp\_hd-高清,lp\_ud-超清,lp\_ld\_v-竖屏流畅,lp\_sd\_v-竖屏标清,lp\_hd\_v-竖屏高清,lp\_ud\_v-竖屏超清|

## 返回参数 { .section}

|参数|类型|描述|
|:-|:-|:-|
|RequestId|String|该条任务请求Id|
|CasterId|String|导播台ID|

## 示例 { .section}

请求示例

```
https://live.aliyuncs.com?Action=CreateCaster&CasterName=coco-caster5&ClientToken=53200b81-b761-4c10-842a-a0726d972293&normType=1&ChargeType=PrePaid&period=3&casterTemplate=lp_sd&<公共请求参数>


```

返回示例

```language-json
{
    "RequestId": "16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
    "CasterId": "a2b8e671-2fe5-4642-a2ec-bf93880e1a49"
}

```

## 特殊错误码 {#section_trc_plh_dfb .section}

|错误代码|描述|Http 状态码|语义|
|:---|:-|:-------|:-|
|InvalidChargeType.Malformed|Specified parameter ChargeType is invalid, can only be 0 or 1.|400|计费类型错误|
|InvalidPeriod.Malformed|Specified parameter Period is invalid|400|计费时长无效|
|InvalidNormType.Malformed|Specified parameter NormType is invalid|400|规格不支持|
|InvalidParameter.Malformed|CasterTemplate is mandatory when ChargeType is PrePaid|400|参数错误|
|MissingParameter|ClientToken is mandatory for this action|400|参数缺失|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|内部错误|
|ResourceNumberExceed|Number of resource exceeded video norm|500|导播台资源超限|
|CreateCaster.Timeout|CreateCaster timeout, retry again with the same Token|408|导播台创建超时，请使用当前ClientToken重试|

