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
  appId: 'PXaOtQIWNf',
  jsClientSrc: '/aOtQIWNf/init.js',
  firstPartyEnabled: true,
  uuid: '013b4cad-ece3-11ee-a877-09542f9a30cf',
  hostUrl: '/aOtQIWNf/xhr',
  blockScript: '/aOtQIWNf/captcha/captcha.js?a=c&u=013b4cad-ece3-11ee-a877-09542f9a30cf&v=&m=0',
  altBlockScript: 'https://captcha.px-cloud.net/PXaOtQIWNf/captcha.js?a=c&u=013b4cad-ece3-11ee-a877-09542f9a30cf&v=&m=0',
  customLogo: 'https://chegg-mobile-promotions.cheggcdn.com/px/Chegg-logo-79X22.png'
}
```
* `html`: 如果触发接口直接返回 `html` 数据格式, 则需要自己构造 `captcha` 参数, 找到 `window._pxAppId =` 的地方, 自行匹配出相关数据字段
```
<html lang="en">

<head>
    <title>Robot or human?</title>
    <meta name="viewport" content="width=device-width">
    <style>
    #sign-in-widget a,
    #sign-in-widget a:active,
    #sign-in-widget a:hover {
        color: #000
    }

    #sign-in-widget h1 {
        font-weight: 500;
        font-size: 20px;
        font-size: 1.25rem;
        letter-spacing: -.6px;
        margin: 1px auto
    }

    @media (min-width:30em) {
        #sign-in-widget h1 {
            margin-top: 24px;
            font-size: 24px;
            font-size: 1.5rem
        }
    }

    #sign-in-widget {
        font-family: BogleWeb, Helvetica Neue, Helvetica, Arial, sans-serif
    }

    #sign-in-widget * {
        box-sizing: border-box
    }

    #sign-in-widget .text-right {
        text-align: right
    }

    @font-face {
        font-family: NewYorkIcons;
        src: url(6255ed72d86ece856725a2d80878bce6.eot);
        font-weight: 400;
        font-style: normal
    }

    @font-face {
        font-family: NewYorkIcons;
        src: url(fd827841624904d4b8f51d20174fa3a4.woff2) format("woff2"), url(5b38b158833d0265af2b1c1093e489bd.woff) format("woff"), url(2ebae25dcb1bb39acbac9cffd8f10b15.ttf) format("truetype");
        font-weight: 400;
        font-style: normal
    }

    @keyframes spin-clockwise {
        0% {
            transform: rotate(0)
        }

        to {
            transform: rotate(1turn)
        }
    }

    @keyframes zoom-inverse {
        0% {
            opacity: 0;
            transform: scale(3)
        }

        33% {
            opacity: 1
        }

        to {
            transform: scale(1)
        }
    }

    @keyframes blinker {
        0% {
            opacity: 1
        }

        to {
            opacity: 0
        }
    }

    @keyframes slide-from-bottom {
        0% {
            transform: translateY(100%)
        }

        to {
            transform: translateY(0)
        }
    }

    @keyframes slide-from-top {
        0% {
            transform: translateY(0)
        }

        to {
            transform: translateY(100%)
        }
    }

    @keyframes fade-in-opacity {
        0% {
            opacity: 0
        }

        to {
            opacity: 1
        }
    }

    .elc-icon-spark:before {
        font-family: NewYorkIcons;
        display: inline;
        speak: none;
        content: "\E935"
    }

    .message {
        text-align: left
    }

    .message.active {
        display: block
    }

    .divider {
        margin: 24px 0 8px;
        text-align: center
    }

    @media (min-width:30em) {
        .divider {
            margin-top: 40px
        }
    }

    #sign-in-widget {
        text-align: center
    }

    #sign-in-widget p {
        margin-bottom: 0
    }

    #sign-in-widget .header-logo {
        text-decoration: none;
        font-size: 36px;
        font-size: 2.25rem
    }

    @media (min-width:30em) {
        #sign-in-widget .message.active+h1 {
            margin-top: 32px
        }
    }

    #sign-in-widget .elc-icon {
        font-family: NewYorkIcons
    }

    .u-sentenceCase {
        display: inline-block;
        text-decoration: inherit;
        text-transform: lowercase
    }

    .u-sentenceCase:first-letter {
        text-transform: uppercase
    }

    .u-sentenceCase--no-transform {
        text-transform: none
    }

    .message {
        -moz-osx-font-smoothing: grayscale;
        -webkit-font-smoothing: antialiased;
        display: none;
        padding: 8px 10px;
        border: 1px solid;
        color: #414042;
        font-size: 14px;
        font-size: .875rem
    }

    .message.active {
        display: inline-block
    }

    .spark {
        color: #ffc400
    }

    .sign-in-widget>* {
        display: none
    }

    [data-active="0"] .sign-in-widget>:first-child,
    [data-active="1"] .sign-in-widget>:nth-child(2),
    [data-active="10"] .sign-in-widget>:nth-child(11),
    [data-active="11"] .sign-in-widget>:nth-child(12),
    [data-active="12"] .sign-in-widget>:nth-child(13),
    [data-active="13"] .sign-in-widget>:nth-child(14),
    [data-active="14"] .sign-in-widget>:nth-child(15),
    [data-active="15"] .sign-in-widget>:nth-child(16),
    [data-active="16"] .sign-in-widget>:nth-child(17),
    [data-active="17"] .sign-in-widget>:nth-child(18),
    [data-active="18"] .sign-in-widget>:nth-child(19),
    [data-active="2"] .sign-in-widget>:nth-child(3),
    [data-active="3"] .sign-in-widget>:nth-child(4),
    [data-active="4"] .sign-in-widget>:nth-child(5),
    [data-active="5"] .sign-in-widget>:nth-child(6),
    [data-active="6"] .sign-in-widget>:nth-child(7),
    [data-active="7"] .sign-in-widget>:nth-child(8),
    [data-active="8"] .sign-in-widget>:nth-child(9),
    [data-active="9"] .sign-in-widget>:nth-child(10) {
        display: block
    }

    [data-active] {
        min-height: 100%;
        position: relative
    }

    [data-active]>* {
        margin-right: auto;
        margin-left: auto
    }

    @media (min-width:240px) {
        [data-active]>* {
            max-width: 304px;
            margin-right: auto;
            margin-left: auto
        }
    }

    @media (min-width:1024px) {
        [data-active]>* {
            max-width: 320px;
            margin-right: auto;
            margin-left: auto
        }
    }

    body,
    html {
        height: 100%;
        margin: 0
    }

    #sign-in-widget .header-logo {
        margin-top: 2px;
        display: inherit
    }

    @media (min-width:30em) {
        #sign-in-widget .header-logo {
            margin-top: 32px
        }
    }

    #sign-in-widget h1~.sign-in-widget {
        padding-bottom: 200px
    }

    .lite-footer {
        width: 100%;
        max-width: 100% !important
    }

    .lite-footer>hr {
        margin: 0;
        width: 100%;
        border-color: #e6e7e8;
        border-style: solid
    }

    @media (min-width:48em) {
        .lite-footer {
            position: absolute;
            bottom: 0;
            margin-top: 200px
        }
    }

    .lite-footer .main-container {
        padding: 16px;
        margin-bottom: 24px;
        font-size: 14px;
        font-size: .875rem;
        display: -ms-flexbox;
        display: flex;
        -ms-flex-direction: column;
        flex-direction: column;
        -ms-flex-pack: center;
        justify-content: center;
        -ms-flex-line-pack: center;
        align-content: center;
        width: 100%;
        max-width: 100% !important
    }

    @media (min-width:64em) {
        .lite-footer .main-container {
            -ms-flex-direction: row;
            flex-direction: row;
            -ms-flex-pack: justify;
            justify-content: space-between;
            -ms-flex-line-pack: start;
            align-content: flex-start
        }
    }

    .lite-footer .main-container .left-section {
        text-align: center
    }

    .lite-footer .main-container .left-section>a {
        display: block;
        margin-bottom: 16px
    }

    @media (min-width:48em) {
        .lite-footer .main-container .left-section {
            text-align: left
        }

        .lite-footer .main-container .left-section>a {
            display: inline;
            margin-right: 16px
        }
    }

    .lite-footer .main-container .right-section {
        text-align: center;
        font-size: 12px;
        font-size: .75rem
    }

    .lite-footer .main-container .right-section>p {
        margin: 0
    }

    @media (min-width:48em) {
        .lite-footer .main-container .right-section {
            text-align: left
        }

        .lite-footer .main-container .right-section>p {
            margin-top: 16px
        }
    }

    @media (min-width:64em) {
        .lite-footer .main-container .right-section>p {
            margin: 0
        }
    }

    /* upload and replace urls with new CDN URL*/
    @font-face {
        font-family: NewYorkIcons;
        src: url(https://i5.wal.co/dfw/63fd9f59-161f/f0d7612f-54fb-4910-a9c7-20c65d03f878/v1/6255ed72d86ece856725a2d80878bce6.eot);
        font-weight: 400;
        font-style: normal
    }

    @font-face {
        font-family: NewYorkIcons;
        src: url(https://i5.wal.co/dfw/63fd9f59-161f/f0d7612f-54fb-4910-a9c7-20c65d03f878/v1/fd827841624904d4b8f51d20174fa3a4.woff2) format("woff2"), url(https://i5.wal.co/dfw/63fd9f59-161f/f0d7612f-54fb-4910-a9c7-20c65d03f878/v1/5b38b158833d0265af2b1c1093e489bd.woff) format("woff"), url(https://i5.wal.co/dfw/63fd9f59-161f/f0d7612f-54fb-4910-a9c7-20c65d03f878/v1/2ebae25dcb1bb39acbac9cffd8f10b15.ttf) format("truetype");
        font-weight: 400;
        font-style: normal
    }

    @font-face {
        font-family: "BogleWeb";
        src: url("https://i5.walmartimages.com/dfw/63fd9f59-a78c/fcfae9b6-2f69-4f89-beed-f0eeb4237946/v1/BogleWeb_subset-Bold.eot");
        src: url("https://i5.walmartimages.com/dfw/63fd9f59-a78c/fcfae9b6-2f69-4f89-beed-f0eeb4237946/v1/BogleWeb_subset-Bold.eot?#iefix") format("embedded-opentype"),
            url("https://i5.walmartimages.com/dfw/63fd9f59-a78c/fcfae9b6-2f69-4f89-beed-f0eeb4237946/v1/BogleWeb_subset-Bold.woff2") format("woff2"),
            url("https://i5.walmartimages.com/dfw/63fd9f59-a78c/fcfae9b6-2f69-4f89-beed-f0eeb4237946/v1/BogleWeb_subset-Bold.woff") format("woff"),
            url("https://i5.walmartimages.com/dfw/63fd9f59-a78c/fcfae9b6-2f69-4f89-beed-f0eeb4237946/v1/BogleWeb_subset-Bold.ttf") format("truetype");
        font-weight: 700;
        font-style: normal;
    }

    @font-face {
        font-family: "BogleWeb";
        src: url("https://i5.walmartimages.com/dfw/63fd9f59-a78c/fcfae9b6-2f69-4f89-beed-f0eeb4237946/v1/BogleWeb_subset-Bold.eot");
        src: url("https://i5.walmartimages.com/dfw/63fd9f59-a78c/fcfae9b6-2f69-4f89-beed-f0eeb4237946/v1/BogleWeb_subset-Bold.eot?#iefix") format("embedded-opentype"),
            url("https://i5.walmartimages.com/dfw/63fd9f59-a78c/fcfae9b6-2f69-4f89-beed-f0eeb4237946/v1/BogleWeb_subset-Bold.woff2") format("woff2"),
            url("https://i5.walmartimages.com/dfw/63fd9f59-a78c/fcfae9b6-2f69-4f89-beed-f0eeb4237946/v1/BogleWeb_subset-Bold.woff") format("woff"),
            url("https://i5.walmartimages.com/dfw/63fd9f59-a78c/fcfae9b6-2f69-4f89-beed-f0eeb4237946/v1/BogleWeb_subset-Bold.ttf") format("truetype");
        font-weight: 600;
        font-style: normal;
    }

    @font-face {
        font-family: "BogleWeb";
        src: url("https://i5.walmartimages.com/dfw/63fd9f59-a78c/fcfae9b6-2f69-4f89-beed-f0eeb4237946/v1/BogleWeb_subset-Regular.eot");
        src: url("https://i5.walmartimages.com/dfw/63fd9f59-a78c/fcfae9b6-2f69-4f89-beed-f0eeb4237946/v1/BogleWeb_subset-Regular.eot?#iefix") format("embedded-opentype"),
            url("https://i5.walmartimages.com/dfw/63fd9f59-a78c/fcfae9b6-2f69-4f89-beed-f0eeb4237946/v1/BogleWeb_subset-Regular.woff2") format("woff2"),
            url("https://i5.walmartimages.com/dfw/63fd9f59-a78c/fcfae9b6-2f69-4f89-beed-f0eeb4237946/v1/BogleWeb_subset-Regular.woff") format("woff"),
            url("https://i5.walmartimages.com/dfw/63fd9f59-a78c/fcfae9b6-2f69-4f89-beed-f0eeb4237946/v1/BogleWeb_subset-Regular.ttf") format("truetype");
        font-weight: 400;
        font-style: normal;
    }
    </style>
    <script>
    function getUrlVars() {
        var vars = {};
        var parts = window.location.href.replace(/[?&]+([^=&]+)=([^&]*)/gi, function(m, key, value) {
            vars[key] = value;
        });
        return vars;
    }

    function getUrlParam(parameter, defaultvalue) {
        var urlparameter = defaultvalue;
        if (window.location.href.indexOf(parameter) > -1) {
            urlparameter = getUrlVars()[parameter];
        }
        return urlparameter;
    }

    </script>
<script >bazadebezolkohpepadr="1881248270"</script><script type="text/javascript" src="https://www.walmart.com/akam/13/7021920a"  defer></script></head>

<body>
    <div>
        <div data-active="0" id="sign-in-widget">
            <a class="header-logo" href="/" aria-atomic="true" aria-label="Walmart. Save Money. Live Better. Home Page">
                <span class="spark elc-icon elc-icon-spark elc-icon-36"></span>
            </a>
            <h1 class="heading heading-d sign-in-widget">
                Robot or human?
            </h1>
            <div class="sign-in-widget">
                <div class="re-captcha">
                    <p class="bot-message" id=message>Activate and hold the button to confirm that you’re human. Thank You!</p>
                    <div id="px-captcha" style="margin:16px;margin-bottom: 32px; margin-top: 32px; align-content:center; align-items: center;"></div>
                </div>
            </div>
            <script>
            window._pxAppId = 'PXu6b0qd2S';
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
            <script id="blockScript"></script>
            <script>
            document.getElementById('blockScript').src = captchajs;
            </script>
            <div class="lite-footer">
                <hr aria-hidden="true" class="divider">
                <div class="main-container">
                    <div class="left-section">
                        <a class="" href="https://help.walmart.com/app/answers/detail/a_id/8">
                            <span class="u-sentenceCase u-sentenceCase--no-transform">Terms of Use</span>
                        </a>
                        <a class="" href="https://corporate.walmart.com/privacy-security">
                            <span class="u-sentenceCase u-sentenceCase--no-transform">Privacy Policy</span>
                        </a>
                        <a class="" href="/account/api/ccpa-intake?native=false&amp;type=sod">
                            <span class="u-sentenceCase u-sentenceCase--no-transform">Do Not Sell My Personal Information</span>
                        </a>
                        <a class="" href="/account/api/ccpa-intake?native=false&amp;type=access">
                            <span class="u-sentenceCase u-sentenceCase--no-transform">Request My Personal Information</span>
                        </a>
                    </div>
                    <div class="right-section">
                        <p class="copy-base-ny">©<span id="year"></span><script>document.getElementById("year").innerHTML = (new Date().getFullYear());</script> Walmart Stores, Inc.</p>
                    </div>
                </div>
            </div>
        </div>
<noscript><img src="https://www.walmart.com/akam/13/pixel_7021920a?a=dD04Nzc0N2NjOTJmYjc5NmFlNGE5MzM3NThjZmYxYjEwOTM1YjI3ZmI1JmpzPW9mZg==" style="visibility: hidden; position: absolute; left: -999px; top: -999px;" /></noscript></body>

</html>
```

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
