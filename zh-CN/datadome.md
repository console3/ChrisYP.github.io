---
# 🚀 免费注册获取API密钥
**[立即注册 NoCaptcha.io →](https://www.nocaptcha.io/register?c=hqLmMS)**  
*专业验证码解决方案 | 高成功率 | 快速响应 | 24/7技术支持*

---

[`返回首页`](../README.md)    [`上一页`](kasada.md)    [`下一页`](shape.md)

# DataDome 验证码破解服务

## 🔥 产品优势

### 为什么选择我们的DataDome解决方案

* **🌐 全模式支持**: 支持无感验证、滑块验证码、设备验证等所有DataDome验证模式
* **⚡ 智能识别**: 自动识别验证类型，无需手动判断验证模式
* **🔄 稳定可靠**: 更新及时，为您的业务提供稳定支撑
* **🎯 高成功率**: 专业算法优化，确保高通过率

## 📋 DataDome验证模式说明

### 🔍 如何识别DataDome验证

当看到 `cookies` 中有 `datadome`，代表存在DataDome验证。有以下三种情况：

### 1️⃣ 无感验证模式（状态码200）

**特征**：访问目标页面状态码为200，F12查看有 `/js/` 结尾的接口响应如下：

```json
{
  "status": 200,
  "cookie": "datadome=66wPBABk21P4x28BLuVse__8_z141EPJEjbgi1HBvNGBcHmX91OT1Z9Z63G4x_suPlRPQ_tgwljYmI5mWxpmkMJ3pKrcnAVKHZs2ymS_2O4nM5wEblvP~~nK3orSol0W; Max-Age=31536000; Domain=.soundcloud.com; Path=/; Secure; SameSite=Lax"
}
```

**处理方式**：必须传入 `js_url` 参数，接口会返回 `did` 参数用于后续验证

![无感验证示例](/images/datadome/js.png)

### 2️⃣ 设备验证模式（状态码403）

**特征**：直接跳转到设备验证页面或滑块验证后再跳转

**处理方式**：设置 `interstitial: true` 参数

![设备验证示例](/images/datadome/interstitial.png)

### 3️⃣ 滑块验证码模式（状态码403）

**特征**：直接跳转到滑块验证页面

![滑块验证示例](/images/datadome/captcha.png)

### 🔄 验证流程示例

```javascript
// 请求目标页面
const response = await fetch(href);

if (response.status === 200) {
    // 无感验证模式
    // 需要传入 js_url 和 js_key 参数
} else if (response.status === 403) {
    // 验证码模式
    // 设置 interstitial: true 处理所有验证类型
}
```

## 🔗 API接口信息

### 请求地址（POST）

| 版本类型 | 接口地址 |
|---------|---------|
| **通用版（Universal）** | `http://api.nocaptcha.io/api/wanda/datadome/universal` |

### 请求头参数

| 参数名 | 说明 | 必填 |
|--------|------|------|
| `User-Token` | 用户密钥，从主页获取 | ✅ |
| `Content-Type` | `application/json` | ✅ |
| `Developer-Id` | 开发者ID，开发者用户使用，用户主页邀请链接的字符串(如 xxx/register?c=abcdef, 则 abcdef 为开发者ID) | ❌ |

### POST请求参数（JSON格式）

| 参数名 | 类型 | 说明 | 必填 |
|--------|------|------|------|
| `href` | `String` | 🚨**触发DataDome验证的页面地址** | ✅ |
| `proxy` | `String` | 代理地址，建议使用海外代理，格式：ip:port 或 usr:pwd@ip:port | ✅ |
| `js_url` | `String` | JS模式下需要传该参数，/js/ 结尾的返回datadome cookie的接口 | ❌ |
| `js_key` | `String` | JS模式下需要传该参数，F12搜索 ddjskey 值 | ❌ |
| `captcha_url` | `String` | POST接口触发的验证码URL | ❌ |
| `interstitial` | `Boolean` | 是否触发设备验证模式，默认false | ❌ |
| `user_agent` | `String` | 自定义User-Agent，必须保持一致 | ❌ |
| `did` | `String` | JS模式返回的指纹ID，后续验证需要传入 | ❌ |
| `cookies` | `String` | 当前页面的cookies | ❌ |
| `timeout` | `Integer` | 验证超时时间 | ❌ |

## 📤 响应数据格式

| 参数名 | 类型 | 说明 |
|--------|------|------|
| `status` | `Integer` | 调用状态：1=成功，0=失败 |
| `msg` | `String` | 调用结果说明 |
| `id` | `String` | 请求唯一ID（可用于记录查询） |
| `data.datadome` | `String` | 验证成功返回的datadome cookie |
| `cost` | `String` | 验证耗时（毫秒） |

### 响应示例

```json
{
  "status": 1,
  "msg": "验证成功",
  "id": "639e056b-49bd-4895-94ab-68d59e00873e",
  "cost": "4635.12ms",
  "data": {
    "datadome": "HYvnTVSxppxMMrSk_Z_MOHoSKkQRd2ppQr~pOeo2nDlL7Lg7QBwb2ew5OYQxSSSH1CR9NzO78A25KHM7kLV6OydtvwvJZ773Jil1mPC7ZoFSQQDrDYVeHZtjq_BWUai6"
  }
}
```

## 💻 代码示例

### CURL命令

```bash
curl -L 'http://api.nocaptcha.io/api/wanda/datadome/universal' \
 -H 'User-Token: xxx' \
 -H 'Developer-Id: hqLmMS' \
 -H 'Content-Type: application/json' \
 --data-raw '{"href": "https://soundcloud.com/", "js_url": "https://dwt.soundcloud.com/js/", "proxy": "user:pass@ip:port"}'
```

### Python调用示例

**安装依赖**
```bash
pip install -U pynocaptcha -i https://pypi.python.org/simple
```

**代码示例**
```python
from pynocaptcha import DatadomeCracker

# DataDome验证码破解
cracker = DatadomeCracker(
    user_token="your_user_token_here",
    developer_id="hqLmMS",  # 开发者ID
    href="https://soundcloud.com/",
    js_url="https://dwt.soundcloud.com/js/",
    proxy="user:pass@ip:port",
    debug=True
)
result = cracker.crack()
print(f"破解结果: {result}")
```

**完整流程示例**
```python
import requests
from pynocaptcha import DatadomeCracker

def handle_datadome_verification(href, user_agent, proxy):
    """处理DataDome验证的完整流程"""
    
    # 1. 先请求目标页面判断验证类型
    response = requests.get(href, headers={"User-Agent": user_agent})
    
    if response.status_code == 200:
        # 无感验证模式
        cracker = DatadomeCracker(
            user_token="your_user_token_here",
            developer_id="hqLmMS",
            href=href,
            user_agent=user_agent,
            js_url="https://example.com/js/",  # 从F12获取
            js_key="E6EAF460AA2A8322D66B42C85B62F9",  # 搜索ddjskey
            proxy=proxy
        )
    elif response.status_code == 403:
        # 验证码模式
        cracker = DatadomeCracker(
            user_token="your_user_token_here",
            developer_id="hqLmMS",
            href=href,
            user_agent=user_agent,
            interstitial=True,  # 处理所有验证类型
            proxy=proxy
        )
    
    return cracker.crack()

# 使用示例
result = handle_datadome_verification(
    href="https://www.vinted.com/",
    user_agent="Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36",
    proxy="user:pass@ip:port"
)
print(f"验证结果: {result}")
```

---

## 🎯 相关服务

- [Kasada验证码破解](kasada.md)
- [Shape验证码破解](shape.md)
- [ReCaptcha验证码破解](recaptcha.md)
- [更多验证码解决方案](../README.md)

**需要技术支持？[立即联系我们](https://www.nocaptcha.io/register?c=hqLmMS)**
