## Overview

**👉[For English](/en-US/en.md)👈**

### 目前支持的接口

|                      类型                      |                           说明                            | 支持同步获取结果 |    消耗点数    | 传入代理IP优惠 | 运行状态 | 独享/包月（请联系客服） |
|:--------------------------------------------:|:-------------------------------------------------------:|:--------:|:----------:|:--------:|:----:|:------------:|
|  [recaptcha:universal](/zh-CN/recaptcha.md)  |           `ReCaptcha（v2/v3 通用版）, 直接返回 token`            |    ✅     |   `300`    |  `150`   |  ✅   |      ❌       |
| [recaptcha:enterprise](/zh-CN/recaptcha.md)  |           `ReCaptcha（v2/v3 企业版）, 直接返回 token`            |    ✅     |   `500`    |  `250`   |  ✅   |      ❌       |
|    [recaptcha:steam](/zh-CN/recaptcha.md)    |             `ReCaptcha（steam）, 直接返回 token`              |    ✅     |   `600`    |  `300`   |  ✅   |      ❌       |
|   [recaptcha:app](/zh-CN/recaptcha_app.md)   |             `ReCaptcha（app 版本）, 直接返回 token`             |    ✅     |   `500`    |  `250`   |  ❌   |      ❌       |
|   [hcaptcha:universal](/zh-CN/hcaptcha.md)   |        `Hcaptcha 通用版, 直接返回 generated_pass_UUID`         |    ✅     |   `300`    |  `150`   |  ✅   |      ❌       |
|   [incapsula:reese84](/zh-CN/incapsula.md)   |        `Incapsula 盾 reese84 通用版, 返回 solution 参数`        |    ✅     |   `210`    |    ❌     |  ✅   |      ✅       |
| [incapsula:utmvc](/zh-CN/incapsula_utmvc.md) |  `Incapsula 盾 __utmvc 通用版, 服务器直接无感验证 或 __utmvc cookie`  |    ✅     |   `150`    |    ❌     |  ✅   |      ✅       |
| [incapsula:rbzid](/zh-CN/incapsula_rbzid.md) |             `Incapsula 盾 rbzid 通用版, 返回验证参数`             |    ✅     |   `100`    |    ❌     |  ✅   |      ✅       |
|        [akamai:v2](/zh-CN/akamai.md)         |                 `Akamai v2, 直接返回 _abck`                 |    ✅     |   `1000`   |    ❌     |  ✅   |      ✅       |
|           [tls:v1](/zh-CN/tls.md)            |  `tls 转发接口, 针对校验 ja3、http2 等指纹（akamai/cloudflare）的接口`   |    ✅     |   `100`    |    ❌     |  ✅   |      ✅       |
|      [discord:guild](/zh-CN/discord.md)      |                     `discord 加群接口`                      |    ✅     |   `500`    |    ❌     |  ✅   |      ❌       |
| [cloudflare:universal](/zh-CN/cloudflare.md) | `CloudFlare 盾通用版, 返回 cookies 或验证码提交参数(turnstile 300 点)` |    ✅     | `1000/300` |    ❌     |  ✅   |      ✅       |
|        [aws:universal](/zh-CN/aws.md)        |        `Aws Waf 盾, 返回 aws-waf-token(仅无感 150 点)`         |    ✅     | `500/150`  |    ✅     |  ✅   |      ✅       |
| [perimeterx:universal](/zh-CN/perimeterx.md) |             `Perimeterx 盾通用版, 返回 _px2、_px3`             |    ✅     |   `1000`   |    ❌     |  ✅   |      ✅       |
|        [kasada:ct](/zh-CN/kasada.md)         |                `Kasada 盾, 返回 x-kpsdk-ct`                |    ✅     |   `1000`   |    ❌     |  ✅   |      ✅       |
|        [kasada:cd](/zh-CN/kasada.md)         |                `Kasada 盾, 返回 x-kpsdk-cd`                |    ✅     |    `50`     |    ❌     |  ✅   |      ✅       |
|        [datadome:universal](/zh-CN/datadome.md)         |                `Datadome 盾, 返回 datadome cookie`                |    ✅     |    `1000`     |    ❌     |  ✅   |      ✅       |

### 名词说明

* `点数`: 服务消耗的点数, `1美金 = 66,000 点` (`$1 = 66,000 points`)
* `User-Token`: 用户令牌, 调用服务需要传入该参数, 在用户主页可以查看
* `Developer-ID`: 开发者 ID, 开发者用户使用, 用户主页邀请链接的字符串(如 xxx/register?c=abcdef, 则 `abcdef` 为开发者 ID)

### 等级说明

| 消费点数            | 等级      | 折扣    | 说明                    |
|-----------------|---------|-------|-----------------------|
| `100,000,000` 点 | `VIP 1` | `90%` | `300` 点服务实际消费 `270` 点 |
| `250,000,000` 点 | `VIP 2` | `80%` | `300` 点服务实际消费 `240` 点 |
| `600,000,000` 点 | `VIP 3` | `70%` | `300` 点服务实际消费 `210` 点 |

### 返利说明

* 邀请返利: 直接邀请的用户消费时, 得消费的 `20%` 返利（即 `A` 邀请 `B`, `B` 每消耗 `300` 点, `A` 得 `60` 点返利）
* 开发者返利: 用户消费调用服务接口时传入开发者 ID, 开发者得消费的 `20%` 返利（此时邀请者不得返利）
* 开发者返利优先级 > 邀请返利（即 `A` 邀请 `B`, `B` 填写 `C` 开发者 ID, `C` 得 `20%` 返利, `A` 不得返利）

### 返利使用

* 转余额: `1:1` 转换为余额, 用于服务消费
* 提现: 目前支持 `10U` `20U` `50U` `100U` 四个额度的提现, 仅支持 `BSC链 (BEP20)` 地址提现

### 钱包数据查询接口

```text
http://api.nocaptcha.io/api/get_user_balance?user_token={User-Token}&nickname={nickname}
```

| 参数名          | 类型       | 说明                | 必须  |
|--------------|----------|-------------------|-----|
| `User-Token` | `String` | `用户令牌xxxx-xxx...` | `是` |
| `nickname`   | `String` | `登录邮箱abc@xxx.com` | `是` |

`http://api.nocaptcha.io/api/get_user_balance?user_token=40201fad-6666-3333-9999-b9f658666666&nickname=admin@nocaptcha.io`

### Response Data（JSON）:

```
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

