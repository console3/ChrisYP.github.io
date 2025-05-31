---
# 🚀 免费注册获取API密钥
**[立即注册 NoCaptcha.io →](https://www.nocaptcha.io/register?c=hqLmMS)**  
*专业验证码解决方案 | 高成功率 | 快速响应 | 24/7技术支持*

---

[`返回首页`](../README.md)    [`上一页`](incapsula_rbzid.md)  [`下一页`](tls.md)	[`English Version`](../en-US/akamai.md)

# Akamai 验证码破解服务

## 🔥 产品优势

### 为什么选择我们的Akamai解决方案

* **🌐 通用兼容性**: 支持Akamai v2/v3所有版本，适用于各种网站验证场景
* **⚡ 极致速度**: 采用`纯算法`计算参数，`协议提交`，`同步返回`结果
* **🔄 稳定可靠**: 更新及时，为您的业务提供稳定支撑
* **🎯 多模式支持**: 支持标准验证、Telemetry验证等多种模式

## 📋 Akamai验证说明

### 🔍 验证模式类型

**标准模式**：常规的sensor_data验证
**Telemetry模式**：headers中的akamai-bm-telemetry参数验证（如Maersk API）

## 🔗 API接口信息

### 请求地址（POST）

| 版本类型 | 接口地址 |
|---------|---------|
| **V2（Universal）** | `http://api.nocaptcha.io/api/wanda/akamai/v2` |

### 请求头参数

| 参数名 | 说明 | 必填 |
|--------|------|------|
| `User-Token` | 用户密钥，从主页获取 | ✅ |
| `Content-Type` | `application/json` | ✅ |
| `Developer-Id` | 开发者ID，开发者用户使用，用户主页邀请链接的字符串(如 xxx/register?c=abcdef, 则 abcdef 为开发者ID) | ❌ |

### POST请求参数（JSON格式）

| 参数名 | 类型 | 说明 | 必填 |
|--------|------|------|------|
| `href` | `String` | 🚨**触发Akamai验证的页面地址** | ✅ |
| `api` | `String` | Akamai提交sensor_data验证接口地址（该地址会定期更换） | ❌ |
| `telemetry` | `Boolean` | 是否为headers中的telemetry参数验证形式，默认false | ❌ |
| `cookies` | `Object` | cookies值，必须包含_abck、bm_sz两个参数 | ❌ |
| `proxy` | `String` | 代理地址，建议使用海外代理，格式：ip:port 或 usr:pwd@ip:port | ❌ |

## 📝 请求示例

### 基础验证示例

```json
{
    "href": "https://www.jetstar.com/"
}
```

### 带Cookies验证示例

```json
{
    "href": "https://www.jetstar.com/",
    "cookies": {
        "value": "_abck=D719B7C0C6B1EBE8FC8F5C1B804B2265~-1~YAAQJescuEJsVzWIAQAAnwAZQQkN297mPe+Q48Xd0/10jSvgz/y69qQbPEwxUuQZhIhisL+GFAMfvabHtQPRUbiIqzDD6vA9iN9lvjzaAbKaL+aNXF/3EhpYYYUsBa0q92JUxusD8F09nFXy3mfZ8p8GzDk+/ikw4Y8QVQcchjC/s6XYbG+I2RSHl+lDOSvR2biGLFZ1dW2PsFZQ6Fs4M1/ccWfaXg6IRvzjlWaF0vH8GIoljDVRvZxwCeUO71QJORFxeVEEO43BiC3LczJhMomt8pnTbnJcMbMbi1zFcYUKUZjYvB7+kJ1JsMHfVdzbrwTB2I3bePGPgX06RvzCReVCETYpJB7H+XEeJgQQDzKiYZhCONfnae3BQUll~-1~-1~1684722838; bm_sz=751A827227D797408E66A3559D978757~YAAQpVcyuNsPVjCIAQAAMTCrRhNw86NLVNcBypYZvOkbMMnc+ef6EeDWu9UtvPw3OfyfpKLmEFQeDw99mddahdMlOj3VxzPz8eV9mfMSWDLxup33fIKAvsMvnUjvAJV0gpZvTTwdk0atKXCg1DXvs+U+VOvPPJtS76B2t+r0jXrB+cUm2hJL7qF59kbHLBl54yypauoWa1qEu9lgelS5kdwiR93A0c9IRagfLG4VjFydhZBoD6ldWEQjQUflrf00GSoxQpL0QBKRlD7fFNRtMhBmndvu5yoGdixtPXCEKk5BzRl/~4605506~4276528",
        "uri": "https://www.jetstar.com/"
    }
}
```

### Telemetry模式示例

```json
{
    "href": "https://www.maersk.com.cn/instantPrice/quotes",
    "telemetry": true
}
```

## 📤 响应数据格式

| 参数名 | 类型 | 说明 |
|--------|------|------|
| `status` | `Integer` | 调用状态：1=成功，0=失败 |
| `msg` | `String` | 调用结果说明 |
| `id` | `String` | 请求唯一ID（可用于记录查询） |
| `data._abck` | `String` | 验证成功返回的_abck cookie |
| `cost` | `String` | 验证耗时（毫秒） |

### 响应示例

```json
{
    "status": 1,
    "msg": "验证通过",
    "id": "8a8f0778-da09-4eea-a32d-e3b508654ba6",
    "cost": "1984.57ms",
    "data": {
        "_abck": "2EDD22DB758F24695963E50D3C9A776F~0~YAAQx/ggF8FPIJ2HAQAA8nKqrQmFx5H17A/jMUd1alzWlJ6VXb6NGDhXkb/1cJW+Bp0jJYvWVj8hQVc1vRKAiKQ1HLm0JIo8kg00KEBoAyRG+VZZPRV6ikricthJ69SlXF99wcHaHwx7mvDZdwwAtJBl+Fp2Kagx62AbUYZjEpc9aOCZ5KXBQhdrwCrzzXWsu5WEgmGovNqegFuIpW1ifsVPe13QSi8EjwF/nsuJQShLeRgsls1JB0Trwx8Kg3qRFiL9g4rtAdeW8OwYQ4DXj3PoBU56G0I4oCrhm6urGs8wMaU3OdpW6SRBAV93r4FO6K+lmcm8BVcfYc70/wVuEx3Fx0zpesE0fkdKC6N5c80AjVtSgJnDLFuShDnXo+wsWGROM1vxP7sC7N6raiSN66sX4UxGlkAJiCU=~-1~||1-hkqRyYlvue-1-10-1000-2||~-1"
    }
}
```

## 💻 代码示例

### CURL命令

```bash
curl -L 'http://api.nocaptcha.io/api/wanda/akamai/v2' \
 -H 'User-Token: xxx' \
 -H 'Developer-Id: hqLmMS' \
 -H 'Content-Type: application/json' \
 --data-raw '{"href": "https://www.jetstar.com/", "api": "https://www.jetstar.com/3Fl6sx/QIvaPL/b/7Hf/iQxyLG8eyP4/acumkkpfYkV7EO/ZyMtejt5PAc/REZU/Jk85Pn4"}'
```

### Python调用示例

**安装依赖**
```bash
pip install -U pynocaptcha -i https://pypi.python.org/simple
```

**代码示例**
```python
from pynocaptcha import AkamaiV2Cracker

# Akamai验证码破解
cracker = AkamaiV2Cracker(
    user_token="your_user_token_here",
    developer_id="hqLmMS",  # 开发者ID
    href="https://www.jetstar.com/",
    debug=True
)
result = cracker.crack()
print(f"破解结果: {result}")
```

**Telemetry模式示例**
```python
from pynocaptcha import AkamaiV2Cracker

# Akamai Telemetry模式验证
cracker = AkamaiV2Cracker(
    user_token="your_user_token_here",
    developer_id="hqLmMS",  # 开发者ID
    href="https://www.maersk.com.cn/instantPrice/quotes",
    telemetry=True,
    debug=True
)
result = cracker.crack()
print(f"破解结果: {result}")
```

---

## 🎯 相关服务

- [Incapsula RBZID验证码破解](incapsula_rbzid.md)
- [TLS指纹验证](tls.md)
- [ReCaptcha验证码破解](recaptcha.md)
- [更多验证码解决方案](../README.md)

**需要技术支持？[立即联系我们](https://www.nocaptcha.io/register?c=hqLmMS)**
