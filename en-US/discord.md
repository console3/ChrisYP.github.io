------
[`Back to homepage`](./en.md)  [`中文文档`](../zh-CN/discord.md)

## Discord
### Frequently Asked Questions

* How to choose between guild_id and guild_name?
    * If it's an invite link, use guild_name. For actively searching and joining a guild, use guild_id.
* Example of guild_name:
    * If the invite link is https://discord.gg/fuxxx, then guild_name is fuxxx.
* Example of guild_id:
    * ID field returned in the guild search or server address https://discord.com/channels/926691xxx/xxx, then guild_id is 926691xxx.
* Some return scenarios:
    * 401 token expired (not logged in).
    * Unknown server: 1. Parameter mistake 2. It might be a private server, join the guild using the guild_name parameter.
    * For other cases, refer to the returned message.

### Request URL (POST):

| Version              | API Address                                         |
|------------------|---------------------------------------------------------|
| `guild (Join Guild)` | `http://api.nocaptcha.io/api/wanda/discord/guild` |

### Request Headers:

| Parameter Name  | Description                                          | Required |
|----------------|------------------------------------------------------|----------|
| `User-Token`   | `User secret key, obtained from homepage`            | `Yes`    |
| `Content-Type` | `application/json`                                  | `Yes`    |
| `Developer-Id` | `Developer ID used by developer users. If invite link on user homepage is like xxx/register?c=abcdef, then abcdef is the Developer ID` | `No`  |

### POST Data (JSON):

| Parameter Name  | Type         | Description                                                                                                                  | Required |
|--------------|------------|-------------------------------------------------------------------------------------------------|----------|
| `authorization`      | `String`   | `Account login credentials`                                                                                                 | `Yes`    |
| `guild_id`           | `String`   | `ID to join the guild (choose either id or guild name)`                                                                     | `No`     |
| `guild_name`         | `String`   | `Guild name (choose either id or guild name)`                                                                               | `No`     |
| `proxy`              | `String`   | `Proxy used in the request process. Supports protocols: http/https/socks5. Format without authentication: {ip}:{port}. With authentication: {user}:{password}@{ip}:{port}. For socks5 proxy, add the protocol: {protocol}://{ip}:{port}` | `No`     |

#### JSON Examples:

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

### Response Data (JSON):

| Parameter Name  | Type        | Description                                     |
|----------------|------------|------------------------------------------------|
| `status`       | `Integer`  | `Call success indicator, 1 for success, 0 for failure. Use this value for judgment` |
| `msg`          | `String`   | `Chinese explanation of the result`            |
| `id`           | `String`   | `ID of this request (unique, can be used for subsequent record queries)` |
| `data`         | `String`   | `Guild joining result`                         |
| `cost`         | `String`   | `Validation time (in milliseconds)`            |

```
{
    "status": 1,
    "msg": "Verification successful",
    "id": "049bfae2-4e84-4f29-99aa-a33688991355",
    "cost": "18809.89ms",
    "data": `{"id":"645607528297922560","name":"...`,
}
```

### Call Example:

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

Note: I translated the "Chinese explanation of the result" in the Response Data as it was in the original, but you may want to ensure that the API actually returns English messages when used in an English context.
