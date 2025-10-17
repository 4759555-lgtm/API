# 玩家转出V2

## 1) 请求地址

> URL: {APIURL}/api/v2/player/transferOut

## 2) 请求参数:

| 参数名        | 类型            | 描述                                                                                                                                           |
| ---------- | ------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| UserID     | string\[4-40] | 运营商的玩家唯一标识                                                                                                                                   |
| Amount     | float         | 转入金额 >0                                                                                                                                      |
| TraceId    | string\[4-40] | 交易单号                                                                                                                                         |
| RealAmount | float         | <p>[全新]<br>• 现实中的实际交易金额<br>• 注: 游戏厂商方将验证此运营商请求的数值<br>• <strong>对于1:1000基础单位的货币且由运营商处理（默认配置）转换的情况：</strong><br>RealAmount = Amount * 1000</p> |

* 示例：\
  由游戏厂商方处理

```json
{
  "UserID": "user_id",
  "Amount": 1,
  "TraceId": "1bcfsa-dskq-req",
  "RealAmount": 1
}
```

由运营商处理，并且对于1:1000基础单位的货币

```json
{
  "UserID": "user_id",
  "Amount": 1,
  "TraceId": "1bcfsa-dskq-req",
  "RealAmount": 1000
}
```

## 3) 返回结果:

| 参数名          | 类型    | 描述                                                                                                                                                                                                                                                              |
| ------------ | ----- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| AfterBalance | float | 转出成功后余额                                                                                                                                                                                                                                                         |
| RealAmount   | float | <p>[全新]<br>现实中的实际交易金额<br>注： 运营商必须验证此数值，并在发现以下任一条件未能满足时通知游戏厂商方：<br>• 对于1:1基础单位的货币：<br>RealAmount = Amount<br>• 对于1:1000基础单位的货币且由游戏厂商方处理转换的情 况：<br>RealAmount = Amount<br>• <strong>对于1:1000基础单位的货币且由运营商处理（默认配置）转换的情况：</strong><br>RealAmount = Amount * 1000</p> |

* 正常返回
* 示例：\
  由游戏厂商方处理

```json
{
  "code": 0,
  "error": "",
  "data": {
    "AfterBalance": 243.9,
	"RealAmount": 1
   }
}
```

由运营商处理，并且对于1:1000基础单位的货币

```json
{
  "code": 0,
  "error": "",
  "data": {
    "AfterBalance": 243.9,
	"RealAmount": 1000
   }
}
```

* 订单号重复
* 示例：

```json
{
  "code": 1,
  "error": "Order already exists",
  "data": null
}
```

* 余额不足
* 示例：

```json
{
  "code": 1,
  "error": "Insufficient wallet balance",
  "data": null
}
```
