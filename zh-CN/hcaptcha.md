------
[`返回首页`](../README.md)    [`上一页`](recaptcha.md)      [`下一页`](incapsula.md)  [`English Version`](../en-US/hcaptcha.md)

## Hcaptcha

### 分数说明
  🚨🚨🚨如果你获取到值 但网站校验不通过 请联系管理员

### referer 参数说明
  🚨🚨🚨触发页面地址，✅请复制浏览器上显示的完整地址✅，不要改动，更不要去开发者工具❌里去找。
  或者找到下图的包, host 参数的值, referer 填写为 http://{host} 如下图所示, 例如: http://democaptcha.com
    ![hcaptcha](/images/hcaptcha/img.png)

### Request URL（POST）:

| 版本               | 接口地址                                                    |
|------------------|---------------------------------------------------------|
| `通用版（universal）` | `http://api.nocaptcha.io/api/wanda/hcaptcha/universal` |

### Request Headers:

| 参数名            | 说明                 | 必须  |
|----------------|--------------------|-----|
| `User-Token`   | `用户密钥, 主页获取`       | `是` |
| `Content-Type` | `application/json` | `是` |
| `Developer-Id` | `开发者 ID, 开发者用户使用, 用户主页邀请链接的字符串(如 xxx/register?c=abcdef, 则 abcdef 为开发者 ID)`           | `否` |

### POST Data（JSON）:

| 参数名          | 类型        | 说明                                                                                                                                                             | 必须  |
|--------------|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|-----|
| `sitekey`    | `String`  | `hcaptcha 对接 key`                                                                                                                          | `是` |
| `referer`    | `String`  | `见上文参数说明`                                                                                         | `是` |
| `rqdata`     | `String`  | `验证码配置接口有返回 captcha_rqdata、captcha_rqtoken 的请携带该值(如 discord 加频道)`                                                                                         | `否` |
| `domain`     | `String`  | `hcaptcha 的验证接口域名（即 getcaptcha/checkcaptcha 等接口的域名）, 某些网站验证域名不一致, 默认 hcaptcha.com`                | `否` |
| `proxy`      | `String`  | `如需要请传 ip:port 或 usr:pwd@ip:port 或 socks5://ip:port (如果有问题联系管理员)` | `否` |
| `internal`   | `Boolean` | `验证流程是否使用国内代理, 默认 true`                                                                                                                                        | `否` |
| `invisible`   | `Boolean` | `触发验证码时是否能看见点击框（或 是否无感验证码）, 默认 false`                                                                                                                                        | `否` |
| `need_ekey`   | `Boolean` | `是否需要返回 `E0_ey...`, 默认 false`                                                                                                                                        | `否` |

#### json 示例

```
{
  "sitekey": "a9b5fb07-92ff-493f-86fe-352a2803b3df",
  "referer": "https://discord.com/channels/253581140072464384/357581480110850049",
  "rqdata": "RRZ5RNoOL4uNPvEp0yB+bMPkBe2lUiM7p4u5lMAVUC9UBmzxJqdDDpGMrcDNApg/DDAQNIIlwEn2dLr7dZMg32I2bi523ZRfkAKpKxxg1sqnVW0xR9Y9ZCcwv54EiHeEqQ+iipixAVozAb6LjtwzNm2H9L15iSN8QfVrcp0Z",
}
```

```
{
  "sitekey": "c7faac4c-1cd7-4b1b-b2d4-42ba98d09c7a",
  "referer": "https://b.stripecdn.com/stripethirdparty-srv/assets/v13.1/HCaptcha.html?id=ab2764cd-d392-4fd0-81b4-9de6c4144c31&origin=https%3A%2F%2Fjs.stripe.com",
  "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/114.0.0.0 Safari/537.36",
  "proxy": "ip:port 或 usr:pwd@ip:port 或 socks5://ip:port"
}
```

