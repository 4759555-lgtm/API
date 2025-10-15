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

**1. 添加线路配置**

* UR&#x4C;**:** `POST /api/v2/line_provider_config/add`

**请求参数 (Request Body)**

| 名称              | 类型      | 必选 | 说明         |
| --------------- | ------- | -- | ---------- |
| `win_max_multi` | integer | 是  | 最大赢取倍数。    |
| `win_max_score` | integer | 是  | 最大赢取分数。    |
| `rtp`           | integer | 是  | RTP（返还率）值。 |
| `experience`    | integer | 是  | 体验类型。      |
| `config_name`   | string  | 是  | 配置的名称。     |

**请求示例**

```json
{
  "win_max_multi": 50,
  "win_max_score": 5000,
  "rtp": 70,
  "experience": 10,
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
    "win_max_multi": 0,
    "win_max_score": 0,
    "rtp": 0,
    "experience": 0,
    "config_name": "string"
}'
```

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
      "experience": 10,
      "config_name": "test"
    }
  }
}
```

***

**2. 删除线路配置**

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

**3. 获取所有线路配置**

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
