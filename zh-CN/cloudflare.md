------

[`返回首页`](../README.md)    [`上一页`](recaptcha_app.md)      [`下一页`](incapsula.md) [`English Version`](../en-US/cloudflare.md)

## CloudFlare

### 类型说明

* 类型一: cookies (普通模式: `cf_clearance`、`__cf_bm`)

![cookies样例](/images/cloudflare/cookies.png)

* 类型二: 验证码式 (turnstile: `cf_turnstile-response`)
    * ps: 一般嵌入在登录框中, 验证参数为 `captcha_api_key` 等键名（只是举例不一定是这个）, 参数值为 `0.` 开头的。

![验证码式样例](/images/cloudflare/captcha.png)

### 参数查找

* cookies 类型: 直接输入触发页面地址即可

* turnstile 类型: 需要额外输入 sitekey 参数
![sitekey](/images/cloudflare/sitekey.png)

### 结果说明

* cloudflare 需要保持 ip、ua 一致
* cloudflare 校验 tls 指纹, 请自行使用 tls 请求库或使用 tls 转发服务

### Request URL（POST）:

| 版本                | 接口地址                                                     |
|-------------------|----------------------------------------------------------|
| `通用版（universal）`  | `http://api.nocaptcha.io/api/wanda/cloudflare/universal`  |

### Request Headers:

| 参数名            | 说明                                                                         | 必须  |
|----------------|----------------------------------------------------------------------------|-----|
| `User-Token`   | `用户密钥, 主页获取`                                                               | `是` |
| `Content-Type` | `application/json`                                                         | `是` |
| `Developer-Id` | `开发者 ID, 开发者用户使用, 用户主页邀请链接的字符串(如 xxx/register?c=abcdef, 则 abcdef 为开发者 ID)` | `否` |

### POST Data（JSON）:

| 参数名        | 类型        | 说明                                                                             | 必须  |
|------------|-----------|--------------------------------------------------------------------------------|-----|
| `href`  | `String`  | `触发验证的地址`                                           | `是` |
| `proxy`    | `String`  | `需要保持代理一致 格式请传 ip:port 或 usr:pwd@ip:port 或 socks5://ip:port (如果有问题联系管理员)` | `是` |
| `sitekey`       | `String`  | `turnstile 类型需要传入`                                         | `否` |
| `user_agent` | `String` | `自定义请求头, 如果返回提示不支持自定义则不要传`                            | `否` |

### 参数示例

#### cookies 类型

```json
{
    "href": "https://nowsecure.nl/",
    "proxy": "usr:pwd@ip:port"
}

```

#### turnstile 类型
```json
{
    "href": "https://visa.vfsglobal.com/chn/zh/deu/login",
    "proxy": "usr:pwd@ip:port",
    "sitekey": "0x4AAAAAAACYaM3U_Dz-4DN1"
}
```


### Response Data（JSON）

| 参数名          | 类型        | 说明                            |
|--------------|-----------|-------------------------------|
| `status`     | `Integer` | `调用是否成功, 1 成功, 0 失败, 请使用该值判断` |
| `msg`        | `String`  | `调用结果中文说明`                    |
| `id`         | `String`  | `该次请求 id（唯一, 可用作后续记录查询）`      |
| `data.cookies` | `String`  | `验证通过返回的 cookies`          |
| `data.token` | `String`  | `验证通过返回的 token(turnstile 使用)`               |
| `cost`       | `String`  | `验证耗时（毫秒）`                    |


```
{
    "cost": "3380.01ms",
    "data": {
        "token": "xxx",
        "cookies": "xxx=xxx;"
    },
    "id": "bc174976-81b2-418e-a6e3-9f7c0bbd41ae",
    "msg": "验证成功",
    "status": 1
}
```

### 调用示例

#### python

```shell
pip install -U pynocaptcha -i https://pypi.python.org/simple
```

```python
from pynocaptcha import CloudFlareCracker

cracker = CloudFlareCracker(
    user_token="xxx,
    sitekey="0x4AAAAAAACYaM3U_Dz-4DN1",
    href="https://visa.vfsglobal.com/chn/zh/deu/login",
    proxy="usr:pwd@ip:port",
    debug=True,
)
ret = cracker.crack()
print(ret)
```