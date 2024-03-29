------

[`返回首页`](../README.md)    [`上一页`](aws.md)

## PerimeterX

### 价格说明
* 无感模式消耗 `500` 点, 需要传入 `tag`、`href`、`proxy`
* 按压模式消耗 `1000` 点, 需要传入 `tag`、`href`、`captcha`、`proxy`

### 说明
* 当看到 `cookies` 中有 `_px2`、`_px3` 时, 代表存在 `perimeterx` 验证, 有以下两种情况
    * `无感模式`: `*/api/v2/colletor`
    ![验证接口](/images/perimeterx/1.png)
    * `按压验证码`: `*/assets/js/bundle`
    ![验证接口](/images/perimeterx/3.png)
    ![按压验证码样例](/images/perimeterx/2.png)


### Request URL（POST）:

| 版本               | 接口地址                                                    |
|------------------|---------------------------------------------------------|
| `通用版（universal）` | `http://api.nocaptcha.io/api/wanda/perimeterx/universal` |

### Request Headers:

| 参数名            | 说明                 | 必须  |
|----------------|--------------------|-----|
| `User-Token`   | `用户密钥, 主页获取`       | `是` |
| `Content-Type` | `application/json` | `是` |
| `Developer-Id` | `开发者 ID, 开发者用户使用, 用户主页邀请链接的字符串(如 xxx/register?c=abcdef, 则 abcdef 为开发者 ID)`           | `否` |

### POST Data（JSON）:

| 参数名          | 类型        | 说明                                                                                                                                                             | 必须  |
|--------------|-----------|-----------------------------|-----|
| `tag`        | `String`  | `版本号, */api/v2/colletor 或者 */assets/js/bundle 中的 tag 参数`    | `是` |
| `href`    | `String`  | `触发 perimeterx 验证的页面地址`    | `是` |
| `captcha`    | `Object`  | `验证码参数, 按压验证码必传, 详细说明见下`    | `否` |
| `user_agent` | `String`  | `自定义 user_agent`       | `否` |
| `cookies` | `String`  | `按压验证码模式下, 当前页面的 cookies`       | `否` |
| `fast` | `Boolean`  | `是否快速验证, 需要高分时请传 false, 默认 true`       | `否` |
| `timeout` | `Integer`  | `验证超时时间`       | `否` |

##### captcha 参数说明

| 参数名          | 类型        | 说明                                                                                                                                                             | 必须  |
|--------------|-----------|-----------------------------|-----|
| `appId`      | `String`  | `用户 id`    | `是` |
| `hostUrl`       | `String`  | `用户自定义路由, 接口返回啥就填啥`    | `是` |
| `jsClientSrc`       | `String`  | `加载脚本地址, 一般为 init.js 结尾, 接口返回啥或者 f12 中是啥就填啥`    | `是` |
| `blockScript` | `String`  | `验证码脚本地址, 一般为 captcha.js, 接口返回啥或者 f12 中是啥就填啥`       | `是` |
| `uuid` | `String`  | `当前验证码的 session id`       | `是` |
| `altBlockScript` | `String`  | `当 blockScript 不可用时的替代脚本`       | `否` |
| `firstPartyEnabled` | `Boolean`  | `接口返回啥就填啥, 不返回就不填`       | `否` |
| `customLogo` | `String`  | `接口返回啥就填啥, 不返回就不填`       | `否` |
| `vid` | `String`  | `接口返回啥就填啥, 不返回就不填`       | `否` |

`captcha` 参数根据触发按压验证码接口返回的数据格式而定, 有两种格式:

* `json`: 如果触发接口直接返回 `json` 数据格式, 则不需要再自己构造 `captcha` 参数, 直接将返回的 `json` 数据传递成 `captcha` 参数即可

```
{
    "appId": "PXaOtQIWNf",
    "jsClientSrc": "/aOtQIWNf/init.js",
    "firstPartyEnabled": true,
    "uuid": "013b4cad-ece3-11ee-a877-09542f9a30cf",
    "hostUrl": "/aOtQIWNf/xhr",
    "blockScript": "/aOtQIWNf/captcha/captcha.js?a=c&u=013b4cad-ece3-11ee-a877-09542f9a30cf&v=&m=0",
    "altBlockScript": "https://captcha.px-cloud.net/PXaOtQIWNf/captcha.js?a=c&"u=013b4cad-ece3-11ee-a877-09542f9a30cf&v=&m=0",
    "customLogo": "https://chegg-mobile-promotions.cheggcdn.com/px/Chegg-logo-79X22.png"
}
```

* `html`: 如果触发接口直接返回 `html` 数据格式, 则需要自己构造 `captcha` 参数, 找到 `window._pxAppId =` 的地方, 自行匹配出相关数据字段, 比如下方这段 `html`:

