---
# 🚀 免费注册获取API密钥
**[立即注册 NoCaptcha.io →](https://www.nocaptcha.io/register?c=hqLmMS)**  
*专业验证码解决方案 | 高成功率 | 快速响应 | 24/7技术支持*

---

[`返回首页`](../README.md)    [`上一页`](aws.md)   [`下一页`](kasada.md)

# PerimeterX 验证码破解服务

## 🔥 产品优势

### 为什么选择我们的PerimeterX解决方案

* **🌐 全模式支持**: 支持无感验证、按压验证码等所有PerimeterX验证模式
* **⚡ 智能识别**: 自动识别验证类型，支持多种验证场景
* **🔄 稳定可靠**: 更新及时，为您的业务提供稳定支撑
* **🎯 高成功率**: 专业算法优化，确保高通过率

## 📋 PerimeterX验证模式说明

### 🔍 如何识别PerimeterX验证

当看到 `cookies` 中有 `_px2`、`_px3` 时，代表存在PerimeterX验证。有以下三种模式：

### 1️⃣ 仅无感模式（*/api/v2/colletor）

**特征**：
- 打开目标页面没有出现任何验证
- F12中不停发送 `*/api/v2/colletor` 接口

**必传参数**：`app_id`、`href`、`proxy`

![验证接口](/images/perimeterx/1.png)

### 2️⃣ 首页无感＋按压模式（*/assets/js/bundle）

**特征**：
- 打开目标页面直接出现按压验证码

**必传参数**：`tag`、`href`、`proxy`

![验证接口](/images/perimeterx/1.png)

### 3️⃣ XHR按压验证模式（*/assets/js/bundle）

**特征**：
- 打开目标页面未直接出现按压验证码
- 在点击登录、注册或搜索等关键接口时出现按压验证码

**必传参数**：`app_id`、`href`、`captcha`、`proxy`

![验证接口](/images/perimeterx/3.png)
![按压验证码样例](/images/perimeterx/2.png)

### 💰 价格说明

**按压模式消耗**: 1000点/次  
**必传参数**: `app_id`、`href`、`captcha`

### ⚠️ 重要提示

1. **代理质量影响**：无感模式和首页按压模式通常取决于代理质量
2. **使用建议**：按压模式返回的cookie通常需要等几秒才能正常使用
3. **模式判断**：建议先挂代理请求目标页面判断状态码
   - 状态码403：使用首页按压模式
   - 状态码200/302：使用无感模式

## 🔗 API接口信息

### 请求地址（POST）

| 版本类型 | 接口地址 |
|---------|---------|
| **通用版（Universal）** | `http://api.nocaptcha.io/api/wanda/perimeterx/universal` |

### 请求头参数

| 参数名 | 说明 | 必填 |
|--------|------|------|
| `User-Token` | 用户密钥，从主页获取 | ✅ |
| `Content-Type` | `application/json` | ✅ |
| `Developer-Id` | 开发者ID，开发者用户使用，用户主页邀请链接的字符串(如 xxx/register?c=abcdef, 则 abcdef 为开发者ID) | ❌ |

### POST请求参数（JSON格式）

| 参数名 | 类型 | 说明 | 必填 |
|--------|------|------|------|
| `href` | `String` | 🚨**触发PerimeterX验证的页面地址** | ✅ |
| `tag` | `String` | 版本号，*/api/v2/colletor 或 */assets/js/bundle 中的tag参数（不传tag就必须传app_id） | ❌ |
| `app_id` | `String` | */api/v2/colletor 或 */assets/js/bundle 中的appId参数（PX开头，不传app_id就必须传tag） | ❌ |
| `captcha` | `Object` | 验证码参数，xhr接口返回的按压验证码必传 | ❌ |
| `captcha_html` | `String` | 验证码参数，请求href返回的按压验证码的响应源码 | ❌ |
| `uuid` | `String` | window._pxUuid | ❌ |
| `vid` | `String` | window._pxVid | ❌ |
| `proxy` | `String` | 代理地址，建议使用海外代理，格式：ip:port 或 usr:pwd@ip:port | ❌ |
| `did` | `String` | 无感模式返回的指纹ID，后续xhr接口出现的按压验证码请传该参数 | ❌ |
| `country` | `String` | 业务流程使用的代理所属地区国家code，如美国（us）、英国（uk） | ❌ |
| `ip` | `String` | 业务流程使用的代理IP地址（例：56.214.78.94） | ❌ |
| `user_agent` | `String` | 自定义user_agent，请传最新版windows ua | ❌ |
| `cookies` | `String` | 按压验证码模式下，当前页面的cookies | ❌ |
| `actions` | `Integer` | 随机行为次数，越大耗时越久，风控高的站点可以设置大一点，默认1 | ❌ |
| `timeout` | `Integer` | 验证超时时间 | ❌ |

## 📝 请求示例

### 仅无感模式

```json
{
    "app_id": "PXu6b0qd2S",
    "href": "https://www.walmart.com/",
    "proxy": "user:pass@ip:port"
}
```

### 无感＋按压模式（打开目标页面直接弹按压验证码）

```json
{
    "tag": "v8.6.6",
    "href": "https://www.walmart.com/",
    "proxy": "user:pass@ip:port"
}
```

### XHR接口返回的纯按压验证码

如果触发接口直接返回JSON数据格式，直接将返回的JSON数据传递成captcha参数即可：

![xhr按压验证码](/images/perimeterx/4.png)

```json
{
    "app_id": "PXaOtQIWNf",
    "href": "https://www.chegg.com/auth?action=login&redirect=https%3A%2F%2Fwww.chegg.com%2Ftextbooks%2Fstudent-solutions-manual-chapters-1-11-for-stewart-s-single-variable-calculus-8th-edition-9781305271814-1305271815%3Ftrackid%3D74b04883b359%26strackid%3Db48a54386409%26searchid%3Db06489ae-fb76-4dc5-8d8e-dae3ce250966",
    "captcha": {
        "appId": "PXaOtQIWNf",
        "jsClientSrc": "/aOtQIWNf/init.js", 
        "firstPartyEnabled": true, 
        "uuid": "bd2deef7-0b95-11ef-8c49-cb4c98cbe205", 
        "hostUrl": "/aOtQIWNf/xhr", 
        "blockScript": "/aOtQIWNf/captcha/captcha.js?a=c&u=bd2deef7-0b95-11ef-8c49-cb4c98cbe205&v=&m=0", 
        "altBlockScript": "https://captcha.px-cloud.net/PXaOtQIWNf/captcha.js?a=c&u=bd2deef7-0b95-11ef-8c49-cb4c98cbe205&v=&m=0", 
        "customLogo": "https://chegg-mobile-promotions.cheggcdn.com/px/Chegg-logo-79X22.png"
    },
    "did": "无感模式返回的did",
    "proxy": "user:pass@ip:port"
}
```

## 📤 响应数据格式

| 参数名 | 类型 | 说明 |
|--------|------|------|
| `status` | `Integer` | 调用状态：1=成功，0=失败 |
| `msg` | `String` | 调用结果说明 |
| `id` | `String` | 请求唯一ID（可用于记录查询） |
| `data.cookies` | `String` | 验证成功返回的_px2、_px3 cookie |
| `cost` | `String` | 验证耗时（毫秒） |

### 响应示例

```json
{
  "status": 1,
  "msg": "验证成功",
  "id": "639e056b-49bd-4895-94ab-68d59e00873e",
  "cost": "2635.12ms",
  "data": {
    "cookies": {
        "_px3": "eb9fb4aab8cbd8d9c7018d0928bdccd972ef2a879383dec6b8999bca90ef4fdd:0r5KU/5t6VOMgwq7DnwmGd246hJVZbhPeI72OXfd8QSyRuK1hBRSBog3nrfQah8dLHd5X7cJZJnydq09AginIw==:1000:7eMdz1/BzkA4xQ8/rxujv5jsju6W1PbCAAp+gNDX8fox23jXH2mvzBzg0IwYLDX576aAHr3TeWqHFWvutnqxAKgTSIyR8cutzM7CG6zHQSV0N8piaWjjXlozbaWh77V3BGC7EZ/e3Rj3cbhl9Z4bufg6/87I91c7vv3Ka4ewGi+9EkKABRSCjAs4wEJYu6SneH1ZiiQAWVRW/EAULvFKJpxC07/qpxYuCblvaPljf14=", 
        "_pxde": "9a14782e5832ac4ba515c98e3e9f6b6e7b2e3d8ecb36320e659f85bb4f7359ac:eyJ0aW1lc3RhbXAiOjE3MTE2ODA3MDcyNzd9", 
        "pxcts": "48247186-ed77-11ee-8c23-8bccbc7b0e91",
        "_pxvid": "bcc357c3-ed78-11ee-aaf0-a24906ed7b54",
        "_pxde": "370c1218665b160f442e1e2b63603a15b046b7831b83de27de7c5211bf102f77:eyJ0aW1lc3RhbXAiOjE3MTE2ODI5NTE5MzZ9"
    }
  }
}
```

## 💻 代码示例

### CURL命令

```bash
curl -L 'http://api.nocaptcha.io/api/wanda/perimeterx/universal' \
 -H 'User-Token: xxx' \
 -H 'Developer-Id: hqLmMS' \
 -H 'Content-Type: application/json' \
 --data-raw '{"app_id": "PXu6b0qd2S", "href": "https://www.walmart.com/", "proxy": "user:pass@ip:port"}'
```

### Python调用示例

**安装依赖**
```bash
pip install -U pynocaptcha -i https://pypi.python.org/simple
```

**代码示例**
```python
from pynocaptcha import PerimeterxUniversalCracker

# PerimeterX验证码破解
cracker = PerimeterxUniversalCracker(
    user_token="your_user_token_here",
    developer_id="hqLmMS",  # 开发者ID
    app_id="PXu6b0qd2S",
    href="https://www.walmart.com/",
    captcha={
        "redirectUrl": "/blocked?url=Lw==&uuid=40f6c510-eb71-11ee-9952-619a9b96c881&vid=418e19e7-eb71-11ee-8541-88227401c984&g=b",
        "appId": "PXu6b0qd2S",
        "jsClientSrc": "/px/PXu6b0qd2S/init.js",
        "firstPartyEnabled": True,
        "vid": "418e19e7-eb71-11ee-8541-88227401c984",
        "uuid": "40f6c510-eb71-11ee-9952-619a9b96c881",
        "hostUrl": "/px/PXu6b0qd2S/xhr",
        "blockScript": "/px/PXu6b0qd2S/captcha/captcha.js?a=c&m=0&u=40f6c510-eb71-11ee-9952-619a9b96c881&v=418e19e7-eb71-11ee-8541-88227401c984&g=b",
    },
    proxy="user:pass@ip:port",
    debug=True
)
result = cracker.crack()
print(f"破解结果: {result}")
```

**完整流程示例**
```python
import requests
from pynocaptcha import PerimeterxUniversalCracker

def handle_perimeterx_verification(href, proxy):
    """处理PerimeterX验证的完整流程"""
    
    # 1. 先请求目标页面判断验证类型
    response = requests.get(href, proxies={"http": proxy, "https": proxy})
    
    if response.status_code == 403:
        # 按压验证模式
        print("检测到按压验证模式")
        cracker = PerimeterxUniversalCracker(
            user_token="your_user_token_here",
            developer_id="hqLmMS",
            tag="v8.6.6",  # 从页面获取
            href=href,
            proxy=proxy
        )
    else:
        # 无感验证模式
        print("检测到无感验证模式")
        cracker = PerimeterxUniversalCracker(
            user_token="your_user_token_here",
            developer_id="hqLmMS",
            app_id="PXu6b0qd2S",  # 从页面获取
            href=href,
            proxy=proxy
        )
    
    return cracker.crack()

# 使用示例
result = handle_perimeterx_verification(
    href="https://www.walmart.com/",
    proxy="user:pass@ip:port"
)
print(f"验证结果: {result}")
```

---

## 🎯 相关服务

- [AWS WAF验证码破解](aws.md)
- [Kasada验证码破解](kasada.md)
- [ReCaptcha验证码破解](recaptcha.md)
- [更多验证码解决方案](../README.md)

**需要技术支持？[立即联系我们](https://www.nocaptcha.io/register?c=hqLmMS)**
