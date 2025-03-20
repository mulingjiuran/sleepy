# API 简要说明及示例

|         | 路径                                                         | 方法   | 作用                                                         |
| ------- | ------------------------------------------------------------ | ------ | ------------------------------------------------------------ |
|         | 密钥`cWob7BAY2xkgYFkJDsqmyFyJMgaNcUGADfmbnyRKi8k`            |        |                                                              |
| read    | `/`                                                          | `GET`  | 显示主页                                                     |
| read    | `/query`                                                     | `GET`  | 获取状态                                                     |
| read    | `/status_list`                                               | `GET`  | 获取可用状态列表                                             |
| read    | `/metrics`                                                   | `GET`  | 获取统计信息                                                 |
| status  | `/set?secret=<secret>&status=<状态索引数字>`                 | `GET`  | 设置状态                                                     |
| status  | `/device/set`<br />{<br/>    "secret": "cWob7BAY2xkgYFkJDsqmyFyJMgaNcUGADfmbnyRKi8k",<br/>    "id": "device-1", // 设备标识符<br/>    "show_name": "MyDevice1", // 显示名称<br/>    "using": true, // 是否正在使用<br/>    "app_name": "VSCode" // 正在使用应用的名称<br/>} | `POST` | 设置单个设备的状态 (打开应用)                                |
| status  | `/device/remove?secret=<secret>&name=<device_name>`          | `GET`  | 移除单个设备的状态                                           |
| status  | `/device/clear?secret=<secret>`                              | `GET`  | 清除所有设备的状态                                           |
| private | `/device/private_mode?secret=<secret>&private=<bool>`        | `GET`  | 设置隐私模式<br />在 [/query]的返回中设置 `device` 项为空 `{}` |
| Storage | `/save_data?secret=<secret>`                                 | `GET`  | 保存内存中的状态信息到`data.json`                            |



## 调用

#### cmd调用

> GET命令：`curl https://moranadd-sleepy.hf.space/<路径>`

> POST命令：`curl -X POST https://moranadd-sleepy.hf.space/device/set -H "Content-Type: application/json" -d '{"secret": "密钥", "id": "设备唯一标识", "show_name": "我的手机", "using": true, "app_name": "微信"}'`

#### python调用

```python
#调用GET
import requests

# 显示主页
response = requests.get('https://moranadd-sleepy.hf.space/')
print(response.text)

# 获取当前状态
response = requests.get('https://moranadd-sleepy.hf.space/query')
print(response.json())

# 获取所有预定义状态列表
response = requests.get('https://moranadd-sleepy.hf.space/status_list')
print(response.json())

# 获取服务统计信息
response = requests.get('https://moranadd-sleepy.hf.space/metrics')
print(response.json())

# 设置当前状态码
response = requests.get('https://moranadd-sleepy.hf.space/set?secret=MySecret&status=1')
print(response.json())
```

```python
# 设置单个设备状态
response = requests.post('https://moranadd-sleepy.hf.space/device/set', json={
    "secret": "MySecret",
    "id": "phone-1",
    "show_name": "我的手机",
    "using": true,
    "app_name": "微信"
})
print(response.json())
```

> 附：
>
> GET 和 POST 是 HTTP 请求的两种基本方法，用于客户端和服务器之间的通信。
>
> - **GET** 方法通常用于请求服务器发送数据给客户端。它通常用于信息检索，并且可以在 URL 中直接看到请求的数据。
> - **POST** 方法用于向服务器提交数据。它通常用于更新或创建资源，请求体（body）中包含了要提交的数据，不会显示在 URL 中。

## 简要解释

#### 1. 只读接口

- **GET /**  
  **作用**：显示主页。  
  **示例请求**：`GET /`  
  **响应**：HTML 格式的主页内容。

- **GET /query**  
  **作用**：获取当前状态（时间、状态码、设备信息等）。  
  **示例请求**：`GET /query`  
  **响应示例**：

  ```json
  {
    "time": "2024-12-28 00:21:24",
    "status": 0,
    "device": {"device-1": {"show_name": "MyDevice1", "using": false}},
    "refresh": 5000
  }
  ```

- **GET /status_list**  
  **作用**：获取所有预定义状态列表。  
  **示例请求**：`GET /status_list`  
  **响应示例**：

  ```json
  [
    {"id": 0, "name": "活着", "desc": "在线状态", "color": "awake"}
  ]
  ```

- **GET /metrics**  
  **作用**：获取服务统计信息（当日/月/年请求量）。  
  **条件**：需服务端启用统计功能。  
  **示例请求**：`GET /metrics`  
  **响应示例**：

  ```json
  {
    "today": {"/query": 2},
    "total": {"/query": 10}
  }
  ```

---

#### 2. 状态接口

- **GET /set**  
  **作用**：设置当前状态码。  
  **参数**：

  - `secret`：服务端配置的密钥。
  - `status`：状态码（整数）。  
    **示例请求**：`GET /set?secret=MySecret&status=1`  
    **成功响应**：

  ```json
  {"success": true, "set_to": 1}
  ```

  **失败响应**（密钥错误）：

  ```json
  {"success": false, "code": "not authorized"}
  ```

---

#### 3. 设备接口

- **POST /device/set**  
  **作用**：设置单个设备状态（如设备正在使用的应用）。  
  **参数**（JSON Body）：

  - `secret`：密钥。
  - `id`：设备唯一标识。
  - `show_name`：显示名称。
  - `using`：是否在使用（布尔值）。
  - `app_name`：应用名（若使用中）。  
    **示例请求**：

  ```json
  {
    "secret": "MySecret",
    "id": "phone-1",
    "show_name": "我的手机",
    "using": true,
    "app_name": "微信"
  }
  ```

  **响应**：`{"success": true}`

- **GET /device/remove**  
  **作用**：移除指定设备状态。  
  **参数**：

  - `secret`：密钥。
  - `id`：设备ID。  
    **示例请求**：`GET /device/remove?secret=MySecret&id=phone-1`  
    **响应**：`{"success": true}`

- **GET /device/clear**  
  **作用**：清除所有设备状态。  
  **参数**：`secret`。  
  **示例请求**：`GET /device/clear?secret=MySecret`  
  **响应**：`{"success": true}`

- **GET /device/private_mode**  
  **作用**：开启/关闭隐私模式（隐藏设备信息）。  
  **参数**：

  - `secret`：密钥。
  - `private`：`true` 或 `false`。  
    **示例请求**：`GET /device/private_mode?secret=MySecret&private=true`  
    **响应**：`{"success": true}`

---

#### 4. 存储接口

- **GET /save_data**  
  **作用**：手动保存内存中的数据到文件（如状态、设备信息）。  
  **参数**：`secret`。  
  **示例请求**：`GET /save_data?secret=MySecret`  
  **响应示例**：

  ```json
  {
    "success": true,
    "data": {"status": 0, "device_status": {}}
  }
  ```