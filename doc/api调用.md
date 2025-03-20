



### 在命令行（cmd）中调用：

#### 使用 `curl` 调用 GET 接口：

1. 显示主页：
   ```
   curl https://moranadd-sleepy.hf.space/
   ```

2. 获取当前状态：
   ```
   curl https://moranadd-sleepy.hf.space/query
   ```

3. 获取所有预定义状态列表：
   ```
   curl https://moranadd-sleepy.hf.space/status_list
   ```

4. 获取服务统计信息：
   ```
   curl https://moranadd-sleepy.hf.space/metrics
   ```

#### 使用 `curl` 调用 POST 接口：

1. 设置单个设备状态（假设这是 POST 请求，虽然示例中未提供）：
   ```
   curl -X POST https://moranadd-sleepy.hf.space/device/set -H "Content-Type: application/json" -d '{"secret": "密钥", "id": "设备唯一标识", "show_name": "我的手机", "using": true, "app_name": "微信"}'
   ```

#### 使用 `curl` 调用 GET 接口（设置状态）：
1. 设置当前状态码：
   ```
   curl "https://moranadd-sleepy.hf.space/set?secret=MySecret&status=1"
   ```

### 在 Python 中调用：

1. 使用 `requests` 库调用 GET 接口：

```python
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

2. 使用 `requests` 库调用 POST 接口：

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

请确保在实际调用这些接口之前，服务端是可用的，并且有权限进行这些操作。同时，记得替换示例中的 `secret` 为实际的服务端配置密钥。