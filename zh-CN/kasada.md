------

[`返回首页`](../README.md)    [`上一页`](perimeterx.md)     [`下一页`](datadome.md)

## Kasada

### 价格说明
* `x-kpsdk-ct` 消耗 `1000` 点, 必传 `href`、`script_url`
* `x-kpsdk-cd` 消耗 `50` 点, 必传 `href`

### 说明
* 当看到请求头中有 `x-kpsdk-ct`、`x-kpsdk-cd` 时, 代表存在 `kasada` 验证
* x-kpsdk-ct 请保持 user_agent 一致, 结果可多次使用
* x-kpsdk-cd 仅可使用一次


### Request URL（POST）:

| 版本               | 接口地址                                                    |
|------------------|---------------------------------------------------------|
| `x-kpsdk-ct` | `http://api.nocaptcha.io/api/wanda/kasada/ct` |
| `x-kpsdk-cd` | `http://api.nocaptcha.io/api/wanda/kasada/cd` |

### Request Headers:

| 参数名            | 说明                 | 必须  |
|----------------|--------------------|-----|
| `User-Token`   | `用户密钥, 主页获取`       | `是` |
| `Content-Type` | `application/json` | `是` |
| `Developer-Id` | `开发者 ID, 开发者用户使用, 用户主页邀请链接的字符串(如 xxx/register?c=abcdef, 则 abcdef 为开发者 ID)`           | `否` |

### x-kpsdk-ct POST Data（JSON）:

| 参数名          | 类型        | 说明                                                                                                                                                             | 必须  |
|--------------|-----------|-----------------------------|-----|
| `href`    | `String`  | `触发 kasada 验证的页面地址`    | `是` |
| `script_url`    | `String`  | `p.js 结尾的脚本地址`    | `是` |
| `proxy`    | `String`  | `无需保持代理一致, 请使用海外代理, 格式请传 ip:port 或 usr:pwd@ip:port (如果有问题联系管理员)` | `是` |
| `user_agent` | `String`  | `自定义 user_agent, 请保持跟后续验证请求接口的 ua 一致`       | `否` |
| `timeout` | `Integer`  | `验证超时时间`       | `否` |

### x-kpsdk-cd POST Data（JSON）:

| 参数名          | 类型        | 说明                                                                                                                                                             | 必须  |
|--------------|-----------|-----------------------------|-----|
| `href`    | `String`  | `触发 kasada 验证的页面地址`    | `是` |
| `x-kpsdk-st`    | `Integer`  | `ct 接口返回的`    | `否` |

#### x-kpsdk-ct json 示例

```
{
    "href": "https://xxxxxx/",
    "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/123.0.0.0 Safari/537.36",
    "script_url": "https://mcprod.xxxx/149e9513-01fa-4fb0-aad4-566afd725d1b/2d206a39-8ed7-437e-a3be-862e0f06eea3/p.js",
    "proxy": "user:pass@ip:port",
}
```

#### x-kpsdk-cd json 示例

```
{
    "href": "https://xxxxxx/",
    "x-kpsdk-st": 1716775584627
}
```


### x-kpsdk-ct Response Data（JSON）:

| 参数名            | 类型        | 说明                            |
|----------------|-----------|-------------------------------|
| `status`       | `Integer` | `调用是否成功, 1 成功, 0 失败, 请使用该值判断` |
| `msg`          | `String`  | `调用结果中文说明`                    |
| `id`           | `String`  | `该次请求 id（唯一, 可用作后续记录查询）`      |
| `data['x-kpsdk-ct']`   | `String`  | `验证通过返回的可用 x-kpsdk-ct 参数, 可用于请求头中携带后续验证接口`    |
| `cost`         | `String`  | `验证耗时（毫秒）`                    |

### x-kpsdk-cd Response Data（JSON）:

| 参数名            | 类型        | 说明                            |
|----------------|-----------|-------------------------------|
| `status`       | `Integer` | `调用是否成功, 1 成功, 0 失败, 请使用该值判断` |
| `msg`          | `String`  | `调用结果中文说明`                    |
| `id`           | `String`  | `该次请求 id（唯一, 可用作后续记录查询）`      |
| `data['x-kpsdk-cd']`   | `String`  | `验证通过返回的可用 x-kpsdk-cd 参数, 可用于请求头中携带后续验证接口(仅可使用一次)`    |
| `cost`         | `String`  | `验证耗时（毫秒）`                    |


```
{
  "status": 1,
  "msg": "验证成功",
  "id": "639e056b-49bd-4895-94ab-68d59e00873e",
  "cost": "4635.12ms",
  "data": {
    "x-kpsdk-st": 1716775584627,
    "x-kpsdk-cd": '{"workTime":1716775584627,"id":"e7910834208cfc67a3340ff934bdb5b1","answers":[9,9],"duration":39,"d":1886,"st":1716775584814,"rst":1716775586700}', 
    "x-kpsdk-ct": "0aTWZlyuZj8xdBYhR3kCblUF4ljSLJNyk8LWEbjERVaayHo5DUU5VTEh7NWYldd5brUpu0KHOR38y2H6ObgzziQA28FKq4i5DX14UVmY93efP2ejJNYybda4Tmqc6v2EscnP4K3tEAxP1a7uUtPEXMuTYutYLhSrDxOEzJa"
  }
}
```

```
{
  "status": 1,
  "msg": "验证成功",
  "id": "639e056b-49bd-4895-94ab-68d59e00873e",
  "cost": "3.12ms",
  "data": {
    "x-kpsdk-cd": '{"workTime":1713525047123,"id":"2dfd146efb6b06495ae42e24457807ce","answers":[2,7],"duration":1663,"d":2177,"st":1713525049300,"rst":1713525051477}'
  }
}
```

### 调用示例

#### python

```shell
pip install -U pynocaptcha -i https://pypi.python.org/simple
```

```python
from pynocaptcha import KasadaCtCracker, KasadaCdCracker


cracker = KasadaCtCracker(
    user_token="xxx",
    href="https://xxxxxx/",
    script_url="https://mcprod.xxxxx/149e9513-01fa-4fb0-aad4-566afd725d1b/2d206a39-8ed7-437e-a3be-862e0f06eea3/p.js",
    user_agent="Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/124.0.0.0 Safari/537.36",
    proxy="user:pass@ip:port",
    debug=True,
)
ret = cracker.crack()
print(ret)


cracker = KasadaCdCracker(
    user_token="xxx",
    href="https://xxxxxx/",
    debug=True,
)
ret = cracker.crack()
print(ret)
```
