------
[`返回首页`](../README.md)    [`下一页`](cloudflare.md)

## ReCaptcha

### 有问必答

  * 如何区分 v2、v3 ？
    * 与其他平台不同的是，我们只区分普通版和企业版，`v2`、`v3` 的区别在于 `size` 参数的不同，`v2` `size` 参数为 `normal`，`v3` `size` 参数为 `invisible`，并且 `v3` 需要传 `action` 参数，请打开 `f12` 搜索 `grecaptcha.execute`，找到该函数的入参对象的 `action` 值，填入 `action` 参数即可。（ps：普通版、企业版接口参数完全相同，唯一不同在于请求路由的不同：普通版 `recaptcha/universal`/企业版 `recaptcha/enterprise`）。

### 为什么选择我们

* 通用性: 目前已知网站均能通过验证，且接口统一 `v2`、`v3` 。
* 极致的速度: 市面上其他接口都是异步的，需要先创建任务，然后获取任务 id 不停的去轮询获取验证结果，有时耗时会达到 1
  分钟之久，这是难以接受的。而我们的接口使用`纯算法`计算参数，`协议提交`，`同步返回`，`v3 invisible `、`v2 nocaptcha`
  类型平均 `1s` 返回，`v2` 其他图片点击类型最快 `2s`，最慢不会超过 `10s` （这也取决于代理的速度）。
* 高可用: `v3` 分值高，大部分风控强度高的站点（如各种企业版），我们接口生产的 `token` 值，都能通过风控成功获取到目标数据。
* 稳定性: 更新及时（不会超过两小时），更好地支撑您的业务。

### Request URL（POST）:

| 版本                  | 接口地址                                                  |
|----------------------|----------------------------------------------------------|
| `通用版（universal）`  | `http://api.nocaptcha.io/api/wanda/recaptcha/universal`  |
| `企业版（enterprise）` | `http://api.nocaptcha.io/api/wanda/recaptcha/enterprise` |

### Request Headers:

| 参数名            | 说明                 | 必须  |
|----------------|-----------------------|-----|
| `User-Token`   | `用户密钥, 主页获取`     | `是` |
| `Content-Type` | `application/json`    | `是` |
| `Developer-Id` | `开发者 id`            | `否` |

### POST Data（JSON）:

| 参数名 | 类型 | 说明 | 必须 |
|------|------|------|------|
| `sitekey` |    `String`  |   `谷歌验证码对接 key(anchor/reload 接口的 k 值)`    |  `是` |
| `referer` |     `String`    | `触发页面地址` | `是` |
| `size` |   `String`    |  `验证类型(invisible/normal, 只有这两个选择, 具体查看 anchor/reload 接口的 size 值, 必须对应)`  |  `是` |
| `title` |   `String`    |  `触发页面的 title (f12 打开控制台, 输入 document.title)`  |  `是` |
| `action` |   `String`    |  `验证码触发页面搜索 grecaptcha.execute(client, {action: action}), 其中的 action 值, v3 才需要`  |  `否` |
| `domain` |   `String`    |  `验证域名(默认使用 recaptcha.google.cn, 另外一个选择 www.recaptcha.net)`  |  `否` |

#### json 示例

```
{
  "domain": "recaptcha.google.cn",
  "referer": "https://www.trustpilot.com/",
  "sitekey": "6Lcxp2UaAAAAABkIC5izuDmTEeXYfgfaoQ9v69Q4",
  "size": "invisible",
  "title": "Login",
  "action": "login",
  "domain": "www.recaptcha.net",
}
```

### Response Data（JSON）

| 参数名          | 类型        | 说明                            |
|--------------|-----------|-------------------------------|
| `status`     | `Integer` | `调用是否成功, 1 成功, 0 失败, 请使用该值判断` |
| `msg`        | `String`  | `调用结果中文说明`                    |
| `id`         | `String`  | `该次请求 id（唯一, 可用作后续记录查询）`      |
| `data.token` | `String`  | `验证通过返回的 token`               |
| `cost`       | `String`  | `验证耗时（毫秒）`                    |

