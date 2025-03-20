### API 简要说明及示例

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