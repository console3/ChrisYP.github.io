## Overview

### 目前支持的接口

| 类型                                                     | 说明                                                                     | 支持同步获取结果 | 消耗点数   | 共享  | 独享（请联系客服） |
|--------------------------------------------------------|------------------------------------------------------------------------|----------|--------|-----|-----------|
| [recaptcha:universal](api.nocaptcha.io/recaptcha.md)   | `ReCaptcha（v2/v3 通用版）, 直接返回 token`                                     | ✅        | `300`  | ✅   | ✅         |
| [recaptcha:enterprise](api.nocaptcha.io/recaptcha.md)  | `ReCaptcha（v2/v3 企业版）, 直接返回 token`                                     | ✅        | `500`  | ✅   | ✅         |
| [recaptcha:steam](api.nocaptcha.io/recaptcha.md)       | `ReCaptcha（steam）, 直接返回 token`                                         | ✅        | `600`  | ✅   | ✅         |
| [cloudflare:universal](api.nocaptcha.io/cloudflare.md) | `CloudFlare 盾通用版, 返回 cf_clearance、__cf_bm 、正确响应源码 html、验证流程使用的 tls 指纹` | ✅        | `1000` | ✅   | ✅         |
| [incapsula:universal](api.nocaptcha.io/incapsula.md)   | `Incapsula 盾通用版, 返回 reese84 cookie`                                    | ✅        | `300` | ✅   | ✅         |
| [incapsula:universal](api.nocaptcha.io/incapsula.md)   | `Incapsula 盾通用版, 返回 solution 等提交参数`                                    | ✅        | `100`  | ✅   | ✅         |
| [hcaptcha:universal](api.nocaptcha.io/hcaptcha.md)     | `Hcaptcha 通用版, 直接返回 generated_pass_UUID`                                    | ✅        | `300`  | ✅   | ✅         |
| [akamai:v2](api.nocaptcha.io/akamai.md)                | `Akamai v2, 直接返回 _abck`                                                 | ✅        | `1000`  | ✅   | ✅         |

### 名词说明

* `点数`: 服务消耗的点数, 1 元 = 10000 点, 1U = 66000 点
* `User-Token`: 用户令牌, 调用服务需要传入该参数, 在用户主页可以查看
* `Developer-ID`: 开发者 ID, 开发者用户使用, 用户主页邀请链接的字符串(如 xxx/register?c=abcdef, 则 `abcdef` 为开发者 ID)

### 等级说明

| 消费点数          | 实际消费      | 等级      |
|---------------|-----------|---------|
| `100000000` 点 | `10000` 元 | `VIP 1` |
| `250000000` 点 | `25000` 元 | `VIP 2` |
| `600000000` 点 | `60000` 元 | `VIP 3` |

### 折扣说明

| 等级      | 折扣    | 例子                    |
|---------|-------|-----------------------|
| `VIP 1` | `90%` | `300` 点服务实际消费 `270` 点 |
| `VIP 2` | `80%` | `300` 点服务实际消费 `240` 点 |
| `VIP 3` | `70%` | `300` 点服务实际消费 `210` 点 |

### 返利说明

* 邀请返利: 直接邀请的用户消费时, 得消费的 `20%` 返利（即 `A` 邀请 `B`, `B` 每消耗 `300` 点, `A` 得 `60` 点返利）
* 开发者返利: 用户消费调用服务接口时传入开发者 ID, 开发者得消费的 `20%` 返利（此时邀请者不得返利）
* 开发者返利优先级 > 邀请返利（即 `A` 邀请 `B`, `B` 填写 `C` 开发者 ID, `C` 得 `20%` 返利, `A` 不得返利）

### 返利使用

* 转余额: `1:1` 转换为余额, 用于服务消费
* 提现: 满 `50000` 点可提现

### 钱包数据查询接口

```angular2html
http://api.nocaptcha.io/api/get_user_balance?user_token={User-Token}&nickname={nickname}
```