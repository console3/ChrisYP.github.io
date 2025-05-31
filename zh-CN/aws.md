# 🚀 免费注册获取API密钥
**[立即注册 NoCaptcha.io →](https://www.nocaptcha.io/register?c=hqLmMS)**  
*专业验证码解决方案 | 高成功率 | 快速响应 | 24/7技术支持*

---

[`返回首页`](../README.md)    [`上一页`](cloudflare.md)      [`下一页`](perimeterx.md)

# AWS WAF 验证码破解服务

## 🔥 产品优势

### 为什么选择我们的AWS WAF解决方案

* **🛡️ 专业破解**: 专门针对AWS WAF防护系统的破解技术
* **⚡ 高效处理**: 快速绕过AWS WAF验证，提升访问效率
* **🎯 精准识别**: 智能识别不同类型的AWS WAF验证
* **💰 价格优惠**: 无感验证仅需150点，传入代理享受折扣

## 📋 服务说明

### 重要提醒
* 线上仅为测试服务，稳定/量大/独享/包月/优惠请联系管理员

## 🔍 验证类型说明

### AWS WAF Token验证
**特征**：返回 `aws-waf-token` 用于后续请求验证
- **无感验证**：150点（推荐）
- **标准验证**：500点
- **传入代理优惠**：250点/150点

## 🔗 API接口信息

### 请求地址（POST）

| 版本类型 | 接口地址 |
|---------|---------|
| **通用版（Universal）** | `http://api.nocaptcha.io/api/wanda/aws/universal` |

### 请求头参数

| 参数名 | 说明 | 必填 |
|--------|------|------|
| `User-Token` | 用户密钥，从主页获取 | ✅ |
| `Content-Type` | `application/json` | ✅ |
| `Developer-Id` | 开发者ID，开发者用户使用，用户主页邀请链接的字符串(如 xxx/register?c=abcdef, 则 abcdef 为开发者ID) | ❌ |

### POST请求参数（JSON格式）

| 参数名 | 类型 | 说明 | 必填 |
|--------|------|------|------|
| `href` | `String` | 触发验证的页面地址 | ✅ |
| `proxy` | `String` | 代理地址，格式：ip:port 或 usr:pwd@ip:port 或 socks5://ip:port | ❌ |
| `user_agent` | `String` | 自定义User-Agent（如返回不支持则不要传） | ❌ |
| `invisible` | `Boolean` | 是否为无感验证（推荐使用，仅150点） | ❌ |

## 📝 请求示例

### 无感验证示例（推荐）
```json
{
    "href": "https://example.com/protected-page",
    "proxy": "usr:pwd@ip:port",
    "invisible": true,
    "user_agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36"
}
```

### 标准验证示例
```json
{
    "href": "https://example.com/protected-page",
    "proxy": "usr:pwd@ip:port",
    "user_agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36"
}
```

## 📤 响应数据格式

| 参数名 | 类型 | 说明 |
|--------|------|------|
| `status` | `Integer` | 调用状态：1=成功，0=失败 |
| `msg` | `String` | 调用结果说明 |
| `id` | `String` | 请求唯一ID（可用于记录查询） |
| `data.aws_waf_token` | `String` | AWS WAF验证通过返回的token |
| `data.cookies` | `String` | 验证通过返回的相关cookies |
| `cost` | `String` | 验证耗时（毫秒） |

### 响应示例

```json
{
    "cost": "2180.45ms",
    "data": {
        "aws_waf_token": "12345678-1234-1234-1234-123456789abc:B8BkdVjHtM0=:example_token_value",
        "cookies": "aws-waf-token=12345678-1234-1234-1234-123456789abc:B8BkdVjHtM0=:example_token_value; Path=/; Secure; HttpOnly"
    },
    "id": "aws-waf-request-12345",
    "msg": "验证成功",
    "status": 1
}
```

## 💻 代码示例

### CURL命令

```bash
curl -L 'http://api.nocaptcha.io/api/wanda/aws/universal' \
 -H 'User-Token: your_user_token_here' \
 -H 'Developer-Id: hqLmMS' \
 -H 'Content-Type: application/json' \
 --data-raw '{"href": "https://example.com/protected-page", "proxy": "usr:pwd@ip:port", "invisible": true}'
```

### Python调用示例

**安装依赖**
```bash
pip install -U pynocaptcha -i https://pypi.python.org/simple
```

**基础调用示例**
```python
from pynocaptcha import AwsCracker

# AWS WAF验证码破解
cracker = AwsCracker(
    user_token="your_user_token_here",
    developer_id="hqLmMS",  # 开发者ID
    href="https://example.com/protected-page",
    proxy="usr:pwd@ip:port",
    invisible=True,  # 使用无感验证（推荐）
    debug=True,
)
result = cracker.crack()
print(f"破解结果: {result}")

# 使用返回的token进行后续请求
if result['status'] == 1:
    aws_waf_token = result['data']['aws_waf_token']
    print(f"AWS WAF Token: {aws_waf_token}")
```

## ⚠️ 重要说明

### 使用注意事项
- **保持一致性**: 使用返回的token时，保持IP、User-Agent一致
- **及时使用**: AWS WAF token有时效性，建议及时使用
- **代理质量**: 使用高质量代理可提高成功率
- **无感优先**: 推荐使用无感验证，成本更低且成功率更高

### 常见问题
- **Token失效**: 检查是否超过有效期，重新获取
- **验证失败**: 确认代理质量和网络连接
- **参数错误**: 检查href参数是否为完整的URL

---

## 🎯 相关服务

- [CloudFlare验证码破解](cloudflare.md)
- [ReCaptcha验证码破解](recaptcha.md)
- [HCaptcha验证码破解](hcaptcha.md)
- [更多验证码解决方案](../README.md)

**需要技术支持？[立即联系我们](https://www.nocaptcha.io/register?c=hqLmMS)**
