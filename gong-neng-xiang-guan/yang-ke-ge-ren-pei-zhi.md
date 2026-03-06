---
icon: arrow-up-from-bracket
---

# 养客个人配置

## 养客个人配置

**1. 新建养个人客配置**

* URL: `POST /api/v2/dp/addDevelopPlayersByPlayers`

**请求参数 (Request Body)**

| 名称                 | 类型      | 必选 | 说明                                                                                  |
| ------------------ | ------- | -- | ----------------------------------------------------------------------------------- |
| profitthreshold    | integer | 是  | 盈利阈值，可填值：10，20,30,50,70,100，200,500,700,1000，1500,2000,3000，5000,10000,50000,100000 |
| turnovermultiplier | integer | 是  | 流水倍数，可填值：1-20倍，30倍，50倍,100倍,500倍,1000倍,5000倍                                        |
| cycletype          | integer | 是  | 周期类型，1-4分别对应每日/每周/每月/终生，5为自选时间段。选5时必填开始结束时间戳。                                       |
| maxcontrols        | integer | 是  | 周期内可被系统控制的次数，可填值：可填值：1-20次，30次，50次,100次,500次,1000次,5000次                            |
| intervalrounds     | integer | 是  | 间隔轮数，可填值：5,10,15,20,30,40,50，60,80,100，150，200，300                                  |
| customstart        | integer | 是  | 自定义开始时间戳                                                                            |
| customend          | integer | 是  | 自定义结束时间戳                                                                            |
| userids            | array   | 是  | 用户ID列表                                                                              |

**请求示例**

```json
{
    "profitthreshold": 70,
    "turnovermultiplier": 10,
    "cycletype": 5,
    "maxcontrols": 1,
    "intervalrounds": 30,
    "customstart": 1761899229279,
    "customend": 1761899237267,
    "userids": ["mIVcJFin-1757491156383-DemoUser"]
}
```

**请求代码示例：**

```bash
curl --location --request POST '/api/v2/dp/addDevelopPlayersByPlayers' \
--header 'X-Sign;' \
--header 'X-Request-Id;' \
--header 'X-Appid;' \
--header 'Content-Type: application/json' \
--data-raw '{
    "profitthreshold": 70,
    "turnovermultiplier": 10,
    "cycletype": 5,
    "maxcontrols": 1,
    "intervalrounds": 30,
    "customstart": 1761899229279,
    "customend": 1761899237267,
    "userids": [""]
}'
```

**返回结果**

| 参数名              | 类型         | 描述            |
| ---------------- | ---------- | ------------- |
| code             | integer    | 返回状态码，0 表示成功  |
| error            | string     | 错误信息，成功时为空字符串 |
| data             | object     | 返回数据          |
| data.OnExistPids | array/null | 已存在的产品ID列表    |

**成功返回示例**

```json
{
    "code": 0,
    "error": "",
    "data": {
        "OnExistPids": null
    }
}
```

***

**2. 更新个人养客配置**

* URL: `POST /api/v2/dp/updateDPStatusByPlayers`

**请求参数 (Request Body)**

| 名称      | 类型      | 必选 | 说明                |
| ------- | ------- | -- | ----------------- |
| userids | array   | 是  | 运营商的玩家ID列表        |
| status  | integer | 是  | 状态值（1是开启，0是关闭）    |
| type    | integer | 是  | 类型（1是个人养客，0是商户养客） |

**请求示例**

```json
{
    "userids": [
        "mIVcJFin-1757491156383-DemoUser"
    ],
    "status": 1,
    "type": 1
}
```

**请求代码示例：**

