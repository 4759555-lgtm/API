---
icon: distribute-spacing-vertical
---

# 线路控分组

## 线路控分组

### 添加线路控分组

#### 1) 请求地址

> URL: `{APIURL}/api/v2/line_provider_groups/add`

#### 2) 请求参数

| 参数名              | 类型      | 必填 | 描述        |
| ---------------- | ------- | -- | --------- |
| is\_control\_rtp | integer | 是  | 是否启用RTP控制 |
| groups\_name     | string  | 是  | 分组名称      |
| config\_id       | integer | 是  | 线路控配置ID   |

示例：

```json
{
  "is_control_rtp": 1,
  "groups_name": "aa",
  "config_id": 100003
}
```

请求示例代码：

```bash
curl --location --request POST '{APIURL}/api/v2/line_provider_groups/add' \
--header 'Content-Type: application/json' \
--data-raw '{
  "is_control_rtp": 1,
  "groups_name": "aa",
  "config_id": 100003
}'
```

#### 3) 返回结果

**响应参数**

| 参数名                    | 类型      | 描述        |
| ---------------------- | ------- | --------- |
| code                   | integer | 状态码，0表示成功 |
| error                  | string  | 错误信息      |
| data                   | object  | 返回数据      |
| line\_provider\_groups | object  | 线路控分组对象   |
| id                     | integer | 分组ID      |
| is\_control\_rtp       | integer | 是否启用RTP控制 |
| app\_id                | string  | 应用ID      |
| groups\_name           | string  | 分组名称      |
| config\_id             | integer | 线路控配置ID   |

示例：

```json
{
  "code": 0,
  "error": "",
  "data": {
    "line_provider_groups":{
      "id": 100001,
      "is_control_rtp": 1,
      "app_id": "qwe456_USD_2",
      "groups_name": "aa",
      "config_id": 100003
    }
  }
}
```

***

### POST 更新线路控分组

#### 1) 请求地址

> URL: `{APIURL}/api/v2/line_provider_groups/update`

#### 2) 请求参数

| 参数名              | 类型      | 必填 | 描述        |
| ---------------- | ------- | -- | --------- |
| id               | integer | 是  | 分组ID      |
| is\_control\_rtp | integer | 是  | 是否启用RTP控制 |
| groups\_name     | string  | 是  | 分组名称      |
| config\_id       | integer | 是  | 线路控配置ID   |

示例：

```json
{
  "id": 100001,
  "is_control_rtp": 2,
  "groups_name": "bb",
  "config_id": 100005
}
```

请求示例代码：

```bash
curl --location --request POST '{APIURL}/api/v2/line_provider_groups/update' \
--header 'Content-Type: application/json' \
--data-raw '{
  "id": 100001,
  "is_control_rtp": 2,
  "groups_name": "bb",
  "config_id": 100005
}'
```

#### 3) 返回结果

**响应参数**

| 参数名                    | 类型      | 描述          |
| ---------------------- | ------- | ----------- |
| code                   | integer | 状态码，0表示成功 |
| error                  | string  | 错误信息        |
| data                   | object  | 返回数据        |
| line\_provider\_groups | object  | 线路控分组对象     |
| id                     | integer | 分组ID        |
| is\_control\_rtp       | integer | 是否启用RTP控制   |
| app\_id                | string  | 应用ID        |
| groups\_name           | string  | 分组名称        |
| config\_id             | integer | 线路控配置ID     |

示例：

```json
{
  "code": 0,
  "error": "",
  "data": {
    "line_provider_groups": {
      "id": 100001,
      "is_control_rtp": 2,
      "app_id": "qwe456_USD_2",
      "groups_name": "bb",
      "config_id": 100003
    }
  }
}
```

***

### POST 获取所有线路控分组

#### 1) 请求地址

> URL: `{APIURL}/api/v2/line_provider_groups/list`

#### 2) 请求参数

| 参数名        | 类型      | 必填 | 描述      |
| ---------- | ------- | -- | ------- |
| page       | integer | 是  | 页码，从1开始 |
| page\_size | integer | 是  | 每页大小    |

示例：

```json
{
  "page": 1,
  "page_size": 20
}
```

请求示例代码：

```bash
curl --location --request POST '{APIURL}/api/v2/line_provider_groups/list' \
--header 'Content-Type: application/json' \
--data-raw '{
  "page": 1,
  "page_size": 20
}'
```

#### 3) 返回结果

**响应参数**

| 参数名                    | 类型      | 描述          |
| ---------------------- | ------- | ----------- |
| code                   | integer | 状态码，0表示成功 |
| error                  | string  | 错误信息        |
| data                   | object  | 返回数据        |
| page                   | integer | 当前页码        |
| page\_size             | integer | 每页大小        |
| pages                  | integer | 总页数         |
| total                  | integer | 总记录数        |
| line\_provider\_groups | array   | 线路控分组列表     |
| id                     | integer | 分组ID        |
| is\_control\_rtp       | integer | 是否启用RTP控制   |
| app\_id                | string  | 应用ID        |
| groups\_name           | string  | 分组名称        |
| config\_id             | integer | 线路控配置ID     |

示例：

```json
{
  "code": 0,
  "error": "",
  "data": {
    "page": 1,
    "page_size": 20,
    "pages": 1,
    "total": 2,
    "line_provider_groups": [
      {
        "id": 100001,
        "is_control_rtp": 2,
        "app_id": "qwe456_USD_2",
        "groups_name": "bb",
        "config_id": 100003
      },
      {
        "id": 100002,
        "is_control_rtp": 1,
        "app_id": "qwe456_USD_2",
        "groups_name": "bb",
        "config_id": 100003
      }
    ]
  }
}
```

***

### POST 删除线路控分组

#### 1) 请求地址

> URL: `{APIURL}/api/v2/line_provider_groups/del`

#### 2) 请求参数

| 参数名 | 类型      | 必填 | 描述   |
| --- | ------- | -- | ---- |
| id  | integer | 是  | 分组ID |

示例：

```json
{
  "id": 100001
}
```

请求示例代码：

```bash
curl --location --request POST '{APIURL}/api/v2/line_provider_groups/del' \
--header 'Content-Type: application/json' \
--data-raw '{
  "id": 100001
}'
```

#### 3) 返回结果

**响应参数**

| 参数名     | 类型      | 描述          |
| ------- | ------- | ----------- |
| code    | integer | 状态码，0表示成功 |
| error   | string  | 错误信息        |
| data    | object  | 返回数据        |
| message | string  | 操作结果信息      |

示例：

```json
{
  "code": 0,
  "error": "",
  "data": {
    "message": "success"
  }
}
```
