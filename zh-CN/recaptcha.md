# 🚀 免费注册获取API密钥
**[立即注册 NoCaptcha.io →](https://www.nocaptcha.io/register?c=hqLmMS)**  
*专业验证码解决方案 | 高成功率 | 快速响应 | 24/7技术支持*

---

[`返回首页`](../README.md)    [`下一页`](hcaptcha.md)   [`English Version`](../en-US/recaptcha.md)

# ReCaptcha 验证码破解服务

## 🔥 产品优势

### 为什么选择我们的ReCaptcha解决方案

* **🌐 通用兼容性**: 支持所有已知网站的ReCaptcha验证（包括其他平台无法处理的带 `s` 值的企业版，如 `steam`），统一支持 `v2`、`v3` 版本
* **⚡ 极致速度**: 采用`纯算法`计算参数，`协议提交`，`同步返回`结果
  - `v3 invisible`、`v2 nocaptcha` 类型平均 `1秒` 返回
  - `v2` 图片点击类型最快 `2秒`，最慢不超过 `10秒`
* **🎯 高成功率**: `v3` 分值高，适用于各种高风控强度站点（包括企业版），成功通过验证获取目标数据
* **🔄 稳定可靠**: 更新及时（不超过2小时），为您的业务提供稳定支撑

## 📋 常见问题解答

### 如何区分 ReCaptcha v2 和 v3？

与其他平台不同，我们只区分普通版和企业版：

**v3 特征**：
- 到 `reload` 接口就结束
- `size` 参数通常为 `invisible`
- 需要传入 `action` 参数
- 查找方法：打开 `F12` 搜索 `grecaptcha.execute`，找到函数入参对象的 `action` 值

**v2 特征**：
- 通过 `reload` 接口后还需请求 `userverify` 接口
- `size` 通常为 `normal`
- 不需要 `action` 参数

### 如何区分普通版和企业版？

- **普通版**：`anchor` 接口路由为 `/recaptcha/api2/anchor`
- **企业版**：`anchor` 接口路由为 `/recaptcha/enterprise/anchor`

### 企业版带 s 值（如 steam）的token为什么无法使用？

这与代理质量相关，建议：
1. 先尝试使用本机IP
2. 更换高质量代理
3. 如仍无法使用，请联系客服

## 🔗 API接口信息

### 请求地址（POST）

| 版本类型 | 接口地址 |
|---------|---------|
| **通用版（Universal）** | `http://api.nocaptcha.io/api/wanda/recaptcha/universal` |
| **企业版（Enterprise）** | `http://api.nocaptcha.io/api/wanda/recaptcha/enterprise` |
| **Steam版** | `http://api.nocaptcha.io/api/wanda/recaptcha/steam` |

### 请求头参数

| 参数名 | 说明 | 必填 |
|--------|------|------|
| `User-Token` | 用户密钥，从主页获取 | ✅ |
| `Content-Type` | `application/json` | ✅ |
| `Developer-Id` | 开发者ID，开发者用户使用，用户主页邀请链接的字符串(如 xxx/register?c=abcdef, 则 abcdef 为开发者ID) | ❌ |

### POST请求参数（JSON格式）

| 参数名 | 类型 | 说明 | 必填 |
|--------|------|------|------|
| `sitekey` | `String` | 谷歌验证码对接key（anchor/reload接口的k值） | ✅ |
| `referer` | `String` | 🚨**触发页面地址**，请复制浏览器完整地址，不要修改 | ✅ |
| `size` | `String` | 验证类型（invisible/normal），必须与anchor接口的size值对应 | ✅ |
| `title` | `String` | 触发页面的title（F12控制台输入 document.title） | ✅ |
| `action` | `String` | v3版本需要的action值，搜索 grecaptcha.execute 获取 | ❌ |
| `proxy` | `String` | 代理地址，格式：ip:port 或 usr:pwd@ip:port 或 socks5://ip:port | ❌ |
| `ubd` | `Boolean` | 是否为特殊ubd类型路由，默认false | ❌ |
| `s` | `String` | Steam的s值，一般不需要填写，仅Steam需要 | ❌ |
| `sa` | `String` | 个别网站anchor接口路由的sa值，企业版可能需要 | ❌ |

## 🔍 参数获取方法

### 方法1：[🔥强烈推荐🔥 使用插件获取全部参数](plugin.md)

### 方法2：开发者工具手动获取

**步骤1：获取基础参数**
- 搜索 `anchor` 接口，获取 `k`、`size`、`hl` 参数
- `k` 值即为 `sitekey`
- 如果 `hl` 为 `zh-CN` 可不填

![参数获取步骤1](/images/recaptcha/arg1.png)

**步骤2：获取页面信息**
- `referer`：直接复制浏览器地址栏完整URL
- `title`：F12控制台输入 `document.title` 获取

![参数获取步骤3](/images/recaptcha/arg3.png)

**步骤3：获取action参数（仅v3需要）**

*方法1*：搜索代码
- 通用版搜索 `.execute(`
- 企业版搜索 `.enterprise.execute`
- 查找代码中的 `action` 参数

![参数获取步骤5](/images/recaptcha/arg5.png)

*方法2*：断点调试
- 通用版输入 `debug(grecaptcha.execute)`
- 企业版输入 `debug(grecaptcha.enterprise.execute)`
- 触发验证后在Scope中复制action值

![参数获取步骤6](/images/recaptcha/arg6.png)
![参数获取步骤7](/images/recaptcha/arg7.png)

**步骤4：检查UBD类型**
- 检查验证路由是否为 `ubd` 类型
- 如果是，设置 `ubd` 参数为 `true`

![参数获取步骤8](/images/recaptcha/arg8.png)

## 📝 请求示例

### Anchor接口示例
![anchor示例](/images/recaptcha/anchor.jpg)

### JSON请求示例

```json
{
  "referer": "https://www.trustpilot.com/",
  "sitekey": "6Lcxp2UaAAAAABkIC5izuDmTEeXYfgfaoQ9v69Q4",
  "size": "invisible",
  "title": "Login",
  "action": "login"
}
```

## 📤 响应数据格式

| 参数名 | 类型 | 说明 |
|--------|------|------|
| `status` | `Integer` | 调用状态：1=成功，0=失败 |
| `msg` | `String` | 调用结果说明 |
| `id` | `String` | 请求唯一ID（可用于记录查询） |
| `data.token` | `String` | 验证成功返回的token |
| `cost` | `String` | 验证耗时（毫秒） |

### 响应示例

```json
{
  "cost": "1380.01ms",
  "data": {
    "token": "03AFY_a8UL3OTinrQHai6iE4c9l--oZAtVsDsAGBtijmv3QgBWmeOWWvbJvZ_DPT8p2ttvUlr4FmE5gDSTON0f4mPpYqxwPdVYxRbC0nmLuZJ0k9UmOjiK4HgUShuFu4RL7w1hyoFQ1YbUpLtW-KuAqC1KSs4GGBrI3k4Cx4u7e57DQPhVdzzpVGqQjGq9ZnI5YY9546_jRybKrIv2FMLeIkvcOJnCPUTnUREewSn7VO1bCvpdAP3Wj8DoH8jtv-RXij9aypLnFcpLGMTwrJOCE9z2U7As7AzAxcMnVEr9AWyKipKj4t-A2m77uNvHv-f1XhSMNI_Dk4bIYLe5n0N-STCLUc5tFfPc5rtuNQdoTRxdl6ie9gOpzpUyg6dwcA3tEiERya9Tej-6FMpwo4G4F61u8buUAMgCVn-4OoAB9AfH5mjN3GapQf3Yc_mK2u99xErSwEgwuhVsBsMzC22JiVaqHWO8EOzDRso6AMpUmuZw27b3Kl8IhFH1OiIL9WdfMfEXtEDgUFZxL085MxyS_mv5iGDbcxLkXN5PupgT2ieoQ8grbHsbHWF1-9Un0cxF5MVfmIilzbSUtItZ7i2SZcJZlPOG86D1CKby2T7nnprtoVd7hAN4r5yTnQ52f_8oShEKd3n0ArHsfti4TXPuVgafP8jp4uIkgK3YDlF2QvnnuGeEq58dZ91nllOQOBnzc_GiNLvd1h8XrZxexZ2eI_LDueF2p4uSWQBDLXloHV_2lmDf5QsDcUJy46JyhlehLK-MOzLt-BDJ9wVJdtHhY_GT-IymY757nYurqWCLdY7k7ofeIcd51I35Hz88VADyp_EYtRzmd5CIRX_sHx4rlw7Yw1khFG6Ktw-7bRd1nSw1rNZlwFIxvLk4Bgp9WGZS8rqRCKIJgAMAJOzt872i1P9GQ3k6Ee5nn8qTs0CmpckzrvqJLzexQfM69G-A1O0s99PMn0Hr5ruUU_jsj3rtzWu1zXr0soPtArvN2tvTLsRSARIL1G5unTeX7YpURkbVVkmaa08oqpR7eIFVO7I7SZ99jk-DJdXSL5uUs3ZcIe8fzIp_hGtCkSQIrHrB0F5anyER7ZdBH1ynT7aFltOlikAWB_s4lTIYZk7VDUrrwKOSMI3SMHus7BxKZNanhTO34c_9s62t9FRrLaiQfTXy4ZUlCgVAkWt1f_6lrRwj9VZDQRiplJQwIIDpT2jhXrgGLdqIjOBtJ2Doy3Gx4dkpPCuquqhnzyvFCEJdyG-QKaONu4tbFjbUWB7TwIgREUVdrR5k3YN21sVTY2yvNZjc8YVCw-YXIYygZE6OpPJUIhxxXtB55xpxQ2THITBlkIu5QmBtQ4lXi3GBbq_UKB_Lxn5SVjK88yTZ3TD3m8nfH4WDdb4c36Ff4lpGEEIsZtS7U11FqTGu_xv-dgIYN0-t1tK8TKhJLHDG8nRwady2Xiq190yBXI3sDDcumMpCYqf2wE6Hmu2gnLRGlqPYdsnlC0JQMoeUTHhdEBslQb4iPV_0azLHp_kCEZvYZYalmyIibmmI2O9qY9gROUHt7NRLl_-T3mxr7cdRP2kG801i8Y87nY6PVllAs5JCVcRcMu3UXxvgianbXX_VVsuEf3Y-uxoRV7LKHYesm7tsxxcDwUtZiWzjY0PTCMUXgAjWrJDs-w9VUQGGeOWxqebTx-Mg_fTEXvqkmChhFTyBRDF0yQnMx0KaCnOogEK2XxI_ts_M-DWrXFBHUZa9a9a09T-73kpJqlVCcwgQjV-LhyaeQxUIT02_diqL-xM00AWhJmqwnojmmP6cXU34"
  },
  "id": "bc174976-81b2-418e-a6e3-9f7c0bbd41ae",
  "msg": "验证成功",
  "status": 1
}
```

## 💻 代码示例

### CURL命令

```bash
curl -L 'http://api.nocaptcha.io/api/wanda/recaptcha/universal' \
 -H 'User-Token: xxx' \
 -H 'Developer-Id: hqLmMS' \
 -H 'Content-Type: application/json' \
 --data-raw '{"sitekey": "6Lcxp2UaAAAAABkIC5izuDmTEeXYfgfaoQ9v69Q4", "referer": "https://www.trustpilot.com/", "size": "invisible", "title": "Login", "action": "login"}'
```

### Python调用示例

**安装依赖**
```bash
pip install -U pynocaptcha -i https://pypi.python.org/simple
```

**通用版示例**
```python
from pynocaptcha import ReCaptchaUniversalCracker

# 通用版ReCaptcha破解
cracker = ReCaptchaUniversalCracker(
    user_token="your_user_token_here",
    developer_id="hqLmMS",  # 开发者ID
    sitekey="6Le6xNgUAAAAAHDXXUgcrCYACaq_K-iUTa-BIm4h",
    referer="https://visa-fr.tlscontact.com/gb/lon/login.php",
    size="invisible",
    action="login_form",
    title="Login",
    debug=True,
)
result = cracker.crack()
print(f"破解结果: {result}")
```

**企业版示例**
```python
from pynocaptcha import ReCaptchaEnterpriseCracker

# 企业版ReCaptcha破解
cracker = ReCaptchaEnterpriseCracker(
    user_token="your_user_token_here",
    developer_id="hqLmMS",  # 开发者ID
    sitekey="6LcTV7IcAAAAAI1CwwRBm58wKn1n6vwyV1QFaoxr",
    referer="https://login.coinbase.com/",
    size="invisible",
    debug=True,
)
result = cracker.crack()
print(f"破解结果: {result}")
```

**Steam版示例**
```python
from pynocaptcha import ReCaptchaSteamCracker

# Steam版ReCaptcha破解
cracker = ReCaptchaSteamCracker(
    user_token="your_user_token_here",
    developer_id="hqLmMS",  # 开发者ID
    sitekey="6LfNGb0ZAAAAAI_j6L2y1eXXWAoSbtjvccEcEq2P",
    referer="https://help.steampowered.com/zh-cn/wizard/HelpWithLoginInfo?issueid=406",
    size="normal",
    title="Steam 客服 - 我忘了我的 Steam 帐户登录名称或密码",
    debug=True,
    s="steam_s_value",  # 网站接口返回的s值
)
result = cracker.crack()
print(f"破解结果: {result}")
```

---

## 🎯 相关服务

- [HCaptcha验证码破解](hcaptcha.md)
- [Cloudflare验证码破解](cloudflare.md)
- [Incapsula验证码破解](incapsula.md)
- [更多验证码解决方案](../README.md)

**需要技术支持？[立即联系我们](https://www.nocaptcha.io/register?c=hqLmMS)**
