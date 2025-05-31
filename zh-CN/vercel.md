---
# 🚀 免费注册获取API密钥
**[立即注册 NoCaptcha.io →](https://www.nocaptcha.io/register?c=hqLmMS)**  
*专业验证码解决方案 | 高成功率 | 快速响应 | 24/7技术支持*

---

[`返回首页`](../README.md)    [`上一页`](shape.md)

# Vercel 验证码破解服务

## 🔥 产品优势

### 为什么选择我们的Vercel解决方案

* **🌐 专业支持**: 专门针对Vercel安全验证进行优化，支持所有Vercel验证场景
* **⚡ 高效处理**: 快速识别和处理Vercel验证挑战
* **🔄 稳定可靠**: 更新及时，为您的业务提供稳定支撑
* **🎯 高成功率**: 专业算法优化，确保高通过率

## 📋 Vercel验证说明

### 🔍 如何识别Vercel验证

当打开目标页面出现以下情况时，表示存在Vercel验证：
- 页面显示安全验证提示
- 抓包发现有 `/.well-known/vercel/security/request-challenge` 接口请求
- Cookies中包含 `_vcrcs` 参数

![Vercel验证样式](/images/vercel/img1.png)

### 💰 价格说明

**消耗点数**: 1000点/次  
**代理要求**: 必须传入proxy参数

## 🔗 API接口信息

### 请求地址（POST）

| 版本类型 | 接口地址 |
|---------|---------|
| **通用版（Universal）** | `http://api.nocaptcha.io/api/wanda/vercel/universal` |

### 请求头参数

| 参数名 | 说明 | 必填 |
|--------|------|------|
| `User-Token` | 用户密钥，从主页获取 | ✅ |
| `Content-Type` | `application/json` | ✅ |
| `Developer-Id` | 开发者ID，开发者用户使用，用户主页邀请链接的字符串(如 xxx/register?c=abcdef, 则 abcdef 为开发者ID) | ❌ |

### POST请求参数（JSON格式）

| 参数名 | 类型 | 说明 | 必填 |
|--------|------|------|------|
| `href` | `String` | 🚨**触发Vercel验证的页面地址** | ✅ |
| `proxy` | `String` | 代理地址，需保持一致，建议使用海外代理，格式：ip:port 或 usr:pwd@ip:port | ✅ |
| `user_agent` | `String` | 自定义User-Agent | ❌ |
| `timeout` | `Integer` | 验证超时时间 | ❌ |

## 📝 请求示例

```json
{
    "href": "https://faucet.story.foundation/",
    "proxy": "user:pass@ip:port"
}
```

## 📤 响应数据格式

| 参数名 | 类型 | 说明 |
|--------|------|------|
| `status` | `Integer` | 调用状态：1=成功，0=失败 |
| `msg` | `String` | 调用结果说明 |
| `id` | `String` | 请求唯一ID（可用于记录查询） |
| `data._vcrcs` | `String` | 验证成功返回的_vcrcs cookie |
| `cost` | `String` | 验证耗时（毫秒） |

### 响应示例

```json
{
  "status": 1,
  "msg": "验证成功",
  "id": "639e056b-49bd-4895-94ab-68d59e00873e",
  "cost": "2635.12ms",
  "data": {
    "_vcrcs": "1.1726824386.3600.NGZhZDA1MjA3YzE0ZWM1ZjQwYzZmYmNiMTRmNGI0ODY=.98089ffd4040710db7cee73152aafefb"
  },
  "extra": {
    "user-agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.0.0 Safari/537.36",
    "sec-ch-ua-platform": "\"Windows\"",
    "sec-ch-ua": "\"Not)A;Brand\";v=\"99\", \"Google Chrome\";v=\"127\", \"Chromium\";v=\"127\"",
    "accept-language": "en-US,en;q=0.9",
    "sec-ch-ua-arch": "\"x86\"",
    "sec-ch-ua-bitness": "\"64\"",
    "sec-ch-ua-full-version": "\"127.0.6533.4\"",
    "sec-ch-ua-full-version-list": "\"Not)A;Brand\";v=\"99.0.0.0\", \"Google Chrome\";v=\"127.0.6533.4\", \"Chromium\";v=\"127.0.6533.4\"",
    "sec-ch-ua-mobile": "?0",
    "sec-ch-ua-model": "\"\"",
    "sec-ch-ua-platform-version": "\"12.0.0\""
  }
}
```

## 💻 代码示例

### CURL命令

```bash
curl -L 'http://api.nocaptcha.io/api/wanda/vercel/universal' \
 -H 'User-Token: xxx' \
 -H 'Developer-Id: hqLmMS' \
 -H 'Content-Type: application/json' \
 --data-raw '{"href": "https://faucet.story.foundation/", "proxy": "user:pass@ip:port"}'
```

### Python调用示例

**基础示例**
```python
import requests
import random

# 随机生成User-Agent
version = random.randint(118, 128)
user_agent = random.choice([
    f"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/{version}.0.0.0 Safari/537.36",
    f'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/{version}.0.0.0 Safari/537.36'
])

# Vercel验证码破解
href = 'https://faucet.story.foundation/'
proxy = "user:pass@ip:port"

response = requests.post("http://api.nocaptcha.io/api/wanda/vercel/universal", 
    headers={
        "User-Token": "your_user_token_here",
        "Developer-Id": "hqLmMS",  # 开发者ID
        "Content-Type": "application/json"
    }, 
    json={
        "href": href,
        "user_agent": user_agent,
        "proxy": proxy,
        "timeout": 30
    }
)

result = response.json()
print(f"破解结果: {result}")

# 获取_vcrcs cookie
if result.get('status') == 1:
    vcrcs_cookie = result['data']['_vcrcs']
    print(f"获取到的_vcrcs: {vcrcs_cookie}")
```

**完整使用示例**
```python
import requests
import random

class VercelSolver:
    def __init__(self, user_token, developer_id="hqLmMS"):
        self.user_token = user_token
        self.developer_id = developer_id
        self.api_url = "http://api.nocaptcha.io/api/wanda/vercel/universal"
    
    def generate_user_agent(self):
        """生成随机User-Agent"""
        version = random.randint(118, 128)
        return random.choice([
            f"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/{version}.0.0.0 Safari/537.36",
            f'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/{version}.0.0.0 Safari/537.36'
        ])
    
    def solve(self, href, proxy, timeout=30):
        """解决Vercel验证"""
        headers = {
            "User-Token": self.user_token,
            "Developer-Id": self.developer_id,
            "Content-Type": "application/json"
        }
        
        data = {
            "href": href,
            "user_agent": self.generate_user_agent(),
            "proxy": proxy,
            "timeout": timeout
        }
        
        try:
            response = requests.post(self.api_url, headers=headers, json=data)
            result = response.json()
            
            if result.get('status') == 1:
                return {
                    'success': True,
                    'vcrcs': result['data']['_vcrcs'],
                    'extra': result.get('extra', {}),
                    'cost': result.get('cost')
                }
            else:
                return {
                    'success': False,
                    'error': result.get('msg', 'Unknown error')
                }
        except Exception as e:
            return {
                'success': False,
                'error': str(e)
            }

# 使用示例
solver = VercelSolver("your_user_token_here")
result = solver.solve(
    href="https://faucet.story.foundation/",
    proxy="user:pass@ip:port"
)

if result['success']:
    print(f"验证成功！_vcrcs: {result['vcrcs']}")
else:
    print(f"验证失败：{result['error']}")
```

---

## 🎯 相关服务

- [Shape验证码破解](shape.md)
- [ReCaptcha验证码破解](recaptcha.md)
- [Cloudflare验证码破解](cloudflare.md)
- [更多验证码解决方案](../README.md)

**需要技术支持？[立即联系我们](https://www.nocaptcha.io/register?c=hqLmMS)**
