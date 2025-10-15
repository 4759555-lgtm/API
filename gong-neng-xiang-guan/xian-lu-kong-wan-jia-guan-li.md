---
icon: objects-align-center-vertical
---

# 线路控玩家管理

## 线路控玩家管理

### POST 添加玩家至线路控分组

#### 1) 请求地址

URL: `{APIURL}/api/v2/line-provider-group/player/add`

#### 2) 请求参数

| 参数名       | 类型             | 必填  | 描述       |
| --------- | -------------- | --- | -------- |
| group\_id | integer        | 是   | 组ID      |
| uids      | array\[string] | 是   | 玩家唯一ID列表 |

示例：

```json
{
  "group_id": 100002,
  "uids": ["test_web", "test_web1"]
}
```

请求示例代码：

```bash
curl --location --request POST '{APIURL}/api/v2/line-provider-group/player/add' \
--header 'Content-Type: application/json' \
--data-raw '{
  "group_id": 100002,
  "uids": ["test_web", "test_web1"]
}'
```

#### 3) 返回结果

**响应参数**

| 参数名   | 类型      | 描述          |
| ----- | ------- | ----------- |
| code  | integer | 状态码，200表示成功 |
| error | string  | 错误信息        |
| data  | object  | 返回数据        |

示例：

```json
{
  "code": 0,
  "error": "",
  "data": {}
}
```

***

### POST 查询玩家线路控分组

#### 1) 请求地址

URL: `{APIURL}/api/v2/line-provider-group/player/page`

#### 2) 请求参数

| 参数名        | 类型      | 必填  | 描述      |
| ---------- | ------- | --- | ------- |
| pid        | integer | 否   | 玩家ID    |
| aid        | string  | 否   | 商户ID    |
| gid        | integer | 否   | 组ID     |
| page       | integer | 是   | 页码，从1开始 |
| page\_size | integer | 是   | 每页大小    |

示例：

```json
{
  "pid": 107998,
  "aid": "qwe456_USD_1",
  "gid": 0,
  "page": 1,
  "page_size": 20
}
```

请求示例代码：

```bash
curl --location --request POST '{APIURL}/api/v2/line-provider-group/player/page' \
--header 'Content-Type: application/json' \
--data-raw '{
  "pid": 107998,
  "aid": "qwe456_USD_1",
  "gid": 0,
  "page": 1,
  "page_size": 20
}'
```

#### 3) 返回结果

**响应参数**

| 参数名         | 类型      | 描述        |
| ----------- | ------- | --------- |
| code        | integer | 状态码，0表示成功 |
| error       | string  | 错误信息      |
| data        | object  | 返回数据      |
| page        | integer | 当前页码      |
| page\_size  | integer | 每页大小      |
| pages       | integer | 总页数       |
| total       | integer | 总记录数      |
| record      | array   | 玩家记录列表    |
| id          | integer | 记录ID      |
| group\_id   | integer | 组ID       |
| group\_name | string  | 组名称       |
| app\_id     | string  | 商户ID      |
| pid         | integer | 玩家ID      |

示例：

```json
{
  "code": 0,
  "error": "",
  "data": {
    "page": 1,
    "page_size": 20,
    "pages": 1,
    "total": 1,
    "record": [
      {
        "id": 100001,
        "group_id": 100002,
        "group_name": "bb",
        "app_id": "qwe456_USD_2",
        "pid": 107998
      }
    ]
  }
}
```

***

### POST 删除玩家线路控分组

#### 1) 请求地址

URL: `{APIURL}/api/v2/line-provider-group/player/del`

#### 2) 请求参数

| 参数名 | 类型      | 必填  | 描述   |
| --- | ------- | --- | ---- |
| id  | integer | 是   | 记录ID |

示例：

```json
{
  "id": 100002
}
```

请求示例代码：

```bash
curl --location --request POST '{APIURL}/api/v2/line-provider-group/player/del' \
--header 'Content-Type: application/json' \
--data-raw '{
  "id": 100002
}'
```

#### 3) 返回结果

**响应参数**

| 参数名   | 类型      | 描述          |
| ----- | ------- | ----------- |
| code  | integer | 状态码，200表示成功 |
| error | string  | 错误信息        |
| data  | object  | 返回数据        |

示例：

```json
{
  "code": 0,
  "error": "",
  "data": {}
}
```

***

### POST 修改玩家线路控分组

#### 1) 请求地址

URL: `{APIURL}/api/v2/line-provider-group/player/update`

#### 2) 请求参数

| 参数名     | 类型      | 必填  | 描述   |
| ------- | ------- | --- | ---- |
| gid     | integer | 是   | 组ID  |
| pid     | integer | 是   | 玩家ID |
| app\_id | string  | 是   | 商户ID |

示例：

```json
{
  "gid": 100003,
  "pid": 107998,
  "app_id": "qwe456_USD_2"
}
```

请求示例代码：

```bash
curl --location --request POST '{APIURL}/api/v2/line-provider-group/player/update' \
--header 'Content-Type: application/json' \
--data-raw '{
  "gid": 100003,
  "pid": 107998,
  "app_id": "qwe456_USD_2"
}'
```

#### 3) 返回结果

**响应参数**

| 参数名   | 类型      | 描述        |
| ----- | ------- | --------- |
| code  | integer | 状态码，0表示成功 |
| error | string  | 错误信息      |
| data  | object  | 返回数据      |

示例：

```json
{
  "code": 0,
  "error": "",
  "data": {}
}
```