```
{
  "sitekey": "c7faac4c-1cd7-4b1b-b2d4-42ba98d09c7a",
  "referer": "https://b.stripecdn.com/stripethirdparty-srv/assets/v13.1/HCaptcha.html?id=ab2764cd-d392-4fd0-81b4-9de6c4144c31&origin=https%3A%2F%2Fjs.stripe.com",
  "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/114.0.0.0 Safari/537.36",
  "proxy": "ip:port 或 usr:pwd@ip:port 或 socks5://ip:port"
}
```

```
{
  "sitekey": "c7faac4c-1cd7-4b1b-b2d4-42ba98d09c7a",
  "referer": "https://b.stripecdn.com/stripethirdparty-srv/assets/v13.1/HCaptcha.html?id=ab2764cd-d392-4fd0-81b4-9de6c4144c31&origin=https%3A%2F%2Fjs.stripe.com",
  "domain": "hcaptcha-endpoint.ecosec.on.epicgames.com",
  "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/114.0.0.0 Safari/537.36",
  "rqdata": "RRZ5RNoOL4uNPvEp0yB+bMPkBe2lUiM7p4u5lMAVUC9UBmzxJqdDDpGMrcDNApg/DDAQNIIlwEn2dLr7dZMg32I2bi523ZRfkAKpKxxg1sqnVW0xR9Y9ZCcwv54EiHeEqQ+iipixAVozAb6LjtwzNm2H9L15iSN8QfVrcp0Z",
}
```

### Response Data（JSON）:

#### 提交验证（submit=true）

| 参数名            | 类型        | 说明                            |
|----------------|-----------|-------------------------------|
| `status`       | `Integer` | `调用是否成功, 1 成功, 0 失败, 请使用该值判断` |
| `msg`          | `String`  | `调用结果中文说明`                    |
| `id`           | `String`  | `该次请求 id（唯一, 可用作后续记录查询）`      |
| `data.generated_pass_UUID` | `String`  | `验证通过返回的 uuid(P1_xxx/F1_xxx) 凭证, 可用于后续验证接口`    |
| `data.ekey` | `String`      | `验证通过返回的 key(E0_xxx), 可用于后续验证接口`    |
| `cost`         | `String`  | `验证耗时（毫秒）`                    |

```
{
  "cost": "9187.84ms",
  "data": {
    "generated_pass_UUID": "P1_eyxxx",
    "user_agent": "..."
  },
  "id": "c5b976bd-4c01-4378-bb44-324c76e9fe0f",
  "msg": "验证成功",
  "status": 1
}
```

### CURL command:

```
curl \
 -H "Host: api.nocaptcha.io" \
 -H "User-Agent: python-requests/2.28.2" \
 -H "Accept: */*" \
 -H "User-Token: xxx" \
 -H "Content-Type: application/json" \
 --data-binary "{\"sitekey\": \"f5561ba9-8f1e-40ca-9b5b-a0b3f719ef34\", \"referer\": \"https://discord.com/login\"}" \
 --compressed "http://api.nocaptcha.io/api/wanda/hcaptcha/universal"
```

### 调用示例

#### python

```shell
pip install -U pynocaptcha -i https://pypi.python.org/simple
```

```python
from pynocaptcha import HcaptchaCracker


cracker = HcaptchaCracker(
    user_token="xxx",
    sitekey='a9b5fb07-92ff-493f-86fe-352a2803b3df',
    referer="https://discord.com/channels/253581140072464384/357581480110850049",
    rqdata="RRZ5RNoOL4uNPvEp0yB+bMPkBe2lUiM7p4u5lMAVUC9UBmzxJqdDDpGMrcDNApg/DDAQNIIlwEn2dLr7dZMg32I2bi523ZRfkAKpKxxg1sqnVW0xR9Y9ZCcwv54EiHeEqQ+iipixAVozAb6LjtwzNm2H9L15iSN8QfVrcp0Z",
    debug=True,
)
ret = cracker.crack()
print(ret)
```
