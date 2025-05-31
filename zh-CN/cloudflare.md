# 🚀 免费注册获取API密钥
**[立即注册 NoCaptcha.io →](https://www.nocaptcha.io/register?c=hqLmMS)**  
*专业验证码解决方案 | 高成功率 | 快速响应 | 24/7技术支持*

---

[`返回首页`](../README.md)    [`上一页`](discord.md)      [`下一页`](aws.md)

# CloudFlare 验证码破解服务

## 🔥 产品优势

### 为什么选择我们的CloudFlare解决方案

* **🛡️ 全面支持**: 支持CloudFlare所有验证类型（Cookies模式、Turnstile验证码）
* **⚡ 高效破解**: 专业算法快速绕过CloudFlare防护
* **🎯 高成功率**: 针对不同类型验证提供最优解决方案
* **🔧 灵活配置**: 支持多种参数配置，适应各种网站需求

## 📋 服务说明

### 重要提醒
* 线上仅为测试服务，稳定/量大/独享/包月/优惠请联系管理员

## 🔍 验证类型说明

### 类型一：Cookies模式
**特征**：普通模式返回 `cf_clearance`、`__cf_bm` 等cookies
- 当未出现跳转页面但存在 `cf_clearance` 时，可设置 `alpha=true` 进行无感验证
- **必须传入代理**

![Cookies模式示例](/images/cloudflare/cookies.png)

### 类型二：Turnstile验证码模式
**特征**：验证码式，返回 `cf_turnstile-response`
- 消耗点数：300点（传入代理150点）
- 一般嵌入在登录框中，验证参数为 `captcha_api_key` 等键名
- 参数值以 `0.` 开头
- **代理非必传**

![Turnstile验证码示例](/images/cloudflare/captcha.png)

## 🔍 参数查找方法

### Cookies类型
- 直接输入触发页面地址即可

### Turnstile类型
- 需要额外输入 `sitekey` 参数
- 查找方法如下图所示：

![Sitekey查找](/images/cloudflare/sitekey.png)

## ⚠️ 重要说明

### Cookies模式注意事项
- 需要保持IP、User-Agent一致
- 校验TLS指纹，请使用TLS请求库或TLS转发服务

### Turnstile模式注意事项
- 结果通常可直接使用
- 传入代理只需150点

## 🔗 API接口信息

### 请求地址（POST）

| 版本类型 | 接口地址 |
|---------|---------|
| **通用版（Universal）** | `http://api.nocaptcha.io/api/wanda/cloudflare/universal` |

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
| `proxy` | `String` | 代理地址（Cookies模式必传，Turnstile非必传） | 视情况 |
| `sitekey` | `String` | Turnstile类型需要传入（价格为300点） | ❌ |
| `explicit` | `Boolean` | Turnstile类型，检查api.js链接是否有render=explicit参数 | ❌ |
| `action` | `String` | Turnstile类型中传入的action值 | ❌ |
| `cdata` | `String` | Turnstile类型，turnstile.render参数中有cdata才传 | ❌ |
| `user_agent` | `String` | 自定义请求头（如返回不支持则不要传） | ❌ |
| `alpha` | `Boolean` | 是否为无感cookies验证 | ❌ |

## 🔍 Action/Cdata参数查找（高级功能）

当验证类型为 `turnstile` 且在目标网站的 `*turnstile/v0/api.js` 链接中发现 `render=explicit` 参数时：

**步骤1**：设置 `explicit=true`

**步骤2**：查找action和cdata参数
- 打开F12搜索 `window.turnstile.render`

![Render查找](/images/cloudflare/render.png)

- 在该处下断点，清除cookie缓存刷新页面
- 查看 `action` 的值并填入

![Action查找](/images/cloudflare/action.png)

## 📝 请求示例

### Cookies类型示例
```json
{
    "href": "https://nowsecure.nl/",
    "proxy": "usr:pwd@ip:port",
    "alpha": true
}
```

### Turnstile类型示例
```json
{
    "href": "https://visa.vfsglobal.com/chn/zh/deu/login",
    "proxy": "usr:pwd@ip:port",
    "sitekey": "0x4AAAAAAACYaM3U_Dz-4DN1"
}
```

### Turnstile Action类型示例
```json
{
    "href": "https://app.ogcom.xyz/signup?step=first",
    "proxy": "usr:pwd@ip:port",
    "sitekey": "0x4AAAAAAASTIy9n6lEJjrIE",
    "action": "verification_code",
    "explicit": true
}
```

## 📤 响应数据格式

| 参数名 | 类型 | 说明 |
|--------|------|------|
| `status` | `Integer` | 调用状态：1=成功，0=失败 |
| `msg` | `String` | 调用结果说明 |
| `id` | `String` | 请求唯一ID（可用于记录查询） |
| `data.cookies` | `String` | 验证通过返回的cookies |
| `data.token` | `String` | 验证通过返回的token（Turnstile使用） |
| `cost` | `String` | 验证耗时（毫秒） |

### 响应示例

```json
{
    "cost": "3380.01ms",
    "data": {
        "token": "xxx",
        "cookies": "xxx=xxx;"
    },
    "id": "bc174976-81b2-418e-a6e3-9f7c0bbd41ae",
    "msg": "验证成功",
    "status": 1
}
```

## 💻 代码示例

### Python调用示例

**安装依赖**
```bash
pip install -U pynocaptcha -i https://pypi.python.org/simple
```

**基础调用示例**
```python
from pynocaptcha import CloudFlareCracker

# CloudFlare验证码破解
cracker = CloudFlareCracker(
    user_token="your_user_token_here",
    developer_id="hqLmMS",  # 开发者ID
    sitekey="0x4AAAAAAACYaM3U_Dz-4DN1",
    href="https://visa.vfsglobal.com/chn/zh/deu/login",
    proxy="usr:pwd@ip:port",
    debug=True,
)
result = cracker.crack()
print(f"破解结果: {result}")
```

---

## 🎯 相关服务

- [ReCaptcha验证码破解](recaptcha.md)
- [HCaptcha验证码破解](hcaptcha.md)
- [AWS WAF验证码破解](aws.md)
- [更多验证码解决方案](../README.md)

**需要技术支持？[立即联系我们](https://www.nocaptcha.io/register?c=hqLmMS)**

