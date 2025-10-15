---
icon: window
---

# 运营商提供API

### 运营商提供的API <a href="#h2--api" id="h2--api"></a>

#### 接口说明 <a href="#jie-kou-shuo-ming" id="jie-kou-shuo-ming"></a>

* 请求地址 OPURL 是由运营商提供的 HTTP 访问地址（服务器回调地址），我方系统会通过 HTTP POST 实时请求向该地址发送玩家数据。
* 请求地址的所有请求和响应均使用 JSON 编码。
* 请求地址中，请首先检查 header中的X-Sign，X-Appid和 X-Request-Id 字段是否与运营商的配置匹配。
* 请求地址示例: OPURL=[https://yunyingshang.com/xxxx](https://yunyingshang.com/xxxx) or [http://10.0.0.1:8888](http://10.0.0.1:8888/)

