---
# 🚀 Free Registration for API Key
**[Register Now at NoCaptcha.io →](https://www.nocaptcha.io/register?c=hqLmMS)**  
*Professional CAPTCHA Solutions | High Success Rate | Fast Response | 24/7 Technical Support*

---

[`Return to Home`](en.md)  [`中文文档`](../zh-CN/plugin.md)

# Browser Plugin for ReCaptcha & hCaptcha

## 🔥 Product Advantages

### Why Choose Our Browser Plugin

* **🌐 Universal Support**: Automatically handles ReCaptcha and hCaptcha on any website
* **⚡ One-Click Solution**: Automatic parameter extraction and solving
* **🔄 Real-time Processing**: Instant captcha solving with live parameter capture
* **🎯 Developer Friendly**: Easy parameter extraction for API integration

## 📋 Plugin Features

### 🔍 Key Capabilities

* **Automatic Detection**: Recognizes ReCaptcha and hCaptcha automatically
* **Parameter Extraction**: Captures all necessary parameters for API calls
* **Live Monitoring**: Real-time network monitoring for parameter collection
* **Easy Integration**: Seamless workflow for developers

## 🚀 Installation & Setup

### Step 1: Install the Extension

Download and install the NoCaptcha Solver extension from Chrome Web Store:

**[📥 Download NoCaptcha Solver Extension](https://chrome.google.com/webstore/detail/nocaptcha-solver/kkphlbgphimpedeckcepigahenlmpggc?utm_source=ext_sidebar&hl=zh-CN)**

![Extension Installation](/images/fill-params/1.png)

### Step 2: Configure Your Account

After installation, pin the `NoCaptcha Solver` extension to your extensions bar and log in with your platform credentials:

- **Token**: Your API token from the platform
- **Username**: Your platform login email address

![Extension Configuration](/images/fill-params/3.png)

![Login Interface](/images/fill-params/2.png)

### Step 3: Access Developer Tools

1. Click `Manage extensions` or navigate to `chrome://extensions/`
2. Find the NoCaptcha Solver extension and click `Service Worker`

![Extension Management](/images/fill-params/4.png)

3. This opens the developer tools - switch to the `Network` panel

![Developer Tools](/images/fill-params/5.png)

## 💻 Usage Instructions

### Step 4: Capture Parameters

1. **Visit Target Website**: Open any website with ReCaptcha or hCaptcha (e.g., `https://democaptcha.com/demo-form-eng/recaptcha-2.html`)

2. **Automatic Processing**: The extension will automatically detect and start solving the captcha

![Captcha Detection](/images/fill-params/6.png)

![Solving Process](/images/fill-params/7.png)

3. **Parameter Extraction**: In the Network panel, you'll see all the parameters needed for API integration

![Parameter Capture](/images/fill-params/8.png)

### 📝 Extracted Parameters Example

```json
{
    "sitekey": "6LfGqN0UAAAAAFdGo4OSj5Awi8hM_9kmR7VfXUP2",
    "referer": "https://democaptcha.com/demo-form-eng/recaptcha-2.html",
    "title": "reCAPTCHA 2 demo form | AntiCaptcha plugin demo forms",
    "size": "normal",
    "action": null,
    "s": null,
    "extra": {
        "origin": "chrome-plugin",
        "cb": null
    }
}
```

### ⚠️ Important Notes

- **Ignore the `extra` object** - do not submit this parameter in your API calls
- **Use extracted parameters** for your API integration with Developer-Id: `hqLmMS`
- **hCaptcha works identically** to ReCaptcha with the same process

## 🔗 API Integration

### Using Extracted Parameters

Once you have the parameters, you can use them with our API:

```bash
curl -L 'http://api.nocaptcha.io/api/wanda/recaptcha/universal' \
 -H 'User-Token: your_token_here' \
 -H 'Developer-Id: hqLmMS' \
 -H 'Content-Type: application/json' \
 --data-raw '{
   "sitekey": "6LfGqN0UAAAAAFdGo4OSj5Awi8hM_9kmR7VfXUP2",
   "referer": "https://democaptcha.com/demo-form-eng/recaptcha-2.html",
   "size": "normal"
 }'
```

### Python Integration Example

```python
from pynocaptcha import RecaptchaV2Cracker

# Use extracted parameters from plugin
cracker = RecaptchaV2Cracker(
    user_token="your_user_token_here",
    developer_id="hqLmMS",  # Developer ID
    sitekey="6LfGqN0UAAAAAFdGo4OSj5Awi8hM_9kmR7VfXUP2",
    referer="https://democaptcha.com/demo-form-eng/recaptcha-2.html",
    size="normal"
)

result = cracker.crack()
print(f"Captcha solution: {result}")
```

## 🎯 Supported Captcha Types

- **✅ ReCaptcha v2**: All variants including invisible
- **✅ ReCaptcha v3**: Action-based verification
- **✅ hCaptcha**: All difficulty levels
- **✅ Enterprise**: Both ReCaptcha and hCaptcha enterprise versions

---

## 🎯 Related Services

- [ReCaptcha API Solving](recaptcha.md)
- [hCaptcha API Solving](hcaptcha.md)
- [TLS Client Service](tls.md)
- [More CAPTCHA Solutions](en.md)

**Need Technical Support? [Contact Us Now](https://www.nocaptcha.io/register?c=hqLmMS)** 