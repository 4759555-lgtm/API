---
icon: calendar-arrow-up
---

# 养客控制历史

### 获取历史控制记录

#### 1) 请求地址

> URL: `{APIURL}/api/v2/dp/getDPHistoryLog`

#### 2) 请求参数

| 参数名       | 类型      | 必填 | 描述        |
| --------- | ------- | -- | --------- |
| userid    | string  | 否  | 运营商的玩家ID  |
| status    | integer | 否  | 状态        |
| starttime | integer | 否  | 开始时间戳     |
| endtime   | integer | 否  | 结束时间戳     |
| pageindex | integer | 是  | 页码索引，从0开始 |
| pagesize  | integer | 是  | 每页大小      |

```json
{
    "userid": "",
    "status": 1,
    "starttime": 0,
    "endtime": 0,
    "pageindex": 0,
    "pagesize": 50
}
```

请求示例代码：

```bash
curl --location --request POST '/api/v2/dp/getDPHistoryLog' \
--header 'X-Sign;' \
--header 'X-Request-Id;' \
--header 'X-Appid;' \
--header 'Content-Type: application/json' \
--data-raw '{
    "userid": "",
    "status": 1,
    "starttime": 0,
    "endtime": 0,
    "pageindex": 0,
    "pagesize": 50
}'
```

#### 3) 返回结果

**响应参数**

| 参数名        | 类型      | 描述        |
| ---------- | ------- | --------- |
| code       | integer | 状态码，0表示成功 |
| error      | string  | 错误信息      |
| data       | object  | 返回数据对象    |
| data.total | integer | 总记录数      |
| data.List  | array   | 控制记录列表    |

**List数组元素参数**

| 参数名                | 类型      | 描述         |
| ------------------ | ------- | ---------- |
| createat           | integer | 创建时间戳（毫秒）  |
| updateat           | integer | 更新时间戳（毫秒）  |
| userid             | string  | 运营商的玩家ID   |
| raisestatus        | integer | 提升状态       |
| raisetype          | integer | 提升类型       |
| profitthreshold    | integer | 设定玩家盈利值    |
| hasprofitthreshold | integer | 已达利润阈值     |
| startbalance       | integer | 起始余额       |
| currentbalance     | integer | 开始养客时携带的金额 |
| cycletype          | integer | 养客状态时玩家余额  |
| controlsused       | integer | 已用控制次数     |
| maxcontrols        | integer | 最大控制次数     |

示例：

```json
{
    "code": 0,
    "error": "",
    "data": {
        "total": 3,
        "List": [
            {
                "createat": 1757390393845,
                "updateat": 1757390461116,
                "userid": "trZXIUZt-1757388232303-DemoUser",
                "raisestatus": 1,
                "raisetype": 2,
                "profitthreshold": 100,
                "hasprofitthreshold": 0,
                "startbalance": 0,
                "currentbalance": 0,
                "cycletype": 4,
                "controlsused": 1,
                "maxcontrols": 1
            },
            {
                "createat": 1757397251961,
                "updateat": 1757397266359,
                "userid": "vtBGtOEM-1757397071624-DemoUser",
                "raisestatus": 1,
                "raisetype": 1,
                "profitthreshold": 100,
                "hasprofitthreshold": 885000,
                "startbalance": 0,
                "currentbalance": 0,
                "cycletype": 4,
                "controlsused": 1,
                "maxcontrols": 1
            },
            {
                "createat": 1757401377906,
                "updateat": 1760066927406,
                "userid": "trZXIUZt-1757388232303-DemoUser",
                "raisestatus": 1,
                "raisetype": 10,
                "profitthreshold": 100,
                "hasprofitthreshold": 83000,
                "startbalance": 0,
                "currentbalance": 0,
                "cycletype": 4,
                "controlsused": 1,
                "maxcontrols": 5
            }
        ]
    }
}
```
