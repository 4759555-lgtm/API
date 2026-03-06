---
icon: chart-line-up
---

# 养客全局配置

### 养客全局配置

**功能概述**

本功能旨在通过后台设置特定数值目标（包括盈利值或流水倍数），动态调整玩家在游戏内的RTP（玩家回报率）档位，从而实现对玩家游戏结果的精细化控制。玩家在达到设定的数值目标之一（盈利值或流水倍数）时，控制自动结束。用于营销活动或维护亏损过大玩家的精准控制，提升玩家盈利。

***

**API 接口详情**

**1. 新建商户养客配置**

* URL: `POST /api/v2/dp/addDevelopPlayersByMerchant`

**请求参数 (Request Body)**

| 名称                 | 类型      | 必选 | 说明                                                                                  |
| ------------------ | ------- | -- | ----------------------------------------------------------------------------------- |
| profitthreshold    | integer | 是  | 盈利阈值，可填值：10，20,30,50,70,100，200,500,700,1000，1500,2000,3000，5000,10000,50000,100000 |
| turnovermultiplier | integer | 是  | 流水倍数，可填值：1-20倍，30倍，50倍,100倍,500倍,1000倍,5000倍                                        |
| cycletype          | integer | 是  | 周期类型，1-4分别对应每日/每周/每月/终生，5为自选时间段。选5时必填开始结束时间戳。                                       |
| maxcontrols        | integer | 是  | 周期内可被系统控制的次数，可填值：可填值：1-20次，30次，50次,100次,500次,1000次,5000次                            |
| intervalrounds     | integer | 是  | 间隔轮数，可填值：5,10,15,20,30,40,50，60,80,100，150，200，300                                  |
| customstart        | integer | 否  | 自定义开始时间戳(毫秒级)                                                                       |
| customend          | integer | 否  | 自定义结束时间戳(毫秒级)                                                                       |

**请求示例**

```json
{
    "profitthreshold": 100,
    "turnovermultiplier": 10,
    "cycletype": 5,
    "maxcontrols": 1,
    "intervalrounds": 30,
    "customstart": 1761899229279,
    "customend": 1761899237267
}
```

**请求代码示例：**

```bash
curl --location --request POST '/api/v2/dp/addDevelopPlayersByMerchant' \
--header 'X-Sign;' \
--header 'X-Request-Id;' \
--header 'X-Appid;' \
--header 'Content-Type: application/json' \
--data-raw '{
    "profitthreshold": 100,
    "turnovermultiplier": 10,
    "cycletype": 5,
    "maxcontrols": 1,
    "intervalrounds": 30,
    "customstart": 1761899229279,
    "customend": 1761899237267
}'
```

**返回结果**

| 参数名   | 类型      | 描述            |
| ----- | ------- | ------------- |
| code  | integer | 返回状态码，0 表示成功  |
| error | string  | 错误信息，成功时为空字符串 |
| data  | object  | 返回数据          |

**成功返回示例**

```json
{
    "code": 0,
    "error": "",
    "data": {}
}
```

***

**2. 更新商户养客配置**

* URL: `POST /api/v2/dp/updateDevelopPlayersByMerchant`

**请求参数 (Request Body)**

| 名称                 | 类型      | 必选 | 说明           |
| ------------------ | ------- | -- | ------------ |
| profitthreshold    | integer | 是  | 盈利阈值         |
| turnovermultiplier | integer | 是  | 流水倍数         |
| cycletype          | integer | 是  | 系统控制的触发周期选择  |
| maxcontrols        | integer | 是  | 周期内可被系统控制的次数 |
| intervalrounds     | integer | 是  | 每次系统控制间隔局数   |
| customstart        | integer | 是  | 自定义开始时间戳     |
| customend          | integer | 是  | 自定义结束时间戳     |

**请求示例**

```json
{
    "profitthreshold": 100,
    "turnovermultiplier": 10,
    "cycletype": 5,
    "maxcontrols": 1,
    "intervalrounds": 30,
    "customstart": 1761899229279,
    "customend": 1761899237267
}
```

**请求代码示例：**

