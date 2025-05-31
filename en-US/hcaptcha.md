---
# 🚀 Get Free API Key Registration
**[Register NoCaptcha.io Now →](https://www.nocaptcha.io/register?c=hqLmMS)**  
*Professional CAPTCHA Solutions | High Success Rate | Fast Response | 24/7 Technical Support*

---

[`Back to homepage`](en.md) [`中文文档`](../zh-CN/hcaptcha.md)

# HCaptcha CAPTCHA Solving Service

## 🔥 Product Features

### Why Choose Our HCaptcha Solution

* **🎯 High Precision Recognition**: Professional HCaptcha recognition algorithms ensuring high success rates
* **⚡ Fast Response**: Short average response time, improving user experience
* **🔧 Flexible Configuration**: Supports various parameter configurations to adapt to different website requirements
* **🛡️ Stable & Reliable**: 24/7 stable service supporting high-concurrency requests

## ⚠️ Important Notes

### Score Information
🚨 **If you get a value but the website verification fails, please contact the administrator**

### Referer Parameter Instructions
🚨 **Trigger page address**:
- ✅ Please copy the complete address displayed in the browser address bar
- ❌ Do not modify, and definitely don't search in developer tools
- Or find the package shown below, use the host parameter value, fill referer as `http://{host}`

![HCaptcha Parameter Acquisition](/images/hcaptcha/img.png)

## 🔗 API Interface Information

### Request URL (POST)

| Version Type | Interface URL |
|-------------|---------------|
| **Universal Version** | `http://api.nocaptcha.io/api/wanda/hcaptcha/universal` |

### Request Headers

| Parameter Name | Description | Required |
|----------------|-------------|----------|
| `User-Token` | User key, obtained from homepage | ✅ |
| `Content-Type` | `application/json` | ✅ |
| `Developer-Id` | Developer ID, used by developer users. The string in the user homepage invitation link (e.g., xxx/register?c=abcdef, then abcdef is the developer ID) | ❌ |

### POST Request Parameters (JSON Format)

| Parameter Name | Type | Description | Required |
|----------------|------|-------------|----------|
| `sitekey` | `String` | HCaptcha docking key | ✅ |
| `referer` | `String` | Trigger page address (see parameter instructions above) | ✅ |
| `rqdata` | `String` | captcha_rqdata, captcha_rqtoken values returned by verification configuration interface (e.g., Discord join channel) | ❌ |
| `domain` | `String` | HCaptcha verification interface domain (getcaptcha/checkcaptcha interface domain), default hcaptcha.com | ❌ |
| `proxy` | `String` | Proxy address, format: ip:port or usr:pwd@ip:port or socks5://ip:port | ❌ |
| `region` | `String` | Proxy region (used when passing proxy), e.g.: hk, sg | ❌ |
| `invisible` | `Boolean` | Whether it's invisible verification (whether click box is visible when triggered), default false | ❌ |
| `need_ekey` | `Boolean` | Whether to return E0_ey... format key, default false | ❌ |

## 📝 Request Examples

### Discord Example
```json
{
  "sitekey": "a9b5fb07-92ff-493f-86fe-352a2803b3df",
  "referer": "https://discord.com/channels/253581140072464384/357581480110850049",
  "rqdata": "RRZ5RNoOL4uNPvEp0yB+bMPkBe2lUiM7p4u5lMAVUC9UBmzxJqdDDpGMrcDNApg/DDAQNIIlwEn2dLr7dZMg32I2bi523ZRfkAKpKxxg1sqnVW0xR9Y9ZCcwv54EiHeEqQ+iipixAVozAb6LjtwzNm2H9L15iSN8QfVrcp0Z"
}
```

### Stripe Example
```json
{
  "sitekey": "c7faac4c-1cd7-4b1b-b2d4-42ba98d09c7a",
  "referer": "https://b.stripecdn.com/stripethirdparty-srv/assets/v13.1/HCaptcha.html?id=ab2764cd-d392-4fd0-81b4-9de6c4144c31&origin=https%3A%2F%2Fjs.stripe.com",
  "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/114.0.0.0 Safari/537.36",
  "proxy": "ip:port"
}
```

## 📤 Response Data Format

### Verification Submission Response (submit=true)

| Parameter Name | Type | Description |
|----------------|------|-------------|
| `status` | `Integer` | Call status: 1=success, 0=failure |
| `msg` | `String` | Call result description |
| `id` | `String` | Unique request ID (can be used for record queries) |
| `data.generated_pass_UUID` | `String` | UUID credential returned upon successful verification (P1_xxx/F1_xxx format), used for subsequent verification interfaces |
| `data.ekey` | `String` | Key returned upon successful verification (E0_xxx format), used for subsequent verification interfaces |
| `cost` | `String` | Verification duration (milliseconds) |

### Response Example

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

## 💻 Code Examples

### CURL Command

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

### Python Call Examples

**Install Dependencies**
```bash
pip install -U pynocaptcha -i https://pypi.python.org/simple
```

**Basic Call Example**
```python
from pynocaptcha import HcaptchaCracker

# HCaptcha CAPTCHA Solving
cracker = HcaptchaCracker(
    user_token="your_user_token_here",
    developer_id="hqLmMS",  # Developer ID
    sitekey='a9b5fb07-92ff-493f-86fe-352a2803b3df',
    referer="https://discord.com/channels/253581140072464384/357581480110850049",
    rqdata="RRZ5RNoOL4uNPvEp0yB+bMPkBe2lUiM7p4u5lMAVUC9UBmzxJqdDDpGMrcDNApg/DDAQNIIlwEn2dLr7dZMg32I2bi523ZRfkAKpKxxg1sqnVW0xR9Y9ZCcwv54EiHeEqQ+iipixAVozAb6LjtwzNm2H9L15iSN8QfVrcp0Z",
    debug=True,
)
result = cracker.crack()
print(f"Solving result: {result}")
```

---

## 🎯 Related Services

- [ReCaptcha CAPTCHA Solving](recaptcha.md)
- [Cloudflare CAPTCHA Solving](../zh-CN/cloudflare.md)
- [Incapsula CAPTCHA Solving](incapsula.md)
- [More CAPTCHA Solutions](en.md)

**Need Technical Support? [Contact Us Now](https://www.nocaptcha.io/register?c=hqLmMS)**
