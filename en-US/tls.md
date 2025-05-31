---
# 🚀 Free Registration for API Key
**[Register Now at NoCaptcha.io →](https://www.nocaptcha.io/register?c=hqLmMS)**  
*Professional CAPTCHA Solutions | High Success Rate | Fast Response | 24/7 Technical Support*

---

[`Back to homepage`](en.md)  [`中文文档`](../zh-CN/tls.md)

# TLS Client Service

## 🔥 Product Advantages

### Why Choose Our TLS Client Solution

* **🌐 Universal Compatibility**: Support for HTTP/HTTPS/SOCKS5 proxies and HTTP2 protocol
* **⚡ High Performance**: Fast request processing with custom JA3 fingerprint support
* **🔄 Reliable & Stable**: Timely updates to ensure stable business support
* **🎯 Advanced Features**: Custom headers, cookies, redirects, and timeout control

## 📋 TLS Client Features

### 🔍 Key Capabilities

* **Multiple Protocols**: Support for HTTP/1.1 and HTTP/2
* **Custom Fingerprints**: JA3 fingerprint customization for advanced stealth
* **Proxy Support**: HTTP, HTTPS, and SOCKS5 proxy compatibility
* **Flexible Requests**: GET/POST methods with JSON and form data support
* **Cookie Management**: Automatic cookie handling with domain specification

## 🔗 API Information

### Request URL (POST)

| Version Type | API Address |
|-------------|-------------|
| **V1 (Universal)** | `http://api.nocaptcha.io/api/wanda/tls/v1` |

### Request Headers

| Parameter | Description | Required |
|-----------|-------------|----------|
| `User-Token` | User key, obtain from homepage | ✅ |
| `Content-Type` | `application/json` | ✅ |
| `Developer-Id` | Developer ID, used by developer users, string from user homepage invite link (e.g., if link is xxx/register?c=abcdef, then abcdef is the developer ID) | ❌ |

### POST Parameters (JSON Format)

| Parameter | Type | Description | Required |
|-----------|------|-------------|----------|
| `url` | `String` | 🚨**Request URL address** | ✅ |
| `method` | `String` | Request method: get/post | ❌ |
| `headers` | `String or Object` | Request headers, can be string or object, default: {'User-Agent': 'random ua'} | ❌ |
| `cookies.value` | `String or Object` | Cookies for request, can be string or object, e.g., {'1': '2', '3': '4'} or '1=2; 3=4' | ❌ |
| `cookies.uri` | `String` | Domain where cookies are set, use URL | ❌ |
| `proxy` | `String` | Proxy for request. Formats: {ip}:{port} or {user}:{password}@{ip}:{port}. For SOCKS5: {protocol}://{ip}:{port} | ❌ |
| `data` | `String or Object` | Body for POST request, can be string or object | ❌ |
| `json` | `String or Object` | JSON data for POST request, example: {'1': '2', '3': '4'} | ❌ |
| `timeout` | `Number` | Request timeout in seconds, default: 15 | ❌ |
| `http2` | `Boolean` | Whether to use HTTP/2 protocol, default: false | ❌ |
| `redirect` | `Boolean` | Whether to follow redirects, default: true | ❌ |
| `ja3` | `String` | Custom JA3 fingerprint. If not provided, defaults to latest random Chrome fingerprint | ❌ |

## 📝 Request Example

```json
{
    "url": "https://api-fashion.dior.com/graph?SubscribeNewsletter",
    "method": "post",
    "headers": {
        "Accept-Language": "zh-CN,zh;q=0.9",
        "Cache-Control": "no-cache",
        "Connection": "keep-alive",
        "DNT": "1",
        "Origin": "https://www.dior.com",
        "Pragma": "no-cache",
        "Referer": "https://www.dior.com/",
        "Sec-Fetch-Dest": "empty",
        "Sec-Fetch-Mode": "cors",
        "Sec-Fetch-Site": "same-site",
        "User-Agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/114.0.0.0 Safari/537.36",
        "accept": "*/*",
        "apollographql-client-name": "Newlook Couture Catalog K8S",
        "apollographql-client-version": "5.282.3-8601f7a7.hotfix",
        "content-type": "application/json",
        "sec-ch-ua": "\"Not.A/Brand\";v=\"8\", \"Chromium\";v=\"114\", \"Google Chrome\";v=\"114\"",
        "sec-ch-ua-mobile": "?0",
        "sec-ch-ua-platform": "\"macOS\"",
        "x-dior-locale": "zh_hk",
        "x-dior-universe": "onedior"
    },
    "cookies": {
        "value": "_abck=D719B7C0C6B1EBE8FC8F5C1B804B2265~-1~YAAQJescuEJsVzWIAQAAnwAZQQkN297mPe+Q48Xd0/10jSvgz/y69qQbPEwxUuQZhIhisL+GFAMfvabHtQPRUbiIqzDD6vA9iN9lvjzaAbKaL+aNXF/3EhpYYYUsBa0q92JUxusD8F09nFXy3mfZ8p8GzDk+/ikw4Y8QVQcchjC/s6XYbG+I2RSHl+lDOSvR2biGLFZ1dW2PsFZQ6Fs4M1/ccWfaXg6IRvzjlWaF0vH8GIoljDVRvZxwCeUO71QJORFxeVEEO43BiC3LczJhMomt8pnTbnJcMbMbi1zFcYUKUZjYvB7+kJ1JsMHfVdzbrwTB2I3bePGPgX06RvzCReVCETYpJB7H+XEeJgQQDzKiYZhCONfnae3BQUll~-1~-1~1684722838",
        "uri": "https://www.dior.com/"
    },
    "json": {
        "operationName": "SubscribeNewsletter",
        "variables": {
            "input": {
                "newsletters": {
                    "couture": true,
                    "beauty": false
                },
                "profiling": {},
                "user": {
                    "title": "Mme",
                    "email": "1456551412@qq.com",
                    "firstName": "afasdf",
                    "lastName": "qweqwe"
                }
            }
        },
        "query": "mutation SubscribeNewsletter($input: NewslettersOptinLegacyInput!) {\n  subscribeNewsletter(input: $input) {\n    success\n    errorMessages\n    errorDetail\n    __typename\n  }\n}\n"
    },
    "proxy": "socks5h://123:456@127.0.0.1:1234",
    "http2": true,
    "redirect": false,
    "ja3": "771,4865-4866-4867-49195-49199-49196-49200-52393-52392-49171-49172-156-157-47-53,5-43-18-10-13-51-23-16-17513-27-65281-35-45-0-11-21,29-23-24,0"
}
```

## 📤 Response Data Format

| Parameter | Type | Description |
|-----------|------|-------------|
| `status` | `Integer` | Call status: 1=success, 0=failure |
| `msg` | `String` | Result description |
| `id` | `String` | Unique request ID (for record queries) |
| `data.status` | `Number` | Response status code |
| `data.text` | `String` | Response body |
| `data.cookies` | `String` | Response cookies |
| `data.location` | `String` | Redirect URL |
| `cost` | `String` | Processing time (milliseconds) |

### Response Example

```json
{
    "status": 1,
    "msg": "Request successful",
    "id": "049bfae2-4e84-4f29-99aa-a33688991355",
    "cost": "1414.15ms",
    "data": {
        "response": {
            "status": 200,
            "text": "{\"data\":{\"subscribeNewsletter\":{\"success\":true,\"errorMessages\":null,\"errorDetail\":null,\"__typename\":\"NewsletterOptinResponse\"}}}\n",
            "tls": {
                "ja3": "771,4865-4866-4867-49195-49199-49196-49200-52393-52392-49171-49172-156-157-47-53,51-23-43-45-27-17513-5-11-18-10-13-0-35-65281-16-21-41,29-23-24,0",
                "ja3_hash": "2795d91de2c9d7e36984350e338ddc9a",
                "akamai": "1:65536,2:0,3:1000,4:6291456,6:262144|15663105|0|m,a,s,p",
                "akamai_hash": "46cedabdca2073198a42fa10ca4494d0"
            },
            "cookies": "dtCookie=v_4_srv_5_sn_2A2A9F901F6BE925EF475041C744108A_perc_100000_ol_0_mul_1_app-3Aea7c4b59f27d43eb_1; _abck=6D43584C164A308CFC85AE1462D56CD1~0~YAAQpqg7FxN5F5+IAQAAXFwfvgpoxc0IH5DxeBHUCgDMC4vh8eHRZkqMr5rUFAxg+Zjwi0ouU4PF9WIT9rdcJtenDDu9T438N+xtPqd0JdzKePw3Y7u7OJkZe95KAzQ/L9VqCPLEvHC9Nap2ELrgIY32GRzJKj2qgPmuX4avgoopJmJ7hLhfq9rGwqkfBWaykDHs1MHb8xSjmr/bGbDHbpzSlThrEU8PlKxL/QWOIgPDyD/hZWi5wVyLG5zim5hVeykHZEiXgucS9u/gTHUGMmlz+EZU+Gj1rZ5/vMRqe9mieGJj+93IZElOAdT5SeXmmr++XZx8PEJaE8UTj+gCADhi74Up9AR7HxFcL5yI2uixdkQt28OYUzA4JwGmk2YpBDH4ZIVTnsxQ2TmlmtC4U3Avhw==~-1~-1~-1"
        }
    }
}
```

## 💻 Code Examples

### CURL Command

```bash
curl -L 'http://api.nocaptcha.io/api/wanda/tls/v1' \
 -H 'User-Token: xxx' \
 -H 'Developer-Id: hqLmMS' \
 -H 'Content-Type: application/json' \
 --data-raw '{"url": "https://www.baidu.com/", "method": "get"}'
```

### Python Example

**Install Dependencies**
```bash
pip install -U pynocaptcha -i https://pypi.python.org/simple
```

**Basic Example**
```python
from pynocaptcha import TlsV1Cracker

# TLS Client request
cracker = TlsV1Cracker(
    user_token="your_user_token_here",
    developer_id="hqLmMS",  # Developer ID
    url="https://www.baidu.com/"
)
result = cracker.crack()
print(f"Request result: {result}")
```

**Advanced Example**
```python
from pynocaptcha import TlsV1Cracker

# Advanced TLS Client with custom settings
cracker = TlsV1Cracker(
    user_token="your_user_token_here",
    developer_id="hqLmMS",
    url="https://api.example.com/data",
    method="post",
    headers={
        "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36",
        "Accept": "application/json",
        "Content-Type": "application/json"
    },
    json={
        "key": "value",
        "data": "example"
    },
    proxy="user:pass@ip:port",
    http2=True,
    ja3="771,4865-4866-4867-49195-49199-49196-49200-52393-52392-49171-49172-156-157-47-53,5-43-18-10-13-51-23-16-17513-27-65281-35-45-0-11-21,29-23-24,0",
    timeout=30
)

result = cracker.crack()

if result.get('status') == 1:
    response_data = result['data']['response']
    print(f"Status Code: {response_data['status']}")
    print(f"Response: {response_data['text']}")
    print(f"Cookies: {response_data.get('cookies', 'None')}")
else:
    print(f"Request failed: {result.get('msg')}")
```

**Complete Usage Example**
```python
import json
from pynocaptcha import TlsV1Cracker

class TlsClient:
    def __init__(self, user_token, developer_id="hqLmMS"):
        self.user_token = user_token
        self.developer_id = developer_id
    
    def request(self, url, method="get", **kwargs):
        """Make TLS request with custom parameters"""
        cracker = TlsV1Cracker(
            user_token=self.user_token,
            developer_id=self.developer_id,
            url=url,
            method=method,
            **kwargs
        )
        
        result = cracker.crack()
        
        if result.get('status') == 1:
            return {
                'success': True,
                'status_code': result['data']['response']['status'],
                'text': result['data']['response']['text'],
                'cookies': result['data']['response'].get('cookies'),
                'tls_info': result['data']['response'].get('tls', {}),
                'cost': result.get('cost')
            }
        else:
            return {
                'success': False,
                'error': result.get('msg', 'Unknown error')
            }
    
    def get(self, url, **kwargs):
        """Make GET request"""
        return self.request(url, method="get", **kwargs)
    
    def post(self, url, **kwargs):
        """Make POST request"""
        return self.request(url, method="post", **kwargs)

# Usage example
client = TlsClient("your_user_token_here")

# GET request
response = client.get(
    "https://httpbin.org/get",
    headers={"User-Agent": "Custom-Agent/1.0"},
    proxy="user:pass@ip:port"
)

if response['success']:
    print(f"GET Response: {response['text']}")
else:
    print(f"GET Failed: {response['error']}")

# POST request with JSON
response = client.post(
    "https://httpbin.org/post",
    json={"test": "data", "number": 123},
    headers={"Content-Type": "application/json"},
    http2=True
)

if response['success']:
    print(f"POST Response: {response['text']}")
    print(f"TLS Info: {response['tls_info']}")
else:
    print(f"POST Failed: {response['error']}")
```

---

## 🎯 Related Services

- [ReCaptcha Solving](recaptcha.md)
- [hCaptcha Solving](hcaptcha.md)
- [Browser Plugin](plugin.md)
- [More CAPTCHA Solutions](en.md)

**Need Technical Support? [Contact Us Now](https://www.nocaptcha.io/register?c=hqLmMS)**
