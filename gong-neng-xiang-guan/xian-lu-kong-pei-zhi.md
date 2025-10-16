---
icon: objects-align-left
---

# 线路控配置

#### **线路控配置接口**

**功能概述**

通过线路控接口可以实现对玩家使用不同线路配置的精细化管理。

**流程逻辑**

1. **创建线路配置** → 2. **创建与其对应的分组** → 3. **将玩家添加到分组**

当玩家被添加到某个分组后，系统会自动使用该分组关联的线路控配置来处理该玩家的游戏行为。

***

#### **API 接口详情**

**1. 添加线路控配置**

* UR&#x4C;**:** `POST /api/v2/line_provider_config/add`

**请求参数 (Request Body)**

| 名称              | 类型      | 必选 | 说明                                                                                                                                                                                                                         |
| --------------- | ------- | -- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `win_max_multi` | integer | 是  | 最大赢取倍数。                                                                                                                                                                                                                    |
| `win_max_score` | integer | 是  | 最大赢取分数。                                                                                                                                                                                                                    |
| `rtp`           | integer | 是  | 设置线路玩家控制的RTP值，可填值`10, 20, 30, 40, 50, 60, 70, 80, 85, 90, 91, 92, 93, 94, 95, 96, 97, 98, 99, 100, 102, 105, 110, 120, 130, 140, 150, 160, 170, 180, 190, 200, 220, 240, 260, 280, 300`注意，根据运营商权限不同，可能仅支持10-97或93-300的RTP值 |
| `experience`    | integer | 是  | 体验类型：可填值\`0,1,2, 3, 4,                                                                                                                                                                                                     |
| `config_name`   | string  | 是  | 配置的名称。                                                                                                                                                                                                                     |

**请求示例**

```json
{
  "win_max_multi": 50,
  "win_max_score": 5000,
  "rtp": 70,
  "experience": 1,
  "config_name": "test"
}
```

**请求代码示例：**

```bash
curl --location --request POST 'https://{APIURL}/api/v2/line_provider_config/add' \
--header 'X-Sign;' \
--header 'X-Request-Id;' \
--header 'X-Appid;' \
--header 'Content-Type: application/json' \
--data-raw '{
    "win_max_multi": 50,
    "win_max_score": 5000,
    "rtp": 70,
    "experience": 1,
    "config_name": "test"
}'
```

**返回结果**

| 参数名                                         | 类型      | 描述            |
| ------------------------------------------- | ------- | ------------- |
| code                                        | integer | 返回状态码，0 表示成功  |
| error                                       | string  | 错误信息，成功时为空字符串 |
| data                                        | object  | 返回数据          |
| data.line\_provider\_config                 | string  | 线路控配置         |
| data.line\_provider\_config.id              | integer | 线路控配置ID       |
| data.line\_provider\_config.rtp             | integer | 线路控配置RTP      |
| data.line\_provider\_config.win\_max\_multi | integer | 线路控配置最大赢钱倍数   |
| data.line\_provider\_config.win\_max\_score | integer | 线路控配置最大赢钱数    |
| data.line\_provider\_config.experience      | integer | 线路控配置数值体验类型   |
| data.line\_provider\_config.config\_name    | string  | 线路控配置名称       |

**成功返回示例**

```json
{
  "code": 0,
  "error": "",
  "data": {
    "line_provider_config": {
      "id": 100002,
      "rtp": 70,
      "win_max_multi": 50,
      "win_max_score": 5000,
      "experience": 1,
      "config_name": "test"
    }
  }
}
```

***

**2. 删除线路控配置**

* UR&#x4C;**:** `POST /api/v2/line_provider_config/del`

**请求参数 (Request Body)**

| 名称   | 类型      | 必选 | 说明        |
| ---- | ------- | -- | --------- |
| `id` | integer | 是  | 要删除的配置ID。 |

**请求示例**

```json
{
    "id": 100002
}
```

**请求代码示例：**

```bash
curl --location --request POST 'https://{APIURL}/api/v2/line_provider_config/del' \
--header 'X-Sign;' \
--header 'X-Request-Id;' \
--header 'X-Appid;' \
--header 'Content-Type: application/json' \
--data-raw '{
    "id": 0
}'
```

**成功返回示例**

```json
{
  "code": 0,
  "error": "",
  "data": {
    "message": "success"
  }
}
```

***

**3. 获取所有线路控配置**

* UR&#x4C;**:** `POST /api/v2/line_provider_config/list`

**请求参数 (Request Body)**

| 名称          | 类型      | 必选 | 说明           |
| ----------- | ------- | -- | ------------ |
| `page`      | integer | 是  | 页号，从 `1` 开始。 |
| `page_size` | integer | 是  | 每页显示的条目数量。   |

**请求示例**

```json
{
    "page": 1,
    "page_size": 20
}
```

**请求代码示例：**

```bash
curl --location --request POST 'https://{APIURL}/api/v2/line_provider_config/list' \
--header 'X-Sign;' \
--header 'X-Request-Id;' \
--header 'X-Appid;' \
--header 'Content-Type: application/json' \
--data-raw '{
    "page": 1,
    "pagesize": 20
}'
```

返回结果

| 参数名                                         | 类型      | 描述            |
| ------------------------------------------- | ------- | ------------- |
| code                                        | integer | 返回状态码，0 表示成功  |
| error                                       | string  | 错误信息，成功时为空字符串 |
| data                                        | object  | 返回数据          |
| data.line\_provider\_config                 | string  | 线路控配置         |
| data.line\_provider\_config.id              | integer | 线路控配置ID       |
| data.line\_provider\_config.rtp             | integer | 线路控配置RTP      |
| data.line\_provider\_config.win\_max\_multi | integer | 线路控配置最大赢钱倍数   |
| data.line\_provider\_config.win\_max\_score | integer | 线路控配置最大赢钱数    |
| data.line\_provider\_config.experience      | integer | 线路控配置数值体验类型   |
| data.line\_provider\_config.config\_name    | string  | 线路控配置名称       |

**成功返回示例**

```json
{
  "code": 0,
  "error": "",
  "data": {
    "page": 1,
    "page_size": 20,
    "pages": 1,
    "total": 1,
    "line_provider_config": [
      {
        "id": 100003,
        "rtp": 70,
        "win_max_multi": 50,
        "win_max_score": 5000,
        "experience": 10,
        "config_name": "test"
      }
    ]
  }
}
```