```
<script>
    window._pxAppId = 'PXu6b0qd2S';
    window._pxUuid = '013b4cad-ece3-11ee-a877-09542f9a30cf';
    window._pxJsClientSrc = '/px/' + window._pxAppId + '/init.js';
    window._pxFirstPartyEnabled = true;
    window._pxHostUrl = '/px/' + window._pxAppId + '/xhr';
    window._pxreCaptchaTheme = 'light';
    window._PXETnJ2Y5H = {
        challenge: {
            view: {
                    textFont: "BogleWeb, Helvetica Neue, Helvetica, Arial, sans-serif"
            }
        }
    };

    var hc = getUrlParam('g', 'b');
    var alt = hc
    if (alt=='a') {
        document.getElementById('message').innerHTML = '<p>Check the box to confirm that you’re human. Thank You!</p>';
    }
    var captchajs = "/px/" + window._pxAppId + "/captcha/captcha.js?a=c&m=0&g=" + hc
</script>
```

构造出的 `captcha` 参数为: 

```
{
    "appId": "PXu6b0qd2S",
    "jsClientSrc": "/px/PXu6b0qd2S/init.js",
    "firstPartyEnabled": true,
    "uuid": "013b4cad-ece3-11ee-a877-09542f9a30cf",
    "hostUrl": "/px/PXu6b0qd2S/xhr",
    "blockScript": "/px/PXu6b0qd2S/captcha/captcha.js?a=c&m=0&g=b",
}
```

* `重定向`: 还有的会重定向到只有 `perimeterx` 验证的页面, 如 `www.walmart.com`, 重定向后的地址为 `/blocked?url=Lw==&uuid=40f6c510-eb71-11ee-9952-619a9b96c881&vid=418e19e7-eb71-11ee-8541-88227401c984&g=b`, 此时 `uuid` 参数取该重定向链接中的（如何 `html` 中没有 `window._pxUuid = *`）

#### json 示例

```
{
    "tag": "v8.6.6",
    "href": "https://www.walmart.com/",
    "captcha": {
        "redirectUrl": "/blocked?url=Lw==&uuid=40f6c510-eb71-11ee-9952-619a9b96c881&vid=418e19e7-eb71-11ee-8541-88227401c984&g=b",
        "appId": "PXu6b0qd2S",
        "jsClientSrc": "/px/PXu6b0qd2S/init.js",
        "firstPartyEnabled": true,
        "vid": "418e19e7-eb71-11ee-8541-88227401c984",
        "uuid": "40f6c510-eb71-11ee-9952-619a9b96c881",
        "hostUrl": "/px/PXu6b0qd2S/xhr",
        "blockScript": "/px/PXu6b0qd2S/captcha/captcha.js?a=c&m=0&u=40f6c510-eb71-11ee-9952-619a9b96c881&v=418e19e7-eb71-11ee-8541-88227401c984&g=b",
    },
    "proxy": "user:pass@ip:port",
}
```


### Response Data（JSON）:

#### 提交验证（submit=true）

| 参数名            | 类型        | 说明                            |
|----------------|-----------|-------------------------------|
| `status`       | `Integer` | `调用是否成功, 1 成功, 0 失败, 请使用该值判断` |
| `msg`          | `String`  | `调用结果中文说明`                    |
| `id`           | `String`  | `该次请求 id（唯一, 可用作后续记录查询）`      |
| `data.cookies`   | `String`  | `验证通过返回的可用的 _px2、_px3 cookie, 可用于后续验证接口`    |
| `cost`         | `String`  | `验证耗时（毫秒）`                    |

```
{
  "status": 1,
  "msg": "验证成功",
  "id": "639e056b-49bd-4895-94ab-68d59e00873e",
  "cost": "2635.12ms",
  "data": {
    "cookies": {
        "_px3": "eb9fb4aab8cbd8d9c7018d0928bdccd972ef2a879383dec6b8999bca90ef4fdd:0r5KU/5t6VOMgwq7DnwmGd246hJVZbhPeI72OXfd8QSyRuK1hBRSBog3nrfQah8dLHd5X7cJZJnydq09AginIw==:1000:7eMdz1/BzkA4xQ8/rxujv5jsju6W1PbCAAp+gNDX8fox23jXH2mvzBzg0IwYLDX576aAHr3TeWqHFWvutnqxAKgTSIyR8cutzM7CG6zHQSV0N8piaWjjXlozbaWh77V3BGC7EZ/e3Rj3cbhl9Z4bufg6/87I91c7vv3Ka4ewGi+9EkKABRSCjAs4wEJYu6SneH1ZiiQAWVRW/EAULvFKJpxC07/qpxYuCblvaPljf14=", 
        "_pxde": "9a14782e5832ac4ba515c98e3e9f6b6e7b2e3d8ecb36320e659f85bb4f7359ac:eyJ0aW1lc3RhbXAiOjE3MTE2ODA3MDcyNzd9", 
        "pxcts": "48247186-ed77-11ee-8c23-8bccbc7b0e91"
        "_pxvid": "bcc357c3-ed78-11ee-aaf0-a24906ed7b54",
        "_pxde": "370c1218665b160f442e1e2b63603a15b046b7831b83de27de7c5211bf102f77:eyJ0aW1lc3RhbXAiOjE3MTE2ODI5NTE5MzZ9"
    }
}
```

### 调用示例

#### python

```shell
pip install -U pynocaptcha -i https://pypi.python.org/simple
```

```python
from pynocaptcha import PerimeterxUniversalCracker


cracker = PerimeterxUniversalCracker(
    user_token="xxx",
    tag="v8.6.6",
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
    debug=True,
)
ret = cracker.crack()
print(ret)
```