```bash
curl --location --request POST '/api/v2/dp/updateDevelopPlayersByMerchant' \
--header 'X-Sign;' \
--header 'X-Request-Id;' \
--header 'X-Appid;' \
--header 'Content-Type: application/json' \
--data-raw '{
    "profitthreshold": 100,
    "turnovermultiplier": 10,
    "cycletype": 5,
    "maxcontrols": 1,
    "intervalrounds": 30,
    "customstart": 1761899229279,
    "customend": 1761899237267
}'
```

**成功返回示例**

```json
{
    "code": 0,
    "error": "",
    "data": {}
}
```

***

**3. 开关商户养客功能**

* URL: `POST /api/v2/dp/updateDPStatusByMerchant`

**请求参数 (Request Body)**

| 名称      | 类型      | 必选 | 说明                |
| ------- | ------- | -- | ----------------- |
| userids | array   | 否  | 运营商的玩家ID列表        |
| status  | integer | 是  | 状态值（1是开启，0是关闭）    |
| type    | integer | 是  | 类型（1是个人养客，0是商户养客） |

**请求示例**

```json
{
    "userids": [
        ""
    ],
    "status": 0,
    "type": 0
}
```

**请求代码示例：**

```bash
curl --location --request POST '/api/v2/dp/updateDPStatusByMerchant' \
--header 'X-Sign;' \
--header 'X-Request-Id;' \
--header 'X-Appid;' \
--header 'Content-Type: application/json' \
--data-raw '{
    "userids": [
        ""
    ],
    "status": 0,
    "type": 0
}'
```

**返回结果**

| 参数名   | 类型      | 描述            |
| ----- | ------- | ------------- |
| code  | integer | 返回状态码，0 表示成功  |
| error | string  | 错误信息，成功时为空字符串 |
| data  | object  | 返回数据          |

**成功返回示例**

```json
{
    "code": 0,
    "error": "",
    "data": {}
}
```

***

**4. 获取商户养客功能**

* URL: `POST /api/v2/dp/getDPByMerchant`

**请求参数 (Request Body)**

| 名称        | 类型      | 必选 | 说明        |
| --------- | ------- | -- | --------- |
| pageindex | integer | 是  | 页码索引，从0开始 |
| pagesize  | integer | 是  | 每页显示的条目数量 |

**请求示例**

```json
{
    "pageindex": 0,
    "pagesize": 50
}
```

**请求代码示例：**

```bash
curl --location --request POST '/api/v2/dp/getDPByMerchant' \
--header 'X-Sign;' \
--header 'X-Request-Id;' \
--header 'X-Appid;' \
--header 'Content-Type: application/json' \
--data-raw '{
    "pageindex": 0,
    "pagesize": 50
}'
```

**返回结果**

| 参数名        | 类型      | 描述            |
| ---------- | ------- | ------------- |
| code       | integer | 返回状态码，0 表示成功  |
| error      | string  | 错误信息，成功时为空字符串 |
| data       | object  | 返回数据对象        |
| data.total | integer | 总记录数          |
| data.List  | array   | 养客配置列表        |

**List 数组元素参数**

| 参数名                | 类型      | 描述               |
| ------------------ | ------- | ---------------- |
| profitthreshold    | integer | 盈利阈值             |
| turnovermultiplier | integer | 流水倍数             |
| cycletype          | integer | 系统控制的触发周期选择      |
| maxcontrols        | integer | 周期内可被系统控制的次数     |
| intervalrounds     | integer | 间隔轮次             |
| customstart        | integer | 自定义开始时间戳（毫秒）     |
| customend          | integer | 自定义结束时间戳（毫秒）     |
| iscontrolRTP       | integer | 是否控制RTP（0:否，1:是） |
| createat           | integer | 创建时间戳（毫秒）        |
| updateat           | integer | 更新时间戳（毫秒）        |

**成功返回示例**

```json
{
    "code": 0,
    "error": "",
    "data": {
        "List": [
            {
                "profitthreshold": 100,
                "turnovermultiplier": 10,
                "cycletype": 4,
                "maxcontrols": 1,
                "intervalrounds": 30,
                "customstart": 28800000,
                "customend": 28800000,
                "iscontrolRTP": 0,
                "createat": 1757397132240,
                "updateat": 1761118266455
            }
        ],
        "total": 1
    }
}
```
