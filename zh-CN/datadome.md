------

[`返回首页`](../README.md)    [`上一页`](kasada.md)    [`下一页`](shape.md)

## Datadome

### 说明
* 当看到 `cookies` 中有 `datadome`, 代表存在 `datadome` 验证, 有以下三种情况
    * `无感模式`: 
      * 如果进入目标页面, 没有直接出现 `datadome` 的滑块验证码或者设备验证模式, 打开 f12 查看是否有 `/js/` 结尾并且接口响应如下类似:
      ```
      {
        "status": 200,
        "cookie": "datadome=66wPBABk21P4x28BLuVse__8_z141EPJEjbgi1HBvNGBcHmX91OT1Z9Z63G4x_suPlRPQ_tgwljYmI5mWxpmkMJ3pKrcnAVKHZs2ymS_2O4nM5wEblvP~~nK3orSol0W; Max-Age=31536000; Domain=.soundcloud.com; Path=/; Secure; SameSite=Lax"
      }
      ```
      则是 `无感` 验证类型, 必须要传 `js_url` (该 `/js/` 结尾的 url), 该种模式会在我们的接口响应的 `extra` 参数中返回一个 `did` 参数, 该参数对于该页面后续的 `datadome` 验证非常重要！！！
      * 如果首页是 `无感模式`, 则后续的关键数据接口（如 `登录`、`查询`等）中携带有 `datadome` cookie, 并且会返回以下类似响应:
      ```
      {
        "url": "https://geo.captcha-delivery.com/captcha/?initialCid=AHrlqAAAAAMAqpOrr0GfIWgAudQ9Vg==&cid=w9vlJ4Xaf117hm82ORPnno7AnVvPPCoZ2gCDLj~Nch09ENObNXSzDWFekvMpp8ScynMSrB3~jsXcFtU9Y8mhOUscfnu1k_a~4_GMyGRE29_Gy~skFDqfX8tQJv1Va5Fv&referer=http%3A%2F%2Fapi-auth.soundcloud.com%2Fweb-auth%2Fidentifier%3Fq%3Desbiya1%2540gmail.com%26client_id%3D1q3v4x1lu3DpcWb4fAz0urivByipMEMK&hash=7FC6D561817844F25B65CDD97F28A1&t=fe&s=48134&e=faa8c1fb03676ac05d3bbe1d876a2d60168a7a2bab3adb5366483fc829465498"
      }
      ```
      则过掉该验证码需要传 `href` (当前浏览器页面的地址), `captcha_url`(响应中的 url `https://geo.captcha-delivery.com/captcha/?initialCid=AHrlqAAAAAMAqpOrr0GfIWgAudQ9Vg==&cid=w9vlJ4Xaf117hm82ORPnno7AnVvPPCoZ2gCDLj~Nch09ENObNXSzDWFekvMpp8ScynMSrB3~jsXcFtU9Y8mhOUscfnu1k_a~4_GMyGRE29_Gy~skFDqfX8tQJv1Va5Fv&referer=http%3A%2F%2Fapi-auth.soundcloud.com%2Fweb-auth%2Fidentifier%3Fq%3Desbiya1%2540gmail.com%26client_id%3D1q3v4x1lu3DpcWb4fAz0urivByipMEMK&hash=7FC6D561817844F25B65CDD97F28A1&t=fe&s=48134&e=faa8c1fb03676ac05d3bbe1d876a2d60168a7a2bab3adb5366483fc829465498` )
      以及上面所说的 `无感` 模式返回的 `did` 参数必须携带
      也就是使用无感模式返回的 `datadome` cookie 访问你的目标数据接口又继续返回了滑块验证码或者设备验证码模式的话, 则需要携带 `href`、`captcha_url`、`did`
    ![无感验证码样例](/images/datadome/js.png)
    * `设备验证模式`: 
      * 如果进入目标页面直接跳转至下面这样验证的页面或者是过掉滑块验证之后又跳转到这个验证了, 则是 `interstitial` 设备验证模式, 请传参数 `interstitial: true`
    ![无感验证码样例](/images/datadome/interstitial.png)
    * `滑块验证码`:
      * 如果进入目标页面直接跳转至下面这样验证的页面, 则是 `captcha` 滑块验证码模式
    ![滑块验证码样例](/images/datadome/captcha.png)


### Request URL（POST）:

| 版本               | 接口地址                                                    |
|------------------|---------------------------------------------------------|
| `通用版（universal）` | `http://api.nocaptcha.io/api/wanda/datadome/universal` |

### Request Headers:

| 参数名            | 说明                 | 必须  |
|----------------|--------------------|-----|
| `User-Token`   | `用户密钥, 主页获取`       | `是` |
| `Content-Type` | `application/json` | `是` |
| `Developer-Id` | `开发者 ID, 开发者用户使用, 用户主页邀请链接的字符串(如 xxx/register?c=abcdef, 则 abcdef 为开发者 ID)`           | `否` |

### POST Data（JSON）:

| 参数名          | 类型        | 说明                                                                                                                                                             | 必须  |
|--------------|-----------|-----------------------------|-----|
| `href`    | `String`  | `触发 datadome 验证的页面地址`    | `是` |
| `proxy`    | `String`  | `无需保持代理一致, 若传代理请使用海外代理, 格式请传 ip:port 或 usr:pwd@ip:port (如果有问题联系管理员)` | `是` |
| `js_url`    | `String`  | `js 模式下需要传该参数, /js/ 结尾的返回 datadome cookie 的接口, 如: https://dwt.soundcloud.com/js/`    | `否` |
| `captcha_url`    | `String`  | `post(xhr) 接口触发的 "url": "/captcha?initCid=xxx"`    | `否` |
| `interstitial`    | `Boolean`  | `是否会触发 interstitial 设备验证模式, 默认 false`    | `否` |
| `user_agent` | `String`  | `自定义 user_agent, 必须保持 user-agent 一致`       | `否` |
| `cookies` | `String`  | `当前页面的 cookies`       | `否` |
| `timeout` | `Integer`  | `验证超时时间`       | `否` |

### Response Data（JSON）:

#### 提交验证（submit=true）

| 参数名            | 类型        | 说明                            |
|----------------|-----------|-------------------------------|
| `status`       | `Integer` | `调用是否成功, 1 成功, 0 失败, 请使用该值判断` |
| `msg`          | `String`  | `调用结果中文说明`                    |
| `id`           | `String`  | `该次请求 id（唯一, 可用作后续记录查询）`      |
| `data.datadome`   | `String`  | `验证通过返回的可用的 datadome cookie, 可用于后续验证接口`    |
| `cost`         | `String`  | `验证耗时（毫秒）`                    |

```
{
  "status": 1,
  "msg": "验证成功",
  "id": "639e056b-49bd-4895-94ab-68d59e00873e",
  "cost": "4635.12ms",
  "data": {
    "datadome": "HYvnTVSxppxMMrSk_Z_MOHoSKkQRd2ppQr~pOeo2nDlL7Lg7QBwb2ew5OYQxSSSH1CR9NzO78A25KHM7kLV6OydtvwvJZ773Jil1mPC7ZoFSQQDrDYVeHZtjq_BWUai6"
  }
}
```

### 调用示例

#### python

```shell
pip install -U pynocaptcha -i https://pypi.python.org/simple
```

```python
from pynocaptcha import DatadomeCracker


cracker = DatadomeCracker(
    user_token="xxx",
    href="https://soundcloud.com/",
    js_url='https://dwt.soundcloud.com/js/',
    proxy="user:pass@ip:port",
    debug=True,
)
ret = cracker.crack()
print(ret)
```