```bash
curl --location --request POST '/api/v2/dp/updateDPStatusByPlayers' \
--header 'X-Sign;' \
--header 'X-Request-Id;' \
--header 'X-Appid;' \
--header 'Content-Type: application/json' \
--data-raw '{
    "userids": [
        "mIVcJFin-1757491156383-DemoUser"
    ],
    "status": 1,
    "type": 1
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

**3. 获取个人养客配置**

* URL: `POST /api/v2/dp/getDPByPlayers`

**请求参数 (Request Body)**

| 名称        | 类型      | 必选 | 说明        |
| --------- | ------- | -- | --------- |
| userid    | string  | 是  | 运营商的玩家ID  |
| starttime | integer | 是  | 开始时间戳     |
| endtime   | integer | 是  | 结束时间戳     |
| pageindex | integer | 是  | 页码索引，从0开始 |
| pagesize  | integer | 是  | 每页显示的条目数量 |

**请求示例**

```json
{
    "userid": "mIVcJFin-1757491156383-DemoUser",
    "starttime": 0,
    "endtime": 0,
    "pageindex": 0,
    "pagesize": 50
}
```

**请求代码示例：**

```bash
curl --location --request POST '/api/v2/dp/getDPByPlayers' \
--header 'X-Sign;' \
--header 'X-Request-Id;' \
--header 'X-Appid;' \
--header 'Content-Type: application/json' \
--data-raw '{
    "userid": "",
    "starttime": 0,
    "endtime": 0,
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

**List数组元素参数**

| 参数名                | 类型      | 描述               |
| ------------------ | ------- | ---------------- |
| turnovermultiplier | integer | 流水倍数             |
| cycletype          | integer | 系统控制的触发周期选择      |
| maxcontrols        | integer | 周期内可被系统控制的次数     |
| intervalrounds     | integer | 每次系统控制间隔局数       |
| customstart        | integer | 自定义开始时间戳（毫秒）     |
| customend          | integer | 自定义结束时间戳（毫秒）     |
| iscontrolRTP       | integer | 是否控制RTP（0:否，1:是） |
| createat           | integer | 创建时间戳（毫秒）        |
| updateat           | integer | 更新时间戳（毫秒）        |
| userid             | string  | 用户ID             |
| currentcyclestart  | integer | 当前周期开始时间戳（毫秒）    |
| controlsused       | integer | 已用控制次数           |
| lastcontroltime    | integer | 上次控制时间戳（毫秒）      |
| lastcontrolround   | integer | 上次控制轮次           |
| currentprofit      | integer | 当前盈利金额           |
| currentturnover    | integer | 当前流水金额           |
| iscontrolactive    | boolean | 是否开启控制           |
| totalroundsplayed  | integer | 玩家总轮次            |
| raisestartrtp      | integer | 提升开始RTP          |
| raisecurrentrtp    | integer | 提升当前RTP          |
| raisebetamount     | integer | 玩家养客期间盈利         |
| raisespincount     | integer | 提升旋转次数           |
| raisewinloss       | integer | 提升盈亏             |
| profitthreshold    | integer | 盈利阈值             |
| hasprofitthreshold | integer | 已达盈利阈值           |
| startbalance       | integer | 开始养客时携带的金额       |
| currentbalance     | integer | 养客状态时玩家余额        |

**成功返回示例**

```json
{
    "code": 0,
    "error": "",
    "data": {
        "List": [
            {
                "turnovermultiplier": 10,
                "cycletype": 4,
                "maxcontrols": 1,
                "intervalrounds": 30,
                "customstart": 28800000,
                "customend": 28800000,
                "iscontrolRTP": 1,
                "createat": 1761103442899,
                "updateat": 1761104700760,
                "userid": "mIVcJFin-1757491156383-DemoUser",
                "currentcyclestart": -62135596800000,
                "controlsused": 0,
                "lastcontroltime": -62135596800000,
                "lastcontrolround": 0,
                "currentprofit": 0,
                "currentturnover": 0,
                "iscontrolactive": false,
                "totalroundsplayed": 0,
                "raisestartrtp": 0,
                "raisecurrentrtp": 0,
                "raisebetamount": 0,
                "raisespincount": 0,
                "raisewinloss": 0,
                "profitthreshold": 0,
                "hasprofitthreshold": 0,
                "startbalance": 0,
                "currentbalance": 0
            }
        ],
        "total": 1
    }
}
```
