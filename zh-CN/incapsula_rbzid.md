---
# 🚀 免费注册获取API密钥
**[立即注册 NoCaptcha.io →](https://www.nocaptcha.io/register?c=hqLmMS)**  
*专业验证码解决方案 | 高成功率 | 快速响应 | 24/7技术支持*

---

[`返回首页`](../README.md)    [`上一页`](incapsula_utmvc.md)     [`下一页`](akamai.md) 

# Incapsula (rbzid) 验证码破解服务

## 🔥 产品优势

### 为什么选择我们的Incapsula RBZID解决方案

* **🌐 专业支持**: 专门针对Incapsula rbzid验证进行优化
* **⚡ 高效处理**: 快速生成有效的验证头信息
* **🔄 稳定可靠**: 更新及时，为您的业务提供稳定支撑
* **🎯 高成功率**: 专业算法优化，确保高通过率

## 📋 Incapsula RBZID验证说明

### 🔍 如何识别RBZID验证

当请求Incapsula脚本时，返回如下情况代表触发了rbzid验证：
- 脚本包含 `kramericaindustries.ac.lib.js`
- 出现 `window.rbzns...` 相关代码

![RBZID验证示例](/images/incapsula/rbzid.png)

### 📄 结果使用方法

1. **保持UA一致**：使用返回的verify_url和headers进行GET请求
2. **获取cookies**：从响应中获取cookies，后续请求需要带上
3. **请求头设置**：返回的请求头固定为`x-zebra-zebra`，可随机化为`x-zebra-` + random(5)

## 🔗 API接口信息

### 请求地址（POST）

| 版本类型 | 接口地址 |
|---------|---------|
| **RBZID** | `http://api.nocaptcha.io/api/wanda/incapsula/rbzid` |

### 请求头参数

| 参数名 | 说明 | 必填 |
|--------|------|------|
| `User-Token` | 用户密钥，从主页获取 | ✅ |
| `Content-Type` | `application/json` | ✅ |
| `Developer-Id` | 开发者ID，开发者用户使用，用户主页邀请链接的字符串(如 xxx/register?c=abcdef, 则 abcdef 为开发者ID) | ❌ |

### POST请求参数（JSON格式）

| 参数名 | 类型 | 说明 | 必填 |
|--------|------|------|------|
| `href` | `String` | 🚨**返回rbzid脚本的URL** | ✅ |
| `user_agent` | `String` | RBZID cookies使用需要UA一致，请传您将使用的UA | ✅ |
| `script` | `String` | href请求的结果脚本 | ✅ |

## 📝 请求示例

```json
{
    "href": "https://premier.hkticketing.com/_Incapsula_Resource?SWJIYLWA=719d34d31c8e3a6e6fffd425f7e032f3",
    "script": "href 请求结果",
    "user_agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36"
}
```

## 📤 响应数据格式

| 参数名 | 类型 | 说明 |
|--------|------|------|
| `status` | `Integer` | 调用状态：1=成功，0=失败 |
| `msg` | `String` | 调用结果说明 |
| `id` | `String` | 请求唯一ID（可用于记录查询） |
| `data` | `Object` | 包含verify_url和headers用于后续验证 |
| `cost` | `String` | 验证耗时（毫秒） |

### 响应示例

```json
{
    "status": 1,
    "msg": "验证成功",
    "id": "61b4bb7f-abf9-4875-ae58-38916e1ecbff",
    "cost": "36.42ms",
    "data": {
        "x-zebra-zebra": "ZDM4ZjBlMjcyOGE1MjhmY2E3ZTFjNjNlODRiN2EyN2RlMzA5ZWM4MTskKGhhc2gpO194Y2FsYyhhcmd1bWVudHMuY2FsbGUpOzA7JChoYXNoKTtfeGNhbGMoYXJndW1lbnRzLmNhbGxlKTstNTkyNTkyNTg3MjA7JChoYXNoKTtfeGNhbGMoYXJndW1lbnRzLmNhbGxlKTtkaXNhYmxlZDskKGhhc2gpO194Y2FsYyhhcmd1bWVudHMuY2FsbGUpOzEyMzEyMw==", 
        "user-agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36"
    }
}
```

## 💻 代码示例

### CURL命令

```bash
curl -L 'http://api.nocaptcha.io/api/wanda/incapsula/rbzid' \
 -H 'User-Token: xxx' \
 -H 'Developer-Id: hqLmMS' \
 -H 'Content-Type: application/json' \
 --data-raw '{"href": "https://premier.hkticketing.com/_Incapsula_Resource?SWJIYLWA=719d34d31c8e3a6e6fffd425f7e032f3", "script": "href 请求结果", "user_agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36"}'
```

### Python调用示例

**安装依赖**
```bash
pip install -U pynocaptcha -i https://pypi.python.org/simple
```

**代码示例**
```python
from pynocaptcha import IncapsulaRbzidCracker

# Incapsula RBZID验证码破解
cracker = IncapsulaRbzidCracker(
    user_token="your_user_token_here",
    developer_id="hqLmMS",  # 开发者ID
    href="https://premier.hkticketing.com/_Incapsula_Resource?SWJIYLWA=719d34d31c8e3a6e6fffd425f7e032f3",
    script="href 请求结果",
    user_agent="Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36"
)
result = cracker.crack()
print(f"破解结果: {result}")
```

**完整使用示例**
```python
import requests
from pynocaptcha import IncapsulaRbzidCracker

def solve_incapsula_rbzid(target_url):
    """完整的Incapsula RBZID解决流程"""
    
    # 1. 请求目标页面，获取rbzid脚本URL
    session = requests.Session()
    response = session.get(target_url)
    
    # 2. 从页面中提取rbzid脚本URL
    # 这里需要解析页面源码找到包含SWJIYLWA的URL
    rbzid_script_url = "https://premier.hkticketing.com/_Incapsula_Resource?SWJIYLWA=719d34d31c8e3a6e6fffd425f7e032f3"
    
    # 3. 获取脚本内容
    script_response = session.get(rbzid_script_url)
    script_content = script_response.text
    
    # 4. 检查是否包含rbzid特征
    if "kramericaindustries.ac.lib.js" in script_content or "window.rbzns" in script_content:
        print("检测到RBZID验证")
        
        # 5. 调用破解服务
        cracker = IncapsulaRbzidCracker(
            user_token="your_user_token_here",
            developer_id="hqLmMS",
            href=rbzid_script_url,
            script=script_content,
            user_agent="Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36"
        )
        
        result = cracker.crack()
        
        if result.get('status') == 1:
            zebra_header = result['data']['x-zebra-zebra']
            user_agent = result['data']['user-agent']
            
            print(f"成功获取验证头: {zebra_header}")
            
            # 6. 使用验证头进行后续请求
            headers = {
                'x-zebra-zebra': zebra_header,
                'User-Agent': user_agent
            }
            
            # 进行验证请求获取cookies
            verify_response = session.get(target_url, headers=headers)
            cookies = session.cookies.get_dict()
            
            return {
                'success': True,
                'headers': headers,
                'cookies': cookies
            }
        else:
            return {
                'success': False,
                'error': result.get('msg')
            }
    else:
        print("未检测到RBZID验证")
        return {'success': False, 'error': 'No RBZID verification detected'}

# 使用示例
result = solve_incapsula_rbzid("https://premier.hkticketing.com/")

if result['success']:
    print(f"验证成功！")
    print(f"Headers: {result['headers']}")
    print(f"Cookies: {result['cookies']}")
else:
    print(f"验证失败：{result['error']}")
```

---

## 🎯 相关服务

- [Incapsula Reese84验证码破解](incapsula.md)
- [Incapsula UTMVC验证码破解](incapsula_utmvc.md)
- [Akamai验证码破解](akamai.md)
- [更多验证码解决方案](../README.md)

**需要技术支持？[立即联系我们](https://www.nocaptcha.io/register?c=hqLmMS)**
