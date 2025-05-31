---
# 🚀 Get Free API Key Registration
**[Register NoCaptcha.io Now →](https://www.nocaptcha.io/register?c=hqLmMS)**  
*Professional CAPTCHA Solutions | High Success Rate | Fast Response | 24/7 Technical Support*

---

[`Back to homepage`](en.md) [`中文文档`](../zh-CN/recaptcha.md)

# ReCaptcha CAPTCHA Solving Service

## 🔥 Product Advantages

### Why Choose Our ReCaptcha Solution

* **🌐 Universal Compatibility**: Supports ReCaptcha verification for all known websites (including enterprise versions with `s` values that other platforms can't handle, like `steam`), unified support for `v2` and `v3` versions
* **⚡ Ultimate Speed**: Uses `pure algorithm` parameter calculation, `protocol submission`, and `synchronous return` results
  - `v3 invisible` and `v2 nocaptcha` types average `1 second` return
  - `v2` image-click types fastest at `2 seconds`, never exceeding `10 seconds`
* **🎯 High Success Rate**: High `v3` scores, suitable for various high-risk control sites (including enterprise versions), successfully passing verification to obtain target data
* **🔄 Stable & Reliable**: Timely updates (within 2 hours), providing stable support for your business

## 📋 Frequently Asked Questions

### How to Distinguish Between ReCaptcha v2 and v3?

Unlike other platforms, we only differentiate between regular and enterprise versions:

**v3 Characteristics**:
- Ends at the `reload` interface
- `size` parameter is typically `invisible`
- Requires `action` parameter
- Finding method: Open `F12`, search for `grecaptcha.execute`, find the `action` value in the function parameter object

**v2 Characteristics**:
- After the `reload` interface, still needs to request the `userverify` interface
- `size` is usually `normal`
- No `action` parameter needed

### How to Differentiate Between Regular and Enterprise Versions?

- **Regular Version**: `anchor` interface route is `/recaptcha/api2/anchor`
- **Enterprise Version**: `anchor` interface route is `/recaptcha/enterprise/anchor`

### Why Can't Enterprise Versions with s Values (like Steam) Use the Token?

This is related to proxy quality. Recommendations:
1. Try using your local IP first
2. Switch to high-quality proxies
3. If still unusable, contact customer service

## 🔗 API Interface Information

### Request URL (POST)

| Version Type | Interface URL |
|-------------|---------------|
| **Universal Version** | `http://api.nocaptcha.io/api/wanda/recaptcha/universal` |
| **Enterprise Version** | `http://api.nocaptcha.io/api/wanda/recaptcha/enterprise` |
| **Steam Version** | `http://api.nocaptcha.io/api/wanda/recaptcha/steam` |

### Request Headers

| Parameter Name | Description | Required |
|----------------|-------------|----------|
| `User-Token` | User key, obtained from homepage | ✅ |
| `Content-Type` | `application/json` | ✅ |
| `Developer-Id` | Developer ID, used by developer users. The string in the user homepage invitation link (e.g., xxx/register?c=abcdef, then abcdef is the developer ID) | ❌ |

### POST Request Parameters (JSON Format)

| Parameter Name | Type | Description | Required |
|----------------|------|-------------|----------|
| `sitekey` | `String` | Google verification docking key (k value of anchor/reload interface) | ✅ |
| `referer` | `String` | 🚨**Trigger page address**, please copy the complete browser address, do not modify | ✅ |
| `size` | `String` | Validation type (invisible/normal), must correspond to the size value of the anchor interface | ✅ |
| `title` | `String` | Title of the trigger page (F12 console input document.title) | ✅ |
| `action` | `String` | Action value needed for v3 version, search grecaptcha.execute to get | ❌ |
| `proxy` | `String` | Proxy address, format: ip:port or usr:pwd@ip:port or socks5://ip:port | ❌ |
| `ubd` | `Boolean` | Whether it's a special ubd type route, default false | ❌ |
| `s` | `String` | Steam's s value, generally not needed, only Steam requires | ❌ |
| `sa` | `String` | Sa value of some website anchor interface routes, enterprise version may need | ❌ |

## 🔍 Parameter Acquisition Methods

### Method 1: [🔥Highly Recommended🔥 Get All Parameters Using Plugin](plugin.md)

### Method 2: Manual Acquisition with Developer Tools

**Step 1: Get Basic Parameters**
- Search for `anchor` interface, get `k`, `size`, `hl` parameters
- `k` value is the `sitekey`
- If `hl` is `zh-CN`, it can be left blank

![Parameter Acquisition Step 1](/images/recaptcha/arg1.png)

**Step 2: Get Page Information**
- `referer`: Directly copy the complete URL from browser address bar
- `title`: F12 console input `document.title` to get

![Parameter Acquisition Step 3](/images/recaptcha/arg3.png)

**Step 3: Get Action Parameter (v3 Only)**

*Method 1*: Search Code
- Universal version search `.execute(`
- Enterprise version search `.enterprise.execute`
- Find the `action` parameter in the code

![Parameter Acquisition Step 5](/images/recaptcha/arg5.png)

*Method 2*: Breakpoint Debugging
- Universal version input `debug(grecaptcha.execute)`
- Enterprise version input `debug(grecaptcha.enterprise.execute)`
- Copy action value from Scope after triggering verification

![Parameter Acquisition Step 6](/images/recaptcha/arg6.png)
![Parameter Acquisition Step 7](/images/recaptcha/arg7.png)

**Step 4: Check UBD Type**
- Check if verification route is `ubd` type
- If yes, set `ubd` parameter to `true`

![Parameter Acquisition Step 8](/images/recaptcha/arg8.png)

## 📝 Request Examples

### Anchor Interface Example
![Anchor Example](/images/recaptcha/anchor.jpg)

### JSON Request Example

```json
{
  "referer": "https://www.trustpilot.com/",
  "sitekey": "6Lcxp2UaAAAAABkIC5izuDmTEeXYfgfaoQ9v69Q4",
  "size": "invisible",
  "title": "Login",
  "action": "login"
}
```

## 📤 Response Data Format

| Parameter Name | Type | Description |
|----------------|------|-------------|
| `status` | `Integer` | Call status: 1=success, 0=failure |
| `msg` | `String` | Call result description |
| `id` | `String` | Unique request ID (can be used for record queries) |
| `data.token` | `String` | Token returned upon successful verification |
| `cost` | `String` | Verification duration (milliseconds) |

### Response Example

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

## 💻 Code Examples

### CURL Command

```bash
curl -L 'http://api.nocaptcha.io/api/wanda/recaptcha/universal' \
 -H 'User-Token: xxx' \
 -H 'Developer-Id: hqLmMS' \
 -H 'Content-Type: application/json' \
 --data-raw '{"sitekey": "6Lcxp2UaAAAAABkIC5izuDmTEeXYfgfaoQ9v69Q4", "referer": "https://www.trustpilot.com/", "size": "invisible", "title": "Login", "action": "login"}'
```

### Python Call Examples

**Install Dependencies**
```bash
pip install -U pynocaptcha -i https://pypi.python.org/simple
```

**Universal Version Example**
```python
from pynocaptcha import ReCaptchaUniversalCracker

# Universal ReCaptcha Solving
cracker = ReCaptchaUniversalCracker(
    user_token="your_user_token_here",
    developer_id="hqLmMS",  # Developer ID
    sitekey="6Le6xNgUAAAAAHDXXUgcrCYACaq_K-iUTa-BIm4h",
    referer="https://visa-fr.tlscontact.com/gb/lon/login.php",
    size="invisible",
    action="login_form",
    title="Login",
    debug=True,
)
result = cracker.crack()
print(f"Solving result: {result}")
```

**Enterprise Version Example**
```python
from pynocaptcha import ReCaptchaEnterpriseCracker

# Enterprise ReCaptcha Solving
cracker = ReCaptchaEnterpriseCracker(
    user_token="your_user_token_here",
    developer_id="hqLmMS",  # Developer ID
    sitekey="6LcTV7IcAAAAAI1CwwRBm58wKn1n6vwyV1QFaoxr",
    referer="https://login.coinbase.com/",
    size="invisible",
    debug=True,
)
result = cracker.crack()
print(f"Solving result: {result}")
```

**Steam Version Example**
```python
from pynocaptcha import ReCaptchaSteamCracker

# Steam ReCaptcha Solving
cracker = ReCaptchaSteamCracker(
    user_token="your_user_token_here",
    developer_id="hqLmMS",  # Developer ID
    sitekey="6LfNGb0ZAAAAAI_j6L2y1eXXWAoSbtjvccEcEq2P",
    referer="https://help.steampowered.com/zh-cn/wizard/HelpWithLoginInfo?issueid=406",
    size="normal",
    title="Steam Support - I forgot my Steam account login name or password",
    debug=True,
    s="steam_s_value",  # The s value returned by the Steam website API
)
result = cracker.crack()
print(f"Solving result: {result}")
```

---

## 🎯 Related Services

- [HCaptcha CAPTCHA Solving](hcaptcha.md)
- [Cloudflare CAPTCHA Solving](../zh-CN/cloudflare.md)
- [Incapsula CAPTCHA Solving](incapsula.md)
- [More CAPTCHA Solutions](en.md)

**Need Technical Support? [Contact Us Now](https://www.nocaptcha.io/register?c=hqLmMS)**
