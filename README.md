---
icon: calendar-check
---

# 公共说明和错误码

### 1. 运营商接入说明

#### 基本信息

* **API提供方{APIURL}**：游戏厂商方（我方）
* **接入方{OPURL}**：运营商
* **服务器时区**：UTC+0（接入时需注意数据统计的时区计算）
* **成功标识**：接口返回 `code = 0` 表示成功

#### 账号获取流程

1. 运营商提交开户申请
2. 审核通过后，游戏厂商方提供运营商后台账号
3. 运营商登录后台获取以下信息：


* {APIURL}：接口地址
* `AppID`：商户号（商户名称）
* `AppSecret`：商户编码

***

### 2. 公共参数与签名算法

| 参数           | 所处位置   | 必填 | 类型     | 说明                    |
| ------------ | ------ | -- | ------ | --------------------- |
| X-Sign       | header | 是  | string | 签名算法见 签名算法及示例         |
| X-Request-Id | header | 是  | string | 唯一，建议格式：UTC时间戳\_6位随机码 |
| X-Appid      | header | 是  | string | 商户号                   |

### &#x20;<a href="#qian-ming-suan-fa-ji-shi-li" id="qian-ming-suan-fa-ji-shi-li"></a>

### &#x20;<a href="#qian-ming-suan-fa-ji-shi-li" id="qian-ming-suan-fa-ji-shi-li"></a>

### &#x20;<a href="#qian-ming-suan-fa-ji-shi-li" id="qian-ming-suan-fa-ji-shi-li"></a>

### 签名算法及示例 <a href="#qian-ming-suan-fa-ji-shi-li" id="qian-ming-suan-fa-ji-shi-li"></a>

**sign=md5(**&#x52;equest-I&#x64;**+body中的json字符串+签名密钥key)**

**注意这里的body中的json字符串必须是请求中最原始的body中的字符，不能使用json包转出来之后的字符，最终使用小写输出**


请求url : `{APIURL}`/api/v1/game/list

请求方式 : POST

Content-Type  "application/json; charset=utf-8"

X-Appid ：qwe123

X-Sign：847f08989098ed696e2b8ac085e0e808

X-Request-Id：1723

请求body中json数据

{"Language":"en"}

签名密钥key

39a6581c31ef3203a22edb2daa2ab6d1

需要md5加密的字符串

trace\_id=dhf1aboc1iio{"player\_logon\_token":"b27cfe9b-f01c-11ee-a0b5-000c2901d9cc","account\_id":"1002402","timestamp":1711971655}39a6581c31ef3203a22edb2daa2ab6d1

最终加密出来md5字符串

e3f8dc79e875e46f6755ef540c2d24f3

### 调用返回 <a href="#diao-yong-fan-hui" id="diao-yong-fan-hui"></a>

当平台返回的http code为200时，为HTTP访问API正常，可正常解析返回结果。其余http错误时为链路异常。 返回的Content-Type为 **"application/json; charset=utf-8"**

```json
{
    "code": 1,
    "msg": "success",
    "data": {
        "glist": [
            {
                "gameid": "9",
                "name": "mine",
                "platform": "1"
            }
        ]
    }
}
```



***

### 3. 接口协议规范

#### 请求规范

* **Content-Type**：`application/json;charset=UTF-8`
* **请求方法**：POST
* **时间格式**：UTC时间戳

#### 响应规范

* **HTTP状态码**：200  表示HTTP访问正常，其他状态码表示链路异常
* **Content-Type**：`application/json;charset=UTF-8`
* **响应格式**：`{"code": int, "error": string, "data": object}`

#### 响应字段说明

| 参数名   | 类型      | 说明                |
| ----- | ------- | ----------------- |
| code  | integer | 错误编码，0表示成功，非0表示失败 |
| error | string  | 错误信息描述            |
| data  | object  | 返回的业务数据（有错误不会生效）  |

#### 响应示例

```json
{
  "code": 0,
  "error": "",
  "data": {
    "glist": [
      {
        "gameid": "9",
        "name": "mine",
        "platform": "1"
      }
    ]
  }
}
```

***

### 4. 错误码说明

| Code | 说明                    |
| ---- | --------------------- |
| 0    | 成功                    |
| 1001 | 运营商被禁用                |
| 1002 | 无效的商户ID               |
| 1003 | 线路商被禁用                |
| 1004 | 游戏未找到                 |
| 1005 | 该游戏正在进行维护             |
| 1006 | 该游戏已关闭                |
| 1007 | 该游戏已隐藏                |
| 1008 | 用户ID为空                |
| 1009 | 无效的钱包类型               |
| 1011 | 无效的商户编码               |
| 1012 | 您所在的国家或地区受到限制         |
| 1013 | 线路商不允许调用接口            |
| 1014 | IP不允许访问               |
| 1015 | 错误的RTP赋值              |
| 1016 | 错误的转账金额               |
| 1017 | 订单已存在                 |
| 1018 | 订单不存在                 |
| 1019 | 请求太频繁                 |
| 1020 | 无效的游戏类型               |
| 1021 | 未开启商户调控RTP开关          |
| 1022 | 商户未审核                 |
| 1023 | 余额不足                  |
| 1024 | 开关值错误                 |
| 1025 | RTP生效次数值错误            |
| 1026 | 最大倍数值小于等于最小倍数值        |
| 1027 | 购买RTP开关权限未开启          |
| 1028 | 个人最高赢分设置值错误           |
| 1029 | 个人最高倍数设置值错误           |
| 1030 | 监控类型或监控开关值错误          |
| 1031 | 监控新手局数值错误             |
| 1032 | 监控玩家RTP误差范围值错误        |
| 1033 | 监控游戏内统计数据周期值错误        |
| 1034 | 监控增加RTP范围或减少RTP范围为空   |
| 1035 | 监控新手非新手游戏调控的触发概率值设置错误 |
| 1036 | 获取下注历史每页数据条数需要小于10000 |
| 2001 | 玩家不存在                 |
| 2002 | 玩家被禁用                 |

***

### 5. 技术支持

如有技术问题或需要进一步的接入支持，请联系我方客服团队。
