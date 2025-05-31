---
# 🚀 Get Your Free API Key
**[Register Now at NoCaptcha.io →](https://www.nocaptcha.io/register?c=hqLmMS)**  
*Professional CAPTCHA Solutions | High Success Rate | Fast Response | 24/7 Support*

---

[`Back to homepage`](/en-US/en.md)   [`中文文档`](../zh-CN/incapsula.md)

# Incapsula (Reese84) CAPTCHA Solving Service

## 🔥 Why Choose Our Solution

### Advantages of Our Incapsula Service

* **🌐 Universal Compatibility**: All known websites can pass verification, supporting all Incapsula Reese84 types
* **⚡ Supreme Speed**: Uses `pure algorithm` to calculate parameters with `protocol submission` and `synchronous return`
* **🔄 Reliable Stability**: Timely updates (within 2 hours) to better support your business
* **🎯 High Success Rate**: Professional algorithm optimization ensures high pass rates

## 📋 Frequently Asked Questions

### How to Get the href Parameter?

**Important Note**: When there are multiple src links on the page, choose the one with the `async` keyword

![Incapsula Parameter Extraction](/images/incapsula/incapsula.png)

### href Response Example

The response will include obfuscated code, which is normal:

![Incapsula Response Example](/images/incapsula/incapsula2.png)

## 🔗 API Information

### Request URL (POST)

| Version Type | Interface URL |
|--------------|---------------|
| **Reese84 (Universal)** | `http://api.nocaptcha.io/api/wanda/incapsula/reese84` |

### Request Headers

| Parameter | Description | Required |
|-----------|-------------|----------|
| `User-Token` | User secret key, obtained from homepage | ✅ |
| `Content-Type` | `application/json` | ✅ |
| `Developer-Id` | Developer ID for developer users, invitation link string from user homepage (e.g. xxx/register?c=abcdef, then abcdef is developer ID) | ❌ |

### POST Parameters (JSON Format)

| Parameter | Type | Description | Required |
|-----------|------|-------------|----------|
| `href` | `String` | 🚨**Address to get Incapsula JS when triggering verification**, choose link with async keyword | ✅ |
| `user_agent` | `String` | User agent for request process, subsequent requests check UA consistency | ✅ |
| `cookies` | `Object` | Use when prompted that cookies containing rbzid and rbzsessionid are required | ❌ |

## 📝 Request Example

```json
{
  "href": "https://www.priceline.com.au/Cawdor-asse-my-Nightning-we-from-Dealell-Come-Ty",
  "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/108.0.0.0 Safari/537.36"
}
```

## 📤 Response Format

| Parameter | Type | Description |
|-----------|------|-------------|
| `status` | `Integer` | Call status: 1=success, 0=failure |
| `msg` | `String` | Result description |
| `id` | `String` | Unique request ID (for record queries) |
| `data.solution` | `String` | Verification solution for subsequent reese84 interface requests |
| `cost` | `String` | Verification time (milliseconds) |

### Response Example

```json
{
  "status": 1,
  "msg": "Verification successful",
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

## 💻 Code Examples

### CURL Command

```bash
curl -L 'http://api.nocaptcha.io/api/wanda/incapsula/reese84' \
 -H 'User-Token: xxx' \
 -H 'Developer-Id: hqLmMS' \
 -H 'Content-Type: application/json' \
 --data-raw '{"href": "https://www.priceline.com.au/Cawdor-asse-my-Nightning-we-from-Dealell-Come-Ty", "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/108.0.0.0 Safari/537.36"}'
```

### Python Implementation

**Install Dependencies**
```bash
pip install -U pynocaptcha -i https://pypi.python.org/simple
```

**Code Example**
```python
from pynocaptcha import IncapsulaReee84Cracker

# Incapsula Reese84 CAPTCHA solving
cracker = IncapsulaReee84Cracker(
    user_token="your_user_token_here",
    developer_id="hqLmMS",  # Developer ID
    href="https://www.priceline.com.au/Cawdor-asse-my-Nightning-we-from-Dealell-Come-Ty",
    user_agent="Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/108.0.0.0 Safari/537.36",
    debug=True
)
result = cracker.crack()
print(f"Solving result: {result}")
```

---

## 🎯 Related Services

- [Incapsula UTMVC CAPTCHA Solving](incapsula_utmvc.md)
- [ReCaptcha CAPTCHA Solving](recaptcha.md)
- [HCaptcha CAPTCHA Solving](hcaptcha.md)
- [More CAPTCHA Solutions](en.md)

**Need Technical Support? [Contact Us Now](https://www.nocaptcha.io/register?c=hqLmMS)**
