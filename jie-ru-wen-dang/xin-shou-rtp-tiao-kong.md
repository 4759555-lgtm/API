# 新手RTP调控

## 1) 请求地址

> URL: {APIURL}/api/v1/operator/setExtraRtp

## 2) 请求参数

| 参数名                         | 类型     | 描述                                 |
| --------------------------- | ------ | ---------------------------------- |
| AppID                       | string | 运营商AppID，需要与header中的AppID一致否则将会报错  |
| IsProtection                | int    | 保护开关,新人rtp调控开关,值为`0(关闭)`或`1(开启)`   |
| ProtectionRotateCount       | int    | 保护次数,新手rtp调控的生效的spin次数值为`1~100`的整数 |
| ProtectionRewardPercentLess | int    | 保护内获取比率,新手rtp可调控的获取比率值为`1~20`的整数   |

* 示例：

```json
{
	"AppID": "test",
	"IsProtection": 1,
	"ProtectionRotateCount": 50,
	"ProtectionRewardPercentLess": 15
}
```

## 3) 返回结果

| 参数名   | 类型     | 描述       |
| ----- | ------ | -------- |
| AppId | string | 运营商AppID |

* 示例：

```json
{
    "code": 0,
    "error": "",
    "data": {
        "AppId": "test",
    }
}
```
