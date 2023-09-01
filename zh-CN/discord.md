------
[`返回首页`](../README.md)    [`上一页`](tls.md) [`English Version`](../en-US/discord.md)

## Discord
### 有问必答

* guild_id 和 guild_name 怎么选
    * 如果是邀请链接, 使用 guild_name. 主动搜索加群, 使用 guild_id.
* guild_name 样例
    * 如邀请链接为 https://discord.gg/fuxxx , 则 guild_name 为 fuxxx
* guild_id 样例
    * 搜索群组中返回的 id 字段 或 服务器地址 https://discord.com/channels/926691xxx/xxx, 则 guild_id 为 926691xxx
* 一些返回的情况
    * 401 token 过期(账号未登录)
    * 未知服务器 1、参数填错 2、可能非公开的服务器,使用 guild_name 参数加群
    * 其他情况根据返回的 message 判断

### Request URL（POST）:

| 版本               | 接口地址                                                    |
|------------------|---------------------------------------------------------|
| `guild（加群）` | `http://api.nocaptcha.io/api/wanda/discord/guild` |

### Request Headers:

| 参数名            | 说明                 | 必须  |
|----------------|--------------------|-----|
| `User-Token`   | `用户密钥, 主页获取`       | `是` |
| `Content-Type` | `application/json` | `是` |
| `Developer-Id` | `开发者 ID, 开发者用户使用, 用户主页邀请链接的字符串(如 xxx/register?c=abcdef, 则 abcdef 为开发者 ID)`           | `否` |

### POST Data（JSON）:

| 参数名          | 类型        | 说明                                                                                                                                                             | 必须  |
|--------------|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|-----|
| `authorization`           | `String`  | `账号登录凭证`                                                                                                                          | `是` |
| `guild_id`        | `String`  | `加群的 id（id 和群名二选一都可以）`       | `否` |
| `guild_name`        | `String`  | `群名（id 和群名二选一都可以）`       | `否` |
| `proxy`         | `String`  | `请求流程使用的代理, 支持 protocol: http/https/socks5, 无验证代理格式: {ip}:{port}, 有验证代理格式: {user}:{password}@{ip}:{port}, socsk5 代理需要加上代理协议: {protocol}://{ip}:{port}`   | `否` |

#### json 示例

```
{
    "authorization": "MTExNzI1NDQ3NzA2NjU0MzE5NQ.xxxxxx",
    "guild_id": '6456075xxx',
}
```

```
{
    "authorization": "MTExNzI1NDQ3NzA2NjU0MzE5NQ.xxxxxx",
    "guild_name": 'fuxxx',
}
```

### Response Data（JSON）:

| 参数名            | 类型        | 说明                            |
|----------------|-----------|-------------------------------|
| `status`       | `Integer` | `调用是否成功, 1 成功, 0 失败, 请使用该值判断` |
| `msg`          | `String`  | `调用结果中文说明`                    |
| `id`           | `String`  | `该次请求 id（唯一, 可用作后续记录查询）`      |
| `data`         | `String`  | `加群结果`    |
| `cost`         | `String`  | `验证耗时（毫秒）`                    |

```
{
    "status": 1,
    "msg": "验证成功",
    "id": "049bfae2-4e84-4f29-99aa-a33688991355",
    "cost": "18809.89ms",
    "data": `{"id":"645607528297922560","name":"...`,
}
```

### 调用示例

#### python

```shell
pip install -U pynocaptcha -i https://pypi.python.org/simple
```

```python
from pynocaptcha import DiscordCracker


cracker = DiscordCracker(
    user_token="xxx",
    authorization="MTExNzI1NDQ3NzA2NjU0MzE5NQ.GZoD5U.xxx",
    # guild_id='6456075xxx',
    guild_name='fuxxx',
    debug=True
)
ret = cracker.crack()
print(ret)
```
