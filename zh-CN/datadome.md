------

[`返回首页`](../README.md)    [`上一页`](kasada.md)    [`下一页`](shape.md)

## Datadome

### 说明
* 当看到 `cookies` 中有 `datadome`, 代表存在 `datadome` 验证, 有以下两种情况
    * `无感模式`: 
    ![无感验证码样例](/images/datadome/interstitial.png)
    * `滑块验证码`:
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
    href="https://rendezvousparis.hermes.com/client/register",
    proxy="user:pass@ip:port",
    debug=True,
)
ret = cracker.crack()
print(ret)
```
