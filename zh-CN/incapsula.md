---
# 🚀 免费注册获取API密钥
**[立即注册 NoCaptcha.io →](https://www.nocaptcha.io/register?c=hqLmMS)**  
*专业验证码解决方案 | 高成功率 | 快速响应 | 24/7技术支持*

---

[`返回首页`](../README.md)    [`上一页`](hcaptcha.md)       [`下一页`](incapsula_utmvc.md)   [`English Version`](../en-US/incapsula.md)

# Incapsula (Reese84) 验证码破解服务

## 🔥 产品优势

### 为什么选择我们的Incapsula解决方案

* **🌐 通用兼容性**: 目前已知网站均能通过验证，支持所有Incapsula Reese84类型验证
* **⚡ 极致速度**: 采用`纯算法`计算参数，`协议提交`，`同步返回`结果
* **🔄 稳定可靠**: 更新及时（不超过2小时），为您的业务提供稳定支撑
* **🎯 高成功率**: 专业算法优化，确保高通过率

## 📋 常见问题解答

### 如何获取href参数？

**重要提示**：当页面有多个src链接时，请选择包含 `async` 关键字的链接

![incapsula参数获取](/images/incapsula/incapsula.png)

### href返回内容示例

响应中会包含类似混淆代码，这是正常现象：

![incapsula响应示例](/images/incapsula/incapsula2.png)

## 🔗 API接口信息

### 请求地址（POST）

| 版本类型 | 接口地址 |
|---------|---------|
| **Reese84（Universal）** | `http://api.nocaptcha.io/api/wanda/incapsula/reese84` |

### 请求头参数

| 参数名 | 说明 | 必填 |
|--------|------|------|
| `User-Token` | 用户密钥，从主页获取 | ✅ |
| `Content-Type` | `application/json` | ✅ |
| `Developer-Id` | 开发者ID，开发者用户使用，用户主页邀请链接的字符串(如 xxx/register?c=abcdef, 则 abcdef 为开发者ID) | ❌ |

### POST请求参数（JSON格式）

| 参数名 | 类型 | 说明 | 必填 |
|--------|------|------|------|
| `href` | `String` | 🚨**触发Incapsula验证的获取JS地址**，选择带async关键字的链接 | ✅ |
| `user_agent` | `String` | 请求流程使用的UA，后续请求会校验UA一致性 | ✅ |
| `cookies` | `Object` | 当提示需要包含rbzid、rbzsessionid的cookies时使用 | ❌ |

### 📝 请求示例

```json
{
  "href": "https://www.priceline.com.au/Cawdor-asse-my-Nightning-we-from-Dealell-Come-Ty",
  "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/108.0.0.0 Safari/537.36"
}
```

## 📤 响应数据格式

| 参数名 | 类型 | 说明 |
|--------|------|------|
| `status` | `Integer` | 调用状态：1=成功，0=失败 |
| `msg` | `String` | 调用结果说明 |
| `id` | `String` | 请求唯一ID（可用于记录查询） |
| `data.solution` | `String` | 验证成功返回的solution，用于后续请求获取reese84接口 |
| `cost` | `String` | 验证耗时（毫秒） |

### 响应示例

```json
{
  "status": 1,
  "msg": "验证成功",
  "id": "4a8019cc-321b-467f-9273-2698fb14288b",
  "cost": "2575.75ms",
  "data": {
    "solution": {
      "interrogation": {
        "p": "A long string",
        "st": 1691455449,
        "sr": 1259062184,
        "cr": 352269128,
        "og": 1
      },
      "version": "beta"
    },
    "old_token": null,
    "error": null,
    "performance": {
      "interrogation": 643
    }
  },
  "extra": {}
}
```

## 💻 代码示例

### CURL命令

```bash
curl -L 'http://api.nocaptcha.io/api/wanda/incapsula/reese84' \
 -H 'User-Token: xxx' \
 -H 'Developer-Id: hqLmMS' \
 -H 'Content-Type: application/json' \
 --data-raw '{"href": "https://www.priceline.com.au/Cawdor-asse-my-Nightning-we-from-Dealell-Come-Ty", "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/108.0.0.0 Safari/537.36"}'
```

### Python调用示例

**安装依赖**
```bash
pip install -U pynocaptcha -i https://pypi.python.org/simple
```

**代码示例**
```python
from pynocaptcha import IncapsulaReee84Cracker

# Incapsula Reese84验证码破解
cracker = IncapsulaReee84Cracker(
    user_token="your_user_token_here",
    developer_id="hqLmMS",  # 开发者ID
    href="https://www.priceline.com.au/Cawdor-asse-my-Nightning-we-from-Dealell-Come-Ty",
    user_agent="Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/108.0.0.0 Safari/537.36",
    debug=True
)
result = cracker.crack()
print(f"破解结果: {result}")
```

---

## 🎯 相关服务

- [Incapsula UTMVC验证码破解](incapsula_utmvc.md)
- [Incapsula RBZID验证码破解](incapsula_rbzid.md)
- [ReCaptcha验证码破解](recaptcha.md)
- [更多验证码解决方案](../README.md)

**需要技术支持？[立即联系我们](https://www.nocaptcha.io/register?c=hqLmMS)**
