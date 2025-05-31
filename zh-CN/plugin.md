---
# 🚀 免费注册获取API密钥
**[立即注册 NoCaptcha.io →](https://www.nocaptcha.io/register?c=hqLmMS)**  
*专业验证码解决方案 | 高成功率 | 快速响应 | 24/7技术支持*

---

[`返回首页`](../README.md)     [`English Version`](../en-US/plugin.md)

# NoCaptcha 浏览器插件使用指南

## 🔥 插件特色

### 为什么使用我们的浏览器插件

* **🎯 一键获取参数**: 自动识别并提取验证码所需的所有参数
* **⚡ 快速便捷**: 无需手动查找复杂的验证码参数
* **🔧 智能识别**: 支持ReCaptcha和HCaptcha类型的参数自动提取
* **📋 一键复制**: 提取的参数可一键复制，方便API调用

## 📥 插件安装

### Chrome浏览器插件下载
**官方下载地址**: [NoCaptcha Solver](https://chrome.google.com/webstore/detail/nocaptcha-solver/kkphlbgphimpedeckcepigahenlmpggc?utm_source=ext_sidebar&hl=zh-CN)

![插件安装](/images/fill-params/1.png)

### 安装后配置
1. 将`NoCaptcha Solver`扩展固定在扩展栏中（方便操作）
2. 登录您的平台账号
   - `token`: 您的消费令牌（User-Token）
   - `user name`: 平台登录账号（邮箱地址）

![插件配置1](/images/fill-params/3.png)
![插件配置2](/images/fill-params/2.png)

## 🔍 使用方法

### 步骤1：打开开发者工具
1. 点击`管理扩展程序`或在浏览器输入`chrome://extensions/`
2. 找到NoCaptcha Solver插件，点击`Service Worker`

![开发者工具](/images/fill-params/4.png)

### 步骤2：切换到Network面板
点击后会打开开发者工具，切换至`Network`面板

![Network面板](/images/fill-params/5.png)

### 步骤3：访问目标网站
打开需要破解的网站，例如：`https://democaptcha.com/demo-form-eng/recaptcha-2.html`

扩展会自动开始破解`ReCaptcha`或`HCaptcha`

![自动破解1](/images/fill-params/6.png)
![自动破解2](/images/fill-params/7.png)

### 步骤4：获取API参数
在`Network`栏中，可以获取到验证码需要的所有参数

⚠️ **注意**: 无需理会`extra`对象，也不要提交该参数

![参数获取](/images/fill-params/8.png)

### 参数示例

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

## 📝 参数说明

### 自动提取的关键参数
- `sitekey`: 验证码站点密钥（必需）
- `referer`: 页面引用地址（必需）
- `title`: 页面标题（必需）
- `size`: 验证码尺寸类型（必需）
- `action`: 验证动作（v3专用，可选）
- `s`: Steam特殊参数（特定网站需要）

### 支持的验证码类型
- ✅ ReCaptcha v2/v3
- ✅ ReCaptcha Enterprise
- ✅ HCaptcha
- ✅ 更多类型持续更新中...

## 🛠️ 技术支持

### 常见问题解决
- **插件无法识别验证码**: 请确保页面已完全加载
- **参数提取不完整**: 尝试刷新页面后重新提取
- **插件无法安装**: 检查浏览器版本是否支持Chrome扩展

### 获取帮助
如遇到问题，请通过以下方式联系我们：
- **官网客服**: [NoCaptcha.io](https://www.nocaptcha.io/register?c=hqLmMS)
- **技术支持**: 通过官网联系在线客服

## 💡 使用技巧

1. **确保网络稳定**: 插件需要与服务器通信，请保持网络连接稳定
2. **及时更新插件**: 定期检查插件更新，获取最新功能
3. **正确配置账户**: 确保User-Token和邮箱地址配置正确
4. **注意参数完整性**: 使用前检查所有必需参数是否已正确提取

---

## 🎯 相关服务

- [ReCaptcha验证码破解](recaptcha.md)
- [HCaptcha验证码破解](hcaptcha.md)
- [CloudFlare验证码破解](cloudflare.md)
- [更多验证码解决方案](../README.md)

**需要技术支持？[立即联系我们](https://www.nocaptcha.io/register?c=hqLmMS)**