```
{
  "cost": "1380.01ms",
  "data": {
    "token": "03AFY_a8UL3OTinrQHai6iE4c9l--oZAtVsDsAGBtijmv3QgBWmeOWWvbJvZ_DPT8p2ttvUlr4FmE5gDSTON0f4mPpYqxwPdVYxRbC0nmLuZJ0k9UmOjiK4HgUShuFu4RL7w1hyoFQ1YbUpLtW-KuAqC1KSs4GGBrI3k4Cx4u7e57DQPhVdzzpVGqQjGq9ZnI5YY9546_jRybKrIv2FMLeIkvcOJnCPUTnUREewSn7VO1bCvpdAP3Wj8DoH8jtv-RXij9aypLnFcpLGMTwrJOCE9z2U7As7AzAxcMnVEr9AWyKipKj4t-A2m77uNvHv-f1XhSMNI_Dk4bIYLe5n0N-STCLUc5tFfPc5rtuNQdoTRxdl6ie9gOpzpUyg6dwcA3tEiERya9Tej-6FMpwo4G4F61u8buUAMgCVn-4OoAB9AfH5mjN3GapQf3Yc_mK2u99xErSwEgwuhVsBsMzC22JiVaqHWO8EOzDRso6AMpUmuZw27b3Kl8IhFH1OiIL9WdfMfEXtEDgUFZxL085MxyS_mv5iGDbcxLkXN5PupgT2ieoQ8grbHsbHWF1-9Un0cxF5MVfmIilzbSUtItZ7i2SZcJZlPOG86D1CKby2T7nnprtoVd7hAN4r5yTnQ52f_8oShEKd3n0ArHsfti4TXPuVgafP8jp4uIkgK3YDlF2QvnnuGeEq58dZ91nllOQOBnzc_GiNLvd1h8XrZxexZ2eI_LDueF2p4uSWQBDLXloHV_2lmDf5QsDcUJy46JyhlehLK-MOzLt-BDJ9wVJdtHhY_GT-IymY757nYurqWCLdY7k7ofeIcd51I35Hz88VADyp_EYtRzmd5CIRX_sHx4rlw7Yw1khFG6Ktw-7bRd1nSw1rNZlwFIxvLk4Bgp9WGZS8rqRCKIJgAMAJOzt872i1P9GQ3k6Ee5nn8qTs0CmpckzrvqJLzexQfM69G-A1O0s99PMn0Hr5ruUU_jsj3rtzWu1zXr0soPtArvN2tvTLsRSARIL1G5unTeX7YpURkbVVkmaa08oqpR7eIFVO7I7SZ99jk-DJdXSL5uUs3ZcIe8fzIp_hGtCkSQIrHrB0F5anyER7ZdBH1ynT7aFltOlikAWB_s4lTIYZk7VDUrrwKOSMI3SMHus7BxKZNanhTO34c_9s62t9FRrLaiQfTXy4ZUlCgVAkWt1f_6lrRwj9VZDQRiplJQwIIDpT2jhXrgGLdqIjOBtJ2Doy3Gx4dkpPCuquqhnzyvFCEJdyG-QKaONu4tbFjbUWB7TwIgREUVdrR5k3YN21sVTY2yvNZjc8YVCw-YXIYygZE6OpPJUIhxxXtB55xpxQ2THITBlkIu5QmBtQ4lXi3GBbq_UKB_Lxn5SVjK88yTZ3TD3m8nfH4WDdb4c36Ff4lpGEEIsZtS7U11FqTGu_xv-dgIYN0-t1tK8TKhJLHDG8nRwady2Xiq190yBXI3sDDcumMpCYqf2wE6Hmu2gnLRGlqPYdsnlC0JQMoeUTHhdEBslQb4iPV_0azLHp_kCEZvYZYalmyIibmmI2O9qY9gROUHt7NRLl_-T3mxr7cdRP2kG801i8Y87nY6PVllAs5JCVcRcMu3UXxvgianbXX_VVsuEf3Y-uxoRV7LKHYesm7tsxxcDwUtZiWzjY0PTCMUXgAjWrJDs-w9VUQGGeOWxqebTx-Mg_fTEXvqkmChhFTyBRDF0yQnMx0KaCnOogEK2XxI_ts_M-DWrXFBHUZa9a9a09T-73kpJqlVCcwgQjV-LhyaeQxUIT02_diqL-xM00AWhJmqwnojmmP6cXU34"
  },
  "id": "bc174976-81b2-418e-a6e3-9f7c0bbd41ae",
  "msg": "验证成功",
  "status": 1
}
```

### CURL command

```
curl -L 'http://api.nocaptcha.io/api/wanda/recaptcha/universal' \
 -H 'User-Token: xxx' \
 -H 'Content-Type: application/json' \
 --data-raw '{"sitekey": "6Lcxp2UaAAAAABkIC5izuDmTEeXYfgfaoQ9v69Q4", "referer": "https://www.trustpilot.com/", "size": "invisible", "title": "Login"}' 
```

### 调用示例

#### python

```shell
pip install pynocaptcha
```

```python
from pynocaptcha import ReCaptchaUniversalCracker, ReCaptchaEnterpriseCracker

cracker = ReCaptchaUniversalCracker(
    user_token="xxx",
    sitekey="6LftSMEUAAAAANe9O4IJt4lDNV2naDxJwOu88w5o",
    referer="https://www.52pojie.cn/member.php?mod=logging&action=login&auth=fcadNvTAUrfVccVR6KRBhCrrtEPA6sKbByl0",
    size="normal",
    title='登录 - 吾爱破解 - LCG - LSG |安卓破解|病毒分析|www.52pojie.cn',
    debug=True,
)
ret = cracker.crack()
print(ret)

cracker = ReCaptchaEnterpriseCracker(
    user_token="xxx",
    sitekey="6LcTV7IcAAAAAI1CwwRBm58wKn1n6vwyV1QFaoxr",
    referer="https://login.coinbase.com/",
    size="invisible",
    debug=True,
)

ret = cracker.crack()
print(ret)
```
