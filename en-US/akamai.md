---
# 🚀 Get Your Free API Key
**[Register Now at NoCaptcha.io →](https://www.nocaptcha.io/register?c=hqLmMS)**  
*Professional CAPTCHA Solutions | High Success Rate | Fast Response | 24/7 Support*

---

[`Back to homepage`](en.md) 	[`中文文档`](../zh-CN/akamai.md)

# Akamai CAPTCHA Solving Service

## 🔥 Why Choose Our Solution

### Advantages of Our Akamai Service

* **🌐 Universal Compatibility**: Supports Akamai v2/v3 all versions, suitable for various website verification scenarios
* **⚡ Supreme Speed**: Uses `pure algorithm` to calculate parameters with `protocol submission` and `synchronous return`
* **🔄 Reliable Stability**: Timely updates to better support your business
* **🎯 Multi-Mode Support**: Supports standard verification, Telemetry verification, and other modes

## 📋 Akamai Verification Types

### 🔍 Verification Mode Types

**Standard Mode**: Regular sensor_data verification
**Telemetry Mode**: akamai-bm-telemetry parameter verification in headers (e.g., Maersk API)

## 🔗 API Information

### Request URL (POST)

| Version Type | API Endpoint |
|--------------|--------------|
| **V2 (Universal)** | `http://api.nocaptcha.io/api/wanda/akamai/v2` |

### Request Headers

| Parameter | Description | Required |
|-----------|-------------|----------|
| `User-Token` | User secret key, obtained from homepage | ✅ |
| `Content-Type` | `application/json` | ✅ |
| `Developer-Id` | Developer ID for developer users, invitation link string from user homepage (e.g. xxx/register?c=abcdef, then abcdef is developer ID) | ❌ |

### POST Parameters (JSON Format)

| Parameter | Type | Description | Required |
|-----------|------|-------------|----------|
| `href` | `String` | 🚨**URL that triggers Akamai verification** | ✅ |
| `api` | `String` | Akamai endpoint for submitting sensor_data (this endpoint changes periodically) | ❌ |
| `telemetry` | `Boolean` | Whether it's telemetry parameter verification in headers, defaults to false | ❌ |
| `cookies` | `Object` | Cookie values, must include _abck and bm_sz parameters | ❌ |
| `proxy` | `String` | Proxy address, recommend overseas proxy, format: ip:port or usr:pwd@ip:port | ❌ |

## 📝 Request Examples

### Basic Verification Example

```json
{
    "href": "https://www.jetstar.com/"
}
```

### With Cookies Verification Example

```json
{
    "href": "https://www.jetstar.com/",
    "cookies": {
        "value": "_abck=D719B7C0C6B1EBE8FC8F5C1B804B2265~-1~YAAQJescuEJsVzWIAQAAnwAZQQkN297mPe+Q48Xd0/10jSvgz/y69qQbPEwxUuQZhIhisL+GFAMfvabHtQPRUbiIqzDD6vA9iN9lvjzaAbKaL+aNXF/3EhpYYYUsBa0q92JUxusD8F09nFXy3mfZ8p8GzDk+/ikw4Y8QVQcchjC/s6XYbG+I2RSHl+lDOSvR2biGLFZ1dW2PsFZQ6Fs4M1/ccWfaXg6IRvzjlWaF0vH8GIoljDVRvZxwCeUO71QJORFxeVEEO43BiC3LczJhMomt8pnTbnJcMbMbi1zFcYUKUZjYvB7+kJ1JsMHfVdzbrwTB2I3bePGPgX06RvzCReVCETYpJB7H+XEeJgQQDzKiYZhCONfnae3BQUll~-1~-1~1684722838; bm_sz=751A827227D797408E66A3559D978757~YAAQpVcyuNsPVjCIAQAAMTCrRhNw86NLVNcBypYZvOkbMMnc+ef6EeDWu9UtvPw3OfyfpKLmEFQeDw99mddahdMlOj3VxzPz8eV9mfMSWDLxup33fIKAvsMvnUjvAJV0gpZvTTwdk0atKXCg1DXvs+U+VOvPPJtS76B2t+r0jXrB+cUm2hJL7qF59kbHLBl54yypauoWa1qEu9lgelS5kdwiR93A0c9IRagfLG4VjFydhZBoD6ldWEQjQUflrf00GSoxQpL0QBKRlD7fFNRtMhBmndvu5yoGdixtPXCEKk5BzRl/~4605506~4276528",
        "uri": "https://www.jetstar.com/"
    }
}
```

### Telemetry Mode Example

```json
{
    "href": "https://www.maersk.com.cn/instantPrice/quotes",
    "telemetry": true
}
```

## 📤 Response Format

| Parameter | Type | Description |
|-----------|------|-------------|
| `status` | `Integer` | Call status: 1=success, 0=failure |
| `msg` | `String` | Result description |
| `id` | `String` | Unique request ID (for record queries) |
| `data._abck` | `String` | Valid _abck cookie returned after verification |
| `cost` | `String` | Verification time (milliseconds) |

### Response Example

```json
{
    "status": 1,
    "msg": "Verification passed",
    "id": "8a8f0778-da09-4eea-a32d-e3b508654ba6",
    "cost": "1984.57ms",
    "data": {
        "_abck": "2EDD22DB758F24695963E50D3C9A776F~0~YAAQx/ggF8FPIJ2HAQAA8nKqrQmFx5H17A/jMUd1alzWlJ6VXb6NGDhXkb/1cJW+Bp0jJYvWVj8hQVc1vRKAiKQ1HLm0JIo8kg00KEBoAyRG+VZZPRV6ikricthJ69SlXF99wcHaHwx7mvDZdwwAtJBl+Fp2Kagx62AbUYZjEpc9aOCZ5KXBQhdrwCrzzXWsu5WEgmGovNqegFuIpW1ifsVPe13QSi8EjwF/nsuJQShLeRgsls1JB0Trwx8Kg3qRFiL9g4rtAdeW8OwYQ4DXj3PoBU56G0I4oCrhm6urGs8wMaU3OdpW6SRBAV93r4FO6K+lmcm8BVcfYc70/wVuEx3Fx0zpesE0fkdKC6N5c80AjVtSgJnDLFuShDnXo+wsWGROM1vxP7sC7N6raiSN66sX4UxGlkAJiCU=~-1~||1-hkqRyYlvue-1-10-1000-2||~-1"
    }
}
```

## 💻 Code Examples

### CURL Command

```bash
curl -L 'http://api.nocaptcha.io/api/wanda/akamai/v2' \
 -H 'User-Token: xxx' \
 -H 'Developer-Id: hqLmMS' \
 -H 'Content-Type: application/json' \
 --data-raw '{"href": "https://www.jetstar.com/", "api": "https://www.jetstar.com/3Fl6sx/QIvaPL/b/7Hf/iQxyLG8eyP4/acumkkpfYkV7EO/ZyMtejt5PAc/REZU/Jk85Pn4"}'
```

### Python Implementation

**Install Dependencies**
```bash
pip install -U pynocaptcha -i https://pypi.python.org/simple
```

**Code Example**
```python
from pynocaptcha import AkamaiV2Cracker

# Akamai CAPTCHA solving
cracker = AkamaiV2Cracker(
    user_token="your_user_token_here",
    developer_id="hqLmMS",  # Developer ID
    href="https://www.jetstar.com/",
    debug=True
)
result = cracker.crack()
print(f"Solving result: {result}")
```

**Telemetry Mode Example**
```python
from pynocaptcha import AkamaiV2Cracker

# Akamai Telemetry mode verification
cracker = AkamaiV2Cracker(
    user_token="your_user_token_here",
    developer_id="hqLmMS",  # Developer ID
    href="https://www.maersk.com.cn/instantPrice/quotes",
    telemetry=True,
    debug=True
)
result = cracker.crack()
print(f"Solving result: {result}")
```

## 🎯 Use Cases

The API is designed for multiple scenarios:

1. **🔍 Basic URL Verification**: Send only the `href` to check if it triggers an Akamai challenge
2. **🍪 Detailed Verification with Cookies**: Submit `href` with cookies from previous response when API endpoint changes
3. **📱 Device-Specific Verification**: Specify device type to get responses for mobile or PC devices
4. **📊 Telemetry Verification**: Handle special Akamai challenges like Maersk that involve telemetry

---

## 🎯 Related Services

- [ReCaptcha CAPTCHA Solving](recaptcha.md)
- [HCaptcha CAPTCHA Solving](hcaptcha.md)
- [Incapsula CAPTCHA Solving](incapsula.md)
- [More CAPTCHA Solutions](en.md)

**Need Technical Support? [Contact Us Now](https://www.nocaptcha.io/register?c=hqLmMS)**
