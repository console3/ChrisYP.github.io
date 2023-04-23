------
[`返回首页`](../README.md)    [`上一页`](hcaptcha.md)

## Akamai

### Request URL（POST）:

| 版本               | 接口地址                                                    |
|------------------|---------------------------------------------------------|
| `v2（universal）` | `http://api.nocaptcha.io/api/wanda/akamai/v2` |

### Request Headers:

| 参数名            | 说明                 | 必须  |
|----------------|--------------------|-----|
| `User-Token`   | `用户密钥, 主页获取`       | `是` |
| `Content-Type` | `application/json` | `是` |
| `Developer-Id` | `开发者 ID, 开发者用户使用, 用户主页邀请链接的字符串(如 xxx/register?c=abcdef, 则 abcdef 为开发者 ID)`           | `否` |

### POST Data（JSON）:

| 参数名          | 类型        | 说明                                                                                                                                                             | 必须  |
|--------------|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|-----|
| `href`       | `String`  | `触发 akamai 验证的页面地址`                                                                                                                          | `是` |
| `api`        | `String`  | `akamai 提交 sensor_data 验证接口地址, 该地址过段时间会换, 建议获取该参数的最新值提交, 不提交该参数的话, 我们会帮你获取, 但是有些网站可能不太精准, 可能会验证失败`       | `否` |
| `telemetry`  | `Boolean` | `是否 headers 中的 telemetry 参数验证形式（如 https://api.maersk.com/ 接口的 akamai-bm-telemetry）, 默认 false`   | `否` |
| `user_agent` | `String`  | `请求流程使用 ua, 默认随机` | `否` |
| `internal`   | `Boolean` | `验证流程是否使用国内代理, 默认 true`                                                                                                                                        | `否` |

#### json 示例

```
{
	"href": "https://www.jetstar.com/",
	"api": "https://www.jetstar.com/3Fl6sx/QIvaPL/b/7Hf/iQxyLG8eyP4/acumkkpfYkV7EO/ZyMtejt5PAc/REZU/Jk85Pn4"
}
```

### Response Data（JSON）:

#### 提交验证（submit=true）

| 参数名            | 类型        | 说明                            |
|----------------|-----------|-------------------------------|
| `status`       | `Integer` | `调用是否成功, 1 成功, 0 失败, 请使用该值判断` |
| `msg`          | `String`  | `调用结果中文说明`                    |
| `id`           | `String`  | `该次请求 id（唯一, 可用作后续记录查询）`      |
| `data._abck`   | `String`  | `验证通过返回的可用的 _abck cookie, 可用于后续验证接口`    |
| `cost`         | `String`  | `验证耗时（毫秒）`                    |

```
{
	"status": 1,
	"msg": "验证通过",
	"id": "8a8f0778-da09-4eea-a32d-e3b508654ba6",
	"cost": "1984.57ms",
	"data": {
		"_abck": "2EDD22DB758F24695963E50D3C9A776F~0~YAAQx\/ggF8FPIJ2HAQAA8nKqrQmFx5H17A\/jMUd1alzWlJ6VXb6NGDhXkb\/1cJW+Bp0jJYvWVj8hQVc1vRKAiKQ1HLm0JIo8kg00KEBoAyRG+VZZPRV6ikricthJ69SlXF99wcHaHwx7mvDZdwwAtJBl+Fp2Kagx62AbUYZjEpc9aOCZ5KXBQhdrwCrzzXWsu5WEgmGovNqegFuIpW1ifsVPe13QSi8EjwF\/nsuJQShLeRgsls1JB0Trwx8Kg3qRFiL9g4rtAdeW8OwYQ4DXj3PoBU56G0I4oCrhm6urGs8wMaU3OdpW6SRBAV93r4FO6K+lmcm8BVcfYc70\/wVuEx3Fx0zpesE0fkdKC6N5c80AjVtSgJnDLFuShDnXo+wsWGROM1vxP7sC7N6raiSN66sX4UxGlkAJiCU=~-1~||1-hkqRyYlvue-1-10-1000-2||~-1"
	}
}
```

### CURL command:

```
curl 
    -H "User-Agent: python-requests/2.28.2" -H "Accept: */*" 
    -H "User-Token: xxx" 
    -H "Content-Type: application/json" 
    --data-binary "{\"href\": \"https://www.jetstar.com/\", \"api\": \"https://www.jetstar.com/3Fl6sx/QIvaPL/b/7Hf/iQxyLG8eyP4/acumkkpfYkV7EO/ZyMtejt5PAc/REZU/Jk85Pn4\"}" 
    --compressed "http://api.nocaptcha.io/api/wanda/akamai/v2"
```

### 调用示例

#### python

```shell
pip install -U pynocaptcha -i https://pypi.python.org/simple
```

```python
from pynocaptcha import AkamaiV2Cracker


cracker = AkamaiV2Cracker(
    user_token="xxx",
    sitekey='a9b5fb07-92ff-493f-86fe-352a2803b3df',
    referer="https://discord.com/channels/253581140072464384/357581480110850049",
    rqdata="RRZ5RNoOL4uNPvEp0yB+bMPkBe2lUiM7p4u5lMAVUC9UBmzxJqdDDpGMrcDNApg/DDAQNIIlwEn2dLr7dZMg32I2bi523ZRfkAKpKxxg1sqnVW0xR9Y9ZCcwv54EiHeEqQ+iipixAVozAb6LjtwzNm2H9L15iSN8QfVrcp0Z",
    debug=True,
    # proxy=proxy,
)
ret = cracker.crack()
print(ret)
```
