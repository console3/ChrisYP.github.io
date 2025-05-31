---
# 🚀 免费注册获取API密钥
**[立即注册 NoCaptcha.io →](https://www.nocaptcha.io/register?c=hqLmMS)**  
*专业验证码解决方案 | 高成功率 | 快速响应 | 24/7技术支持*

---

[`返回首页`](../README.md)    [`上一页`](recaptcha.md)      [`下一页`](incapsula.md)  [`English Version`](../en-US/hcaptcha.md)

# HCaptcha 验证码破解服务

## 🔥 产品特色

### 为什么选择我们的HCaptcha解决方案

* **🎯 高精度识别**: 专业的HCaptcha识别算法，确保高成功率
* **⚡ 快速响应**: 平均响应时间短，提升用户体验
* **🔧 灵活配置**: 支持多种参数配置，适应不同网站需求
* **🛡️ 稳定可靠**: 7x24小时稳定服务，支持高并发请求

## ⚠️ 重要说明

### 分数说明
🚨 **如果您获取到值但网站校验不通过，请联系管理员**

### Referer参数说明
🚨 **触发页面地址**：
- ✅ 请复制浏览器地址栏显示的完整地址
- ❌ 不要修改，更不要在开发者工具中查找
- 或者找到下图的包，使用host参数值，referer填写为 `http://{host}`

![HCaptcha参数获取](/images/hcaptcha/img.png)

## 🔗 API接口信息

### 请求地址（POST）

| 版本类型 | 接口地址 |
|---------|---------|
| **通用版（Universal）** | `http://api.nocaptcha.io/api/wanda/hcaptcha/universal` |

### 请求头参数

| 参数名 | 说明 | 必填 |
|--------|------|------|
| `User-Token` | 用户密钥，从主页获取 | ✅ |
| `Content-Type` | `application/json` | ✅ |
| `Developer-Id` | 开发者ID，开发者用户使用，用户主页邀请链接的字符串(如 xxx/register?c=abcdef, 则 abcdef 为开发者ID) | ❌ |

### POST请求参数（JSON格式）

| 参数名 | 类型 | 说明 | 必填 |
|--------|------|------|------|
| `sitekey` | `String` | HCaptcha对接key | ✅ |
| `referer` | `String` | 触发页面地址（见上文参数说明） | ✅ |
| `rqdata` | `String` | 验证码配置接口返回的captcha_rqdata、captcha_rqtoken值（如Discord加频道） | ❌ |
| `domain` | `String` | HCaptcha验证接口域名（getcaptcha/checkcaptcha等接口域名），默认hcaptcha.com | ❌ |
| `proxy` | `String` | 代理地址，格式：ip:port 或 usr:pwd@ip:port 或 socks5://ip:port | ❌ |
| `region` | `String` | 代理地区（传入proxy时使用），如：hk, sg | ❌ |
| `invisible` | `Boolean` | 是否为无感验证码（触发时是否能看见点击框），默认false | ❌ |
| `need_ekey` | `Boolean` | 是否需要返回E0_ey...格式的key，默认false | ❌ |

## 📝 请求示例

### Discord示例
```json
{
  "sitekey": "a9b5fb07-92ff-493f-86fe-352a2803b3df",
  "referer": "https://discord.com/channels/253581140072464384/357581480110850049",
  "rqdata": "RRZ5RNoOL4uNPvEp0yB+bMPkBe2lUiM7p4u5lMAVUC9UBmzxJqdDDpGMrcDNApg/DDAQNIIlwEn2dLr7dZMg32I2bi523ZRfkAKpKxxg1sqnVW0xR9Y9ZCcwv54EiHeEqQ+iipixAVozAb6LjtwzNm2H9L15iSN8QfVrcp0Z"
}
```

### Stripe示例
```json
{
  "sitekey": "c7faac4c-1cd7-4b1b-b2d4-42ba98d09c7a",
  "referer": "https://b.stripecdn.com/stripethirdparty-srv/assets/v13.1/HCaptcha.html?id=ab2764cd-d392-4fd0-81b4-9de6c4144c31&origin=https%3A%2F%2Fjs.stripe.com",
  "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/114.0.0.0 Safari/537.36",
  "proxy": "ip:port"
}
```

### Epic Games示例
```json
{
  "sitekey": "c7faac4c-1cd7-4b1b-b2d4-42ba98d09c7a",
  "referer": "https://b.stripecdn.com/stripethirdparty-srv/assets/v13.1/HCaptcha.html?id=ab2764cd-d392-4fd0-81b4-9de6c4144c31&origin=https%3A%2F%2Fjs.stripe.com",
  "domain": "hcaptcha-endpoint.ecosec.on.epicgames.com",
  "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/114.0.0.0 Safari/537.36",
  "rqdata": "RRZ5RNoOL4uNPvEp0yB+bMPkBe2lUiM7p4u5lMAVUC9UBmzxJqdDDpGMrcDNApg/DDAQNIIlwEn2dLr7dZMg32I2bi523ZRfkAKpKxxg1sqnVW0xR9Y9ZCcwv54EiHeEqQ+iipixAVozAb6LjtwzNm2H9L15iSN8QfVrcp0Z"
}
```

## 📤 响应数据格式

### 验证提交响应（submit=true）

| 参数名 | 类型 | 说明 |
|--------|------|------|
| `status` | `Integer` | 调用状态：1=成功，0=失败 |
| `msg` | `String` | 调用结果说明 |
| `id` | `String` | 请求唯一ID（可用于记录查询） |
| `data.generated_pass_UUID` | `String` | 验证通过返回的UUID凭证（P1_xxx/F1_xxx格式），用于后续验证接口 |
| `data.ekey` | `String` | 验证通过返回的key（E0_xxx格式），用于后续验证接口 |
| `cost` | `String` | 验证耗时（毫秒） |

### 响应示例

```json
{
  "cost": "9187.84ms",
  "data": {
    "generated_pass_UUID": "P1_eyxxx",
    "user_agent": "..."
  },
  "id": "c5b976bd-4c01-4378-bb44-324c76e9fe0f",
  "msg": "验证成功",
  "status": 1
}
```

## 💻 代码示例

### CURL命令

```bash
curl \
 -H "Host: api.nocaptcha.io" \
 -H "User-Agent: python-requests/2.28.2" \
 -H "Accept: */*" \
 -H "User-Token: xxx" \
 -H "Developer-Id: hqLmMS" \
 -H "Content-Type: application/json" \
 --data-binary '{"sitekey": "f5561ba9-8f1e-40ca-9b5b-a0b3f719ef34", "referer": "https://discord.com/login"}' \
 --compressed "http://api.nocaptcha.io/api/wanda/hcaptcha/universal"
```

### Python调用示例

**安装依赖**
```bash
pip install -U pynocaptcha -i https://pypi.python.org/simple
```

**基础调用示例**
```python
from pynocaptcha import HcaptchaCracker

# HCaptcha验证码破解
cracker = HcaptchaCracker(
    user_token="your_user_token_here",
    developer_id="hqLmMS",  # 开发者ID
    sitekey='a9b5fb07-92ff-493f-86fe-352a2803b3df',
    referer="https://discord.com/channels/253581140072464384/357581480110850049",
    rqdata="RRZ5RNoOL4uNPvEp0yB+bMPkBe2lUiM7p4u5lMAVUC9UBmzxJqdDDpGMrcDNApg/DDAQNIIlwEn2dLr7dZMg32I2bi523ZRfkAKpKxxg1sqnVW0xR9Y9ZCcwv54EiHeEqQ+iipixAVozAb6LjtwzNm2H9L15iSN8QfVrcp0Z",
    debug=True,
)
result = cracker.crack()
print(f"破解结果: {result}")
```

---

## 🎯 相关服务

- [ReCaptcha验证码破解](recaptcha.md)
- [Cloudflare验证码破解](cloudflare.md)
- [Incapsula验证码破解](incapsula.md)
- [更多验证码解决方案](../README.md)

**需要技术支持？[立即联系我们](https://www.nocaptcha.io/register?c=hqLmMS)**
