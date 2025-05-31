---
# 🚀 Get Free API Key Registration
**[Register NoCaptcha.io Now →](https://www.nocaptcha.io/register?c=hqLmMS)**  
*Professional CAPTCHA Solutions | High Success Rate | Fast Response | 24/7 Technical Support*

---

# NoCaptcha.io - Professional CAPTCHA Solving Service Platform

## 🌟 Product Overview

**👉[中文文档](../README.md)👈**

NoCaptcha.io is the industry-leading CAPTCHA solving service platform, providing comprehensive CAPTCHA solutions that support all mainstream CAPTCHA types on the market. We use advanced algorithmic technology to provide developers and enterprises with efficient, stable, and reliable CAPTCHA solving services.

## 🔥 Core Advantages

* **🌐 Universal Compatibility**: Supports all mainstream CAPTCHA types, one-stop solution
* **⚡ Lightning Fast**: Synchronous result return, average response time 1-10 seconds
* **🎯 High Success Rate**: Professional algorithm optimization ensuring high pass rates
* **🛡️ Stable & Reliable**: 24/7 service with timely updates and maintenance
* **💰 Cost Effective**: Proxy discounts available, VIP levels offer more savings

## 📊 Supported CAPTCHA Types

|                      Type                      |                           Description                            | Sync Results | Point Cost |  Proxy Discount  | Status | Dedicated/Monthly |
|:--------------------------------------------:|:---------------------------------------------------------------:|:--------:|:----------:|:----------:|:----:|:------------:|
|  [recaptcha:universal](/en-US/recaptcha.md)  |           `ReCaptcha (v2/v3 Universal), returns token directly`            |    ✅     |   `300`    |   `150`    |  ✅   |      ❌       |
| [recaptcha:enterprise](/en-US/recaptcha.md)  |           `ReCaptcha (v2/v3 Enterprise), returns token directly`            |    ✅     |   `500`    |   `250`    |  ✅   |      ❌       |
|    [recaptcha:steam](/en-US/recaptcha.md)    |             `ReCaptcha (Steam), returns token directly`              |    ✅     |   `600`    |   `300`    |  ✅   |      ❌       |
|   [recaptcha:app](/en-US/recaptcha_app.md)   |             `ReCaptcha (App version), returns token directly`             |    ✅     |  `❌Discontinued❌`  |   `250`    |  ❌   |      ❌       |
|   [hcaptcha:universal](/en-US/hcaptcha.md)   |        `HCaptcha Universal, returns generated_pass_UUID directly`         |    ✅     |   `300`    |   `150`    |  ✅   |      ❌       |
|   [incapsula:reese84](/en-US/incapsula.md)   |        `Incapsula Shield reese84 Universal, returns solution parameter`        |    ✅     |   `210`    |     ❌      |  ✅   |      ❌       |
| [incapsula:utmvc](/en-US/incapsula_utmvc.md) |  `Incapsula Shield __utmvc Universal, server direct verification or __utmvc cookie`  |    ✅     |   `150`    |     ❌      |  ✅   |      ✅       |
|        [akamai:v2](/en-US/akamai.md)         |                 `Akamai v2/v3, returns _abck directly`                 |    ✅     |   `1000`   |     ❌      |  ✅   |      ✅       |
|           [tls:v1](../zh-CN/tls.md)            |  `TLS forwarding interface for ja3, http2 fingerprint verification (akamai/cloudflare)`   |    ✅     |   `100`    |     ❌      |  ✅   |      ❌       |

## 🔧 Proxy Configuration

### Proxy Format Requirements
* Use credential authentication or no whitelist authentication proxies
* Format: `ip:port` or `usr:pwd@ip:port`
* Use sticky/session proxies (IP remains unchanged for n minutes)
* Monitor proxy usage frequency, avoid using the same proxy repeatedly

![Proxy Configuration Example](/images/proxy.png)

## 💰 Pricing System

### Basic Pricing
* **Point Exchange Rate**: `$1 = 66,000 points`
* **User-Token**: User token, required parameter for service calls, viewable on user homepage
* **Developer-ID**: Developer ID, used by developer users, string from user homepage invitation link (e.g., xxx/register?c=hqLmMS, then `hqLmMS` is the developer ID)

### VIP Level Discounts

| Points Consumed     | Level   | Discount | Description                    |
|-----------------|---------|-------|-----------------------|
| `100,000,000` points | `VIP 1` | `90%` | `300` point service actually costs `270` points |
| `250,000,000` points | `VIP 2` | `80%` | `300` point service actually costs `240` points |
| `600,000,000` points | `VIP 3` | `70%` | `300` point service actually costs `210` points |

## 💸 Referral System

### Invitation Referrals
* Get `20%` referral from directly invited users' consumption
* Example: `A` invites `B`, for every `300` points `B` consumes, `A` gets `60` points referral

### Developer Referrals
* When users call service interface with developer ID, developer gets `20%` referral from consumption
* Developer referral priority > Invitation referral
* Example: `A` invites `B`, `B` fills in `C` developer ID, `C` gets `20%` referral, `A` gets no referral
* Note: Cannot get referral when using your own developer ID

### Referral Usage
* **Convert to Balance**: `1:1` conversion to balance for service consumption
* **Withdrawal**: Supports `10U` `20U` `50U` `100U` withdrawal amounts, only supports `BSC Chain (BEP20)` addresses

## 📊 Wallet Data Query API

### API Endpoint
```
http://api.nocaptcha.io/api/get_user_balance?user_token={User-Token}&nickname={nickname}
```

### Request Parameters

| Parameter Name | Type | Description | Required |
|--------------|----------|-------------------|-----|
| `User-Token` | `String` | `User token xxxx-xxx...` | `Yes` |
| `nickname`   | `String` | `Login email abc@xxx.com` | `Yes` |

### Request Example
```
http://api.nocaptcha.io/api/get_user_balance?user_token=40201fad-6666-3333-9999-b9f658666666&nickname=admin@nocaptcha.io
```

### Response Data (JSON)

```json
{
    "code": 200,
    "msg": "success",
    "data": {
        "money_data": {
            "balance": "9112475",
            "profit": "3471240",
            "used_profit": "0",
            "consume": "887524",
            "today_consume": "0"
        }
    }
}
```

## 🚀 Quick Start

### 1. Register Account
[Register Now](https://www.nocaptcha.io/register?c=hqLmMS) to get your free API key

### 2. Get User-Token
After login, get your User-Token from the user homepage

### 3. Choose CAPTCHA Type
Select the corresponding CAPTCHA solving service based on your needs

### 4. Start Integration
Use our provided API documentation and code examples to start integration

## 📚 Technical Documentation

### Main Service Documentation
- [ReCaptcha Solving Service](/en-US/recaptcha.md)
- [HCaptcha Solving Service](/en-US/hcaptcha.md)
- [Incapsula Solving Service](/en-US/incapsula.md)
- [Akamai Solving Service](/en-US/akamai.md)

### Tools and Plugins
- [Browser Plugin](../zh-CN/plugin.md)
- [TLS Forwarding Service](../zh-CN/tls.md)

## 🎯 Use Cases

* **Data Collection**: Bypass website CAPTCHA restrictions for automated data scraping
* **Automated Testing**: Handle CAPTCHA verification in automated testing
* **Batch Operations**: Support batch registration, login and other operations
* **API Integration**: Easy integration into existing systems

## 🛠️ Technical Support

* **24/7 Customer Support**: Professional technical team ready to answer your questions
* **Detailed Documentation**: Complete API documentation and code examples
* **Quick Response**: Fast problem feedback processing
* **Custom Services**: Enterprise-level customization solutions available

## 📞 Contact Us

* **Official Website**: [https://www.nocaptcha.io](https://www.nocaptcha.io/register?c=hqLmMS)
* **Technical Support**: Contact customer service through official website
* **Developer Community**: Join our developer exchange group

---

**Start using NoCaptcha.io now and experience professional CAPTCHA solving services!**

[🚀 Register Now](https://www.nocaptcha.io/register?c=hqLmMS)

